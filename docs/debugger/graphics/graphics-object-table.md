﻿---
title: グラフィックス オブジェクト テーブル |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20a78d7bb3e27ddfd0a5a248436b5c5392558410
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848422"
---
# <a name="graphics-object-table"></a>グラフィックス オブジェクト テーブル
Visual Studio のグラフィックス分析に含まれるグラフィックス オブジェクト テーブルは、ゲームまたはアプリのフレームをサポートする Direct3D オブジェクトについて理解するために役立ちます。

 グラフィックス オブジェクト テーブルを次に示します。

 ![アプリによって作成された Direct3D オブジェクト](media/gfx_diag_demo_object_table_orientation.png "gfx_diag_demo_object_table_orientation")

## <a name="understanding-the-graphics-object-table"></a>グラフィックス オブジェクト テーブルについて
 オブジェクト テーブルを使用すると、特定のフレームのレンダリングをサポートする Direct3D のオブジェクトを解析できます。 プロパティとデータを調べることによってレンダリングの問題を特定のオブジェクトに絞り込むことができます (その時点までの診断で使用した他のグラフィックス診断ツールにより、リストを絞り込んで不要と思われるオブジェクトを除外できます)。問題のあるオブジェクトが見つかったら、その種類に固有の視覚化ツールを使用して調査できます。たとえば、テクスチャを表示するにはイメージ エディターを、バッファーの内容を表示するには*バッファー ビジュアライザー*を使用できます。

 オブジェクト テーブルは、コピーして貼り付ける操作をサポートしているため、Microsoft Excel などの別のツールを使用してその内容を調べることができます。

 また、使用することができます、**型**上部にあるドロップダウン リストの左上隅にある型のオブジェクトの表示を切り替える**バッファー**、**シェーダー**または**テクスチャ**、これらのすべての項目を一度にまたはします。  また、右上隅にある検索ボックスを使用するにはすべて表示されているデータの特定の行を検索します。  たとえばを検索することが*D32_FLOAT*一覧内でその形式のオブジェクトのすべてのインスタンスを検索します。

### <a name="graphics-object-table-format"></a>グラフィックス オブジェクト テーブルの形式
 オブジェクト テーブルには、選択したイベントに関連付けられたフレームをサポートする Direct3D のオブジェクトとリソース (状態オブジェクト、バッファー、シェーダー、テクスチャなど) が表示されます。 前のフレームで作成され、キャプチャされたフレームの間に使用されないオブジェクトは、オブジェクト テーブルから除外されます。 キャプチャされたフレームの間に、前のイベントによって破棄されたオブジェクトは、後続のイベントで除外されます。 D3D10Device または D3D11DeviceContext に設定されていないオブジェクトは灰色のテキストで表示されます。 オブジェクトは、テーブル形式で表示されます。

|Column|説明|
|------------|-----------------|
|**識別子**|オブジェクト ID。|
|**Name**|Direct3D 関数 `SetPrivateData` を使用してオブジェクトに設定されたアプリケーション固有の情報。通常は、オブジェクトに関する追加の識別情報が表示されます。|
|**Type**|オブジェクトの型。|
|**Active**|キャプチャされたフレームの間に D3D10Device または D3D11DeviceContext に設定されたオブジェクトの場合は "*" が表示されます。<br /><br /> これは灰色のテキストで表示されるオブジェクトに対応しますが、オブジェクト テーブルを並べ替えるのに役立つ列エントリが用意されています。|
|**Size**|オブジェクトのサイズ (バイト単位)。|
|**Format**|オブジェクトの形式。 たとえば、テクスチャ オブジェクトの形式や、シェーダー オブジェクトのシェーダー モデル。|
|**Width**|テクスチャ オブジェクトの幅。 他のオブジェクトの種類には適用されません。|
|**Height**|テクスチャ オブジェクトの高さ。 他のオブジェクトの種類には適用されません。|
|**Depth**|3-D テクスチャ オブジェクトの深さ。 テクスチャが 3-D でない場合、値は 0 です。 他のオブジェクトの種類には適用されません。|
|**Mips**|テクスチャ オブジェクトにある MIP レベルの数。 他のオブジェクトの種類には適用されません。|
|**ArraySize**|テクスチャ配列内のテクスチャの数。 範囲は、1 から、現在の機能レベルで定義されている上限までです。 キューブ マップの場合、この値は配列内のキューブ マップ数の 6 倍です。|
|**サンプル**|ピクセルあたりのマルチサンプルの数。|

