---
title: CA1721:プロパティ名は get メソッドと同一にすることはできません
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 44028caf027191846fa653db06abbe4027fdde8d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547096"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721:プロパティ名は get メソッドと同一にすることはできません

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Category|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

メンバーの名前は、' Get ' で始まり、それ以外の場合はプロパティの名前と一致します。 たとえば、' GetColor ' という名前のメソッドと ' Color ' という名前のプロパティがある型には、規則違反が発生します。

既定では、この規則は外部から参照できるメンバーとプロパティのみを参照しますが、これは[構成可能](#configurability)です。

## <a name="rule-description"></a>規則の説明

"Get" メソッドとプロパティには、それぞれの機能を明確に区別する名前を指定しなければなりません。

名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 この一貫性により、新しいソフトウェアライブラリを学習するために必要な時間が短縮され、マネージコードの開発に関する専門知識を持つユーザーがライブラリを開発したことによる信頼度が向上します。

## <a name="how-to-fix-violations"></a>違反の修正方法

名前を変更して、先頭に ' Get ' が付いているメソッドの名前と一致しないようにします。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合

この規則による警告は抑制しないでください。

> [!NOTE]
> この警告は、IExtenderProvider インターフェイスの実装によって "Get" メソッドが発生した場合に除外される可能性があります。

## <a name="configurability"></a>かつ

この規則を[FxCop アナライザー](install-fxcop-analyzers.md) (レガシ分析ではなく) から実行している場合は、ユーザー補助に基づいて、この規則を実行するコードベースの部分を構成できます。 たとえば、パブリックでない API サーフェイスに対してのみルールを実行するように指定するには、プロジェクトの editorconfig ファイルに次のキーと値のペアを追加します。

```ini
dotnet_code_quality.ca1721.api_surface = private, internal
```

このオプションは、この規則、すべての規則、またはこのカテゴリのすべての規則 (名前付け) に対してのみ構成できます。 詳細については、「 [FxCop アナライザーの構成](configure-fxcop-analyzers.md)」を参照してください。

## <a name="example"></a>例

次の例には、この規則に違反するメソッドとプロパティが含まれています。

[!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
[!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>関連するルール

- [CA1024適切な場所にプロパティを使用する](../code-quality/ca1024-use-properties-where-appropriate.md)