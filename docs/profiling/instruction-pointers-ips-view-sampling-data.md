---
title: 命令ポインター (IP) ビュー - サンプリング データ | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 579887c22df16d555c3f309b4326740060aefc1f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442235"
---
# <a name="instruction-pointers-ips-view---sampling-data"></a>命令ポインター (IP) ビュー - サンプリング データ
サンプリング データの IP ビューには、プロファイルを実行してサンプルを収集したときに直接実行したアセンブリ命令のパフォーマンス データが一覧表示されます。

> [!NOTE]
> Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。 UWP アプリにも新しい収集手法が必要です。 「[Windows 8 および Windows Server 2012 アプリケーションのパフォーマンス ツール](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。

|Column|説明|
|------------|-----------------|
|**プロセス ID**|プロファイリング実行のプロセス ID (PID) です。|
|**プロセス名**|プロセスの名前です。|
|**モジュール名**|命令を含むモジュールの名前。|
|**モジュール パス**|命令を含むモジュールのパスです。|
|**ソース ファイル**|命令を含むソース ファイルです。|
|**関数名**|命令を含む関数の名前です。|
|**関数行番号**|ソース ファイルでのこの関数の開始行番号です。|
|**関数アドレス**|読み込まれたバイナリ内の関数の開始メモリ アドレス。|
|**ソース開始行**|このサンプルが収集されたソース ファイル内の開始行番号です。|
|**ソース終了行**|このサンプルが収集されたソース ファイル内の終了行番号です。|
|**ソース開始文字番号**|このサンプルが収集されたソース ファイル行内の開始文字のオフセットです。|
|**ソース終了文字番号**|このサンプルが収集されたソース ファイル行内の終了文字のオフセットです。|
|**命令ポインター アドレス**|読み込まれたバイナリ内の命令のアドレスです。|
|**サンプル数 (関数のみ)**|命令を実行していたときに収集されたサンプルの合計数です。|
|**サンプル % (関数のみ)**|命令を実行していたときに収集された、プロファイル実行内のすべてのサンプルの割合です。|

## <a name="see-also"></a>関連項目
- [命令ポインター (IP) ビュー - サンプリング](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)