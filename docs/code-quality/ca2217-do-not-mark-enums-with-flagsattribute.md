---
title: CA2217:列挙型を FlagsAttribute に設定しません
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 377188183acdaa9aa86ae3344c8f6d5727b82ccc
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546835"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217:列挙型を FlagsAttribute に設定しません

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Category|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

列挙体はで<xref:System.FlagsAttribute>マークされ、列挙体の2つまたは複数の定義済みの値の組み合わせではない1つ以上の値を含んでいます。

既定では、この規則は外部から参照できる列挙のみを参照しますが、これは[構成可能](#configurability)です。

## <a name="rule-description"></a>規則の説明

列挙体で定義<xref:System.FlagsAttribute>されている各値が、定義された値の2つまたは組み合わせの累乗である場合にのみ、列挙が存在する必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を修正するには、 <xref:System.FlagsAttribute>列挙体からを削除します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合

この規則による警告は抑制しないでください。

## <a name="configurability"></a>かつ

この規則を[FxCop アナライザー](install-fxcop-analyzers.md) (レガシ分析ではなく) から実行している場合は、ユーザー補助に基づいて、この規則を実行するコードベースの部分を構成できます。 たとえば、パブリックでない API サーフェイスに対してのみルールを実行するように指定するには、プロジェクトの editorconfig ファイルに次のキーと値のペアを追加します。

```ini
dotnet_code_quality.ca2217.api_surface = private, internal
```

このオプションは、この規則、すべての規則、またはこのカテゴリのすべての規則 (使用状況) に対してのみ構成できます。 詳細については、「 [FxCop アナライザーの構成](configure-fxcop-analyzers.md)」を参照してください。

## <a name="examples"></a>使用例

次のコードは、値 3 `Color`を含む列挙型を示しています。 3は2の累乗ではなく、定義された値の組み合わせでもありません。 列挙型をで<xref:System.FlagsAttribute>マークすることはできません。 `Color`

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

次のコードは、で`Days` <xref:System.FlagsAttribute>マークされるの要件を満たす列挙型を示しています。

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>関連するルール

[CA1027FlagsAttribute で列挙をマークする](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>関連項目

- <xref:System.FlagsAttribute?displayProperty=fullName>
