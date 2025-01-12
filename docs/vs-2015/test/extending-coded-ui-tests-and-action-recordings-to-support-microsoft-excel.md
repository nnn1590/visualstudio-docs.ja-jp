---
title: コード化された UI テストと操作の記録を拡張して Microsoft Excel をサポート | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6b0f72a4-70ca-4e55-b236-2ea1034fd8a7
caps.latest.revision: 32
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6eb44970cc29198ad9044281e566727a64b893c8
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871562"
---
# <a name="extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel"></a>コード化された UI テストと操作の記録を拡張して Microsoft Exce をサポート
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

コード化された UI テストおよび操作の記録のテスト フレームワークは、すべてのユーザー インターフェイスでサポートされているとは限りません。 テストする特定の UI がサポートされていない場合があります。 たとえば、[!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] スプレッドシート向けのコード化された UI テストや操作の記録をすぐに作成することはできません。 ただし、コード化された UI テスト フレームワークの拡張機能を使用すると、特定の UI をサポートするコード化された UI テスト フレームワーク向けの独自の拡張機能を作成できます。 次のトピックでは、コード化された UI テストの作成と [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] の操作の記録をサポートするようフレームワークを拡張する方法の例について説明します。 サポートされているプラットフォームの詳細については、[「コード化された UI テストと操作の記録でサポートされている構成とプラットフォーム」](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) を参照してください。

 **必要条件**

- Visual Studio Enterprise

  このセクションでは、Excel ワークシートのテストの記録と再生を行うことができるコード化された UI テストの拡張機能について説明します。 拡張機能の各部分については、それぞれの拡張機能を作成する開発者向けに、このセクションとコード コメントで説明します。

  ![UI テストのアーキテクチャ](../test/media/ui-testarch.png "UI_TestArch")アーキテクチャの概要

## <a name="download-the-sample"></a>サンプルのダウンロード
 サンプルは、`CodedUIExtensibilitySample.sln` ソリューションの次の 4 つのプロジェクトで構成されています。

- CodedUIextensibilitySample

- ExcelCodedUIAddInHelper

- ExcelUICommunicationHelper

- SampleTestProject

  この[ブログの投稿](http://go.microsoft.com/fwlink/?LinkID=185592)からサンプルを入手してください。

> [!NOTE]
> サンプルは、Microsoft Excel 2010 での使用を意図しています。 Microsoft Excel の他のバージョンでも使用できる可能性がありますが、現時点ではサポートされていません。

## <a name="details-about-the-sample"></a>サンプルについての詳細
 次のセクションでは、サンプルとその構造の詳細について説明します。

### <a name="microsoft-excel-add-in-excelcodeduiaddinhelper"></a>Microsoft Excel アドイン:ExcelCodedUIAddinHelper
 このプロジェクトには、Excel プロセスで実行するアドインが含まれています。 アドイン プロジェクトの概要については、[「コード化された UI テスト用の Excel アドインのサンプル」](../test/sample-excel-add-in-for-coded-ui-testing.md) を参照してください。

 詳細については、「[チュートリアル:初めての Excel](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)用 VSTO アドインを作成する。

### <a name="excel-ui-communication-exceluicommunicationhelper"></a>Excel UI 通信:ExcelUIcommunicationHelper
 このプロジェクトには、コード化された UI テスト フレームワークと Excel の間でデータを渡すのに使用する `IExcelUICommunication` インターフェイスと情報クラスが含まれています。 詳細については、「[Excel Communicator インターフェイスのサンプル](../test/sample-excel-communicator-interface.md)」を参照してください。

### <a name="coded-ui-test-extension-codeduiexentsibilitysample"></a>コード化された UI テストの拡張機能:CodedUIExentsibilitySample
 このプロジェクトには、Excel ワークシートのテストで使用するカスタム クラスが含まれています。 それぞれのクラスのコードは、自己記述的です。 ただし、各カスタム クラスについて簡単に説明しています。 詳細については、[「Excel 用にコード化された UI テストの拡張子のサンプル」](../test/sample-coded-ui-test-extension-for-excel.md) を参照してください。

### <a name="deploying-your-add-in-and-extension"></a>アドインと拡張機能の配置
 すべてのプロジェクトとオブジェクトを作成したら、提供された `CopyDrop.bat` ファイルを管理者として実行します。 このファイルは、`ExcelCodedUIAddinHelper` の DLL ファイルおよび PDB ファイルを以下の場所にコピーします。

 "`%CommonProgramFiles(x86)%\Microsoft Shared\VSTT\<version number>\UITestExtensionPackages\*.*`"。ここで、バージョン番号は 11.0、12.0 など、Visual Studio のバージョンに基づいたものとなります。

 `ExcelUICommunicationHelper` の DLL ファイルおよび PDB ファイルは、`"%ProgramFiles(x86)%\Microsoft Visual Studio <version number>\Common7\IDE\PrivateAssemblies”` にコピーされます。

 コピーの正確なパスの調整が必要になる場合がありますが、追加のインストールを行う必要はありません。 64 ビット コンピューターでは、32 ビット Visual Studio Enterprise コマンド プロンプトを使用して、`CopyDrop.bat` ファイルを実行します。

### <a name="testing-excel-with-the-sampletestproject"></a>SampleTestProject を使用した Excel のテスト
 所有していない特定の Excel バージョンを使用する、提供されたテスト プロジェクトでのテストを実行できます。または、独自のテスト プロジェクトを作成して、独自のテストを記録できます。 詳細については、[「コード化された UI テストを作成する」](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) を参照してください。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [タイムアウト](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [UI オートメーションを使用してコードをテストする](../test/use-ui-automation-to-test-your-code.md)
- [コード化された UI テストのベスト プラクティス](../test/best-practices-for-coded-ui-tests.md)
- [コード化された UI テストと操作の記録でサポートされている構成とプラットフォーム](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
