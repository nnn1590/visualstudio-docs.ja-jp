---
title: '手順 11: プログラムの実行し、その他の機能 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d5a40d6aa7dca8b14210ea85b8428f4d315cd70b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679538"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>手順 11: プログラムを実行し、その他の機能を試す
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

プログラムが完成し、実行する準備が整いました。 プログラムを実行して PictureBox の背景色を設定できます。 さらに詳しく学習するには、フォームの色の変更、ボタンとチェック ボックスのカスタマイズ、フォームのプロパティの変更などを行って、プログラムを変更してみてください。  
  
 サンプルの完全バージョンをダウンロードするには、「[Complete Picture Viewer tutorial sample](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8)」 (画像ビューアーのチュートリアルの完全なサンプル) を参照してください。  
  
 ![ビデオへのリンク](../data-tools/media/playvideo.gif "PlayVideo")このトピックのビデオ版について、次を参照してください。[チュートリアル 1。Visual basic - ビデオ 5 ピクチャ ビューアーの作成](http://go.microsoft.com/fwlink/?LinkId=205216)または[チュートリアル 1。C# - ビデオ 5 ピクチャ ビューアーの作成](http://go.microsoft.com/fwlink/?LinkId=205206)です。 これらのビデオでは、旧バージョンの Visual Studio を使用しているため、一部のメニュー コマンドやその他のユーザー インターフェイス要素が若干異なります。 ただし、概念および手順は、現在のバージョンの Visual Studio でも同様です。  
  
### <a name="to-run-your-program-and-set-the-background-color"></a>プログラムを実行して背景色を設定するには  
  
1. F5 キーを押すか、メニュー バーで **[デバッグ]** 、 **[デバッグ開始]** の順にクリックします。  
  
2. ピクチャを開く前に、 **[Set the background color]** ボタンをクリックします。 **[色]** ダイアログ ボックスが表示されます。  
  
     ![[色] ダイアログ ボックス](../ide/media/express-colordialog.png "Express_ColorDialog")  
[色] ダイアログ ボックス  
  
3. 色を選択して PictureBox の背景色を設定します。 `backgroundButton_Click()` メソッドを詳しく調べて動作を確認します。  
  
    > [!NOTE]
    > ピクチャは、 **[ファイルを開く]** ダイアログ ボックスに URL を貼り付けることでインターネットから読み込むことができます。 背景色の表示を確認するには、背景が透明な画像を探してみてください。  
  
4. **[Clear the picture]** ボタンをクリックして、ピクチャが消去されることを確認します。 次に、 **[閉じる]** ボタンをクリックしてプログラムを終了します。  
  
### <a name="to-try-other-features"></a>その他の機能を試すには  
  
- **BackColor** プロパティを使用して、フォームとボタンの色を変更します。  
  
- **Font** プロパティと **ForeColor** プロパティを使用して、ボタンとチェック ボックスをカスタマイズします。  
  
- フォームの **FormBorderStyle** プロパティと **ControlBox** プロパティを変更します。  
  
- フォームの **AcceptButton** プロパティと **CancelButton** プロパティを使用して、ユーザーが Enter キーまたは Esc キーを押したときに自動的にそれらのボタンが選択されるようにします。 **[ファイルを開く]** ダイアログ ボックスが、ユーザーが Enter キーを押したときに開き、Esc キーを押したときに閉じるようにプログラムを設定します。  
  
### <a name="to-continue-or-review"></a>続行または確認するには  
  
- Visual Studio でのプログラミングの詳細については、「[プログラミングの概念](https://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6)」を参照してください。  
  
- Visual Basic の詳細については、「[Visual Basic でのアプリケーションの開発](https://msdn.microsoft.com/library/1e1c0c81-6d95-4167-a98b-44b1efb6d25f)」を参照してください。  
  
- Visual C# の詳細については、「[Introduction to the C# Language and the .NET Framework](https://msdn.microsoft.com/library/0a2dff4e-cd84-42ff-8141-e89889b24081)」 (C# 言語と .NET Framework の概要) を参照してください。  
  
- 次のチュートリアルに進むには、「[チュートリアル 2:クイズの作成](../ide/tutorial-2-create-a-timed-math-quiz.md)です。  
  
- チュートリアルの前の手順に戻るには、「[手順 10:その他のボタンおよびチェック ボックスをコードの記述](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)します。
