﻿---
title: スニペットのトラブルシューティング | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 61f1a623d5ee5edee376819ad6c385aead5003f8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62429009"
---
# <a name="troubleshooting-snippets"></a>スニペットのトラブルシューティング
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense コード スニペットに関する問題は、通常は 2 つの問題が原因で発生します。1 つはスニペット ファイルの破損、もう 1 つはスニペット ファイルの不適切な内容です。  
  
## <a name="common-problems"></a>一般的な問題  
  
### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>スニペットをファイル エクスプローラーから Visual Studio のソース ファイルにドラッグできない  
  
- スニペット ファイルの XML が破損している可能性があります。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の **[XML エディター]** を使用すると、XML 構造の問題を特定できます。  
  
- スニペット ファイルがスニペット スキーマに準拠していない可能性があります。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の **[XML エディター]** を使用すると、XML 構造の問題を特定できます。  
  
### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>コードに強調表示されていないコンパイラ エラーがある  
  
- プロジェクト参照がない可能性があります。 スニペットについてのドキュメントを調べてください。 参照がコンピューター上にない場合は、インストールする必要があります。 スニペットを挿入すると、必要な参照がプロジェクトに追加されます。 スニペットに参照情報がない場合は、スニペットの作成者にエラーとして報告できます。  
  
- 変数が未定義の可能性があります。 スニペット内の未定義の変数は強調表示されます。 そうなっていない場合は、スニペットの作成者にエラーとして報告できます。  
  
## <a name="see-also"></a>関連項目  
 [コード スニペット](../ide/code-snippets.md)
