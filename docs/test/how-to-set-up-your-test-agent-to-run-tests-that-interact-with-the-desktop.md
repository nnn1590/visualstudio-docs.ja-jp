---
title: テスト エージェントを構成する
ms.date: 09/18/2018
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 04b1a894fbeb20059b79e65327ed8a7d18730e01
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786007"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>方法: テスト エージェントを設定して、デスクトップと対話するテストを実行する

デスクトップと対話する自動テストを実行する場合、エージェントをサービスではなくプロセスとして実行されるように設定する必要があります。 たとえば、テスト コントローラーとテスト エージェントを使用してコード化された UI テストをリモートで実行する場合、またはテストを実行してテストの実行時にビデオ記録をキャプチャする場合は、エージェントをプロセスとして実行されるように設定する必要があります。 Visual Studio を使用してテストの設定でエージェントをロールに割り当てる場合や、Microsoft Test Manager を使用して環境内でエージェントをロールに割り当てる場合は、デスクトップと対話する必要があるロールに割り当てられたすべてのエージェントの設定を変更する必要があります。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!WARNING]
> Microsoft Test Manager を使用してラボ環境を設定する場合、テスト エージェントがインストールされます。 コード化された UI テストを実行できるようにロールの 1 つを構成する場合は、**環境の作成ウィザード**で指定できます。

> [!IMPORTANT]
> コード化された UI テストを実行するエージェントを実行するコンピューターは、ロックしたり、スクリーン セーバーを有効にしたりできません。

ブラウザーを起動するコード化された UI テストを実行する場合、テスト エージェントのサービス アカウントがそのブラウザーの起動に使用されます。 このサービス アカウントは、このコンピューターでアクティブなユーザーであるユーザー アカウントと同じである必要があります。 同じユーザー アカウントでない場合、ブラウザーは起動しません。

> [!IMPORTANT]
> ビルド定義の一部としてブラウザーを起動するコード化された UI テストを実行する場合、ビルド サービスのサービス アカウントがそのブラウザーの起動に使用されます。 このサービス アカウントは、このコンピューターでアクティブなユーザーであるユーザー アカウントと同じである必要があります。 同じユーザー アカウントでない場合、ブラウザーは起動しません。

デスクトップと対話する必要があるタスクを実行するロールに割り当てられたエージェントを設定するには、次の手順を実行します。

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>エージェントをプロセスとして実行されるように設定するには

1. インストールしたテスト エージェントをプロセスとして実行されるように構成するには、 **[スタート]**  >  **[Test Agent 構成ツール]** の順に移動します。

   **[Test Agent の構成]** ダイアログ ボックスが表示されます。

   ![Visual Studio 用のテスト エージェントを構成する](media/configure-test-agent.png)

2. **[対話型プロセス]** を選択します。 テスト エージェントは、サービスではなくプロセスとして起動されます。 **[次へ]** をクリックします。

3. テスト エージェントのプロセスを実行するユーザーのユーザー名とパスワードを入力します。

   > [!NOTE]
   > - プロセスを起動するために追加したユーザーは、このエージェントのテスト コントローラーであるコンピューターの TeamTestAgentService グループのメンバーとしても追加する必要があります。 このユーザーが現在のユーザーである場合は、このユーザーをテスト コントローラー コンピューターに追加するときにログオフまたは再起動する必要があります。
   > - ユーザー アカウントに null パスワードは使用できません。
   > - IntelliTrace またはネットワーク エミュレーション データ診断アダプターを使用するには、ユーザー アカウントが Administrators グループのメンバーである必要があります。 テスト エージェントを実行するコンピューターで最小特権のユーザー アカウントを持つ OS が実行されている場合は、(昇格した) 管理者としてテスト エージェントを実行する必要があります。 エージェント ユーザー名がエージェント サービスにない場合は、そのユーザー名を追加しようとするので、テスト コントローラーに対するアクセス許可が必要です。
   > - テスト コントローラーを使用するユーザーは、テスト コントローラーの Users アカウントに属している必要があります。このアカウントに属していない場合は、コントローラーに対してテストを実行できません。

4. テスト エージェントが構成されたコンピューターで、コンピューターの再起動後にテストを実行できることを確認するには、テスト エージェント ユーザーとして自動的にサインインするようにコンピューターを設定します。 **[自動的にログオンする]** をオンにします。 これで、ユーザー名とパスワードが暗号化された形式でレジストリに保存されます。

   > [!NOTE]
   > リモート デスクトップまたはゲスト ベース接続を使用してラボ環境に接続しているときに、予期しない切断が頻繁に発生することがあります。 接続が失われる原因の 1 つとして、コンピューターがネットワークに自動的にログオンするように構成されていることが考えられます。

5. スクリーン セーバーはデスクトップと対話する必要がある自動テストに干渉する可能性があるため、スクリーン セーバーを確実に無効にするには、 **[スクリーン セーバーを無効にする]** をオンにします。

   > [!WARNING]
   > 自動的にログオンする、またはスクリーン セーバーを無効にすると、セキュリティ上のリスクが生じます。 自動ログオンを有効にすると、他のユーザーがこのコンピューターを起動して、自動ログオンするアカウントを使用できるようになります。 スクリーン セーバーを無効にすると、コンピューターのロックを解除するためにユーザーのログオンを要求するプロンプトが表示されなくなる可能性があります。 この結果、コンピューターに物理的にアクセスできれば、だれでもコンピューターを使用できるようになります。 これらの機能をコンピューターで有効にする場合は、これらのコンピューターが物理的に安全であることを確認してください。 たとえば、これらのコンピューターを物理的に安全なラボに設置するなどの措置を講じます。 **[スクリーン セーバーを無効にする]** をオフにしても、この操作だけではスクリーン セーバーは有効になりません。

   エージェントがサービスとして実行されるように戻すには、このツールを使用して **[サービス]** を選択します。

6. 変更を適用するには、 **[設定の適用]** をクリックします。

   テスト エージェントを構成する各ステップの状態を示す **[構成の概要]** ダイアログ ボックスが表示されます。

7. **[構成の概要]** ダイアログ ボックスを閉じるには、 **[閉じる]** を選択します。 **[閉じる]** をもう一度選択して、**Test Agent 構成ツール**を終了します。

   > [!NOTE]
   > コンピューターには、プロセスとして実行されているテスト エージェントに関する通知領域アイコンが表示されます。 このアイコンは、テスト エージェントの状態を示します。 このツールを使用してエージェントがプロセスとして実行されている場合は、エージェントを起動、停止、または再起動できます。 テスト エージェントが実行されていない場合にプロセスとして開始するには、 **[スタート]**  >  **[Visual Studio]**  >  **[Microsoft Visual Studio Test Agent]** の順に選択します。

   このテスト エージェントのテスト コントローラーが Team Foundation Server に登録されている場合、対話型プロセスとして実行されているテスト エージェントの状態が Microsoft Test Manager の **[ラボ センター]** の **[コントローラー]** ビューに表示されます。 対話型プロセスとして実行されていることを示すために、前にアスタリスク (*) 記号が付いています。 このテスト エージェントを再開するには、 **[コントローラー]** ビューではなく、テスト エージェントのコンピューターで実行されるツールを使用する必要があります。

## <a name="see-also"></a>関連項目

- [テスト エージェントをインストールして構成する](../test/lab-management/install-configure-test-agents.md)