---
title: Idiasession::getenumtables |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumTables method
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 759972fa02c7645ae457e0b715d835b2d717e26f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839174"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
シンボル ストアに含まれているすべてのテーブルの列挙子を取得します。

## <a name="syntax"></a>構文

```C++
HRESULT getEnumTables (
    IDiaEnumTables** ppEnumTables
);
```

#### <a name="parameters"></a>パラメーター
`ppEnumTables`

[out]返します、 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)オブジェクト。 シンボル ストア内のテーブルを列挙するのにには、このインターフェイスを使用します。

## <a name="return-value"></a>戻り値
成功した場合、返します`S_OK`、それ以外のエラー コードを返します。

## <a name="example"></a>例
この例で使用する一般的な関数、`getEnumTables`特定の列挙子オブジェクトを取得するメソッド。 関数が、必要なインターフェイスにキャスト可能なポインターを返します、列挙子が見つかった場合関数を返しますそれ以外の場合、`NULL`します。

```C++
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)
{
    IUnknown *pUnknown = NULL;
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumTables> pEnumTables;
        if (pSession->getEnumTables(&pEnumTables) == S_OK)
        {
            CComPtr<IDiaTable> pTable;
            DWORD celt = 0;
            while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&
                  celt == 1)
            {
                if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)
                {
                    break;
                }
                pTable = NULL;
            }
        }
    }
    return(pUnknown);
}
```

## <a name="see-also"></a>関連項目
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
