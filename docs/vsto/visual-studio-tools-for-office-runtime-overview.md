---
title: Visual Studio のツール for Office runtime の概要
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio], about Office runtime
- VSTOLoader.dll
- runtime loader [Office development in Visual Studio]
- Office runtime [Office development in Visual Studio], assemblies
- Office runtime [Office development in Visual Studio]
- runtime [Office development in Visual Studio], assemblies
- vstoee.dll
- Visual Studio Tools for Office runtime
- Office solutions [Office development in Visual Studio], runtime
- solutions [Office development in Visual Studio], runtime
- versions [Office development in Visual Studio], runtime
- assemblies [Office development in Visual Studio], runtime
- runtime [Office development in Visual Studio], about VSTO runtime
- solution loader [Office development in Visual Studio]
- runtime [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e78d20fa0c7d4d0db6db50c2cbb5cde0b79023fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982330"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Visual Studio のツール for Office runtime の概要
  Visual Studio で Microsoft Office developer tools を使用して作成されたソリューションを実行するには、するには、エンドユーザーのコンピューターに、Visual Studio 2010 Tools for Office ランタイムをインストールする必要があります。 詳細については、「[方法 :Visual Studio Tools for Office ランタイム再頒布可能パッケージをインストール](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)します。 Visual Studio 2010 Tools for Office ランタイムは、2 つの主要なコンポーネントで構成されます。

- .NET Framework 用の Office 拡張機能。 これらのコンポーネントは、ソリューションと Microsoft Office アプリケーションの間の通信レイヤーとなるマネージド アセンブリです。 詳細については、次を参照してください。 [.NET Framework 用の Office 拡張機能を理解する](#officeextensions)します。

- Office ソリューション ローダー。 このコンポーネントは、Office アプリケーションがランタイムおよびソリューションの読み込みに使用する一連のアンマネージ DLL です。 詳細については、次を参照してください。 [Office ソリューション ローダーについて理解](#UnmanagedLoader)します。

  ランタイムをインストールする方法はいくつかあります。 ランタイムをインストールするときには、コンピューターの構成に応じて異なるランタイム コンポーネントがインストールされます。 詳細については、[Visual Studio Tools for Office runtime のインストール シナリオ](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)を参照してください。

## <a name="officeextensions"></a> .NET Framework 用の Office 拡張機能を理解します。
 Visual Studio 2010 Tools for Office ランタイムには、.NET Framework 3.5 用の Office 拡張機能が含まれています、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]以降。 .NET Framework の各バージョンを対象とするソリューションでは、そのバージョンに適した拡張機能が使用されます。

 これらの拡張機能は、ソリューションが Office アプリケーションの自動化および拡張に使用するアセンブリで構成されています。 Office プロジェクトを作成すると、Visual Studio によって、そのプロジェクト タイプおよびプロジェクトの対象 .NET Framework に使用するアセンブリへの参照が自動的に追加されます。 Office 拡張機能アセンブリの詳細については、次を参照してください。 [、Visual Studio Tools for Office ランタイムのアセンブリ](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)します。

### <a name="design-differences-in-the-office-extensions"></a>Office 拡張機能の設計の相違点
 .NET Framework 3.5 用の Office 拡張機能で使用する型の大部分は、クラスです。 これらのクラスは、以前のバージョンの [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]に含まれていたクラスと同じです。 これに対して、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降用の Office 拡張機能で使用する型の大部分は、インターフェイスです。 たとえば、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とする場合、 <xref:Microsoft.Office.Tools.Excel.Worksheet> と <xref:Microsoft.Office.Tools.Word.Document> の型はクラスではなくインターフェイスです。

 ほとんどの場合、ソリューションが .NET Framework 3.5 を対象とするかまたは [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]を対象とするかに関係なく、Office ソリューションで記述するコードは同じです。 ただし、一部の機能については、対象となる .NET Framework のバージョンが異なる場合に別のコードが必要になります。 詳細については、次を参照してください。[以降、.NET Framework 4 への移行 Office ソリューション](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)します。

### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>.NET Framework 4 またはそれ以降の Office 拡張機能インターフェイス
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降用の Office 拡張機能に含まれるインターフェイスの大部分は、ユーザー コードで実装されることを意図していません。 直接実装できるインターフェイスは、 **I**という文字で始まる名前の付いたインターフェイスです。たとえば、 <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>などです。

 文字で始まらないすべてのインターフェイス**は**Visual Studio 2010 Tools for Office runtime、によって内部的に実装されると、これらのインターフェイスが将来のリリースで変更があります。 これらのインターフェイスを実装するオブジェクトを作成するには、プロジェクトで `Globals.Factory` オブジェクトによって提供されるメソッドを使用します。 たとえば、<xref:Microsoft.Office.Tools.Excel.SmartTag> インターフェイスを実装するオブジェクトを取得するには、`Globals.Factory.CreateSmartTag` メソッドを使用します。 詳細については`Globals.Factory`を参照してください[Office プロジェクト内のオブジェクトへのアクセスをグローバル](../vsto/global-access-to-objects-in-office-projects.md)します。

### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>型の等価性と埋め込まれた型を .NET Framework 4 以降を対象とするプロジェクトで有効にします。
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降用の Office 拡張機能のオブジェクト モデルはインターフェイスに基づいているため、Visual Studio の Visual C# および Visual Basic の両方で、型の等価性の機能を使用して [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] から取得した型情報をソリューションに埋め込むことができます。 この機能によって、Office ソリューションおよび [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] が、それぞれ独立してバージョン管理できるようになります。 たとえば、ソリューションで <xref:Microsoft.Office.Tools.Word.Document> インターフェイスを埋め込み型として使用し、ランタイムの次のバージョンによって <xref:Microsoft.Office.Tools.Word.Document> インターフェイスにメンバーが追加される場合でも、そのソリューションは引き続きランタイムの次のバージョンで機能します。 ソリューションで <xref:Microsoft.Office.Tools.Word.Document> インターフェイスを埋め込み型として使用しない場合、そのソリューションはランタイムの次のバージョンで機能しません。

 既定では、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とする Office プロジェクトを作成するときに、型の等価性の機能は有効になりません。 この機能を有効にするには、プロジェクト内の次のアセンブリ参照の **相互運用型の埋め込み** プロパティを **True**に設定します。

- Microsoft.Office.Tools.dll

- Microsoft.Office.Tools.Common.dll

- Microsoft.Office.Tools.Excel.dll

- Microsoft.Office.Tools.Outlook.dll

- Microsoft.Office.Tools.Word.dll

  この変更を加えると、プロジェクトをビルドするときに、プロジェクトが使用するすべてのランタイム型の型情報が、ソリューション アセンブリに埋め込まれます。 参照先のアセンブリで型情報ではなく、この埋め込み型情報は、実行時に、ソリューションによって使用されます。

## <a name="UnmanagedLoader"></a> Office ソリューション ローダーを理解します。
 Visual Studio Tools for Office Runtime には、Office アプリケーションがランタイムおよび Office ソリューションの読み込みに使用する複数のアンマネージ DLL が含まれています。 これらの DLL を直接操作する必要が生じることはありませんが、その目的を把握しておくと、Office ソリューションのアーキテクチャについて理解を深めるうえで役に立ちます。

 読み込みプロセス中にこれらのコンポーネントを使用する方法については、次を参照してください。[のドキュメント レベル カスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)と[Architecture of VSTO アドイン](../vsto/architecture-of-vsto-add-ins.md)します。

### <a name="vstoeedll"></a>vstoee.dll
 Office アプリケーションを呼び出すユーザーは、ドキュメント レベルのカスタマイズが表示されます、VSTO アドインを起動したり、 *VSTOEE.dll*読み込みに必要なタスクを実行する、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]します。

 *VSTOEE.dll*ための正しいバージョン、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]ソリューションと Office のインストールされているバージョンに読み込まれます。 複数のバージョンの[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]のインスタンスを 1 つだけ、同じコンピューターにインストールできます*VSTOEE.dll*を同時にインストールします。 これは、 *VSTOEE.dll*ですが、コンピューターにインストールされているランタイムの最新バージョンに含まれています。 異なるバージョンの詳細については、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]の他のソリューションで使用できますを参照してください[で異なるバージョンの Microsoft Office ソリューションを実行](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)します。

