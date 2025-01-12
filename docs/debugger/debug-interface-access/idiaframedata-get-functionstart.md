---
title: Idiaframedata::get_functionstart |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43c825bd621ada3f3e81d76f09a1f4bf9e30a67e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839980"
---
# <a name="idiaframedatagetfunctionstart"></a>IDiaFrameData::get_functionStart
ブロックが関数のエントリ ポイントを含むかどうかを示すフラグを取得します。

## <a name="syntax"></a>構文

```C++
HRESULT get_functionStart ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>パラメーター
 `pRetVal`

[out]返します`TRUE`ブロックには、エントリ ポイントが含まれている場合を返しますそれ以外の場合`FALSE`します。

## <a name="return-value"></a>戻り値
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。

## <a name="remarks"></a>Remarks
 フレームを表す、インライン メソッドや関数の関数に挿入されるため、関数の開始をできないスタック フレームのことができます。

## <a name="see-also"></a>関連項目
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)