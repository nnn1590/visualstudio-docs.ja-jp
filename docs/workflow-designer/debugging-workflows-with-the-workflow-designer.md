---
title: ワークフロー デザイナーを使用したワークフローのデバッグ
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1270e57ae6c9235311569c04ebb982157ea3b608
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949748"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>ワークフロー デザイナーでワークフローをデバッグします。

**ワークフロー デザイナー**ワークフローとカスタム アクティビティをデバッグする機能を提供します。 プロセスと動作は、既定の Visual Studio デバッガーに似ています。

## <a name="invoke-the-workflow-debugger"></a>ワークフロー デバッガーを起動します。

ほとんどの場合、他の Visual Studio プログラミング言語で書かれたプログラムをデバッグするときと同じようにして、ワークフローをデバッグすることができます。 ワークフロー デバッガーは、次の方法で開始できます。

- 選択**プロセスにアタッチ**上、**デバッグ**をワークフロー インスタンスの実行中のホスト プロセスを選択します。 この手順は、マネージド コードのホスト プロセスへのアタッチと同じです。

- キーを押して**F5**ワークフローのインスタンスの実行を開始するか、ブレークポイントにヒットした後に実行を続けます。

- リモート デバッグを使用します。 リモート デバッグの使用方法の詳細については、次を参照してください。[方法。リモート デバッグを有効にする](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100))します。

   > [!NOTE]
   > ワークフロー アプリケーションは、x86 を対象とする場合のアーキテクチャと、Visual Studio がリモート コンピューターにインストールされているか、ワークフロー アプリケーションのターゲットがに変更された場合を除き、リモートデバッグは機能しませんし、64ビットオペレーティングシステムを実行するマシンでホストされます。**任意の CPU**します。

## <a name="step-through-code"></a>コードのステップ実行

- **ステップ イン**:キーを押してアクティビティにステップ イン**F11**します。 デバッガーは、任意の定義済みハンドラーにステップ インします。 ハンドラーが定義されていない場合は、アクティビティをステップ オーバーするか、(他のアクティビティを含む) 複合アクティビティの場合には、実行される最初のアクティビティにステップ インします。

- **ステップ アウトします。** キーを押してアクティビティからステップ**Shift**+**F11**します。 アクティビティからステップ アウトすると、現在のアクティビティとすべての兄弟アクティビティは最後まで実行されます。 その後、デバッガーは現在のアクティビティの親で停止します。 コード ハンドラーからステップ アウトするとき、デバッガーはハンドラーに関連付けられたアクティビティで停止します。

- **ステップ オーバー**:キーを押してステップ アクティビティ オーバー **F10**します。 複合アクティビティをステップ オーバーするときは、デバッガーが、複合アクティビティの最初の実行可能な子で停止します。 複合ではないアクティビティ (<xref:System.Activities.Statements.Assign> アクティビティなど) をステップ オーバーするときは、デバッガーが、そのアクティビティおよび関連するハンドラーを実行して、次のアクティビティで停止します。 実行されるアクティビティが複合アクティビティの最後の子アクティビティである場合、デバッガーは、それを実行した後に親アクティビティで停止します。

## <a name="debug-with-f5"></a>F5 を押すとデバッグします。

ワークフロー コンソール アプリケーションをビルドしている場合が単にキーを押して**F5**には、アプリケーションやワークフローのデバッグを開始します。 独自のアクティビティ ライブラリを構築する場合は、スタートアップ プロジェクトとして実行可能なホスト アプリケーションを指定する必要があります。 スタートアップ プロジェクトを設定する**ソリューション エクスプ ローラー**をホストのプロジェクト名を右クリックし、**スタートアップ プロジェクトとして設定**します。