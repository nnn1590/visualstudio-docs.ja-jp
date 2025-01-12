---
title: 'クイック スタート: 最初の Vue.js アプリを作成する'
description: このクイック スタートでは、Node.js Tools for Visual Studio を利用し、Visual Studio で Vue.js アプリを作成します
ms.custom: seodec18
ms.date: 09/24/2018
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 28e86068b2255d1796363405c0231c1fb6bdd480
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226497"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>クイック スタート: Visual Studio を使用して初めての Vue.js アプリを作成する

ここでは 5 分から 10 分で Visual Studio 統合開発環境 (IDE) の概要を示し、シンプルな Vue.js Web アプリケーションを作成して実行ます。

> [!IMPORTANT]
> この記事には、Visual Studio 2017 バージョン 15.8 以降で使用できる Vue.js テンプレートが必要です。

## <a name="prerequisites"></a>必須コンポーネント

* Visual Studio および Node.js 開発ワークロードをインストールしている必要があります。

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 をまだインストールしていない場合は、 [Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/)  ページに移動し、無料試用版をインストールしてください。
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 をまだインストールしていない場合は、 [Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/)  ページに移動し、無料試用版をインストールしてください。
    ::: moniker-end

    Visual Studio は既にあり、ワークロードだけをインストールする必要がある場合は、**[ツール]** > **[ツールと機能を取得]** に移動すると、Visual Studio インストーラーが開きます。 **[Node.js 開発]** ワークロードを選択し、**[変更]** を選択します。

    ![VS インストーラーの Node.js ワークロード](../ide/media/quickstart-nodejs-workload.png)

