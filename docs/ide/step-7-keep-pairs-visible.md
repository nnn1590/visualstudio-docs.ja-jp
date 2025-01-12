---
title: '手順 7: ペアの表示の維持'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5194d3925393228d951f35a966dff8fd620ea924
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416530"
---
# <a name="step-7-keep-pairs-visible"></a>手順 7: ペアの表示の維持
プレーヤーが一致しないアイコンのペアをクリックしている限り、ゲームは正常に動作します。 しかし、プレーヤーが一致するペアをクリックしたらどうなるでしょうか。 (<xref:System.Windows.Forms.Timer.Start> メソッドを使用して) タイマーを有効にしてアイコンを非表示にする代わりに、ゲームでは、それ自体をリセットすることで、クリックされた 2 つのラベルの色はリセットせずに、`firstClicked` 参照変数および `secondClicked` 参照変数を使用してラベルを追跡しないようにする必要があります。

## <a name="to-keep-pairs-visible"></a>ペアの表示を維持するには

1. 次の `if` ステートメントを、`label_Click()` イベント ハンドラー メソッドの最後の近くの、タイマーを開始するステートメントのすぐ上に追加します。 プログラムにステートメントを追加しながら、コードを注意して見てください。 コードのしくみを検討します。

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

     追加した `if` ステートメントの 1 行目は、プレーヤーがクリックした 1 つ目のラベルのアイコンが 2 つ目のラベルのアイコンと同じかどうかをチェックします。 アイコンが同じである場合、プログラムは、中かっこ内 (Visual C# の場合) または `if` ステートメント内 (Visual Basic の場合) の 3 つのステートメントを実行します。 最初の 2 つのステートメントは、`firstClicked` 参照変数および `secondClicked` 参照変数をリセットし、これらがラベルを追跡しないようにします (これら 2 つのステートメントが、タイマーの <xref:System.Windows.Forms.Timer.Tick> イベント ハンドラーからのものであることを認識できます)。3 つ目のステートメントは `return` ステートメントであり、メソッドの残りのステートメントを実行せずにスキップするようプログラムに指示します。

     Visual C# でプログラミングしている場合、一部のコードでは 1 つの等号 (`=`) が使用されているのに対し、他のステートメントでは 2 つの等号 (`==`) が使用されているのに気付きます。 ある場所では `=` が使用されているのに対し、他の場所では `==` が使用されている理由について考えます。

     違いを示す適切な例を以下に示します。 `if` ステートメントのかっこ内のコードを注意して見てください。

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     次に、コード ブロック内の、`if` ステートメントの後の最初のステートメントを注意して見てください。

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     これら 2 つうち最初のステートメントは、2 つのアイコンが同じであるかどうかをチェックします。 2 つの値を比較しているため、Visual C# のプログラムでは、等値演算子 `==` を使用しています。 2 つ目のステートメントは、実際の値の変更 (*代入*と呼ばれます) を行い、`firstClicked` 参照変数を `null` に設定してリセットします。 代わりに代入演算子 `=` が使用されているのはそのためです。 Visual C# では、`=` を使用して値を設定し、`==` を使用して値を比較します。 Visual Basic では、変数の代入と比較の両方に `=` を使用します。

2. プログラムを保存したら実行し、フォームでアイコンのクリックを開始します。 一致しないペアをクリックした場合、タイマーの Tick イベントがトリガーされ、両方のアイコンが非表示になります。 一致するペアをクリックした場合、新しい `if` ステートメントが実行され、return ステートメントにより、メソッドでタイマーを開始するコードがスキップされるため、次の図に示すように、アイコンが表示されたままになります。

     ![このチュートリアルで作成するゲーム](../ide/media/express_finishedgame.png)
アイコンのペアが表示された **[マッチング ゲーム]**

## <a name="to-continue-or-review"></a>続行または確認するには

- チュートリアルの次の手順に進むには、「[手順 8:プレーヤーが勝利したかどうかを確認するメソッドの追加](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)」を参照してください。

- チュートリアルの前の手順に戻るには、「[手順 6:タイマーの追加](../ide/step-6-add-a-timer.md)」を参照してください。
