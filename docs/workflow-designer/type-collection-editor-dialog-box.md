---
title: ワークフロー デザイナーの [型コレクション エディター] ダイアログ ボックス
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 191635364c445bc3959ee2f5f63c7c72c71f171d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433930"
---
# <a name="type-collection-editor-dialog-box"></a>[型コレクション エディター] ダイアログ ボックス

**型コレクション エディター**既知の型に追加する ダイアログ ボックスを使用、**送信**と**受信**アクティビティ。 ジェネリック型引数に追加するこのダイアログ ボックスを使用しても、 **InvokeMethod**アクティビティ。 使用すると、**送信**と**受信**既知の型を追加するアクティビティ、**型コレクション エディター**  ダイアログ ボックスに追加すると、一意である型が必要です。 重複する型が追加され、クリックして、変更をコミット**OK**、エラー メッセージが返されます。 使用すると、 **InvokeMethod** 、ジェネリック型引数を追加するアクティビティ、**型コレクション エディター**ダイアログ ボックスでは重複する型を追加します。

詳細については、次を参照してください。[既知の型のデータ コントラクト](/dotnet/framework/wcf/feature-details/data-contract-known-types)します。

次の表に、ユーザー インターフェイス (UI) 要素の**型コレクション** ダイアログ ボックス。

|UI 要素|説明|
|-|-----------------|
|**型リスト**|追加または削除された型のリスト。|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Send アクティビティおよび Receive アクティビティの [型コレクション エディター] を表示するには

1. 選択、**送信**または**受信**デザイン ビューでのアクティビティ。

2. キーを押して**F4**を起動、**プロパティ**ウィンドウ。

3. **プロパティ**ウィンドウで、省略記号ボタンをクリックして、 **KnownTypes**プロパティ。

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>InvokeMethod アクティビティの [型コレクション エディター] を表示するには

1. 選択、 **InvokeMethod**デザイン ビューでのアクティビティ。

2. キーを押して**F4**を起動、**プロパティ**ウィンドウ。

3. **プロパティ**ウィンドウで、省略記号ボタンをクリックして、 **GenericTypeArguments**プロパティ。