﻿---
title: グラフィックス ピクセル履歴 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23ada46a28d692daf238147ea07f34d440a99869
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388596"
---
# <a name="graphics-pixel-history"></a>グラフィックス ピクセル履歴
Visual Studio Graphics Analyzer の [ピクセル履歴] ウィンドウでは、特定のピクセルが、ゲームまたはアプリのフレームの生成中に発生する Direct3D イベントによってどのように影響を受けるかを理解できます。

 [ピクセル履歴] ウィンドウを次に示します。

 ![その履歴に次の 3 つの Direct3D イベントがあるピクセル。](media/gfx_diag_demo_pixel_history_orientation.png "gfx_diag_demo_pixel_history_orientation")

## <a name="understanding-the-pixel-history-window"></a>[ピクセル履歴] ウィンドウについて
 [ピクセル履歴] を使用すると、レンダー ターゲットの特定のピクセルが、特定のフレームの処理で Direct3D イベントの影響をどのように受けたかを分析できます。 ピクセルの最終的なカラー値が、後続のイベントまたは同じイベント内の後続のプリミティブによって変更された場合でも、レンダリングに関する問題の発生元である Direct3D イベントを正確に特定できます。 たとえば、ピクセルが正しくレンダリングされず、その色がフレームバッファー内で別の半透明ピクセルの色と混ざり合うことによって、あいまいになる場合があります。 レンダー ターゲットの最終的な内容だけを手がかりに、このような問題を診断することは困難です。

 [ピクセル履歴] ウィンドウには、選択したフレームの処理におけるピクセルの完全な履歴が表示されます。 ウィンドウの上部にある **[最終フレーム バッファー]** には、フレームの最後でフレーム バッファーに書き込まれた色だけでなく、レンダリング元のフレームや画面座標など、ピクセルに関する追加情報が表示されます。 この領域には、**[アルファの描画]** チェック ボックスも含まれています。 このチェック ボックスがオンになっている場合、**[最終フレーム バッファー]** の色と中間のカラー値が、チェッカー ボード パターンを使用して透明に表示されます。 このチェック ボックスがオフの場合、カラー値のアルファ チャネルは無視されます。

 ウィンドウの下部には、ピクセルの色に影響を与える可能性があったイベントと、フレーム バッファー内のピクセルの初期カラー値と最終カラー値を表す **[初期]** および **[最終]** 擬似イベントが表示されます。 初期カラー値は、ピクセルの色を変更した最初のイベントによって決定されます (通常は `Clear` イベント)。 ピクセル履歴には、他のイベントがそのピクセルに影響を与えなかった場合でも、これら 2 つの擬似イベントが常に含まれます。 他のイベントがピクセルに影響を与える可能性があった場合、それらは **[初期]** イベントと **[最終]** イベントの間に表示されます。 イベントを展開すると、それらの詳細を表示できます。 レンダー ターゲットをクリアするイベントなど、単純なイベントが影響を与えるのはカラー値だけです。 描画呼び出しなどのより複雑なイベントは、ピクセルの色に影響を与える可能性がある、1 つ以上のプリミティブを生成します。

 イベントによって描画されたプリミティブは、それらのプリミティブ型とインデックス、およびオブジェクトの合計プリミティブ数によって識別されます。 たとえば、**三角形 (1456) / (6214)** のような識別子は、プリミティブが 6214 個の三角形で構成されるオブジェクトの 1456 番目の三角形に対応することを意味します。 各プリミティブ識別子の左側には、プリミティブがピクセルに与えた影響を要約するアイコンが表示されます。 ピクセルの色に影響を与えるプリミティブは、結果の色で塗りつぶされた角丸四角形で表されます。 ピクセルの色に影響を与えるプリミティブから除外されるプリミティブは、そのピクセルが除外された理由を示すアイコンで表されます。 これらのアイコンについては、この記事で後述する「[プリミティブの除外](#exclusion)」を参照してださい。

 各プリミティブを展開すると、ピクセル シェーダーの出力が、どのように既存のピクセルの色にマージされ、結果の色が作成されたかを調べることができます。 ここでは、プリミティブに関連付けられているピクセル シェーダーのコードを確認またはデバッグしたり、頂点シェーダー ノードをさらに展開して、頂点シェーダーの入力を確認したりすることもできます。

### <a name="exclusion"></a>プリミティブの除外
 プリミティブがピクセルの色に影響を与えるプリミティブから除外される場合、その除外の理由はさまざまです。 それぞれの理由は、次の表に記載されているアイコンで表されます。

|アイコン|除外の理由|
|----------|--------------------------|
|![深度テスト エラーのアイコン。](media/vsg_hist_icon_failed_depth.png "vsg_hist_icon_failed_depth")|ピクセルは深度テストに失敗したため除外されました。|
|![ハサミ テスト エラーのアイコン。](media/vsg_hist_icon_failed_scissor.png "vsg_hist_icon_failed_scissor")|ピクセルはハサミ テストに失敗したため除外されました。|
|![ステンシル テスト エラーのアイコン。](media/vsg_hist_icon_failed_stencil.png "vsg_hist_icon_failed_stencil")|ピクセルはステンシル テストに失敗したため除外されました。|

### <a name="draw-call-exclusion"></a>描画呼び出しの除外
 描画呼び出し内のすべてのプリミティブが、テストに失敗したことが原因で、レンダー ターゲットに影響を与えるプリミティブから除外された場合、その描画呼び出しは展開できず、除外の理由に対応するアイコンが、描画呼び出しの横に表示されます。 描画呼び出しの除外の理由は、プリミティブの除外の理由と似ており、そのアイコンも似ています。

### <a name="viewing-and-debugging-shader-code"></a>シェーダー コードの表示およびデバッグ
 シェーダーに関連付けられたプリミティブの下にあるコントロールを使用して、頂点、ハル、ドメイン、ジオメトリ、およびピクセルの各シェーダーのコードをデバッグできます。

##### <a name="to-view-a-shaders-source-code"></a>シェーダーのソース コードを表示するには

1. **[グラフィックス ピクセル履歴]** ウィンドウで、調査するシェーダーに対応する描画呼び出しを見つけ、それを展開します。

2. 展開した描画呼び出しの下で、該当する問題を示しているプリミティブを選択して展開します。

3. 調査しているプリミティブの下で、シェーダーのステージ タイトルのリンク先を表示します。たとえば、リンク **[頂点シェーダー obj:30]** をクリックし、頂点シェーダーのソース コードを表示します。

    > [!TIP]
    > オブジェクト番号 **obj:30** では、オブジェクト テーブルやパイプライン ステージ ウィンドウなどの Graphics Analyzer インターフェイス全体でこのシェーダーが識別されます。

##### <a name="to-debug-a-shader"></a>シェーダーをデバッグするには

1. **[グラフィックス ピクセル履歴]** ウィンドウで、調査するシェーダーに対応する描画呼び出しを見つけ、それを展開します。

2. 次に、展開した描画呼び出しの下で、該当する問題を示しているプリミティブを選択して展開します。

3. 調査しているプリミティブの下で **[デバッグ開始]** をクリックします。 HLSL デバッガーへのこのエントリ ポイントは、既定で、対応するプリミティブに対するシェーダーの最初の呼び出しに設定されます。つまり、このシェーダーによって処理される最初のピクセルまたは頂点です。 プリミティブに関連付けられるピクセルは 1 つだけですが、直線や三角形に対しては複数の頂点シェーダーが呼び出されます。

     特定の頂点に対する頂点シェーダーの呼び出しをデバッグするには、VertexShader タイトル リンクを展開し、調査する頂点を見つけて選択し、その隣にある **[デバッグ開始]** をクリックします。

### <a name="links-to-graphics-objects"></a>グラフィックス オブジェクトへのリンク
 ピクセル履歴のグラフィック イベントについて理解するために、イベントの発生時点におけるデバイスの状態や、そのイベントで参照されている Direct3D オブジェクトに関する情報が必要になる場合があります。 **[グラフィックス ピクセル履歴]** では、ピクセル履歴内のイベントごとに、その時点のデバイスの状態と関連オブジェクトへのリンクが提供されます。

## <a name="see-also"></a>関連項目
- [チュートリアル: デバイス状態によるオブジェクトの不足](walkthrough-missing-objects-due-to-device-state.md)
- [チュートリアル: 網かけによるレンダリング エラーのデバッグ](walkthrough-debugging-rendering-errors-due-to-shading.md)
