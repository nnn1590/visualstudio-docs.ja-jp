﻿---
title: ManagedType |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagManagedType symbol
- managed type symbol
- ManagedType symbol
ms.assetid: 5db99e2a-4f2e-4796-89b7-b401b151826f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0c121e996972b47a91a018d910a5d3677cb4cffa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855204"
---
# <a name="managedtype"></a>ManagedType
マネージ型 (メタデータ、または c# などの言語のメモリとリソースの管理機能をネイティブで定義されたシンボル) によって識別されます、`SymTagManagedType`シンボル。

## <a name="properties"></a>プロパティ
 次の表では、この記号の型の有効な追加のプロパティを示します。

|プロパティ|データの種類|説明|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|マネージ シンボルの名前です。|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックス ID。|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|返します`SymTagManagedType`(の 1 つ、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)値)。|

## <a name="see-also"></a>関連項目
- [シンボル型のクラス階層](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)