---
title: '[クイック起動] ([オプション] ダイアログ ボックス - [環境])'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.QuickLaunch
- vs.quicklaunch
helpviewer_keywords:
- searching IDE
- IDE, searching
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 1f5026a014b5adc96f0729d130c4398474d6d413
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605897"
---
# <a name="quick-launch-environment-options-dialog-box"></a>[クイック起動] ([オプション] ダイアログ ボックス - [環境])

**クイック起動**を使用すると、オプション、テンプレート、メニューなどの IDE アセットのアクションをすばやく検索して実行できます。 **クイック起動**を使用してコードおよびシンボルを検索できません。 **[クイック起動]** 検索ボックスは、メニュー バーの右上隅にあり、**Ctrl** キーを押しながら **Q** キーを押すことでアクセスできます。 ボックスに検索文字列を入力します。 \@ を含む文字列を検索するには、 '\@\@' を使用します。

Visual Studio をインストールすると、**クイック起動**は既定で有効になります。 メニュー バーで、 **[ツール]**  >  **[オプション]** を選択し、 **[クイック起動]** を表示または非表示にできます。 **[環境]** ノードを展開し、 **[クイック起動]** をクリックします。 **[クイック起動を有効にする]** チェック ボックスをオンまたはオフにします。 また、このページの検索カテゴリを有効または無効にできます。

## <a name="category-list"></a>カテゴリの一覧

クイック起動の検索結果は、 **[直前に使用]** 、 **[メニュー]** 、 **[オプション]** 、および **[開かれているドキュメント]** という 4 つのカテゴリで項目の数と共に表示されます。 検索結果をカテゴリ別に走査するには、**Ctrl** キーを押しながら **Q** キーを押すと、次のカテゴリのすべての結果が表示されます。 最後のカテゴリが表示された後、**Ctrl** キーを押しながら **Q** キーを押すと、各カテゴリのいくつかの結果が表示されます。 **Ctrl** キーと **Shift** キーを押しながら **Q** キーを押すと、カテゴリ間を逆の順序で移動できます。 各カテゴリのすべての検索結果を表示するには、カテゴリ名を選択します。

次のショートカットを使用して、検索を特定のカテゴリに限定できます。

|カテゴリ|ショートカット|ショートカットの説明|
|--------------|--------------| - |
|直前に使用|@mru<br /><br /> たとえば、`@mru font`|**直前に使用**した項目が最大 5 つ表示されます。|
|メニュー|@menu<br /><br /> たとえば、`@menu project`|検索をメニュー項目に制限します。|
|オプション|@opt<br /><br /> たとえば、`@opt font`|検索を **[オプション]** ダイアログ ボックスの設定に制限します。|
|ドキュメント|@doc<br /><br /> たとえば、`@doc program.cs`|検索を検索条件の開いているドキュメントのファイル名とパスに限定しますが、ファイル内のテキストは検索されません。|

> [!NOTE]
> ショートカット キーは、 **[オプション]** ダイアログ ボックスにある **[全般]**  >  **[キーボード]** ページで変更できます。

## <a name="show-previous-results"></a>前の結果の表示

既定では、入力した検索用語は検索セッション間で保持されません。 語句を検索し、カーソルを**クイック起動**領域の外側に移動させてから戻した場合は、検索文字列がクリアされます。 検索結果を保持するには、 **[オプション]** ダイアログ ボックスに移動して、 **[クイック起動]** をクリックし、 **[クイック起動がアクティブ化されたときに以前の検索結果を表示する]** チェック ボックスをオンにします。 次回に検索を実行し、クイック起動領域の外側に移動してから戻ると、クイック起動で最後に使用された検索用語が保持され、検索結果が表示されます。
