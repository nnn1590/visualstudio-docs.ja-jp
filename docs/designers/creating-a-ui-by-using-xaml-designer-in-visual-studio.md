---
title: XAML デザイナーの概要
ms.date: 07/31/2019
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
- Blend.Start.Dev12
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d0d3e6e09eaad4b8c902b6d6c6ec4d20637a6cc9
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822081"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>XAML デザイナーを使用して UI を作成する

Visual Studio と Blend for Visual Studio の XAML デザイナーには、WPF、UWP、Xamarin.Forms アプリなど、XAML ベースのアプリのデザインに便利なビジュアル インターフェイスが用意されています。 アプリのユーザー インターフェイスを作成するには、[ツールボックス] ウィンドウ (Blend for Visual Studio の場合、[アセット] ウィンドウ) からコントロールをドラッグし、プロパティ ウィンドウでプロパティを設定します。 また、XAML ビューで直接、XAML を編集することもできます。

上級ユーザーの場合、[XAML デザイナーをカスタマイズする](../extensibility/xaml-designer-extensibility-migration.md)こともできます。

## <a name="xaml-designer-workspace"></a>XAML デザイナーのワークスペース

XAML デザイナーのワークスペースは、いくつかのビジュアル インターフェイス要素で構成されています。 これには、*アートボード* (ビジュアル デザイン サーフェイス)、XAML エディター、[ドキュメント アウトライン] ウィンドウ (Blend for Visual Studio の場合、[オブジェクトとタイムライン] ウィンドウ)、プロパティ ウィンドウが含まれます。 XAML デザイナーを開くには、 **[ソリューション エクスプローラー]** で XAML ファイルを右クリックし、 **[デザイナーの表示]** を選択します。

XAML デザイナーは、アプリでレンダリングされる XAML マークアップの XAML ビューと、それに同期したデザイン ビューを提供します。 XAML ファイルを Visual Studio または Blend for Visual Studio で開いている状態で、 **[デザイン]** タブと **[XAML]** タブを使用してデザイン ビューと XAML ビューを切り替えることができます。 **[ペインの交換]** ボタン ![XAML デザイナーの [ペインの交換] ボタン](media/swap-panes.PNG) を使用すると、アートボードと XAML エディターのどちらを上に表示するかを切り替えることができます。

### <a name="design-view"></a>デザイン ビュー

[デザイン] ビューでは、アートボードを含むウィンドウがアクティブ ウィンドウになり、主要な作業画面として使用できます。 このビューを使用し、要素を追加、描画、変更することにより、アプリのページを視覚的にデザインできます。 詳細については、「[XAML デザイナーで要素を操作する](../designers/working-with-elements-in-xaml-designer.md)」を参照してください。 次の図は、デザイン ビューに表示されるアートボードを示しています。

![XAML デザイナーのデザイン ビュー](../designers/media/xaml-artboard.png)

アートボードで使用できる機能は次のとおりです。

**スナップ ガイドライン**

スナップ ガイドラインは、コントロールの端が揃ったとき、またはテキストのベースラインが揃ったときに表示される赤色の破線 (*位置揃えライン*) です。 位置揃えラインは、 **[スナップ ガイドラインへのスナップ]** が有効に設定されている場合にのみ表示されます。

**グリッド レール**

グリッド レールを使用し、[[グリッド]](xref:Windows.UI.Xaml.Controls.Grid) パネルの行と列を管理します。 行と列を作成/削除したり、行と列の相対的な幅と高さを調整したりできます。 アートボードの左側に表示される縦のグリッド レールは行のために使用し、上側に表示される横のグリッド レールは列のために使用します。

**グリッド ガイド**

グリッド ガイドは、グリッド レール上に、縦線または横線の付いた三角形として表示されます。 グリッド ガイドをドラッグすると、マウスの移動に従って、隣接する列または行の幅または高さが更新されます。

グリッド ガイドを使用して、グリッドの行と列の幅と高さを制御します。 グリッド レールをクリックすると、新しい列または行を追加できます。 複数の行または列のあるグリッド パネルに新しい行または列を追加すると、レールの外側にミニ ツール バーが表示され、幅と高さを明示的に設定できます。 ミニ ツール バーでは、グリッドの行と列のサイズ変更オプションを設定できます。

![XAML デザイナーのグリッド装飾](media/grid-adorner.png)

**サイズ変更ハンドル**

