---
title: コンテキスト メニュー (XML スキーマ エクスプ ローラー) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d6c14a268ef58dec31f65fe73e176eac8f690d9c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157746"
---
# <a name="context-menus-xml-schema-explorer"></a>コンテキスト メニュー (XML スキーマ エクスプローラー)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

次のコンテキスト メニュー項目は、スキーマ固有の検索やその他の操作を実行するために使用します。  
  
## <a name="node-type-schema-set"></a>ノードの種類:スキーマ セット  
 スキーマ セット ノードに使用できるオプションを次の表に示します。  
  
|オプション|説明|  
|------------|-----------------|  
|**最も可能性の高いルート要素を表示します。**|グローバル要素のうち、それ自体以外のグローバル要素からは参照されていないものをすべて検索して強調表示します。|  
|**グローバル型を表示します。**|スキーマ セット内のすべてのグローバル型を検索して強調表示します。|  
|**グローバル要素を表示します。**|スキーマ セット内のすべてのグローバル要素を検索して強調表示します。|  
|**[プロパティ] ウィンドウ**|開く、**プロパティ**ウィンドウ (は既に開かれていない) 場合。 このウィンドウには、ノードに関する情報が表示されます。|  
  
## <a name="node-type-namespace"></a>ノードの種類:名前空間  
 名前空間ノードに使用できるオプションを次の表に示します。  
  
|オプション|説明|  
|------------|-----------------|  
|**すべての着信参照を表示します。**|選択した名前空間がインポートされるファイルを検索して強調表示します。|  
|**すべての発信参照を表示します。**|選択した名前空間のすべてのファイルについて、以下のものを検索して強調表示します。<br /><br /> 、参照されているすべての名前空間なしのステートメントのインポート、`schemaLocation`属性。<br />の指定されている選択した 1 つ以外の名前空間すべてのファイル、`schemaLocation`インポート属性および include ステートメント。|  
|**グローバル型を表示します。**|選択した名前空間内のすべてのグローバル型を検索して強調表示します。|  
|**グローバル要素を表示します。**|選択した名前空間内のすべてのグローバル要素を検索して強調表示します。|  
|**[プロパティ] ウィンドウ**|開く、**プロパティ**ウィンドウ (は既に開かれていない) 場合。 このウィンドウには、ノードに関する情報が表示されます。|  
  
## <a name="node-type-file"></a>ノードの種類:File  
 ファイル ノードに使用できるオプションを次の表に示します。  
  
|オプション|説明|  
|------------|-----------------|  
|**すべての着信参照を表示します。**|選択したファイルが include ステートメントおよび import ステートメントの `schemaLocation` 属性で指定されたすべてのファイルを検索して強調表示します。|  
|**すべての発信参照を表示します。**|以下のものを検索して強調表示します。<br /><br /> 、すべての名前空間属性で指定されたすべての名前空間インポート ステートメントがない、`schemaLocation`属性。<br />-すべてのファイルで指定された、`schemaLocation`インポート ステートメントおよび include ステートメントのすべての属性。|  
|**グローバル型を表示します。**|このファイル内のすべてのグローバル型を検索して強調表示します。|  
|**グローバル要素を表示します。**|このファイル内のすべてのグローバル要素を検索して強調表示します。|  
|**[コードの表示]**|選択したノードを含むファイルが XML エディターで開きます。 XML エディターには、XML スキーマ エクスプローラーで選択されている項目も表示されます。|  
|**[プロパティ] ウィンドウ**|開く、**プロパティ**ウィンドウ (は既に開かれていない) 場合。 このウィンドウには、ノードに関する情報が表示されます。|  
  
## <a name="all-global-node-types"></a>すべてのグローバル ノード型  
 すべてのグローバル ノードに使用できるオプションを次の表に示します。  
  
|オプション|説明|  
|------------|-----------------|  
|**グラフ ビューで表示します。**|グラフ ビューを開きます。 選択したノードがワークスペースにない場合、ワークスペースにそのノードが追加されて選択されます。|  
|**コンテンツ モデル ビューで表示します。**|コンテンツ モデル ビューを開きます。 選択したノードがワークスペースにない場合、ワークスペースにそのノードが追加されて選択されます。|  
|**[コードの表示]**|選択したノードを含むファイルが XML エディターで開きます。 XML エディターには、XML スキーマ エクスプローラーで選択されている項目も表示されます。|  
|**[プロパティ] ウィンドウ**|開く、**プロパティ**ウィンドウ (は既に開かれていない) 場合。 このウィンドウには、ノードに関する情報が表示されます。|  
  
