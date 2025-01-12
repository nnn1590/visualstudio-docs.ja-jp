﻿---
title: ListThreads コマンド | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90aff3fb3d3cbb596708bde1db8ff171198a5a60
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199109"
---
# <a name="list-threads-command"></a>ListThreads コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

現在のプログラムのスレッド一覧を表示します。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>引数  
 `index`  
 任意。 スレッドをインデックスで選択して、現在のスレッドにします。  
  
## <a name="remarks"></a>解説  
 指定した場合、`index` 引数により、示されたスレッドが現在のスレッドとしてマークされます。 一覧の現在のスレッドの横にはアスタリスク (*) が表示されます。  
  
## <a name="example"></a>例  
  
```  
>Debug.ListThreads   
```  
  
## <a name="see-also"></a>関連項目  
 [ListCallStack コマンド](../../ide/reference/list-call-stack-command.md)   
 [逆アセンブリの一覧表示コマンド](../../ide/reference/list-disassembly-command.md)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
