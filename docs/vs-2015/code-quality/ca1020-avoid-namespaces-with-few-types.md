---
title: CA1020:いくつかの種類と名前空間の回避 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8c94cf09b43eb09482be4a30d9f0b9206678c4dc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435831"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020:型をほとんど含まない名前空間を使用しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 グローバル名前空間以外の名前空間には、5 未満の型が含まれています。

## <a name="rule-description"></a>規則の説明
 各名前空間には、論理的な少ない名前空間で型を配置する正当な理由が存在することを確認します。 名前空間には、ほとんどのシナリオで同時に使用される型を含める必要があります。 自分のアプリケーションが相互に排他的な場合は、個別の名前空間で型を配置する必要があります。 たとえば、<xref:System.Web.UI>名前空間には、Web アプリケーションで使用される型が含まれています。 および<xref:System.Windows.Forms>名前空間で使用される型が含まれています[!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)]-ベースのアプリケーション。 両方の名前空間では、ユーザー インターフェイスの側面を制御する型がある、でも、これらの型では、同じアプリケーションで使用する設計されていません。 そのため、個別の名前空間内にあります。 注意名前空間の組織も役に立ちます機能の探索可能性が増えるためです。 名前空間の階層を確認するには、ライブラリのコンシューマーは、機能を実装する型を特定できる必要があります。

> [!NOTE]
> このガイドラインに準拠する他の名前空間には、デザイン時の型とアクセス許可しないマージする必要があります。 メインの名前空間の下に独自の名前空間に属しているこれらの型と名前空間の末尾に`.Design`と`.Permissions`、それぞれします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するのには、単一の名前空間にはいくつかの種類を含む名前空間を結合するしてみてください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 名前空間には、他の名前空間の型で使用される型が含まれていない場合、このルールから警告を抑制しても安全です。
