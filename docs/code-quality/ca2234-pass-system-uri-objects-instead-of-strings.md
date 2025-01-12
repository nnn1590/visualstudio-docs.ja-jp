---
title: CA2234:文字列の代わりに System.Uri オブジェクトを渡します
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 74484c5f014c9a677c321a0d9fed649f016ea3c9
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546885"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234:文字列の代わりに System.Uri オブジェクトを渡します

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Category|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

名前に "uri"、"uri"、"urn"、"urn"、"url"、または "url" が含まれ、メソッドの宣言する型にパラメーターを<xref:System.Uri?displayProperty=fullName>持つ対応するメソッドのオーバーロードが含まれているメソッドに対して、呼び出しが行われます。

既定では、この規則は外部から参照できるメソッドと型のみを参照しますが、これは[構成可能](#configurability)です。

## <a name="rule-description"></a>規則の説明

パラメーター名は camel 形式の表記規則に基づいてトークンに分割され、各トークンは、"uri"、"Uri"、"urn"、"Urn"、"url"、"Url" に等しいかどうかを確認します。 一致するものがある場合、パラメーターは URI (uniform resource identifier) を表していると見なされます。 URI の文字列表現は解析エラーやエンコーディング エラーが発生しやすく、セキュリティ上の脆弱性の原因となる場合があります。 クラス<xref:System.Uri>は、これらのサービスを安全かつ安全な方法で提供します。 URI の表現に関してのみ異なる2つのオーバーロードのいずれかを選択する場合、ユーザーは引数を<xref:System.Uri>受け取るオーバーロードを選択する必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を修正するには、 <xref:System.Uri>引数を受け取るオーバーロードを呼び出します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合

文字列パラメーターが URI を表していない場合は、この規則からの警告を抑制することが安全です。

## <a name="configurability"></a>かつ

この規則を[FxCop アナライザー](install-fxcop-analyzers.md) (レガシ分析ではなく) から実行している場合は、ユーザー補助に基づいて、この規則を実行するコードベースの部分を構成できます。 たとえば、パブリックでない API サーフェイスに対してのみルールを実行するように指定するには、プロジェクトの editorconfig ファイルに次のキーと値のペアを追加します。

```ini
dotnet_code_quality.ca2234.api_surface = private, internal
```

このオプションは、この規則、すべての規則、またはこのカテゴリのすべての規則 (使用状況) に対してのみ構成できます。 詳細については、「 [FxCop アナライザーの構成](configure-fxcop-analyzers.md)」を参照してください。

## <a name="example"></a>例

次の例は、規則に`ErrorProne`違反するメソッドと、 <xref:System.Uri>オーバーロードを正しく呼び出す`SaferWay`メソッドを示しています。

[!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
[!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
[!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## <a name="related-rules"></a>関連するルール

- [CA1057文字列 URI のオーバーロードは、システムの Uri のオーバーロードを呼び出します](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
- [CA1056URI プロパティを文字列にすることはできません](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054URI パラメーターを文字列にすることはできません](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA1055URI 戻り値を文字列にすることはできません](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)