---
title: ネットワーク エラーまたはプロキシ エラーをトラブルシューティングする
description: ファイアウォールまたはプロキシ サーバーの内側で Visual Studio をインストールし使用するときに発生する可能性があるネットワークまたはプロキシに関連するエラーの解決策を探します。
ms.date: 05/22/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 27364bd028d9fb493da354d3bff7f11efe5f459d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825705"
---
# <a name="troubleshooting-network-related-errors-when-you-install-or-use-visual-studio"></a>Visual Studio をインストールまたは使用するときのネットワーク関連のエラーのトラブルシューティング

ファイアウォールまたはプロキシ サーバーの内側で Visual Studio をインストールし使用するときに発生する可能性があるネットワークまたはプロキシに関連する最も代表的なエラーの解決策を紹介します。

## <a name="error-proxy-authorization-required"></a>エラー :"プロキシ認証を要求するエラー"

このエラーは通常、ユーザーがプロキシ サーバーを経由してインターネットに接続し、Visual Studio が一部のネットワーク リソースに対して行った呼び出しをプロキシ サーバーがブロックしたときに発生します。

### <a name="to-fix-this-proxy-error"></a>このプロキシ エラーを解決するには

- Visual Studio を再起動します。 プロキシ認証のダイアログ ボックスが表示されます。 ダイアログ ボックスに入力を求めるメッセージが表示されたら、資格情報を入力します。

- Visual Studio を再起動しても問題が解決しない場合は、考えられる原因は、プロキシ サーバーが http:&#47;&#47;go.microsoft.com のアドレスに対しては資格情報を要求せず、&#42;.visualStudio.microsoft.com のアドレスに対しては資格情報を要求することです。 これらのサーバーの場合、次の URL を許可リストに追加し、Visual Studio におけるあらゆるサインイン シナリオのブロックを解除することを検討する必要があります。

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- http:&#47;&#47;go.microsoft.com を許可リストから削除すると、Visual Studio を再起動したとき、http:&#47;&#47;go.microsoft.com のアドレスとサーバー エンドポイントの両方にプロキシ認証ダイアログが表示されます。

  または

- プロキシで既定の資格情報を使用する場合は、次のアクションを実行します。

::: moniker range="vs-2017"

  1. **devenv.exe.config** (devenv.exe 構成ファイル) を、 **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** または **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** で見つけます。

  2. 構成ファイル内で、`<system.net>` ブロックを探し、次のコードを追加します。

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      `proxyaddress="<http://<yourproxy:port#>`には、使用しているネットワークの正しいプロキシ アドレスを挿入する必要があります。

     > [!NOTE]
     > 詳細については、「[ &lt;defaultProxy&gt; 要素 (ネットワーク設定)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/)」ページおよび「[&lt;proxy&gt; 要素 (ネットワーク設定)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings)」ページを参照してください。

::: moniker-end

::: moniker range="vs-2019"

  1. **devenv.exe.config** (the devenv.exe 構成ファイル) を、 **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** または **%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** で見つけます。

  2. 構成ファイル内で、`<system.net>` ブロックを探し、次のコードを追加します。

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      `proxyaddress="<http://<yourproxy:port#>`には、使用しているネットワークの正しいプロキシ アドレスを挿入する必要があります。

     > [!NOTE]
     > 詳細については、「[ &lt;defaultProxy&gt; 要素 (ネットワーク設定)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/)」ページおよび「[&lt;proxy&gt; 要素 (ネットワーク設定)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings)」ページを参照してください。

::: moniker-end

## <a name="error-the-underlying-connection-was-closed"></a>エラー :"基になる接続がサーバーによって閉じられました"

ファイアウォールが設定されたプライベート ネットワークで Visual Studio を使用する場合、Visual Studio を一部のネットワーク リソースに接続できない可能性があります。 これらのリソースには、サインインとライセンス取得のための Azure DevOps Services、NuGet、および Azure サービスが含まれます。 Visual Studio でこれらのリソースのいずれかに接続できない場合は、次のエラー メッセージが表示されることがあります。

  **基になる接続がサーバーによって閉じられました:送信時、予期しないエラーが発生しました**

Visual Studio ではトランスポート層セキュリティ (TLS) 1.2 プロトコルを使用して、ネットワーク リソースに接続します。 Visual Studio で TLS 1.2 を使用している場合、一部のプライベート ネットワーク上のセキュリティ アプライアンスによって特定のサーバー接続がブロックされます。

### <a name="to-fix-this-connection-error"></a>この接続エラーを解決するには

次の URL の接続を有効にします。

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (Azure 接続の場合)

- &#42;.visualstudio.microsoft.com

- cdn.vsassets.io (コンテンツ配信ネットワーク (CDN)、コンテンツをホスト)

- &#42;.gallerycdn.vsassets.io (Azure DevOps Services の拡張機能をホスト)

- static2.sharepointonline.com (フォントなど、Visual Studio が使用する Office UI ファブリック キットのリソースをホスト)

- &#42;.nuget.org (NuGet 接続の場合)

  > [!NOTE]
  > プライベートで所有されている NuGet のサーバー URL は、このリストには含まれない場合があります。 %APPData%\Nuget\NuGet.Config で使用している NuGet のサーバーを確認できます。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>関連項目

* [ファイアウォールまたはプロキシ サーバーの内側に Visual Studio をインストールして使用する](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [Visual Studio のインストール](install-visual-studio.md)