## <a name="graphics-object-viewers"></a>グラフィックス オブジェクト ビューアー
 オブジェクトに関する詳細を表示するには、オブジェクト テーブルで名前を選択して開きます。 オブジェクトの詳細は、オブジェクトの種類によって異なる形式で表示されます。 たとえば、テクスチャはテクスチャ ビューアーを使用して表示され、D3D11 Device Context などのデバイスの状態は書式設定されたリストとして表示されます。 Direct3D はバージョンに応じてさまざまなオブジェクトを使用し、多くの場合、各バージョンで重要度の高いオブジェクトについて専用のビジュアライザーが用意されています。

 次のテクスチャ ビューアーには、出力マージャー パイプライン ステージの内容が表示されています。

 ![出力マージャーを表示するテクスチャのプレビュー](media/gfx_diag_texture_preview.png "gfx_diag_texture_preview")

### <a name="d3d12-command-list"></a>D3D12 のコマンド一覧
 Direct3D 12 では、コマンド一覧は、1 つの要求として GPU に送信できるように、コマンド アロケーターにコマンドを記録したオブジェクトです。 コマンド一覧は、通常、状態設定、描画、クリア、およびコピーの一連のコマンドを実行します。 これは、Direct3D 12 のレンダリングで推奨される方法であるため、特に重要です。また、複数のフレーム間で再利用できるため、パフォーマンスの向上に役立ちます。 コマンド一覧の詳細は新しいドキュメント ウィンドウに表示され、各パイプライン ステージに関連した情報がそれぞれのタブに表示されます。

### <a name="d3d12-pipeline-state-object-pso"></a>D3D12 パイプライン状態オブジェクト (PSO)
 Direct3D 12 で、パイプライン状態オブジェクトは GPU の状態の重要な部分を表しており、現在設定されているすべてのシェーダーと特定の固定機能の状態オブジェクトが含まれます。 いったん作成されたパイプライン状態オブジェクトは変更不能です。アプリケーションでパイプラインの構成を変更するには、異なるパイプライン状態オブジェクトをバインドするしか方法がありません。 PSO の詳細は、新しいドキュメント ウィンドウに表示され、パイプラインの構成の詳細が階層的にレイアウトされます。

### <a name="d3d12-root-signature"></a>D3D12 のルート署名
 Direct3D 12 で、ルート署名は、グラフィックス パイプラインまたは計算パイプラインにバインドされたすべてのリソースを定義したものであり、シェーダーが必要とするリソースにコマンド一覧をリンクします。 通常、1 つのアプリには、グラフィックス用に 1 つのルート署名と、計算用に 1 つのルート署名があります。 ルートの署名の詳細は、新しいドキュメント ウィンドウに表示され、ルート署名の詳細が階層的にレイアウトされます。

### <a name="d3d12-resources"></a>D3D12 のリソース
 Direct3D 12 では、リソースはレンダリング パイプラインにデータを提供する多目的オブジェクトです。これは、さまざまな種類とディメンションの専用オブジェクトを多数定義していた Direct3D11 とは対照的です。 Direct3D 12 のリソースには、テクスチャ データ、頂点データ、シェーダー データ、その他を含めることができ、さらには、深度バッファーなどのレンダー ターゲットを表すこともできます。 Direct3D 12 リソースの詳細は、新しいドキュメント ウィンドウに表示されます。リソース オブジェクトの内容を表示する時、グラフィックス分析では、内容の種類を判別できた場合、該当するビューアーが使用されます。 たとえば、テクスチャ データが含まれるリソース オブジェクトは、テクスチャ ビューアーを使用して表示されます (D3D11 のテクスチャ 2D オブジェクトと同様です)。

