---
title: シェーダー デザイナー
ms.date: 09/21/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1377034853907ce0c3585e4672296c1c8747259f
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823865"
---
# <a name="shader-designer"></a>シェーダー デザイナー

このドキュメントでは、Visual Studio **シェーダー デザイナー**を使用して、*シェーダー*というカスタム視覚効果を作成、変更、およびエクスポートする方法について説明します。

**シェーダー デザイナー**を使用すると、上位レベル シェーダー言語 (HLSL) でのプログラミングを知らなくても、ゲームやアプリのカスタム視覚効果を作成できます。 **シェーダー デザイナー**でシェーダーを作成するには、それをグラフとしてレイアウトします。 つまり、データおよび操作を表す "*ノード*" をデザイン サーフェイスに追加し、各ノードを接続することで、操作がどのようにデータを処理するのかを定義します。 各操作ノードでは、その時点までの効果のプレビューを表示して、結果を視覚化することができます。 データは、ノード間を移動して最終ノードに到達します。この最終ノードはシェーダーの出力を表しています。

## <a name="supported-formats"></a>サポートされる形式

**シェーダー デザイナー**は、以下のシェーダー形式をサポートしています。

|形式名|ファイル拡張子|サポートされる操作 (表示、編集、エクスポート)|
|-----------------| - | - |
|Directed Graph Shader Language|*.dgsl*|表示、編集|
|HLSL シェーダー (ソース コード)|*.hlsl*|エクスポート|
|HLSL シェーダー (バイトコード)|*.cso*|エクスポート|
|C++ ヘッダー (HLSL バイトコード配列)|*.h*|エクスポート|

## <a name="get-started"></a>作業開始

このセクションでは、Visual Studio C++ プロジェクトに DGSL シェーダーを追加する方法を説明し、作業の開始に役立つ基本的な情報を提供します。

> [!NOTE]
> シェーダー グラフ (.dgsl ファイル) のようなグラフィックス項目の自動ビルド統合がサポートされるのは、C++ プロジェクトの場合のみです。

### <a name="to-add-a-dgsl-shader-to-your-project"></a>プロジェクトに DGSL シェーダーを追加する手順

1. グラフィックスを操作するために必要な必須 Visual Studio コンポーネントがインストールされていることを確認します。 このコンポーネントは**イメージ エディターと 3D モデル エディター**と呼ばれます。

   これをインストールするには、メニュー バーから **[ツール]**  >  **[ツールと機能を取得]** を選択して Visual Studio インストーラーを開き、 **[個々のコンポーネント]** タブを選択します。 **[ゲームおよびグラフィックス]** カテゴリで **[イメージ エディターと 3D モデル エディター]** コンポーネントを選択し、 **[変更]** を選択します。

   ![イメージ エディターと 3D モデル エディター コンポーネント](media/image-3d-model-editors-component.png)

2. **ソリューション エクスプローラー**で、シェーダーを追加する C++ プロジェクトのショートカット メニューを開き、 **[追加]**  >  **[新しい項目]** の順に選択します。

3. **[新しい項目の追加]** ダイアログ ボックスで、 **[インストール済み]** の下にある **[グラフィックス]** を選択し、 **[視覚シェーダー グラフ (.dgsl)]** を選択します。

   > [!NOTE]
   > **[新しい項目の追加]** ダイアログ ボックスで **[グラフィックス]** カテゴリが表示されず、 **[イメージ エディターと 3D モデル エディター]** コンポーネントをインストール済みである場合は、お使いのプロジェクトの種類でグラフィックス項目がサポートされていません。

4. シェーダー ファイルの **[名前]** を指定し、作成する **[場所]** を指定します。

5. **[追加]** ボタンをクリックします。

### <a name="the-default-shader"></a>既定のシェーダー

DGSL シェーダーを作成するたびに、**ポイントの色**ノードが**最終的な色**ノードに接続されている、最小限のシェーダーが最初に作成されます。 このシェーダーは完全なものとして機能しますが、その機能は限られています。 そのため、実用的なシェーダーを作成するには、多くの場合、最初の手順として**ポイントの色**ノードを削除するか、または**最終的な色**ノードから切断して、他のノードを追加できるようにします。

## <a name="work-with-the-shader-designer"></a>シェーダー デザイナーを操作する

以下のセクションでは、シェーダー デザイナーを使用してカスタム シェーダーを操作する方法について説明します。

### <a name="shader-designer-toolbars"></a>シェーダー デザイナーのツール バー

シェーダー デザイナーのツール バーには、DGSL シェーダー グラフを操作する際に役立つコマンドが用意されています。

