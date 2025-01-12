---
title: SharePoint ソリューションの作成 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2b3138e148ea44371c7bd9b5fb82c583cd00e832
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436426"
---
# <a name="create-sharepoint-solutions"></a>SharePoint ソリューションを作成します。
  SharePoint Designer の代わりに Visual Studio で SharePoint アプリケーションを作成できます。 Visual Studio には、高度なデバッグ ツール、IntelliSense、ステートメント入力候補、プロジェクト テンプレートなど、迅速な SharePoint 開発を促進する機能が用意されています。 さらに、Visual Studio では、高度な .NET Framework ベースのツールと言語も活用されています。 SharePoint プロジェクトは Visual Basic または Visual C# を使用して開発できます。また、SharePoint 用アプリのプロジェクトは JavaScript を使用して開発できます。

 SharePoint 2013 アドインと SharePoint アドインについては、「 [SharePoint 2013](https://products.office.com/previous-versions/microsoft-sharepoint-2013) 」および「 [SharePoint アプリの作成](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)」を参照してください。

> [!NOTE]
> 新しい [SharePoint アドイン モデル](/sharepoint/dev/sp-add-ins/sharepoint-add-ins) を使用してユーザーにとっての SharePoint の操作感を拡張する方法をご覧ください。 これらのアドインのフットプリントは、SharePoint ソリューションと比較して非常に小さく、その作成には、HTML5、JavaScript、CSS3、XML など、ほぼすべての Web プログラミング テクノロジを使用できます。

|||
|-|-|
|![ドキュメント](../sharepoint/media/vs-icon-documentation.gif "ドキュメント")|**ドキュメント**<br /><br /> -   [開始&#40;Visual Studio での SharePoint 開発&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)<br />-   [SharePoint ソリューションを開発します。](../sharepoint/developing-sharepoint-solutions.md)<br />-   [SharePoint ソリューションをローカライズします。](../sharepoint/localizing-sharepoint-solutions.md)<br />-   [ビルドし、SharePoint ソリューションのデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)<br />-   [パッケージと SharePoint の配置のソリューション](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)<br />-   [Visual Studio の SharePoint ツールを拡張します。](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)|
|![ドキュメント](../sharepoint/media/vs-icon-documentation.gif "ドキュメント")|**おすすめのタスク**<br /><br /> -   [チュートリアル: For SharePoint のサイト列、コンテンツの種類、および一覧を作成します。](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)<br />-   [方法: イベント レシーバーを作成します。](../sharepoint/how-to-create-an-event-receiver.md)<br />-   [方法: BDC モデルを作成します。](../sharepoint/how-to-create-a-bdc-model.md)<br />-   [方法: SharePoint Web パーツを作成します。](../sharepoint/how-to-create-a-sharepoint-web-part.md)<br />-   [方法: SharePoint アプリケーション ページまたは web パーツのユーザー コントロールの作成します。](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|
|![チュートリアル](../sharepoint/media/vs-icon-walkthroughs.gif "チュートリアル")|**チュートリアル**<br /><br /> -   [SharePoint 開発のチュートリアル](../sharepoint/sharepoint-development-walkthroughs.md)|
|![コード サンプル](../sharepoint/media/vs-icon-codesamples.gif "コード サンプル")|**コード サンプル**<br /><br /> -   [SharePoint 開発のサンプル](../sharepoint/sharepoint-development-samples.md)<br />-   [SharePoint 開発者向けダウンロード](/sharepoint/dev/)|
|![トレーニング](../sharepoint/media/vs-icon-training.gif "トレーニング")|**トレーニング**<br /><br /> -   [SharePoint の開発者向けトレーニング](/sharepoint/dev/)|
|![フォーラム](../sharepoint/media/vs-icon-forums.gif "フォーラム")|**フォーラム**<br /><br /> -   [Visual Studio を使用した SharePoint 開発](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vssharepointdevelopment)<br />-   [SharePoint 2010](https://social.msdn.microsoft.com/Forums/sharepoint/home?category=sharepoint2010,sharepoint)|
|![トレーニング](../sharepoint/media/vs-icon-training.gif "トレーニング")|**ブログ**<br /><br /> -   [Visual Studio SharePoint 開発チームのブログ](https://blogs.msdn.microsoft.com/vssharepointtoolsblog/)|
|![How Do Iビデオ](../sharepoint/media/vs-icon-howdoivideos.gif "How Do I?ビデオ")|**How Do Iビデオ**<br /><br /> -   [How Do i:Visual Studio 2010 で SharePoint 2010 の視覚的 Web パーツを作成しますか。](https://visualstudio.microsoft.com/)<br />-   [How Do i:Visual Studio 2010 で SharePoint 2010 のコンテンツの種類を作成しますか。](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))<br />-   [How Do i:Visual Studio 2010 で SharePoint 2010 のサイト定義を作成しますか。](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))<br />-   [How Do i:Visual Studio 2010 を使用して SharePoint 2010 のビジネス データ接続モデルを作成しますか。](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))|
|![Channel 9 のビデオ](../sharepoint/media/vs-icon-channel9videos.gif "Channel 9 のビデオ")|**Channel 9 のビデオ**<br /><br /> -   [Visual Studio 2010 での SharePoint 開発の概要](https://channel9.msdn.com/blogs/funkyonex/overview-of-sharepoint-development-in-visual-studio-2010)<br />-   [Visual Studio 2010 で SharePoint 2010 Web パーツを構築する際のベスト プラクティス](https://channel9.msdn.com/blogs/funkyonex/best-practices-on-building-sharepoint-2010-web-parts-with-visual-studio-2010)<br />-   [Visual Studio 2010 の SharePoint フィーチャー デザイナーとパッケージ デザイナー](https://channel9.msdn.com/blogs/funkyonex/sharepoint-feature-and-package-designers-in-visual-studio-2010)|
|![デベロッパー センター](../sharepoint/media/vs-icon-msdndevcenter.gif "デベロッパー センター")|**デベロッパー センター**<br /><br /> -   [Visual Studio 開発者向け技術情報](https://visualstudio.microsoft.com/)<br />-   [SharePoint デベロッパー センター](/sharepoint/dev/)<br />-   [SharePoint Server デベロッパー センター](/previous-versions/office/fp161348\(v\=office.15\))<br />-   [SharePoint Designer デベロッパー センター](/previous-versions/office/fp161348\(v\=office.15\))<br />-   [ASP.NET デベロッパー センター](https://msdn.microsoft.com/aa336522.aspx)|
|![フィードバックを提供する](../sharepoint/media/vs-icon-feedback.gif "フィードバックの送信")|**フィードバックの送信**<br /><br /> Visual Studio に関するフィードバックを送ることができます。<br /><br /> -   [Microsoft Connect](http://go.microsoft.com/fwlink/?LinkID=150463)<br /><br /> Visual Studio のドキュメントに関するフィードバックを送ることができます。<br /><br /> -   **簡易表示:** トピックの上部から、 **[このトピックを評価する]** リンクを選択してトピックの下部に移動します。そこで、 **[この情報は役にたちましたか。]** に対する応答として、 **[はい]** または **[いいえ]** を指定できます。 **[はい]** を選択した場合は、表示される 1 つ以上のチェック ボックスを選択し、テキスト ボックスに詳細情報を入力できます。 終了したら、 **[投稿]** ボタンをクリックします。<br />-   **スクリプトを使用しない表示:** トピックの上部にある選択、**フィードバック**TechNet よぶ式ライブラリ フィードバック フォーラムにフィードバックを提供するリンク。<br />-   **クラシック ビュー** トピックの上部で、 **[クリックして評価とフィードバックをお寄せください]** のアイコンを選択し、ドキュメント チームにそのトピックについてフィードバックしてください。|
