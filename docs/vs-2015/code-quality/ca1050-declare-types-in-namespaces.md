---
title: CA1050:名前空間で型を宣言 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f13684df70db7026e874bc8edb6282faca2cf98d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200544"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050:名前空間で型を宣言します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Category|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型は、名前付きの名前空間のスコープ外に定義されます。

## <a name="rule-description"></a>規則の説明
 名前空間名の競合を回避して、オブジェクト階層内の関連する種類を整理する方法として、型が宣言されます。 任意の名前付き名前空間の外部にある型は、コードでは参照できない、グローバル名前空間でです。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、名前空間の型を配置します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 このルールから警告を抑制することはありませんが、アセンブリは他のアセンブリと共に使用しない場合、これに安全です。

## <a name="example"></a>例
 次の例では、正しくない、名前空間の外部宣言の型を持つライブラリと名前空間で宣言されている同じ名前を持つ型を示します。

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>例
 次のアプリケーションでは、既に定義されているライブラリを使用します。 名前空間の外部で宣言された型が作成されるときに注意してください。 名前`Test`名前空間で修飾されていません。 またにアクセスする、`Test`入力`Goodspace`、名前空間名が必要です。

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]
