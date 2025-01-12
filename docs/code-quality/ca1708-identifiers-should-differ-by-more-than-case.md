---
title: CA1708:識別子は、大文字と小文字の区別以外にも相違していなければなりません
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5098e2feadc6d67c466e31ab19d059ac70c7d833
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547400"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708:識別子は、大文字と小文字の区別以外にも相違していなければなりません

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Category|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

2つの型、メンバー、パラメーター、または完全修飾名前空間の名前は、小文字に変換されるときは同じです。

既定では、この規則は外部から参照できる型、メンバー、および名前空間のみを参照しますが、これは[構成可能](#configurability)です。

## <a name="rule-description"></a>規則の説明

名前空間、型、メンバー、およびパラメーターの各識別子は、大文字/小文字以外のみでは区別できません。共通言語ランタイムを対象とする言語は、大文字と小文字を区別する必要はないためです。 たとえば、は[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 、広く使用されている大文字と小文字を区別しない言語です。

この規則は、パブリックに表示できるメンバーにのみ適用されます。

## <a name="how-to-fix-violations"></a>違反の修正方法

大文字と小文字を区別せずに他の識別子と比較する場合は、一意の名前を選択します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合

この規則による警告は抑制しないでください。 このライブラリは、.NET で使用可能なすべての言語で使用できない場合があります。

## <a name="configurability"></a>かつ

この規則を[FxCop アナライザー](install-fxcop-analyzers.md) (レガシ分析ではなく) から実行している場合は、ユーザー補助に基づいて、この規則を実行するコードベースの部分を構成できます。 たとえば、パブリックでない API サーフェイスに対してのみルールを実行するように指定するには、プロジェクトの editorconfig ファイルに次のキーと値のペアを追加します。

```ini
dotnet_code_quality.ca1708.api_surface = private, internal
```

このオプションは、この規則、すべての規則、またはこのカテゴリのすべての規則 (名前付け) に対してのみ構成できます。 詳細については、「 [FxCop アナライザーの構成](configure-fxcop-analyzers.md)」を参照してください。

## <a name="example-of-a-violation"></a>違反の例

次の例は、このルールの違反を示しています。

[!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>関連するルール

- [CA1709識別子は正しく使用する必要があります](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)