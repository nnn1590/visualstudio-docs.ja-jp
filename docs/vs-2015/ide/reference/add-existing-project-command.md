﻿---
title: 既存プロジェクトの追加コマンド | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4778efc4a50ceb63e72d4283644537345510e833
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194959"
---
# <a name="add-existing-project-command"></a>AddExistingProject コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

既存のプロジェクトを現在のソリューションに追加します。  
  
## <a name="syntax"></a>構文  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 任意。 ソリューションに追加するプロジェクトの完全なパスとプロジェクト名 (拡張子付き)。  
  
 `filename` 引数にスペースが含まれる場合は、引用符で囲む必要があります。  
  
 ファイル名が指定されていない場合、ファイルを開くダイアログ ボックスが表示され、ユーザーがプロジェクトを選択できます。  
  
## <a name="remarks"></a>解説  
 オート コンプリートでは、入力された正しいパスとファイル名の検索を試みます。  
  
## <a name="example"></a>例  
 この例では、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] プロジェクトの TestProject1 を現在のソリューションに追加します。  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>関連項目
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
