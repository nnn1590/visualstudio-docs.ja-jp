---
title: プロパティを削除できません
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c03ba87a7ae7f2321550179ae6354eb473c81465
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460569"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>\<property name> プロパティを削除できません

プロパティ \<property name> は、\<class name> と \<class name> との間の継承のための**識別子のプロパティ**として設定されているため削除できません。

選択されたプロパティは、エラー メッセージに示されているクラス間の継承に対する**識別子のプロパティ**として設定されています。 プロパティがデータ クラス間の継承構成に関与している場合、そのプロパティを削除することはできません。

**識別子のプロパティ**をデータ クラスの別のプロパティに設定して、目的のプロパティが正常に削除されるようにしてください。

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. **O/R デザイナー**で、エラー メッセージに示されているデータ クラスを接続する継承線を選択します。

2. **識別子** プロパティを別のプロパティに設定します。

3. プロパティの削除を再試行します。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)