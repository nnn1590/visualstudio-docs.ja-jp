---
title: 'チュートリアル 2: クイズの作成 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2a87a192f7a14a4d59a5ca5cff15bc62abbdefc6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443283"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>チュートリアル 2: クイズを作成します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルでは、クイズの受け手が制限時間内にランダムに表示される 4 つの計算問題に答えるクイズを作成します。 以下の方法について説明します。  
  
- `Random` クラスを使用して乱数を生成します。  
  
- **Timer** コントロールを使用して特定の時点で発生するようにイベントをトリガーします。  
  
- `if else` ステートメントを使用してプログラム フローを制御します。  
  
- コードで基本的な算術演算を実行します。  
  
  完了すると、クイズは数値が異なることを除いて次の図のようになります。  
  
  ![4 つの問題がある計算クイズ](../ide/media/express-finishedquiz.png "Express_FinishedQuiz")  
  このチュートリアルで作成するクイズ  
  
  クイズの完全バージョンをダウンロードするには、「[Complete Math Quiz tutorial sample](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c)」(計算クイズのチュートリアルの完全なサンプル) を参照してください。  
  
> [!NOTE]
> このチュートリアルでは、Visual C# と Visual Basic の両方が取り上げられているため、使用しているプログラミング言語固有の情報に注意してください。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[手順 1: プロジェクトの作成とフォームへのラベルの追加](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|最初にプロジェクトを作成し、プロパティを変更し、`Label` コントロールを追加します。|  
|[手順 2: ランダムな加算問題の作成](../ide/step-2-create-a-random-addition-problem.md)|加算問題を作成し、`Random` クラスを使用して乱数を生成します。|  
|[手順 3: カウントダウン タイマーの追加](../ide/step-3-add-a-countdown-timer.md)|クイズに制限時間を設定できるようにカウントダウン タイマーを追加します。|  
|[手順 4: CheckTheAnswer() メソッドの追加](../ide/step-4-add-the-checktheanswer-parens-method.md)|クイズの受け手が問題の正しい解答を入力したかどうかを確認するメソッドを追加します。|  
|[手順 5: NumericUpDown コントロールの Enter イベント ハンドラーの追加](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|クイズを受けやすくするイベント ハンドラーを追加します。|  
|[手順 6: 減算問題の追加](../ide/step-6-add-a-subtraction-problem.md)|乱数を生成し、タイマーを使用し、正しい解答を確認する減算問題を追加します。|  
|[手順 7: 乗算問題と除算問題の追加](../ide/step-7-add-multiplication-and-division-problems.md)|乱数を生成し、タイマーを使用し、正しい解答を確認する乗算問題および除算問題を追加します。|  
|[手順 8: クイズのカスタマイズ](../ide/step-8-customize-the-quiz.md)|色の変更、ヒントの追加など、その他の機能を試します。|