シェーダー デザイナーの状態を変更させるコマンドは、Visual Studio のメイン ウィンドウの **[シェーダー デザイナー モード]** ツール バーにあります。 デザイン ツールおよびコマンドは、シェーダー デザイナーのデザイン サーフェイス上の **[シェーダー デザイナー]** ツール バーにあります。

**[シェーダー デザイナー モード]** ツール バーを以下に示します。

![シェーダー デザイナーのモーダル ツール バー。](../designers/media/digit-dsd-modal-toolbar.png)

次の表では、 **[シェーダー デザイナー モード]** ツール バーの各項目について、左から右へ表示される順序で説明します。

|ツール バーの項目|説明|
|------------------|-----------------|
|**選択**|グラフのノードおよびエッジを操作できるようにします。 このモードでは、ノードを選択したり、ノードを移動または削除したり、エッジを設定または解除したりすることができます。|
|**パン**|ウィンドウ フレームに合わせてシェーダー グラフを移動できるようにします。 パンするには、デザイン サーフェイス上のポイントを選択し、周囲に移動します。<br /><br /> **[選択]** モードで **Ctrl** キーを押したままにすると、 **[パン]** モードを一時的に有効にすることができます。|
|**ズーム**|ウィンドウ フレームに合わせてシェーダー グラフの詳細を拡大表示または縮小表示できます。 **[ズーム]** モードで、デザイン サーフェイス上のポイントを選択し、右または下へ移動して拡大表示するか、左または上へ移動して縮小表示します。<br /><br /> **[選択]** モードでは、**Ctrl** キーを押しながらマウス ホイールを使用して、拡大または縮小することができます。|
|**ウィンドウのサイズに合わせて大きさを変更**|ウィンドウ フレームにシェーダー グラフ全体を表示します。|
|**リアルタイム レンダリング モード**|リアルタイム レンダリングを有効にすると、ユーザー動作がない場合でも、Visual Studio でデザイン サーフェスを再描画します。 このモードは、時間と共に変化するシェーダーを使用する場合に役立ちます。|
|**球でプレビュー**|有効な場合、球のモデルを使用してシェーダーをプレビューします。 一度に 1 つのプレビュー図形だけ有効にすることができます。|
|**直方体でプレビュー**|有効な場合、直方体のモデルを使用してシェーダーをプレビューします。 一度に 1 つのプレビュー図形だけ有効にすることができます。|
|**円柱でプレビュー**|有効な場合、円柱のモデルを使用してシェーダーをプレビューします。 一度に 1 つのプレビュー図形だけ有効にすることができます。|
|**円すいでプレビュー**|有効な場合、円すいのモデルを使用してシェーダーをプレビューします。 一度に 1 つのプレビュー図形だけ有効にすることができます。|
|**ティーポットでプレビュー**|有効な場合、ティーポットのモデルを使用してシェーダーをプレビューします。 一度に 1 つのプレビュー図形だけ有効にすることができます。|
|**平面でプレビュー**|有効な場合、平面のモデルを使用してシェーダーをプレビューします。 一度に 1 つのプレビュー図形だけ有効にすることができます。|
|**ツールボックス**|**ツールボックス**の表示または非表示を切り替えます。|
|**プロパティ**|**[プロパティ]** ウィンドウの表示または非表示を切り替えます。|
|**詳細設定**|高度なコマンドとオプションがあります。<br /><br /> **エクスポート**:複数の形式でシェーダーをエクスポートできます。<br /><br /> **名前を付けてエクスポート**:HLSL ソース コードか、またはコンパイル済みシェーダー バイトコードとしてシェーダーをエクスポートします。 シェーダーをエクスポートする方法の詳細については、「[方法:シェーダーをエクスポートする](../designers/how-to-export-a-shader.md)」を参照してください。<br /><br /> **グラフィックス エンジン**:デザイン サーフェイスの表示に使用されるレンダラーを選択できます。<br /><br /> **D3D11 で描画**:Direct3D 11 を使用して、シェーダー デザイナーのデザイン サーフェイスを描画します。<br /><br /> **D3D11WARP で描画**:Direct3D 11 Windows Advanced Rasterization Platform (WARP) を使用して、シェーダー デザイナーのデザイン サーフェイスを描画します。<br /><br /> **表示**:シェーダー デザイナーに関する追加情報を選択できるようにします。<br /><br /> **フレーム レート**:有効にすると、デザイン サーフェイスの右上隅に現在のフレーム レートが表示されます。 フレーム レートは、1 秒あたりの描画フレーム数です。 このオプションは **リアルタイム レンダリング モード** オプションを有効にする場合に便利です。|

> [!TIP]
> **[詳細設定]** ボタンを選択すると、最後のコマンドを再実行できます。

