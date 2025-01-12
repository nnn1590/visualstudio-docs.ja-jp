---
title: Event Tracing for Windows (ETW) レポート | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d13a3db996537005c0d4ec67b85c185ac2841cc0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447254"
---
# <a name="event-tracing-for-windows-etw-report"></a>ETW (Event Tracing for Windows) レポート
Windows イベント トレーシング (ETW) レポートには、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイル ツールのパフォーマンス セッションで記録された ETW イベントが一覧表示されます。 ETW データはバイナリ (.*etl*) ファイルで収集されます。

> [!NOTE]
> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] インターフェイスでは ETW レポートを表示できません。

- [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] インターフェイスのプロファイル ツールを利用して ETW データを収集する方法については、「[方法:ETW (Event Tracing for Windows) データを収集する](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)」を参照してください。

- [VSPerfCmd](../profiling/vsperfcmd.md) コマンド ライン ツールを利用して ETW データを収集する方法については、「[Events](../profiling/events-vsperfcmd.md)」を参照してください。

- ETW レポートは **VSReport/Summary:ETW** コマンドを利用して生成します。 詳細については、「[VSPerfReport](../profiling/vsperfreport.md)」を参照してください。

|Column|説明|
|------------|-----------------|
|**タイムスタンプ**|イベントが発生した日時を識別します。|
|**プロセス ID**|イベントを生成したプロセスを識別します。|
|**スレッド ID**|イベントを生成したスレッドを識別します。|
|**説明**|イベント プロバイダーを識別します。|
|**Type**|イベントの種類を識別します。|
|**プロパティ**|イベントのプロパティ。 各イベントは角かっこで囲まれた名前と値のペアになり、コンマで区切られます。|