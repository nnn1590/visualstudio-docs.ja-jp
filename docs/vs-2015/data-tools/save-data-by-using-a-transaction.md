---
title: トランザクションを使用してデータを保存 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b93c512bafd8b15682ed081c7778660ef52fd1f7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692501"
---
# <a name="save-data-by-using-a-transaction"></a>トランザクションを使用してデータを保存する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用して、トランザクションでデータを保存する、<xref:System.Transactions>名前空間。 使用して、<xref:System.Transactions.TransactionScope>オブジェクトが自動的に管理されているトランザクションに参加します。  
  
 プロジェクトは、トランザクションを使用するプロジェクトへの参照を手動で追加する必要があるため、System.Transactions アセンブリへの参照は作成されません。  
  
> [!NOTE]
> <xref:System.Transactions> Windows 2000 またはそれ以降、名前空間がサポートされています。  
  
 トランザクションを実装する最も簡単な方法がインスタンス化するには、<xref:System.Transactions.TransactionScope>オブジェクト、`using`ステートメント。 (詳細については、次を参照してください[Using ステートメント](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1)、および[ステートメントを使用して](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3)。)。内で実行されるコード、`using`ステートメントがトランザクションに参加します。  
  
 トランザクションをコミットするには、呼び出し、<xref:System.Transactions.TransactionScope.Complete%2A>メソッドを使用して、最後のステートメントをブロックします。  
  
 トランザクションをロールバックするには、呼び出す前に例外をスロー、<xref:System.Transactions.TransactionScope.Complete%2A>メソッド。  
  
 詳細については、次を参照してください。[トランザクションでデータを保存](../data-tools/save-data-in-a-transaction.md)します。  
  
### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>System.Transactions の dll への参照を追加するには  
  
1. **プロジェクト**メニューの **参照の追加**します。  
  
2. **.NET**  タブ (**SQL Server**の SQL Server プロジェクト タブ) を選択します**System.Transactions**、し、 **OK**。  
  
     System.Transactions.dll への参照は、プロジェクトに追加されます。  
  
### <a name="to-save-data-in-a-transaction"></a>トランザクションでデータを保存するには  
  
- 使用して、データを保存するコードを追加するが、トランザクションを含むステートメント。 次のコードを作成し、インスタンス化する方法を示しています、<xref:System.Transactions.TransactionScope>オブジェクトを使用して、ステートメント。  
  
     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]  
  
## <a name="see-also"></a>関連項目  
 [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)