## <a name="node-type-element"></a>ノードの種類:要素  
 要素ノードのコンテキスト メニューには、前述のグローバル ノード オプションに加えて、次のオプションがあります。  
  
|オプション|説明|  
|------------|-----------------|  
|**型定義へ移動**|選択した要素の型定義に移動します。 これは、要素に使用されている型がグローバル型の場合に適用されます。|  
|**元の要素に移動します。**|要素の参照のために、要素の実際の定義に移動します。|  
|**すべての参照を表示します。**|グローバル要素について、選択した要素への参照 (`ref="selectedElement"` が指定された要素) をすべて検索して強調表示します。|  
|**代替グループのメンバーの表示**|代替グループの先頭について、選択した要素が属する代替グループのメンバーであるすべての要素を検索して強調表示します。 直接および間接の参加要素が表示されます。|  
|**表示する代替グループの先頭**|代替グループのメンバーであるグローバル要素について、選択した要素の直接および間接の先頭をすべて検索して強調表示します。たとえば、次のようなものが含まれます。<br /><br /> -代替グループの先頭、選択した要素で指定します。<br />-代替グループの先頭の head 要素で指定します。|  
|**サンプル XML を生成します。**|グローバル要素でのみ使用できます。 グローバル要素のサンプル XML ファイルを生成します。|  
  
## <a name="node-type-global-types"></a>ノードの種類:グローバル型  
 グローバル型ノードのコンテキスト メニューには、前述のグローバル ノード オプションに加えて、次のオプションがあります。  
  
|オプション|説明|  
|------------|-----------------|  
|**基本型を表示します。**|選択した型がグローバル型から派生している場合に、選択した型の基本型に移動します。|  
|**すべての参照を表示します。**|選択した型へのすべての参照を検索して強調表示します。 これには、選択した型および選択した型から派生した型の要素と属性が含まれます。|  
|**すべての派生型の表示**|選択した型から直接または間接的に派生したすべての型を検索して強調表示します。|  
|**すべての先祖を表示します。**|親の型 (基本型) をすべて表示します。|  
  
## <a name="node-type-attribute"></a>ノードの種類:属性  
 属性ノードのコンテキスト メニューには、前述のグローバル ノード オプションに加えて、次のオプションがあります。  
  
|オプション|説明|  
|------------|-----------------|  
|**型定義へ移動**|属性に使用されている型がグローバル型である場合に、選択した属性の型定義に移動します。|  
|**元の属性へ移動します。**|属性の参照のために、属性の実際の定義に移動します。|  
|**すべての参照を表示します。**|グローバル属性について、選択した属性への参照 (`ref="selectedAttribute"` が指定された他の属性) をすべて検索して強調表示します。|  
  
## <a name="node-type-attribute-group"></a>ノードの種類:属性グループ  
 属性グループ ノードのコンテキスト メニューには、前述のグローバル ノード オプションに加えて、次のオプションがあります。  
  
|オプション|説明|  
|------------|-----------------|  
|**定義に移動**|参照のために、属性の実際の定義に移動します。|  
|**すべてのメンバーを表示します。**|属性グループのすべてのメンバーを検索して強調表示します。|  
|**すべての参照を表示します。**|選択した属性グループへの参照 (`ref="selectedAttributeGroup"` が指定された属性グループ) をすべて検索して強調表示します。|  
  
## <a name="node-type-named-group"></a>ノードの種類:名前付きグループ  
 名前付きグループ ノードのコンテキスト メニューには、前述のグローバル ノード オプションに加えて、次のオプションがあります。  
  
|オプション|説明|  
|------------|-----------------|  
|**定義に移動**|参照のために、属性の実際の定義に移動します。|  
|**すべてのメンバーを表示します。**|名前付きグループのすべてのメンバーを検索して強調表示します。|  
|**すべての参照を表示します。**|選択したグループへの参照 (`ref="selectedGroup"` が指定されたグループ) をすべて検索して強調表示します。|  
  
## <a name="see-also"></a>関連項目  
 [XML スキーマ エクスプ ローラー](../xml-tools/xml-schema-explorer.md)   
 [スキーマ セットの検索](../xml-tools/searching-the-schema-set.md)
