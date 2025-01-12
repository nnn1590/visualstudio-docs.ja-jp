---
title: IActiveScriptAuthor::GetEventHandler |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7bba60df6485ddaac0363a3416739efd7be69389
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935634"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
指定された属性を持つスクリプトレットを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdisp`  
 [in]`IDispatch`に対応するオブジェクト、`NamedItem`スクリプトレットがアタッチされます。  
  
 `pszItem`  
 [in]ホストでスクリプトレットの完全修飾の名前の最上位レベルの識別子のバッファーのアドレス。  
  
 `pszSubItem`  
 [in]ホストでスクリプトレットの完全修飾の名前の 2 番目のレベルの識別子のバッファーのアドレス。 名前に 1 つだけのレベルがある場合は NULL に設定します。  
  
 `pszEvent`  
 [in]イベントの名前を格納するバッファーのアドレス。 スクリプトレットは、このイベントのイベント ハンドラーです。  
  
 `ppse`  
 [out]ポインターを受け取る変数のアドレス、`IScriptEntry`を指定された属性を持つスクリプトレットのインターフェイス。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)