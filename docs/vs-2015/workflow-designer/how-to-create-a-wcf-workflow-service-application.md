---
title: '方法: WCF ワークフロー サービス アプリケーションの作成 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d0c258ea081e95179c507f76413ae2a5fc7d71a5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705848"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>方法: WCF ワークフロー サービス アプリケーションを作成する
[!INCLUDE[indigo1](../includes/indigo1-md.md)] ワークフロー サービス アプリケーションは、そのクライアントとの間でプロセスの境界を越えてメッセージを受け渡しする分散型の通信サービスです。 サービス側でのサービス コントラクトの実装は、.NET Framework 3.5 の従来のワークフロー サービスと同様に、[!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] のワークフロー アクティビティを介して宣言形式で行います。  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>WCF ワークフロー サービス アプリケーションを作成するには  
  
1. [!INCLUDE[vs2010](../includes/vs2010-md.md)] を起動します。  
  
2. **ファイル**メニューで、**新規**、し、**プロジェクト**.  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3. **インストールされたテンプレート**ペインで、 **WCF**または**ワークフロー**いずれかから、 **Visual c#** または**Visual Basic**任意の言語に応じてグループ化します。  
  
4. 中央のペインで選択**WCF ワークフロー サービス アプリケーション**します。  
  
5. **名前**ボックスに、簡単に特定できるように、プロジェクトのわかりやすい名前を入力します。  
  
6. **場所**ボックスに、プロジェクトを保存またはをクリックするディレクトリを入力**参照**それに移動します。  
  
7. **ソリューション**ボックスで、新しいソリューションを作成し、をクリックし、いずれかを選択**OK**します。  
  
    > [!NOTE]
    > 既存のソリューションのワークフロー コンソール アプリケーションを追加する場合は、そのソリューションを開きます[!INCLUDE[vs2010](../includes/vs2010-md.md)]でソリューションを右クリックして**ソリューション エクスプ ローラー**、選択および**追加**、し**新しいプロジェクト.** 開く、**新しいプロジェクト** ダイアログ ボックス。 上記の手順を実行します。  
  
8. プロジェクト テンプレートによって、サービス定義が XAML として作成されます。 [!INCLUDE[wfd1](../includes/wfd1-md.md)]のデザイン ビューが開かれ、<xref:System.Activities.Statements.Sequence> と <xref:System.ServiceModel.Activities.Receive> のアクティビティを含む <xref:System.ServiceModel.Activities.SendReply> アクティビティが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [方法: アクティビティを作成します。](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)