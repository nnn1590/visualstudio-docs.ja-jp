---
title: PerfTips | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aac7068fae27e2f0ba699f404374859ef7b91d1a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675306"
---
# <a name="perftips"></a>パフォーマンスのヒント
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio デバッガーの *PerfTips* 、および統合デバッガー **診断ツール** は、デバッグ中のアプリのパフォーマンス監視と分析に役立ちます。  
  
 デバッガー統合診断ツールは開発中のパフォーマンスの問題を発見する優れた手段ですが、デバッガーはアプリのパフォーマンスに大きな影響を与えることがあります。 より正確なパフォーマンス データを収集するには、Visual Studio 診断ツールの使用を検討してください。このツールは、パフォーマンス調査の追加手段としてデバッガーの外部で実行されます。 参照してください[デバッグせずにプロファイリング ツール実行](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)します。  
  
## <a name="perftips"></a>パフォーマンスのヒント  
 デバッガーがブレークポイントで実行を停止するか、ステップ実行を停止した場合、エディター ウィンドウに、ヒントとして前のブレークポイントからその中断までの経過時間が表示されます。 詳細については、「[PerfTips:Performance Information at-a-glance while Debugging with Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx)」 (パフォーマンスのヒント: Visual Studio を使用したデバッグ中のパフォーマンス概要の参照) を参照してください。  
  
 ![PerfTip](../profiling/media/dbgdiag-perf-perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>[診断ツール] ウィンドウ  
 ブレークポイントおよび関連付けられているタイミング データは、[診断ツール] ウィンドウに記録されます。  
  
 次の図は、Visual Studio 2015 Update 1 の [診断ツール] ウィンドウを示しています。  
  
 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
- **[Break イベント]** タイムラインは、デバッグ セッションでヒットしたブレークポイントにマークを付けます。 イベントをクリックして、 **[デバッガー]** の詳細リストで選択します。  
  
- **[CPU 使用率]** グラフには、すべてのプロセッサ コアのデバッグ セッション中の CPU 使用率の変化が表示されます。  
  
- **[デバッガー]** 詳細ペインの **[イベント]** の一覧には、各中断イベントの項目が含まれます。  
  
- 中断イベントの **[期間]** の列には、前のブレークポイントからそのイベントまでの経過時間が表示されます。  
  
## <a name="turn-perftips-on-or-off"></a>PerfTips をオンまたはオフにする  
 PerfTips を有効または無効にするには:  
  
1. **[デバッグ]** メニューの **[オプション]** をクリックします。  
  
2. **[デバッグ中に経過時間の PerfTip を表示する]** チェック ボックスをオンまたはオフにします。  
  
## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>[診断ツール] ウィンドウをオンまたはオフにする  
 [診断ツール] ウィンドウを有効または無効にするには:  
  
1. **[デバッグ]** メニューの **[オプション]** をクリックします。  
  
2. **[デバッグ中に診断ツールを有効にする]** チェック ボックスをオンまたはオフにします。