### <a name="work-with-nodes-and-connections"></a>ノードと接続を操作する

**[選択]** モードを使用して、ノードを追加、削除、位置変更、接続、および構成します。 これらの基本操作を実行する方法を以下に示します。

#### <a name="to-perform-basic-operations-in-select-mode"></a>[選択] モードで基本操作を実行する方法

- 次の手順に従います。

  - グラフにノードを追加するには、**ツールボックス**でノードを選択し、デザイン サーフェイスに移動します。

  - グラフからノードを削除するには、ノードを選択し、**Delete** キーを押します。

  - ノードの位置を変更するには、ノードを選択し、新しい場所に移動します。

  - 2 つのノードを接続するには、一方のノードの出力ターミナルを、もう一方のノードの入力ターミナルに移動します。 互換性のある種類のターミナルのみを接続することができます。 ターミナル間の線は、接続を示しています。

  - 接続を解除するには、接続されたターミナルのいずれかのショートカット メニューで、 **[リンクの解除]** を選択します。

  - ノードのプロパティを構成するには、ノードを選択し、 **[プロパティ]** ウィンドウで、プロパティの新しい値を指定します。

### <a name="preview-shaders"></a>シェーダーをプレビューする

アプリでシェーダーがどのように表示されるかを確認するため、効果のプレビュー方法を構成することができます。 アプリを概観するには、いくつかの描画図形のうちの 1 つを選択し、テクスチャやその他の素材のパラメーターを構成し、時間ベースの効果アニメーションを有効にし、さまざまな角度からプレビューを確認します。

#### <a name="shapes"></a>図形

シェーダー デザイナーには、シェーダーのプレビューに使用できる、球、直方体、円柱、円すい、ティーポット、および平面という 6 つの図形が用意されています。 シェーダーに応じて特定の図形を使用することで、より効果的なプレビューを表示できます。

プレビュー図形を選択するには、 **[シェーダー デザイナー モード]** ツール バーで、適切な図形を選びます。

#### <a name="textures-and-material-parameters"></a>テクスチャおよび素材パラメーター

シェーダーの多くは、テクスチャおよび素材プロパティを基盤として、アプリ内のオブジェクトの種類ごとに固有の外観を生成します。 アプリでシェーダーが表示される様子を確認するには、アプリで使用する可能性があるテクスチャおよびパラメーターに合うように、プレビューの描画に使用するテクスチャおよび素材プロパティを設定します。

別のテクスチャをテクスチャ レジスタにバインドする、または他の素材パラメーターを変更する方法:

1. **[選択]** モードで、デザイン サーフェイスの空の領域を選択します。 すると、 **[プロパティ]** ウィンドウにグローバル シェーダー プロパティが表示されます。

2. **[プロパティ]** ウィンドウで、変更するテクスチャおよびパラメーターのプロパティに新しい値を指定します。

変更可能なシェーダー パラメーターを次の表に示します。

|パラメーター|プロパティ|
|---------------|----------------|
|**テクスチャ 1** - **テクスチャ 8**|**アクセス**:                           このプロパティをモデル エディターから設定できるようにする場合は **Public**、それ以外の場合は **Private** です。<br /><br /> **ファイル名**:このテクスチャ レジスタに関連付けられているテクスチャ ファイルの完全パスです。|
|**素材: アンビエント**|**アクセス**:                           このプロパティをモデル エディターから設定できるようにする場合は **Public**、それ以外の場合は **Private** です。<br /><br /> **値**:間接光 (環境光) による、現在のピクセルの拡散色。|
|**素材: 拡散**|**アクセス**:このプロパティをモデル エディターから設定できるようにする場合は **Public**、それ以外の場合は **Private** です。<br /><br /> **値**:現在のピクセルによる直接光の拡散を示す色です。|
|**素材: 放射**|**アクセス**:                            このプロパティをモデル エディターから設定できるようにする場合は **Public**、それ以外の場合は **Private** です。<br /><br /> **値**:オブジェクト自体から放射される光による、現在のピクセルの色の効果。|
|**素材: 鏡面**|**アクセス**:                            このプロパティをモデル エディターから設定できるようにする場合は **Public**、それ以外の場合は **Private** です。<br /><br /> **値**:現在のピクセルによる直接光の反射を示す色です。|
|**素材: 反射の度合い**|**アクセス**:                           このプロパティをモデル エディターから設定できるようにする場合は **Public**、それ以外の場合は **Private** です。<br /><br /> **値**:現在のピクセルに対する反射の光源の輝度を定義する指数です。|

#### <a name="time-based-effects"></a>時間ベースの効果

