---
title: 選択した接続は、サポートされていないデータベース プロバイダーを使用して |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: adf0dd7392b492364a286b5984de52b2b4640ae2
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700161"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>選択した接続では、サポートされていないデータベース プロバイダーが使用されています
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.NET Framework Data Provider for SQL Server を使用しない項目をドラッグすると、このメッセージが表示されます**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上に、 [LINQ to SQLVisual Studio のツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)します。  
  
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]では、.NET Framework Provider for SQL Server を使用するデータ接続のみがサポートされます。 有効な接続は、Microsoft SQL Server または Microsoft SQL Server データベース ファイルへの接続だけです。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- .NET Framework Data Provider for SQL Server を使用するデータ接続の項目のみを [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]に追加します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Data.SqlClient>   
 [.NET framework データ プロバイダー](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成します。](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)