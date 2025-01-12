---
title: '方法: ASP.NET ベースのワークフロー (レガシ) のデバッグ |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a8fc6c951f1da3fc37fe8e1189a3ec8de9609a48
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68144652"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>方法: ASP.NET ベースのワークフローをデバッグする (レガシ)
このトピックでは、従来の [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]で、[!INCLUDE[wf](../includes/wf-md.md)] または [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] を対象とする [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] ベースの [!INCLUDE[wfd1](../includes/wfd1-md.md)] アプリケーションをデバッグする方法について説明します。  
  
 ワークフローをそのホストとなるプロセスにアタッチすることにより、ASP.NET で開始される従来のワークフロー、または Web サービスとして公開される従来のワークフローをデバッグすることができます。  
  
### <a name="to-debug-an-aspnet-based-workflow"></a>ASP.NET ベースのワークフローをデバッグするには  
  
1. 設定して、ASP.NET アプリケーションのデバッグを有効にする**デバッグ = true** web.config ファイルにします。  
  
2. ワークフロー ライブラリをスタートアップ プロジェクトとして設定し、ワークフローのブレークポイントを設定します。  
  
3. ワークフロー プロジェクトのプロパティの既定の Web ページの URL を入力**デバッグ**オプション**外部 URL にブラウザーを開始**テキスト ボックス。  
  
4. 選択**プロセスにアタッチ**上、**デバッグ**メニュー。  
  
5. アタッチするプロセスの選択、**選択可能なプロセス**一覧。  
  
     ワークフローのホストとなる w3wp.exe、webdev.webserver、または aspnet_wp プロセスにアタッチします。  
  
6. クリックして**選択**横に、 **Attach To**テキスト ボックス。  
  
     **コードの種類の選択** ダイアログ ボックスが表示されます。  
  
7. 選択**コードの種類をデバッグ**選択**ワークフロー**します。  
  
8. **[OK]** をクリックします。  
  
9. **[アタッチ]** をクリックします。  
  
10. ブラウザで既定の Web ページを開いて、ワークフローを開始します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Debugger for Windows Workflow Foundation (レガシ) の起動](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [方法: ワークフロー (レガシ) にブレークポイントを設定](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)