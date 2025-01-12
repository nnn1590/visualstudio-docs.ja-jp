---
title: CA2109:表示するイベント ハンドラーをレビューします |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9cdf4777aa9ec0222656ac02376c5343d2138c0d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687384"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109:表示するイベント ハンドラーを確認します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクトのイベント ハンドラー メソッドが検出されました。

## <a name="rule-description"></a>規則の説明
 外部から見えるイベント処理メソッドは、レビューを必要とするセキュリティ上の問題を表示します。

 イベント ハンドラー メソッドは、絶対に必要な場合を除き公開しないでください。 ハンドラーとイベントのシグネチャが一致する限り、任意のイベントにイベント ハンドラーを公開されているメソッドを呼び出すデリゲート型を追加できます。 イベントは、任意のコードから発生する可能性があると、ボタンのクリックしてなどのユーザー アクションへの応答コードを信頼性の高いシステムによって頻繁に発生します。 イベント処理メソッドへのセキュリティ チェックを追加してもコードからメソッドを呼び出すイベント ハンドラーを登録します。

 要求では、イベント ハンドラーで呼び出されたメソッドを確実に保護できません。 セキュリティ確認要求呼び出し履歴上の呼び出し元を調べることで、信頼されていない呼び出し元からコードを保護します。 イベント ハンドラーのメソッドの実行時に、イベントにイベント ハンドラーを追加するコードは呼び出し履歴上に必ずしも存在ではありません。 そのため、呼び出し履歴可能性がありますが信頼性の高いしか呼び出し元イベント ハンドラー メソッドが呼び出されたときにします。 これにより、要求が成功するイベント ハンドラー メソッドで行われます。 また、メソッドが呼び出されたときに、要求されたアクセス許可をアサートする可能性があります。 これらの理由から、この規則違反を修正しない場合のリスクをイベント処理メソッドを確認した後評価のみできます。 コードを確認するときは、次の問題を考慮してください。

- イベント ハンドラーは、危険性またはアクセス許可のアサートまたはアンマネージ コード アクセス許可などの悪用可能である操作を実行しますか。

- 高いだけでいつでも実行できるため、コードとの間のセキュリティの脅威とは、スタックに呼び出し元が信頼されているでしょうか。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、方法を確認し、次の評価。

- ことができます、イベント処理メソッドをパブリックではないでしょうか。

- イベント ハンドラーからのすべての危険な機能を移動できますか。

- 他の方法では、セキュリティ確認要求が課される場合のこれを実現することができますですか。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 このルールからコードにセキュリティ上の脅威がないかどうかを確認する注意が必要なセキュリティ レビュー後にのみの警告を抑制します。

## <a name="example"></a>例
 次のコードでは、悪意のあるコードで誤用されることができます、イベント処理メソッドを示します。

 [!code-csharp[FxCop.Security.EventSecLib#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.EventSecLib/cs/FxCop.Security.EventSecLib.cs#1)]

## <a name="see-also"></a>関連項目
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
 [セキュリティ要求](https://msdn.microsoft.com/324c14f8-54ff-494d-9fd1-bfd20962c8ba)
