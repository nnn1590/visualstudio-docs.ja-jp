---
title: IDiaLoadCallback2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: daf0b48aca06b404824059030052223a8545a6b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839707"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
DIA シンボル プロシージャを検索する特定のプロセスに適用される制限のことからには、コールバックを受信します。

## <a name="syntax"></a>構文

```
IDiaLoadCallback2 : IDiaLoadCallback
```

## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド
 内のメソッドだけでなく、 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)インターフェイスでは、このインターフェイスは、次のメソッドを公開します。

|メソッド|説明|
|------------|-----------------|
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|元のデバッグ ディレクトリに .pdb ファイルを検索する場合を決定します。|
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|.Exe ファイルが配置されるパスで .pdb ファイルを検索が許可されているかどうかを決定します。|
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|.Dbg ファイルからデバッグ情報を探すことが許可されているかどうかを決定します。|
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|システム ルート ディレクトリで .pdb ファイルの検索を許可するかどうかを決定します。|

## <a name="remarks"></a>Remarks
 クライアント アプリケーションは、このインターフェイスを実装しへの呼び出しでの参照を提供します、 [idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)メソッド。 すべてのメソッドの実装に注意してください、 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)インターフェイスもします。

## <a name="requirements"></a>必要条件
 ヘッダー:Dia2.h

 ライブラリ: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>関連項目
- [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)