---
title: CA1043:インデクサーは整数または文字列引数を使用して、|Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 643d91ad51e9511bbd4440d2f84fbd441c768a53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143213"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043:インデクサーには整数または文字列引数を使用します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Category|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型には、他にもインデックスの型を使用するパブリックまたはプロテクトのインデクサーが含まれています。 <xref:System.Int32?displayProperty=fullName>、 <xref:System.Int64?displayProperty=fullName>、 <xref:System.Object?displayProperty=fullName>、または<xref:System.String?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 インデクサー、つまり、インデックス付きプロパティは、インデックスの整数または文字列型を使用する必要があります。 これらの型は、通常データ構造のインデックス作成に使用され、ライブラリのユーザビリティを向上させます。 使用、<xref:System.Object>型がデザイン時に特定の整数または文字列型を指定できない場合に限定する必要があります。 設計では、インデックスの他の種類が必要とする場合は、型は、論理データ ストアを表すかどうかを再確認します。 論理データ ストアを表さない場合は、メソッドを使用します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、integer または string 型では、インデックスを変更またはインデクサーではなく、メソッドを使用します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 非標準のインデクサーの必要性を慎重に検討した後にのみこの規則による警告を抑制します。

## <a name="example"></a>例
 次の例では、インデクサーを使用する、<xref:System.Int32>インデックス。

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA 1023:インデクサーを多次元することはできません。](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA 1024:適切な場所のプロパティを使用します。](../code-quality/ca1024-use-properties-where-appropriate.md)
