---
title: CA2213:破棄可能なフィールドは破棄されなければなりません
ms.date: 05/14/2019
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b38157fcc23561b47a919151aa78a71f98b3909b
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805007"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213:破棄可能なフィールドは破棄されなければなりません

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

実装する型<xref:System.IDisposable?displayProperty=fullName>も実装する型のフィールドを宣言<xref:System.IDisposable>します。 <xref:System.IDisposable.Dispose%2A>フィールドのメソッドを呼び出さない、<xref:System.IDisposable.Dispose%2A>宣言型のメソッド。

## <a name="rule-description"></a>規則の説明

型は、そのすべてのアンマネージ リソースを破棄します。 破棄可能な型かどうかを確認する ca 2213 チェックの規則 (つまり、1 つを実装する<xref:System.IDisposable>)`T`フィールドを宣言して`F`破棄可能な型のインスタンスである`FT`します。 各フィールドの`F`メソッドまたは包含する型の初期化子内でローカルで作成されたオブジェクトが割り当てられている`T`、ルールの呼び出しを検索しようとしました。`FT.Dispose`します。 このルールによって呼び出されるメソッドを検索する`T.Dispose`と 1 レベル下 (によって呼び出されるメソッドによって呼び出されるメソッドは、 `T.Dispose`)。

> [!NOTE]
> 以外の[特殊なケース](#special-cases)、ルール、含む型のメソッドと初期化子内でローカルで作成された破棄可能なオブジェクトに割り当てられているフィールドに対してのみ ca 2213 が起動します。 オブジェクトが作成または型の外部で割り当てられたかどうか`T`ルールは発生しません。 これには、含んでいる型が、オブジェクトを破棄する責任を所有しない場合のノイズが削減されます。

### <a name="special-cases"></a>特殊なケース

ルール ca 2213 が割り当てられているオブジェクトがローカルで作成されていない場合でもも、次の種類のフィールドの起動できます。

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

これらの型のいずれかのオブジェクトをコンス トラクターに渡すと、フィールドに割り当てることを示します、*所有権の譲渡を dispose*新しく構築された型にします。 つまり、新しく構築された型では、オブジェクトの破棄を担当ようになりました。 オブジェクトは破棄されません ca 2213 の違反が発生します。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するには、呼び出す<xref:System.IDisposable.Dispose%2A>を実装する型のフィールドで<xref:System.IDisposable>します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

場合、この規則による警告を抑制しても安全です。

- フラグが設定された型のフィールドによって保持されているリソースを解放するの責任ではありません (つまり、型はありません*所有権を dispose*)
- 呼び出し<xref:System.IDisposable.Dispose%2A>ルール チェックよりも深い呼び出しレベルで発生します。

## <a name="example"></a>例

次のスニペットは、型`TypeA`を実装する<xref:System.IDisposable>します。

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

次のスニペットは、型`TypeB`フィールドを宣言することで ca 2213 の規則に違反する`aFieldOfADisposableType`破棄可能な型として (`TypeA`) を呼び出さない<xref:System.IDisposable.Dispose%2A>フィールド。

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>関連項目

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose パターン](/dotnet/standard/design-guidelines/dispose-pattern)