### <a name="vstoloaderdll"></a>VSTOLoader.dll
 後*VSTOEE.dll*の適切なバージョンを読み込、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]、 *VSTOLoader.dll*ソリューション アセンブリの読み込みに必要な作業のほとんどを実行します。 *VSTOLoader.dll*いくつかの操作します。

- ソリューション アセンブリごとにアプリケーション ドメインを作成します。

- 一連のセキュリティ チェックによって、ソリューション アセンブリに実行のアクセス許可があることを確認します。

- ソリューションに必要な .NET Framework 用のバージョンの Office 拡張機能を読み込みます。

  *VSTOLoader.dll*も VSTO アドインに固有のいくつかの処理を行います。

- <xref:Extensibility.IDTExtensibility2> インターフェイスを実装します。 <xref:Extensibility.IDTExtensibility2> は、Microsoft Office アプリケーションのすべての VSTO アドインが実装する必要のある COM インターフェイスです。 このインターフェイスには、アプリケーションが VSTO アドインと通信するために呼び出すメソッドが定義されています。

- IManagedAddin インターフェイスを実装します。 このインターフェイスは、Office アプリケーションで VSTO アドインの読み込みに使用されます。詳細については、次を参照してください。 [IManagedAddin インターフェイス](../vsto/imanagedaddin-interface.md)します。

## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>32 ビットおよび 64 ビット バージョンのランタイムを理解します。
 Visual Studio 2010 Tools for Office ランタイムの別の 64 ビットおよび 32 ビット バージョンがあります。 ランタイムのこれらのバージョンは、64 ビット エディションおよび 32 ビット エディションの Office でソリューションを実行するのに使用されます。 次の表は、Windows と Office のそれぞれの組み合わせで必要とされる、ランタイムのバージョンを示しています。

|Windows のエディション|Microsoft Office のエディション|Visual Studio Tools for Office Runtime のバージョン番号|
|------------------------|---------------------------------|--------------------------------------------------------------------|
|32 ビット|32 ビット|32 ビット|
|64 ビット|32 ビット|64 ビット|
|64 ビット|64 ビット|64 ビット|

 Office をインストールするときに、必要なバージョンの [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] が Office と共にインストールされます。 たとえば、64 ビット エディションの Office を 64 ビット バージョンの Windows にインストールすると、64 ビット バージョンの [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] もインストールされます。 インストールの詳細については、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] office では、次を参照してください。 [Visual Studio Tools for Office runtime のインストール シナリオ](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)します。

 64 ビット バージョンの Office は、Visual Studio 2008 で 2007 Microsoft Office system 用のプロジェクト テンプレートを使用して作成された Office ソリューションも実行できます。 ただし、Visual Studio 2008 で Microsoft Office 2003 用のプロジェクト テンプレートを使用して作成された Office ソリューションや、Visual Studio 2005 を使用して作成された Office ソリューションは実行できません。 詳細については、次を参照してください。[で異なるバージョンの Microsoft Office ソリューションを実行](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)します。

## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>Visual Studio 2010 Tools for Office ランタイムを修復します。
 ランタイムを修復する必要がある場合は、[コントロール パネル] の **[プログラムと機能]** または **[プログラムの追加と削除]** を開き、プログラムの一覧から **[Microsoft Visual Studio 2010 Tools for Office Runtime]** をクリックし、 **[アンインストール]** をクリックします。 実行されるセットアップ プログラムを使用して、ランタイムを修復できます。 **[変更]** をクリックした場合、ランタイムを修復するオプションは表示されません。

## <a name="see-also"></a>関連項目
- [Visual Studio のツール for Office runtime のインストール シナリオ](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Visual Studio Tools for Office ランタイムのアセンブリ](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
- [Visual Studio での Office ソリューションのアーキテクチャ](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)
- [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)
- [方法: Visual Studio での Office プロジェクトを作成します。](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office ソリューションのアップグレードと移行](../vsto/upgrading-and-migrating-office-solutions.md)
