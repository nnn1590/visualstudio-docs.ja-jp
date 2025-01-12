---
title: SccQueryChanges 関数 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e2b1e504bef3ec9507afcddf4f75bc5f697e843
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353513"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges 関数
この関数は、指定されたコールバック関数を使用して各ファイルの名前変更に関する情報を提供する、ファイルの一覧を列挙します。

## <a name="syntax"></a>構文

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>パラメーター
 pContext

[in]ソース管理プラグインのコンテキストのポインター。

 nFiles

[in]ファイルの数`lpFileNames`配列。

 lpFileNames

[in]に関する情報を取得するファイル名の配列。

 pfnCallback

[in]リスト内の各ファイル名を呼び出すためのコールバック関数 (を参照してください[QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)詳細については)。

 pvCallerData

[in]コールバック関数に渡される値は変更されません。

## <a name="return-value"></a>戻り値
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。

|[値]|説明|
|-----------|-----------------|
|SCC_OK|クエリの処理が正常に完了しました。|
|SCC_E_PROJNOTOPEN|ソース管理で、プロジェクトが開かれていません。|
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。|
|SCC_E_NONSPECIFICERROR|指定されていないか、一般的なエラーが発生しました。|

## <a name="remarks"></a>Remarks
 名前空間に変更を照会する。 具体的には、名前変更、追加、およびファイルを削除します。

## <a name="see-also"></a>関連項目
- [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [エラー コード](../extensibility/error-codes.md)