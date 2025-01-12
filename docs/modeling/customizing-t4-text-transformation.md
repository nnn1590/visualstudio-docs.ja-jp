---
title: T4 テキスト変換のカスタマイズ
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33f7fd14ff62369de66e4934bf9bb2cf6fd83542
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62994758"
---
# <a name="customize-t4-text-transformation"></a>T4 テキスト変換をカスタマイズする

テキスト テンプレートは、変換プロセスを通して、プログラム コードまたはその他のテキスト ファイルを生成するための Visual Studio の機能です。 [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] を使用して、テキスト テンプレート ディレクティブ プロセッサまたはテキスト テンプレート ホストをカスタマイズすることで、既定のテンプレートの変換プロセスを拡張することができます。

## <a name="in-this-section"></a>このセクションの内容

 [テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md) テキスト変換のしくみについて説明し、テンプレートのホストとディレクティブ プロセッサの役割について説明します。

 [カスタム T4 テキスト テンプレート ディレクティブ プロセッサを作成する](../modeling/creating-custom-t4-text-template-directive-processors.md) ディレクティブ プロセッサは、`<#@template#>.` といったテンプレート中のディレクティブを処理します。テンプレートのコンパイル時に実行され、アセンブリとその他のリソースを読み込むことができます。 実行時にリソースを読み込むコードを挿入することもできます。 ディレクティブ プロセッサを定義することで、テンプレートの複雑さを軽減できます。

 [VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md) メニュー コマンドまたはイベント ハンドラーなどの Visual Studio 拡張機能を作成する場合、拡張機能が任意のテキスト テンプレートを変換するテキスト テンプレート サービスを使用できます。 セッション オブジェクトを使用して、テンプレートにパラメーターのデータを渡し、`<#@parameter#>` ディレクティブを使用して、テンプレート内から値を取得することができます。

 [カスタム ホストを使用したテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md) テンプレートのコードを実行するとき、ホストは外部のファイルへのアクセスとアプリケーションの状態を提供します。 たとえば、Visual Studio 内でテキスト変換を実行するホストは、**ソリューション エクスプローラー**へのアクセスを提供します。 これは、エラーをエラー メッセージ ウィンドウに表示します。 別のコンテキストでテキスト変換を実行する場合は、そのコンテキストで使用可能なサービスへのアクセスを提供する独自のホストを定義できます。

 Visual Studio 拡張機能を作成する場合は、独自のホストを記述する代わりに既存のテキスト変換サービスの使用を検討してください。 詳細については、「[VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md)」を参照してください

## <a name="reference"></a>参照

- [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)は、テキスト テンプレートのディレクティブとコントロール ブロックの構文について説明します。