サイズ変更ハンドルは、選択したコントロールに表示され、これを使用してコントロールのサイズを変更できます。 コントロールのサイズを変更するときは、通常、幅と高さの値が表示され、サイズを決める参考にできます。 **デザイン** ビューのコントロールを操作する方法の詳細については、「[XAML デザイナーで要素を操作する](../designers/working-with-elements-in-xaml-designer.md)」を参照してください。

**余白**

余白は、コントロールの端からそれを含むコンテナーの端までの固定された間隔です。 コントロールの余白は、 **[プロパティ]** ウィンドウの **[レイアウト]** の下にある [Margin](xref:Windows.UI.Xaml.FrameworkElement.Margin) プロパティで設定できます。

**余白ガイド**

余白ガイドを使用し、レイアウト コンテナーを基準として要素の余白を変更します。 余白ガイドが開いている場合は、余白が設定されておらず、余白ガイドには切れたチェーンが表示されます。 余白が設定されていないと、実行時にレイアウト コンテナーのサイズを変更した場合に、要素の位置が変わりません。 余白ガイドが閉じている場合、余白ガイドには切れていないチェーンが表示され、実行時にレイアウト コンテナーのサイズを変更すると、要素が余白と共に移動します (余白は固定されたまま)。

**要素ハンドル**

要素ハンドルを使用すると、要素を変更できます。要素ハンドルは、アートボードで要素を囲む青いボックスの角にマウス ポインターを置くと表示されます。 このハンドルを使用すると、要素を回転、サイズ変更、反転、移動したり、角を丸めたりできます。 要素ハンドルのシンボルは機能に応じてさまざまで、ポインターの正確な場所に応じて変化します。 要素ハンドルが表示されない場合は、要素が選択されていることを確認してください。

**デザイン** ビューでは、ウィンドウの左下に次のように表示される追加のアートボード コマンドを使用できます。

![デザイン ビュー コマンド](../designers/media/xaml-design-view-controls.png)

このツール バーでは、次のコマンドを使用できます。

**ズーム**

ズームでは、デザイン画面のサイズを変更できます。 12.5% から 800% の範囲でズームしたり、 **[選択範囲をズーム]** や **[すべてを合わせる]** などのオプションを選択したりできます。

**スナップ グリッドの表示/スナップ グリッドを隠す**

グリッド線を示すスナップ グリッドを表示したり、非表示にしたりします。 グリッド線は、 **[グリッド線にスナップ]** または **[スナップラインにスナップ]** のいずれかが有効な場合に使用されます。

**グリッド線へのスナップをオン/オフにする**

**[グリッド線へのスナップ]** がオンのときにアートボードで要素をドラッグすると、要素は、最も近い位置にある縦または横のグリッド線に整列されます。

**アートボードの背景を切り替える**

明るい背景と暗い背景を切り替えます。

**スナップ ガイドラインへのスナップをオン/オフにする**

スナップ ガイドラインは、複数のコントロールを相互の位置に合わせて整列するために役立ちます。 **[スナップ ガイドラインへのスナップ]** が有効になっている場合、1 つのコントロールを他のコントロールを基準にしてドラッグしているときに、他のコントロールの端やテキストに垂直または水平位置が揃うと位置揃えラインが表示されます。 位置揃えライン (スナップ ガイドライン) は赤色の破線として表示されます。

**プロジェクト コードの無効化**

[プロジェクト コード](debugging-or-disabling-project-code-in-xaml-designer.md)、たとえば、カスタム コントロールや値コンバーターを無効にし、デザイナーをリロードします。

### <a name="xaml-view"></a>XAML ビュー

**XAML** ビューでは、XAML エディターが含まれているウィンドウがアクティブ ウィンドウであり、XAML エディターが主要な編集ツールです。 Extensible Application Markup Language (XAML) は、アプリケーションのユーザー インターフェイスを指定するための、XML をベースにした宣言型のボキャブラリを提供します。 XAML ビューには、IntelliSense、オート フォーマット、構文の強調表示、およびタグ ナビゲーションが含まれています。 次の図は、IntelliSense メニューが開いている XAML ビューを示しています。

![XAML ビュー](../designers/media/xaml-editor.png)

## <a name="document-outline-window"></a>[ドキュメント アウトライン] ウィンドウ

Visual Studio の [ドキュメント アウトライン] ウィンドウは、Blend for Visual Studio の [[オブジェクトとタイムライン]](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) ウィンドウに似ています。 [ドキュメント アウトライン] を使用すると、次に示すタスクを実行する役にたちます。

- アートボード上のすべての要素の階層構造を表示する。

