---
title: エラー :DNS では、ターゲット コンピューターに正しく構成されているがあることを確認します |。Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d23d13d5dfcd0dc0426f72ea87659fc0c85b323b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562423"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>エラー :ターゲット コンピューターで DNS が正しく構成されていることを確認してください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

リモート デバッグを行おうとすると、次のエラー メッセージが表示される場合があります。  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 このエラーは、ターゲット コンピューターが Visual Studio デバッガー ホスト コンピューターの名前を解決できない場合に発生します。 ターゲット コンピューターの DNS 設定を確認します。  
  
- Windows 8.1、Vista、Windows 7、Windows Server 2012、Windows Server 2008、または Windows Server 2008 R2 で DNS 設定を表示する方法については、**[スタート]** メニューの **[ヘルプとサポート]** を選択し、「**TCP/IP 設定の変更**」を検索してください。  
  
- 詳細については、[Microsoft Windows Web サイト](http://go.microsoft.com/fwlink/?LinkId=252720)にアクセスし、「**TCP/IP 設定の変更**」を検索してください。  
  
  DNS に関する問題を解決できない場合は、別のコンピューターでリモート デバッガーを実行してみてください。 このエラーは、リモート デバッガーをローカル システム アカウントまたはネットワーク サービス アカウントで実行した場合のみ発生します。 リモート デバッガーを別のアカウントで実行する場合は、DNS を必要としない NTLM 認証を使用できます。 . 手順については、次を参照してください。[エラー。ターゲット コンピューターに Visual Studio リモート デバッガー サービスは、このコンピューターに接続できない](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)します。
