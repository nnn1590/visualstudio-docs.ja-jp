---
title: AutoMark | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d2bbd33308ddf14f14746db7f5c2c4ada6826b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62776986"
---
# <a name="automark"></a>AutoMark
**AutoMark** オプションは、Windows ソフトウェア パフォーマンス カウンター イベントを収集する間隔をミリ秒単位で指定します。 Windows パフォーマンス カウンターは **WinCounter** オプションで指定されます。

 **AutoMark** オプションはコマンド ラインで 1 つだけ指定できます。 **AutoMark** によって指定される **WinCounter** サンプリング間隔はメインのサンプリング間隔には依存しません。

## <a name="syntax"></a>構文

```cmd
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds
```

#### <a name="parameters"></a>パラメーター
 `Milliseconds` Windows パフォーマンス カウンター イベントを収集する間隔をミリ秒単位で指定します。

## <a name="required-options"></a>必須オプション
 **WinCounter:**`Path` 収集する Windows パフォーマンス カウンターを指定します。 インストルメンテーション メソッドを使用するとき、複数の Windows カウンターを指定できます。 サンプリング メソッドを使用するとき、ソフトウェア カウンターを 1 つだけ指定できます。 **WinCounter** オプションは、**Start** オプションが含まれるコマンド ラインに指定する必要があります。

## <a name="example"></a>例
 この例では、2 つの Windows パフォーマンス カウンターに対して 1000 ミリ秒単位のサンプリング間隔が設定されます。

```cmd
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>関連項目
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [サービスのプロファイリング](../profiling/command-line-profiling-of-services.md)