- 要素を選択して変更する (たとえば、階層構造内の別の場所に移動したり、プロパティ ウィンドウでプロパティを設定したりする)。 詳細については、「[XAML デザイナーで要素を操作する](../designers/working-with-elements-in-xaml-designer.md)」を参照してください。

- コントロールである要素のテンプレートを作成および変更する。

- [アニメーションを作成する](animate-objects-in-xaml-designer.md) (Blend for Visual Studio のみ)。

Visual Studio で [ドキュメント アウトライン] ウィンドウを表示するには、メニュー バーで **[表示]** 、 **[その他のウィンドウ]** 、 **[ドキュメント アウトライン]** の順に選択します。
Blend for Visual Studio で [オブジェクトとタイムライン] ウィンドウを表示するには、メニューバーで **[表示]** 、 **[ドキュメント アウトライン]** の順に選択します。

![Visual Studio の [ドキュメント アウトライン] ウィンドウ](../designers/media/document-outline-window.png)

[ドキュメント アウトライン]/[オブジェクトとタイムライン] ウィンドウのメインビューには、ドキュメントの階層がツリー構造で表示されます。 ドキュメント アウトラインの階層状の特性を利用して、さまざまな詳細レベルでドキュメントを調査し、要素を 1 つずつ、またはまとめてロックしたり非表示にしたりできます。 [ドキュメント アウトライン]/[オブジェクトとタイムライン] ウィンドウで使用可能なオプションは次のとおりです。

**表示/非表示**

アートボード要素を表示するか、非表示にします。 表示される場合、目の形をした記号として表示されます。 **Ctrl**+**H** を押して要素を非表示にし、**Shift**+**Ctrl**+**H** を押して要素を表示する方法もあります。

**ロック/ロック解除**

アートボード要素をロックまたはロック解除します。 ロックされている要素は変更できません。 ロックされると、南京錠の形をした記号として表示されます。 **Ctrl**+**L** を押して要素をロックし、**Shift**+**Ctrl**+**L** を押してロックを解除する方法もあります。

**スコープを pageRoot に戻す**

[ドキュメント アウトライン]/[オブジェクトとタイムライン] ウィンドウの上端に上向き矢印の記号として表示されるオプションを選択すると、前のスコープに移動します。 スタイルまたはテンプレートのスコープにある場合にのみ使用できます。

## <a name="properties-window"></a>[プロパティ] ウィンドウ

**[プロパティ]** ウィンドウでは、コントロールのプロパティ値を設定できます。 次のように表示されます。

![[プロパティ] ウィンドウ](../designers/media/xaml-designer-properties-window.png)

**[プロパティ]** ウィンドウの上部にはさまざまなオプションがあります。

- **[名前]** ボックスで、現在選択されている要素の名前を変更します。
- 左上にあるアイコンは、現在選択されている要素を表します。
- プロパティをカテゴリ別またはアルファベット順に並べ替えるには、 **[並べ替え]** の一覧で **[カテゴリ]** 、 **[名前]** 、または **[ソース]** をクリックします。
- コントロールのイベントの一覧を表示するには、 **[イベント]** ボタン (稲妻の形をした記号として表示されます) をクリックします。
- プロパティを検索するには、[検索] ボックスにプロパティの名前を入力します。 入力した文字列に一致するプロパティが **[プロパティ]** ウィンドウに表示されます。

一部のプロパティでは、下矢印ボタンを選択して、詳細プロパティを設定することができます。

各プロパティの値の右側には、 *プロパティ マーカー* がボックスのシンボルとして表示されます。 プロパティ マーカーの外観は、プロパティに適用されるデータ バインドやリソースの有無を示します。 たとえば、白色のボックス シンボルは既定値を示します。黒色のボックス シンボルは、通常、ローカル リソースが適用されていることを示します。オレンジ色のボックスは、通常、データ バインドが適用されていることを示します。 プロパティ マーカーをクリックすると、スタイルの定義に移動したり、データ バインディング ビルダーを開いたり、リソース ピッカーを開いたりできます。

プロパティの使用とイベントの処理の詳細については、「[コントロールとパターンの概要](/windows/uwp/design/controls-and-patterns/controls-and-events-intro)」を参照してください。

## <a name="see-also"></a>関連項目

- [XAML デザイナーで要素を操作する](../designers/working-with-elements-in-xaml-designer.md)
- [リソースを作成して適用する方法](../designers/how-to-create-and-apply-a-resource.md)
- [チュートリアル: XAML デザイナーでデータにバインドする](../designers/walkthrough-binding-to-data-in-xaml-designer.md)