### <a name="device-context-object"></a>デバイス コンテキスト オブジェクト
 Direct3D 11 および Direct3D 10 では、デバイス コンテキスト (**D3D11 Device Context** または **D3D10 Device**) オブジェクトは、最も重要な状態情報を保持しているため特に重要であり、現在設定されている他の状態オブジェクトにリンクされます。 デバイス コンテキストの詳細が新しいドキュメント ウィンドウに表示され、そこで情報の各カテゴリがそれぞれのタブに示されます。新しいイベントが選択されると、デバイス コンテキストが現在のデバイスの状態を反映するように変更されます。

### <a name="buffer-object"></a>バッファー オブジェクト
 バッファー オブジェクトの詳細 (D3D11 バッファーまたは D3D10 バッファー) が、新しいドキュメント ウィンドウに表示されます。ウィンドウには、バッファーの内容がテーブルで示され、バッファーの内容を表示する方法を変更するためのインターフェイスが提供されます。 **バッファー データ** テーブルでは、Microsoft Excel などの別のツールを使用してその内容を調べることができるように、コピーと貼り付けがサポートされます。 バッファーの内容は、**バッファー データ** テーブルの上にある **[形式]** コンボ ボックスの値に従って解釈されます。 このボックスには、次の表のデータ型で構成される複合データ形式で入力できます。 たとえば、"float int" には 32 ビット浮動小数点値の後に 32 ビット符号付き整数値が続く構造体がリストに表示されます。 指定した複合データ形式はコンボ ボックスに追加され、後で使用できます。

 また、**[オフセットを表示する]** チェック ボックスを切り替えて、バッファー内の各要素のオフセットを表示または非表示にすることもできます。

|型|説明|
|----------|-----------------|
|**float**|32 ビット浮動小数点値。|
|**float2**|2 個の 32 ビット浮動小数点値を含むベクター。|
|**float3**|3 個の 32 ビット浮動小数点値を含むベクター。|
|**float4**|4 個の 32 ビット浮動小数点値を含むベクター。|
|**byte**|8 ビットの符号付き整数値。|
|**2byte**|16 ビットの符号付き整数値。|
|**4byte**|32 ビットの符号付き整数値。 **int** と同じです。|
|**8byte**|64 ビットの符号付き整数値。 **int64** と同じです。|
|**xbyte**|8 ビットの 16 進値。|
|**x2byte**|16 ビットの 16 進値。|
|**x4byte**|32 ビットの 16 進値。 **xint** と同じです。|
|**x8byte**|64 ビットの 16 進値。 **xint64** と同じです。|
|**ubyte**|8 ビットの符号なし整数値。|
|**u2byte**|16 ビットの符号なし整数値。|
|**u4byte**|32 ビットの符号なし整数値。 **uint** と同じです。|
|**u8byte**|64 ビットの符号なし整数値。 **uint64** と同じです。|
|**half**|16 ビット浮動小数点値。|
|**half2**|2 個の 16 ビット浮動小数点値を含むベクター。|
|**half3**|3 個の 16 ビット浮動小数点値を含むベクター。|
|**half4**|4 個の 16 ビット浮動小数点値を含むベクター。|
|**double**|64 ビット浮動小数点値。|
|**int**|32 ビットの符号付き整数値。 **4byte** と同じです。|
|**int64**|64 ビットの符号付き整数値。 **8byte** と同じです。|
|**xint**|32 ビットの 16 進値。 **x4byte** と同じです。|
|**xint64**|64 ビットの 16 進値。 **x8byte** と同じです。|
|**uint**|32 ビットの符号なし整数値。 **u4byte** と同じです。|
|**uint64**|64 ビットの符号なし整数値。 **u8byte** と同じです。|
|**bool**|ブール型 (`true` または `false`) の値。 それぞれのブール値は 32 ビット値によって表されます。|

## <a name="see-also"></a>関連項目
- [グラフィックス診断 (DirectX グラフィックスのデバッグ)](visual-studio-graphics-diagnostics.md)
- [チュートリアル: デバイス状態によるオブジェクトの不足](walkthrough-missing-objects-due-to-device-state.md)