シェーダーによっては、効果をアニメーション表示する、時間ベースのコンポーネントがあります。 アクションで効果が表示される様子を示すには、プレビューを 1 秒あたりに数回更新する必要があります。 既定では、シェーダーが変更されたときにのみ、プレビューが更新されます。時間ベースの効果を表示できるようにこの動作を変更するには、リアルタイム レンダリングを有効にする必要があります。

リアルタイム レンダリングを有効にするには、シェーダー デザイナー ツール バーで、 **[リアルタイム レンダリング]** を選択します。

#### <a name="examine-the-effect"></a>効果を確認する

多くのシェーダーは、視野角や指向性ライトなどの変数の影響を受けます。 これらの変数を変更することで効果に及ぶ影響を確認するには、プレビュー図形を自由に回転して、シェーダーの動きを確認します。

図形を回転するには、**Alt** キーを押しながら、デザイン サーフェス上の任意のポイントを選択して動かします。

### <a name="export-shaders"></a>シェーダーをエクスポートする

アプリでシェーダーを使用するには、その前に、DirectX が認識できる形式でシェーダーをエクスポートする必要があります。

シェーダーは、HLSL ソース コードまたはコンパイル済みシェーダー バイトコードとしてエクスポートできます。 HLSL ソース コードは、 *.hlsl* ファイル名拡張子の付いたテキスト ファイルにエクスポートされます。 シェーダー バイトコードは、 *.cso* ファイル名拡張子の付いた未処理のバイナリ ファイルにエクスポートするか、またはシェーダー バイトコードを配列にエンコードする C++ ヘッダー ( *.h*) ファイルにエクスポートすることができます。

シェーダーをエクスポートする方法の詳細については、「[方法:シェーダーをエクスポートする](../designers/how-to-export-a-shader.md)」を参照してください。

## <a name="keyboard-shortcuts"></a>キーボード ショートカット

|コマンド|キーボード ショートカット|
|-------------| - |
|**[選択]** モードに切り替え|**Ctrl** + **G**、**Ctrl** + **Q**<br /><br /> **S**|
|**[ズーム]** モードに切り替え|**Ctrl** + **G**、**Ctrl** + **Z**<br /><br /> **Z**|
|**[パン]** モードに切り替え|**Ctrl** + **G**、**Ctrl** + **P**<br /><br /> **K**|
|すべて選択|**Ctrl** + **A**|
|現在の選択範囲を削除します。|**削除**|
|現在の選択を取り消します。|**エスケープ** (**Esc**)|
|拡大表示|**Ctrl** + **マウス ホイール前方移動**<br /><br /> プラス記号 ( **+** )|
|ズーム アウト|**Ctrl** + **マウス ホイール後方移動**<br /><br /> マイナス記号 ( **-** )|
|デザイン サーフェイスを上にパン|**マウス ホイール後方移動**<br /><br /> **PageDown**|
|デザイン サーフェイスを下にパン|**マウス ホイール前方移動**<br /><br /> **PageUp**|
|デザイン サーフェイスを左にパン|**Shift** + **マウス ホイール後方移動**<br /><br /> **マウス ホイール左**<br /><br /> **Shift** + **PageDown**|
|デザイン サーフェイスを右にパン|**Shift** + **マウス ホイール前方移動**<br /><br /> **マウス ホイール右**<br /><br /> **Shift** + **PageUp**|
|キーボード フォーカスを別のノードに移動|**方向**キー|
|キーボード フォーカスのあるノードを選択 (選択グループにノードを追加)|**Shift** + **Space キー**|
|キーボード フォーカスのあるノードの選択を切り替える|**Ctrl** + **Space キー**|
|現在の選択を切り替える (ノードが選択されていない場合、キーボード フォーカスのあるノードを選択)|**Space キー**|
|現在の選択を上に移動|**Shift** + **↑ キー**|
|現在の選択を下に移動|**Shift** + **↓ キー**|
|現在の選択を左に移動|**Shift** + **← キー**|
|現在の選択を右に移動|**Shift** + **→ キー**。|

## <a name="related-topics"></a>関連トピック

|Title|説明|
|-----------|-----------------|
|[ゲームとアプリ用の 3D アセットの操作](../designers/working-with-3-d-assets-for-games-and-apps.md)|テクスチャ、イメージ、3D モデル、およびシェーダー効果の操作に使用できる Visual Studio のツールの概要を説明します。|
|[Image Editor](../designers/image-editor.md)|Visual Studio イメージ エディターを使用してテクスチャとイメージを操作する方法について説明します。|
|[モデル エディター](../designers/model-editor.md)|Visual Studio モデル エディターを使って 3D モデルを操作する方法について説明します。|
