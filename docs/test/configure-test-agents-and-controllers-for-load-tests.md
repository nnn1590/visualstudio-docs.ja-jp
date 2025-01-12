---
title: ロード テストのためのテスト エージェントおよびテスト コントローラーの構成
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test agents and controllers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5c10a624d78c1dc362c9d0e5d7c0e58e24efc3cf
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918371"
---
# <a name="overview-of-test-agents-and-test-controllers-for-running-load-tests"></a>ロード テストを実行するためのテスト エージェントおよびテスト コントローラーの概要

Visual Studio では、物理または仮想マシンを使用して、アプリ用にシミュレートされた負荷を生成することができます。 これらのコンピューターは、単一のテスト コントローラーと 1 つ以上のテスト エージェントとしてセットアップする必要があります。 テスト コントローラーとテスト エージェントを使用すると、単一のコンピューターで生成する場合よりも、高い負荷を生成できます。

> [!NOTE]
> また、クラウド ベースのロード テストを使用すると、多数のユーザーが同時に Web サイトにアクセスした場合と同等の負荷を生成する仮想マシンを用意できます。 クラウド ベースのロード テストの詳細については、[Azure Test Plans を使用したロード テストの実行](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts)に関するページを参照してください。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>ロード シミュレーション アーキテクチャ

ロード シミュレーションのアーキテクチャは、Visual Studio クライアント、テスト コントローラー、およびテスト エージェントから構成されます。

- クライアントは、テストの開発、テストの実行、およびテスト結果の表示のために使用されます。

- テスト コントローラーは、テスト エージェントの管理およびテスト結果の収集のために使用されます。

- テスト エージェントは、テストの実行およびデータの収集のために使用されます。収集されるデータは、システム情報、テスト設定に定義されている ASP.NET プロファイル データなどです。

このアーキテクチャには次のような利点があります。

- 追加テスト エージェントをテスト コントローラーに追加することで、負荷生成の規模を拡大できます。

- クライアント、テスト コントローラー、およびテスト エージェント ソフトウェアを、同じコンピューターにも異なるコンピューターにもインストールできる柔軟性があります。 次に例を示します。

   **ローカル構成:**

  - Machine1:Visual Studio、コントローラー エージェント

    ![コントローラーおよびエージェントを使用したローカル コンピューター](./media/load-test-configa.png)

    **一般的なリモート構成:**

  - Machine1 および 2:Visual Studio (複数のテスト担当者が同じコントローラーを使用可能)。

  - Machine3:コントローラー (エージェントもインストールされている場合あり)。

  - Machine4-n:Machine3 のコントローラーに関連付けられているエージェント。

    ![コントローラーおよびエージェントを使用したリモート コンピューター](./media/load-test-configb.png)

通常、1 つのテスト コントローラーは複数のテスト エージェントを管理しますが、1 つのエージェントは 1 つのコントローラーだけに関連付けることができます。 各テスト エージェントは、開発者チームで共有できます。 このアーキテクチャにより、テスト エージェントの数を簡単に増やすことができるため、より高い負荷の生成が可能になります。

## <a name="test-agent-and-test-controller-interaction"></a>テスト エージェントとテスト コントローラーの対話

テスト コントローラーは、テスト エージェントのセットを管理してテストを実行します。 テスト コントローラーは、テストの開始、テストの停止、テスト エージェント ステータスの追跡、およびテスト結果の収集を行うためにテスト エージェントと通信します。

### <a name="test-controller"></a>テスト コントローラー

テスト コントローラーは、テストを実行するための一般的なアーキテクチャを提供し、ロード テストを実行するための特別な機能を備えています。 テスト コントローラーは、ロード テストをすべてのテスト エージェントに送信し、テスト エージェントがテストの初期化を完了するまで待機します。 すべてのテスト エージェントの準備が整うと、テスト コントローラーはテストを開始するためのメッセージをテスト エージェントに送信します。

### <a name="test-agent"></a>テスト エージェント

テスト エージェントは、新しいテストを開始するためのテスト コントローラーからの要求を待機するサービスとして実行されます。 テスト エージェント サービスが要求を受け取ると、テスト エージェント サービスはテストを実行するプロセスを開始します。 どのテスト エージェントも同じロード テストを実行します。

テスト エージェントには管理者によってウェイトが割り当てられ、テスト エージェントのウェイトに従って負荷が分散されます。 たとえば、テスト エージェント 1 のウェイトが 30、テスト エージェント 2 のウェイトが 70、負荷が 1,000 ユーザーに設定されている場合、テスト エージェント 1 は 300 の仮想ユーザーをシミュレートし、テスト エージェント 2 は 700 の仮想ユーザーをシミュレートします。 「[テスト コントローラーとテスト エージェントの管理](../test/manage-test-controllers-and-test-agents.md)」を参照してください。

テスト エージェントは、テストのセットおよびシミュレーション パラメーターのセットを入力として受け取ります。 テストは、実行しているコンピューターに依存しないという概念が中心となっています。

## <a name="test-controller-and-test-agent-connection-points"></a>テスト コントローラーとテスト エージェントのコネクション ポイント

次の図は、テスト コントローラー、テスト エージェント、およびクライアント間のコネクション ポイントを示しています。 ここでは、着信および発信接続に使用されるポートに加え、これらのポートで使用されるセキュリティ要件の詳細についても説明します。

![テスト コントローラーおよびテスト エージェントのポートとセキュリティ](./media/test-controller-agent-firewall.png)

詳細については、「[テスト コントローラーおよびテスト エージェント用のポートの構成](../test/configure-ports-for-test-controllers-and-test-agents.md)」を参照してください。

## <a name="test-controller-and-agent-installation-information"></a>テスト コントローラーとテスト エージェントのインストールに関する情報

テスト コントローラーおよびテスト エージェントのハードウェア要件とソフトウェア要件、インストール手順、およびパフォーマンスを最適化するための環境の構成方法の詳細については、「[テスト エージェントをインストールして構成する](../test/lab-management/install-configure-test-agents.md)」を参照してください。

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>テスト コントローラーとテスト エージェントを使用した単体テスト

テスト コントローラーと 1 つ以上のエージェントをインストールした後、ロード テストのテスト設定で、テスト コントローラーによるリモート実行を利用するかどうかを指定できます。 また、テストの設定では、エージェントに関連付けられたロールで使用するデータ診断アダプターを指定できます。

## <a name="see-also"></a>関連項目

- [テスト エージェントをインストールして構成する](../test/lab-management/install-configure-test-agents.md)