---
title: ロード テストのブラウザー テスト ミックス
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, web browser types
- load tests, scenarios
- load tests, adding browsers
- load tests, removing browsers
ms.assetid: 47f981d9-3038-45cc-a486-82b9daf9a9a1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6694b850c7fee73e4b0891d37891e44a85f142f2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918250"
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>テスト ミックスを編集して、ロード テスト シナリオに含める Web ブラウザーの種類を指定する

*ブラウザー ミックス*を使用すると、ロード テスト シナリオで負荷をより現実的にシミュレートできます。 単一の Web ブラウザーではなく、複数の種類の Web ブラウザーから構成されるブラウザー ミックスを使用して、負荷が生成されます。 アプリケーションで使用される Web ブラウザーに、より近い状態でシミュレートできます。

ブラウザー ミックスでは、ロード テスト シナリオで仮想ユーザーが特定の Web ブラウザーの種類を実行する確率を指定します。 ロード テストを作成する際に、複数の Web ブラウザーから負荷が生成されていることをシミュレートする必要がある場合があります。 用意されている Web ブラウザーのセットから特定の種類の Web ブラウザーをミックスに追加すると、Web パフォーマンス テストによって送信される各 HTTP 要求に、選択した Web ブラウザーに関連付けられたヘッダーのセットが追加されます。

ブラウザー ミックスは、他のミックス オプションと同様に機能します。 Web ブラウザーの種類は、ブラウザー ミックスに基づいて仮想ユーザーにランダムに関連付けられます。 そのユーザーのテストは、ミックスで指定した確率に基づいて、特定の Web ブラウザーで実行されます。

ブラウザー ミックスを指定した後で、ミックスに対して Web ブラウザーの種類を追加したり、削除したりできます。 また、ミックス コントロールを使用して、ブラウザー ミックスの配分を変更することもできます。 ミックス コントロールを使用すると、シナリオでのブラウザーの配分を簡単に調整できます。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-browsers-to-a-scenario"></a>シナリオに新しいブラウザーを追加する

### <a name="to-add-new-browsers-to-a-scenario"></a>シナリオに新しいブラウザーを追加するには

1. シナリオのブラウザー ミックスを指定するときに、 **[追加]** を選択します。

     新しいブラウザー エントリがグリッドに追加されます。

    > [!NOTE]
    > **[ブラウザー ミックスの編集]** ダイアログ ボックスを表示するには、既存のシナリオを右クリックし、 **[ブラウザー ミックスの編集]** を選択します。

2. **[ブラウザーの種類]** 列で、新しいエントリの矢印を選択し、目的のブラウザーの種類を選択します。

3. (省略可能) ミックス コントロールを調整して、テストの配分を指定します。

4. ブラウザーの追加が終了したら、 **[OK]** を選択します。

## <a name="remove-browsers-from-a-scenario"></a>シナリオからブラウザーを削除する

### <a name="to-remove-browsers-from-a-scenario"></a>シナリオからブラウザーを削除するには

1. ロード テストを開きます。

2. ブラウザーを削除するシナリオを右クリックし、 **[ブラウザー ミックスの編集]** を選択します。

     **[ブラウザー ミックスの編集]** ダイアログ ボックスが表示されます。

3. グリッドでブラウザーを選択し、 **[削除]** を選択します。

4. (省略可能) ミックス コントロールを調整して、テストの配分を指定します。

5. ブラウザーの削除が終了したら、 **[OK]** を選択します。

## <a name="about-the-mix-control"></a>ミックス コントロールについて

ミックス コントロールを使用すると、ロード テストのシナリオで、テスト、ブラウザーの種類、またはネットワークの種類の間で配分する負荷の割合を調整できます。 割合の値はスライダーを動かして調整します。 ブラウザーの種類のミックスの調整では、ロード テストのシナリオで仮想ユーザーが特定の種類のブラウザーを実行する確率を指定します。

スライダーを動かすと、利用できるすべての項目の割合の値が変更されます。 項目が複数ある場合、追加または削除した分が他の項目に均等に配分されます。 この動作は、オーバーライドできます。 特定の項目のロック列のチェック ボックスをオンにすると、その項目に指定された割合の値がロックされます。 この状態でスライダーを動かすと、追加または削除した分はロックされていない残りの項目のみに適用されます。

**[均等化]** ボタンは、割合の値をすべての項目に均等に割り当てる場合に使用します。 たとえば、項目が 3 つある場合、 **[均等化]** を選択することで割合の値が、34、33、および 33 に設定されます。

> [!WARNING]
> **[均等化]** ボタンは、ロックされているあらゆる項目をオーバーライドします。

また、スライダーを使用する代わりに、割合の値を **[%]** 列に直接入力することもできます。 割合の値を直接入力した場合、他の項目は自動的には調整されません。

> [!NOTE]
> 合計が 100% にならない場合、または **[%]** 列に入力された割合の値が小数値の場合、スライダーは無効になります。

割合の値を手動で入力する場合は、すべての項目の合計が 100% になるようにしてください。 ミックスを保存するとき、合計が 100% ではない場合、割合の値をそのままで受け入れるか、または戻って調整するかのどちらかを選択するよう要求されます。 そのままで受け入れることを選択した場合は、100% になるよう比例配分されます。  たとえば、項目が 2 つあって、手動でそれぞれ 80% と 40% に設定されている場合、最初の項目は 66.67% (80/120) に、2 番目の項目は 33.33% (40/120) に、それぞれ設定されます。

## <a name="see-also"></a>関連項目

- [ロード テスト シナリオの編集](../test/edit-load-test-scenarios.md)