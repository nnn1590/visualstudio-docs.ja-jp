---
title: IDiaPropertyStorage::ReadLONG |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2fb277368e23cf51a4d3d3b69226ee6bf093d6c3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839616"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
読み取り`LONG`プロパティ セット内の値。

## <a name="syntax"></a>構文

```C++
HRESULT ReadDLONG ( 
   PROPID id,
   LONG*  pValue
);
```

#### <a name="parameters"></a>パラメーター
 `id`

[in]読み取るプロパティの識別子 (`PROPID`として WTypes.h で定義されている、 `ULONG`)。

 `pValue`

[out]プロパティ値を返します。

## <a name="return-value"></a>戻り値
 成功した場合、返します`S_OK`。 それ以外の場合はエラー コードを返します。 返します`E_INVALIDARG`型のプロパティがない場合`LONG`します。

## <a name="remarks"></a>Remarks
 A `LONG` 32 ビット符号付き整数としての Windows によって定義されます。

## <a name="see-also"></a>関連項目
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)