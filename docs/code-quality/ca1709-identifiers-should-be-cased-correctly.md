---
title: CA1709:識別子では、大文字と小文字が正しく区別されなければなりません
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 864918b7ce394e9f096c6fa9dea9389957983177
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921779"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709:識別子では、大文字と小文字が正しく区別されなければなりません

|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Category|Microsoft.Naming|
|互換性に影響する変更点|中断-アセンブリ、名前空間、型、メンバー、およびパラメーターで発生した場合。<br /><br /> 非ブレーク-ジェネリック型パラメーターで発生した場合。|

## <a name="cause"></a>原因

識別子の名前の大文字と小文字が正しくありません。

\- または -

識別子の名前に2文字の頭字語が含まれ、2番目の文字が小文字になっています。

\- または -

識別子の名前には、3文字以上の大文字の頭字語が含まれています。

## <a name="rule-description"></a>規則の説明

名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 この一貫性により、新しいソフトウェアライブラリに必要な学習曲線が減少し、マネージコードの開発に関する専門知識を持つユーザーによってライブラリが開発されたという自信が高まります。

慣例として、パラメーター名は camel 形式を使用し、名前空間、型、およびメンバー名は Pascal 形式を使用します。 Camel 形式の名前では、最初の文字は小文字で、名前に含まれる残りの単語の最初の文字は大文字になります。 Camel 形式の名前の例と`packetSniffer`し`ioFile`て`fatalErrorCode`、、、があります。 Pascal 形式の名前では、最初の文字は大文字になり、名前の残りの単語の最初の文字は大文字になります。 Pascal 形式の名前の例と`PacketSniffer`し`IOFile`て`FatalErrorCode`、、、があります。

このルールでは、大文字小文字に基づいて名前が単語に分割され、2文字の単語が、"In" や "My" などの一般的な2文字の単語の一覧と照合されます。 一致するものが見つからない場合、単語は頭字語であると見なされます。 さらに、この規則では、名前の先頭に4文字の大文字が含まれている場合に、名前の末尾に3つの大文字が含まれていることを前提としています。

慣例として、2文字の頭字語ではすべて大文字が使用され、3文字以上の頭字語では Pascal 形式が使用されます。 次の例では、この名前付け規則を使用します。' DB '、' CR '、' Cpa '、および ' Ecma '。 次の例は、規則に違反しています。' Io '、' XML '、' DoD '、パラメーター以外の名前 (' xp '、' cpl ') の場合。

"ID" は特殊なケースで、この規則に違反する原因になります。 ' Id ' は頭字語ではありませんが、' id ' の省略形です。

## <a name="how-to-fix-violations"></a>違反の修正方法

大文字と小文字が正しくなるように名前を変更します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合

独自の名前付け規則がある場合、または識別子が会社またはテクノロジの名前などの適切な名前を表す場合は、この警告を抑制することが安全です。

また、コード分析カスタム辞書に特定の用語、略語、および頭字語を追加することもできます。 カスタム辞書に指定された用語は、このルールの違反を引き起こすことはありません。 詳細については、「[方法 :コード分析辞書](../code-quality/how-to-customize-the-code-analysis-dictionary.md)をカスタマイズします。

## <a name="related-rules"></a>関連するルール

[CA1708識別子の大文字と小文字の区別が異なる場合](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)