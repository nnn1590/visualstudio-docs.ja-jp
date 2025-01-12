---
title: 従来の言語サービスのモデル |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6efe97e0a6ca5d2188aee9d44246f1d9fb347cda
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326773"
---
# <a name="model-of-a-legacy-language-service"></a>従来の言語サービスのモデル
言語サービスは、要素と、特定の言語の機能を定義し、その言語に固有の情報に、エディターを提供するために使用します。 たとえば、エディターでは、構文の色分けをサポートするために、要素と言語のキーワードを把握する必要があります。

 言語サービスは、エディターと、エディターを含むビューによって管理されるテキスト バッファーと密接に連携します。 Microsoft IntelliSense**クイック ヒント**オプションは、言語サービスによって提供される機能の例を示します。

## <a name="a-minimal-language-service"></a>最小言語サービス
 最も基本的な言語サービスには、次の 2 つのオブジェクトが含まれています。

- *言語サービス*実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>インターフェイス。 言語サービスでは、名前、ファイル名拡張子、コード ウィンドウ マネージャー、および colorizer を含め、c# 言語に関する情報があります。

- *Colorizer*実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>インターフェイス。

  次の概念図は、基本的な言語サービスのモデルを示しています。

  ![言語サービス モデル グラフィック](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")基本的な言語サービス モデル

  ドキュメント ウィンドウのホスト、*ドキュメント ビュー*ここでは、エディターの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]のコア エディター。 ドキュメントの表示とテキスト バッファーは、エディターによって所有されます。 これらのオブジェクトが使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]と呼ばれる特殊なドキュメント ウィンドウで、*コード ウィンドウ*します。 コード ウィンドウに含まれている、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>が作成され、IDE によって制御されるオブジェクト。

  エディターはその拡張機能に関連付けられた言語サービスを検索し、呼び出すことによって、コード ウィンドウに渡します特定の拡張子を持つファイルが読み込まれるときに、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>メソッド。 言語サービスを返します、*コード ウィンドウ マネージャー*、実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>インターフェイス。

  次の表では、モデル内のオブジェクトの概要を示します。

| コンポーネント | Object | 関数 |
|------------------| - | - |
| テキスト バッファー | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Unicode の読み取り/書き込みテキスト ストリーム。 その他のエンコーディングを使用するテキストのことができます。 |
| コード ウィンドウ | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | ドキュメントのウィンドウで、1 つまたは複数のテキスト ビューが含まれています。 ときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]がマルチ ドキュメント インターフェイス (MDI) モードではコード ウィンドウが MDI 子。 |
| テキスト ビュー | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | ユーザーが移動し、キーボードとマウスを使用してテキストを表示できるウィンドウです。 テキスト ビューは、エディターとしてユーザーに表示されます。 通常のエディター ウィンドウ、出力ウィンドウやイミディ エイト ウィンドウのテキスト ビューを使用することができます。 さらに、コード ウィンドウ内の 1 つまたは複数のテキスト ビューを構成できます。 |
| テキスト マネージャー | によって管理される、<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>から取得する、サービス、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>ポインター | 前に説明したすべてのコンポーネントによって共有される一般的な情報を保持するコンポーネント。 |
| 言語サービス | 実装に依存します。実装します。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | 構文の強調表示、ステートメント入力候補、およびかっこの照合などの言語に固有の情報で、エディターを提供するオブジェクト。 |

## <a name="see-also"></a>関連項目
- [カスタム エディターでのドキュメント データとドキュメント ビュー](../../extensibility/document-data-and-document-view-in-custom-editors.md)