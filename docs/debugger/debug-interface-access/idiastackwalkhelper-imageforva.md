---
title: Idiastackwalkhelper::imageforva |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56f71364f28bec56c058a52f5a9e79c6bba298b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837954"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
メモリの指定実行可能ファイルのメモリ領域で仮想アドレスをどこかで実行可能ファイルのイメージの開始を返します。

## <a name="syntax"></a>構文

```C++
HRESULT imageForVA(
   ULONGLONG  vaContext,
   ULONGLONG *pvaImageStart
);
```

#### <a name="parameters"></a>パラメーター
 `vaContext`

[in]どこかで実行可能ファイルの領域にある仮想アドレス。

 `pvaImageStart`

[out]実行可能ファイルのイメージの開始仮想アドレスを返します。

## <a name="return-value"></a>戻り値
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。

## <a name="see-also"></a>関連項目
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)