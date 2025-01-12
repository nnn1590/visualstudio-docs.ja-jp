---
title: CA1600:アイドル状態のプロセス優先度を使用しません
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c37affc585653807912d00c1cfe365853fd6260b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921807"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600:アイドル状態のプロセス優先度を使用しません

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Category|Microsoft モビリティ|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
このルールは、プロセスがに`ProcessPriorityClass.Idle`設定されている場合に発生します。

## <a name="rule-description"></a>規則の説明
プロセス優先順位に Idle を設定しないでください。 が`System.Diagnostics.ProcessPriorityClass.Idle`あるプロセスは、CPU がアイドル状態になると CPU を占有するため、スタンバイをブロックします。

## <a name="how-to-fix-violations"></a>違反の修正方法
プロセスをに`ProcessPriorityClass.BelowNormal`設定します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
このルールは、アイドル状態のプロセスの優先順位が必要で、モビリティに関する考慮事項を安全に無視できる場合にのみ抑制する必要があります。