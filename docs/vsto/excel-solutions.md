---
title: Excel ソリューション
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0c9af0a0c90d042d5720423150899971ffca8ec9
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551522"
---
# <a name="excel-solutions"></a>Excel ソリューション
  Visual Studio には、Microsoft Office Excel のドキュメント レベルのカスタマイズおよび VSTO アドインの作成に使用できるプロジェクト テンプレートが用意されています。 これらのソリューションを使用して、Excel の自動化、Excel の機能拡張、Excel のユーザー インターフェイス (UI) のカスタマイズを行うことができます。 ドキュメント レベルのカスタマイズと VSTO アドインの違いの詳細については、次の [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) を参照してください。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 ここでは、次の情報について説明します。

- [Excel を自動化します](#automating)。

- [Excel 用ドキュメント レベルのカスタマイズを開発します](#doclevel)。

- [Excel 用 VSTO アドインを開発します](#applevel)。

- [Excel のユーザー インターフェイスをカスタマイズします](#UI)。

## <a name="automating"></a>Excel の自動化
 Excel オブジェクト モデルでは、Excel の自動化に使用できる型が多数公開されています。 たとえば、グラフの作成、ワークシートの書式設定、範囲やセルの値の設定をプログラムを使用して実行できます。 詳細については、次の [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)を参照してください。

 Visual Studio で Excel ソリューションを開発する場合、ソリューションで *ホスト項目* と *ホスト コントロール* も使用できます。 これらのオブジェクトは、Excel オブジェクト モデル内にある、 <xref:Microsoft.Office.Interop.Excel.Worksheet> や <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトなど、よく使用される特定のオブジェクトを拡張したオブジェクトです。 これらの拡張オブジェクトは、基になる Excel オブジェクトと同じように動作しますが、基のオブジェクトにはないイベントとデータ バインディング機能が追加されています。 詳細については、次の[拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)参照してください。

## <a name="doclevel"></a>Excel 用のドキュメントレベルのカスタマイズの作成
 Microsoft Office Excel のドキュメント レベルのカスタマイズは、特定のブックに関連付けられたアセンブリで構成されます。 このアセンブリは、一般には UI のカスタマイズと Excel の自動化によってブックの機能を拡張します。 Excel 自体と関連付けられる VSTO アドインとは異なり、カスタマイズに実装した機能は、関連付けられたブックが Excel で開かれている場合にのみ利用できます。

 Excel 用ドキュメント レベルのカスタマイズ プロジェクトを作成するには、 Visual Studio の**新しいプロジェクト**ダイアログ ボックスから Excel ブックまたは Excel テンプレート プロジェクト テンプレートを使用します。 詳細については、「[方法 :Visual Studio で Office プロジェクトを作成する方法](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。

 ドキュメント レベルのカスタマイズの動作の詳細については、次の[ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)を参照してください。

### <a name="excel-customization-programming-model"></a>Excel カスタマイズのプログラミングモデル
 Excel 用のドキュメント レベルのプロジェクトを作成すると、ソリューションの基礎となるクラス ( `ThisWorkbook`、 `Sheet1`、 `Sheet2`、および `Sheet3`) が Visual Studio によって生成されます。 これらのクラスはソリューションに関連付けられたブックおよびワークシートを表し、コードを記述するための開始点となります。

 これらの生成クラスとその他ドキュメント レベル プロジェクトで使用できる機能については、[ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)を参照してください。

## <a name="applevel"></a>Excel 用の VSTO アドインの開発
 Microsoft Office Excel の VSTO アドインは、Excel によって読み込まれるアセンブリで構成されます。 このアセンブリは、一般には UI のカスタマイズと Excel の自動化によって Excel の機能を拡張します。 特定のブックに関連付けられているドキュメントレベルのカスタマイズとは異なり、VSTO アドインに実装した機能は、1つのブックに限定されません。

 Excel 用 VSTO アドイン プロジェクトを作成するには、Visual Studio の**新しいプロジェクト**ダイアログ ボックスで、 Excel ブックまたは Excel テンプレート プロジェクト テンプレートを使用します。 詳細については、「[方法 :Visual Studio で Office プロジェクトを作成する方法](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。

 VSTO アドインが機能するしくみの概要については、次の [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md) を参照してください。

### <a name="excel-add-in-programming-model"></a>Excel アドインのプログラミングモデル
 Excel VSTO アドイン プロジェクトを作成すると、 `ThisAddIn`と呼ばれる、ソリューションの基礎となるクラスが Visual Studio によって生成されます。 このクラスは、コードを記述するための開始点となり、Excel のオブジェクト モデルを VSTO アドインに公開します。

 `ThisAddIn`クラスおよび vsto アドインで使用できるその他の Visual Studio の機能の詳細については、「[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)」を参照してください。

## <a name="UI"></a>Excel のユーザーインターフェイスをカスタマイズする
 Excel のユーザー インターフェイスをカスタマイズする方法はいくつかあります。 一部のオプションはすべてのプロジェクト タイプで使用できますが、VSTO アドインまたはドキュメント レベルのカスタマイズでのみ使用できるオプションもあります。

### <a name="options-for-all-project-types"></a>すべてのプロジェクトの種類のオプション
 ドキュメント レベルのカスタマイズと VSTO アドインの両方に使用できるカスタマイズ オプションを次の表に示します。

|タスク|詳細情報|
|----------|--------------------------|
|リボンをカスタマイズする。|[リボンの概要](../vsto/ribbon-overview.md)|
|Windows フォーム コントロールまたは拡張された Excel コントロールを、ドキュメント レベルのカスタマイズ用のカスタマイズされたブック内のワークシート、または VSTO アドイン用の任意の開いているブック内のワークシートに追加する。|[方法: Office ドキュメントへの Windows フォームコントロールの追加](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [方法: ワークシートへのグラフコントロールの追加](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [方法: ワークシートへの ListObject コントロールの追加](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [方法: ワークシートへの NamedRange コントロールの追加](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|

### <a name="options-for-document-level-customizations"></a>ドキュメントレベルのカスタマイズのオプション
 ドキュメント レベルのカスタマイズにのみ使用できるカスタマイズ オプションを次の表に示します。

|タスク|詳細情報|
|----------|--------------------------|
|ブックに操作ウィンドウを追加する。|[操作ウィンドウの概要](../vsto/actions-pane-overview.md)<br /><br /> [方法: Word 文書または Excel ブックに操作ウィンドウを追加する](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|XML ノードにマップする拡張範囲コントロールをワークシートに追加する。|[方法: ワークシートへの XMLMappedRange コントロールの追加](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|

### <a name="options-for-vsto-add-ins"></a>VSTO アドインのオプション
 VSTO アドインにのみ使用できるカスタマイズ オプションを次の表に示します。

|タスク|詳細情報|
|----------|--------------------------|
|カスタム作業ウィンドウを作成する。|[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>関連トピック

| タイトル | 説明 |
| - | - |
| [Excel オブジェクトモデルの概要](../vsto/excel-object-model-overview.md) | Excel オブジェクト モデルによって提供される主な型の概要について説明します。 |
| [拡張オブジェクトを使用した Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md) | Excel ソリューションで使用できる ( [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]によって提供される) 拡張オブジェクトについて説明します。 |
| [Excel ソリューションのグローバリゼーションとローカリゼーション](../vsto/globalization-and-localization-of-excel-solutions.md) | Windows が英語以外の言語に設定されているコンピューター上で実行される Excel ソリューションに関する特記事項について説明します。 |
| [Office ドキュメントのコントロールの Windows フォームの概要](../vsto/windows-forms-controls-on-office-documents-overview.md) | Windows フォーム コントロールを Excel ワークシートに追加する方法について説明します。 |
| [チュートリアル: Excel 用のドキュメントレベルのカスタマイズを初めて作成する](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | Excel 用の基本的なドキュメント レベルのカスタマイズを作成する方法を示します。 |
| [チュートリアル: 初めての Excel 用 VSTO アドインを作成する](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | Excel 用の基本的な VSTO アドインを作成する方法を示します。 |
| [チュートリアル: VSTO アドインプロジェクトの実行時にワークシートにコントロールを追加する](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | VSTO アドインを使用して、 Windows フォームのボタン、 <xref:Microsoft.Office.Tools.Excel.NamedRange>、および<xref:Microsoft.Office.Tools.Excel.ListObject>を、実行時にワークシートへ追加する方法を示します。 |
| [共同作成とアドインについて](./understanding-coauthoring-and-addins.md) | 共同作成に対応するためにソリューションに対して行う必要がある調整について説明します。 |
| [Office 開発における Excel 2010](http://go.microsoft.com/fwlink/?LinkId=199011) | Excel ソリューションの開発に関する記事およびリファレンス ドキュメントへのリンクを提供します。 Visual Studio を使用した Office 開発だけの情報ではありません。 |