* Node.js ランタイムをインストールしている必要があります。

    インストールされていない場合は、LTS バージョンを [Node.js](https://nodejs.org/en/download/) Web サイトからインストールしてください。 一般に、Visual Studio はインストール済みの Node.js ランタイムを自動的に検出します。 インストールされているランタイムが検出されない場合は、プロパティ ページで、インストールされているランタイムを参照するプロジェクトを構成することができます (プロジェクトを作成した後、プロジェクト ノードを右クリックして、**[プロパティ]** を選択します)。

## <a name="create-a-project"></a>プロジェクトを作成する

まず、Vue.js Web アプリケーション プロジェクトを作成します。

1. Node.js ランタイムがまだインストールされていない場合は、LTS バージョンを [Node.js](https://nodejs.org/en/download/) Web サイトからインストールしてください。

    一般に、Visual Studio はインストール済みの Node.js ランタイムを自動的に検出します。 インストールされているランタイムが検出されない場合は、プロパティ ページで、インストールされているランタイムを参照するプロジェクトを構成することができます (プロジェクトを作成した後、プロジェクト ノードを右クリックして、**[プロパティ]** を選択します)。

1. Visual Studio を開きます。

1. 新しいプロジェクトを作成します。

    ::: moniker range=">=vs-2019"
    **Esc** キーを押してスタート ウィンドウを閉じます。 **Ctrl + Q** キーを押して検索ボックスを開き、「**Basic Vue.js**」と入力してから、**[基本的な Vue.js Web アプリケーション]** (JavaScript または TypeScript のいずれか) を選択します。 ダイアログ ボックスが表示されたら、**basic-vuejs** という名前を入力し、**[作成]** を選択します。

    ![Vue.js テンプレート](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。 **[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウで、**[JavaScript]** または **[TypeScript]** を展開して、**[Node.js]** を選択します。 中央のウィンドウで、**[Basic Vue.js Web アプリケーション]** を選択し、名前に「**basic-vuejs**」と入力してから、**[OK]** を選択します。

    ![Vue.js テンプレート](../javascript/media/vuejs-template.png)
    ::: moniker-end
    **[基本的な Vue.js Web アプリケーション]** プロジェクト テンプレートが表示されない場合は、**Node.js 開発**ワークロードを追加する必要があります。 手順について詳しくは、「[必須コンポーネント](#prerequisites)」をご覧ください。

    Visual Studio によって新しいプロジェクトが作成されます。 ソリューション エクスプローラーで新しいプロジェクトが開きます (右ウィンドウ)。

1. アプリケーションに必要な npm パッケージのインストールの進捗状況は [出力] ウィンドウで確認できます (下ウィンドウ)。

1. ソリューション エクスプローラーで **npm** ノードを開き、必要なすべての npm パッケージが存在するかどうかを確認します。

    不足しているパッケージ (感嘆符のアイコン) がある場合は、**npm** ノードを右クリックして、**[不足している npm パッケージをインストールする]** を選択します。

## <a name="explore-the-ide"></a>IDE を探索する

1. 右ウィンドウの**ソリューション エクスプローラー**を見てください。

     ![Vue.js ソリューション](../javascript/media/vuejs-solution.png)

   - **[新しいプロジェクト]** ダイアログ ボックスに指定した名前が使用され、太字で強調表示されているのがあなたのプロジェクトです。 ディスク上では、このプロジェクトは、プロジェクト フォルダーの *.njsproj* ファイルに該当します。

   - 最上位レベルにあるのは、ソリューションです。既定では、名前はプロジェクトと同じです。 ディスク上の *.sln* ファイルで表されるソリューションは、1 つ以上の関連プロジェクトのコンテナーです。

   - **npm** ノードには、インストールされているすべての npm パッケージが表示されます。 npm ノードを右クリックし、ダイアログ ボックスを使用して npm パッケージを検索し、インストールすることができます。

2. コマンド プロンプトから npm パッケージをインストールするか、Node.js コマンドを実行する場合は、プロジェクト ノードを右クリックし、**[ここでコマンド プロンプトを開く]** を選択します。

## <a name="add-a-vue-file-to-the-project"></a>.vue ファイルをプロジェクトに追加する

1. ソリューション エクスプローラーで、*src/components* フォルダーなどのフォルダーを右クリックし、**[追加]** > **[新しい項目]** の順に選択します。

1. **[JavaScript Vue 単一ファイル コンポーネント]** または **[TypeScript Vue 単一ファイル コンポーネント]** を選択し、**[追加]** をクリックします。

    Visual Studio によって新しいファイルがプロジェクトに追加されます。

## <a name="build-the-project"></a>プロジェクトをビルドする

1. (TypeScript プロジェクトのみ) Visual Studio から **[ビルド]**、**[ソリューションのクリーン]** の順に選択します。

1. 次に、**[ビルド]**、**[ソリューションのビルド]** の順に選択し、プロジェクトをビルドします。 **[出力]** ウィンドウでビルド結果を確認し、**[出力元]** の一覧から **[ビルド]** を選択します。

    Vue.js プロジェクト テンプレートでは、ビルド後イベントを構成することで、`build` npm スクリプトが使用されます。 この設定を変更する場合、エクスプローラーからプロジェクト ファイル (*\<プロジェクト名\>.njsproj*) を開き、次のコード行を検索します。

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>アプリケーションの実行

1. **Ctrl** キーを押しながら **F5** キーを押すか、**[デバッグ]、[デバッグなしで開始]** の順に選択してアプリケーションを実行します。

   コンソールに "*Starting Development Server*" というメッセージが表示されます。

   その後、アプリがブラウザーで開きます。

   ![ブラウザーで実行されている Vue.js アプリ](../javascript/media/vuejs-running-app.png)

1. Web ブラウザーを閉じます。

このクイック スタートは完了しました。 Visual Studio IDE と Vue.js について少しはご理解いただけたかと思います。 機能についてさらに深く理解したい場合は、目次の**チュートリアル** セクションに示されているチュートリアルを続行してください。

## <a name="next-steps"></a>次の手順

- [Node.js と Express のチュートリアル](../nodejs/tutorial-nodejs.md)を読む
- [Node.js と React のチュートリアル](/visualstudio/javascript/tutorial-nodejs-with-react-and-jsx)を読む
- [アプリを Linux App Service にデプロイする](../javascript/publish-nodejs-app-azure.md)