---
title: '手順 8: クイズのカスタマイズ |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 75bde59c6e4b61c2775f188383fc9058a6c31242
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178547"
---
# <a name="step-8-customize-the-quiz"></a>手順 8: クイズをカスタマイズする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

チュートリアルの最後の部分では、クイズをカスタマイズする方法を説明して、既に学習した内容を掘り下げます。 たとえば、プログラムで解答が決して分数にはならないランダムな除算問題を作成する方法を考えてみます。 さらに詳しく学習するには、`timeLabel` コントロールの色を変更したり、クイズの受け手にヒントを示したりしてみてください。  
  
### <a name="to-customize-the-quiz"></a>クイズをカスタマイズするには  
  
- クイズの残り時間が 5 秒になったら、**BackColor** プロパティを設定して、**timeLabel** コントロールの色を赤に変更します (`timeLabel.BackColor = Color.Red;`)。 クイズが終了したら元の色に戻します。  
  
- NumericUpDown コントロールに正しい解答が入力されたら、サウンドを再生してクイズの受け手にヒントを示します (クイズの受け手がコントロールの値を変更するたびに実行される、各コントロールの `ValueChanged()` イベントのイベント ハンドラーを記述する必要があります)。  
  
### <a name="to-continue-or-review"></a>続行または確認するには  
  
- クイズの完全バージョンをダウンロードするには、「[Complete Math Quiz tutorial sample](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c)」(計算クイズのチュートリアルの完全なサンプル) を参照してください。  
  
- 次のチュートリアルに進むには、「[チュートリアル 3:絵合わせゲームの作成](../ide/tutorial-3-create-a-matching-game.md)です。  
  
- チュートリアルの前の手順に戻るには、「[手順 7:乗算と除算問題の追加](../ide/step-7-add-multiplication-and-division-problems.md)します。
