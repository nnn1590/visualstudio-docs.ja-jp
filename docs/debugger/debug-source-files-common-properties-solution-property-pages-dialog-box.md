---
title: ソース ファイル/共通のプロパティ/ソリューション プロパティ ページをデバッグします。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631ec8ed4f6b5cd410b3af51c55fa87935b9cddf
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263139"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>[デバッグ ソース ファイル] ([ソリューション プロパティ ページ] ダイアログ ボックス - [共通プロパティ])
このプロパティ ページでは、ソリューションのデバッグ時にデバッガーによってソース ファイルが検索される場所を指定します。

 **[デバッグのソース ファイル]** プロパティ ページを開くには、**ソリューション エクスプローラー**でソリューションを右クリックし、ショートカット メニューの **[プロパティ]** をクリックします。 **[共通プロパティ]** フォルダーを展開し、 **[デバッグのソース ファイル]** ページをクリックします。

 **ソース コードを含むディレクトリ**ソリューションのデバッグ時に、デバッガーによってソース ファイルが検索するディレクトリの一覧が含まれています。 指定されたディレクトリのサブディレクトリも検索されます。

 **以下のソース ファイルを探さない**デバッガーによる読み取りが必要ないファイルの名前を入力します。 デバッガーは、上で指定したディレクトリのいずれかでこれらのファイルを見つけた場合、それを無視します。 デバッグ中に **[ソース ファイルの検索]** ダイアログ ボックスが表示されたときに **[キャンセル]** をクリックすると、検索中のファイルがこのリストに追加され、そのファイルの検索が中止されます。

## <a name="see-also"></a>関連項目

- [デバッガーのセキュリティ](../debugger/debugger-security.md)
- [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)