---
title: '方法: クライアント コンピューターに ClickOnce アプリケーション用の信頼された発行元の追加 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7129d8de5e37b24304b7f1cbf862e4cd299cdf72
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442206"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>方法: ClickOnce アプリケーション用のクライアント コンピューターに信頼された発行元を追加します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

信頼されたアプリケーションの配置を使用すると、 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションをユーザーに確認することなく高いレベルの信頼で実行できるように、クライアント コンピューターを構成できます。 以下の手順では、コマンド ライン ツールの CertMgr.exe を使用して、クライアント コンピューターの信頼された発行者ストアに発行者の証明書を追加する方法について説明します。  
  
 使用するコマンドは、証明書を発行した証明機関 (CA) が、クライアント コンピューターの信頼されたルートに属しているかどうかによって多少異なります。 Windows クライアント コンピューターがドメインに属している場合、コンピューターは、信頼されたルートと見なす CA を一覧として保持しています。 この一覧は通常、システム管理者が設定します。 証明書が、これらの信頼されたルートのいずれかから発行されたものであるか、これらの信頼されたルートのいずれかにつながっている CA によって発行された証明書である場合には、クライアント コンピューターの信頼されたルート証明書ストアにその証明書を追加できます。 一方、上記の信頼されたルートのいずれかによって発行された証明書でない場合には、クライアント コンピューターの信頼されたルート証明書ストアおよび信頼された発行者ストアの両方にその証明書を追加する必要があります。  
  
> [!NOTE]
> このようにして、昇格されたアクセス権を必要とする [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションを配置する予定のクライアント コンピューターすべてに対して、証明書を追加する必要があります。 証明書の追加は、手動で行うか、クライアント コンピューターに配置するアプリケーション経由で行います。 コンピューターの構成は一度だけ行う必要があります。一度構成すると、同じ証明書で署名された [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションは好きな数だけ配置できます。  
  
 証明書は、 <xref:System.Security.Cryptography.X509Certificates.X509Store> クラスを使用して、プログラムでストアに追加することもできます。  
  
 信頼されたアプリケーションの配置の概要については、「 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>信頼されたルートの下の信頼された発行者ストアに証明書を追加するには  
  
1. CA からデジタル証明書を取得します。  
  
2. 証明書を Base64 X.509 (.cer) 形式でエクスポートします。 証明書の形式の詳細については、「 [証明書をエクスポートする](http://go.microsoft.com/fwlink/?LinkId=164793)」を参照してください。  
  
3. クライアント コンピューターのコマンド プロンプトで、次のコマンドを実行します。  
  
     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>他のルート下にある信頼された発行者ストアに証明書を追加するには  
  
1. CA からデジタル証明書を取得します。  
  
2. 証明書を Base64 X.509 (.cer) 形式でエクスポートします。 証明書の形式の詳細については、「 [証明書をエクスポートする](http://go.microsoft.com/fwlink/?LinkId=164793)」を参照してください。  
  
3. クライアント コンピューターのコマンド プロンプトで、次のコマンドを実行します。  
  
     **certmgr.exe -add good.cer -c -s -r localMachine Root**  
  
     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: ClickOnce アプリケーションを手動で展開します。](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce アプリケーションのコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce と Authenticode](../deployment/clickonce-and-authenticode.md)   
 [信頼されたアプリケーションの配置の概要](../deployment/trusted-application-deployment-overview.md)   
 [方法: ClickOnce のセキュリティ設定を有効にします。](../deployment/how-to-enable-clickonce-security-settings.md)   
 [方法: ClickOnce アプリケーションのセキュリティ ゾーンを設定します。](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [方法: ClickOnce アプリケーションのカスタム アクセス許可の設定](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [方法: 制限されたアクセス許可を使用して ClickOnce アプリケーションをデバッグします。](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [方法: ClickOnce アプリケーション用のクライアント コンピューターに信頼された発行元を追加します。](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [方法: アプリケーション マニフェストおよび配置マニフェストに再署名します。](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [方法: ClickOnce 信頼プロンプトの動作を構成する](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
