---
title: ワークフロー デザイナー、Assign アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4179c23cefbf995242288c1e778f9e0413bfe28e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993255"
---
# <a name="assign-activity-designer"></a>Assign アクティビティ デザイナー

**割り当てる**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.Assign>アクティビティ。

## <a name="the-assign-activity"></a>Assign アクティビティ

<xref:System.Activities.Statements.Assign> アクティビティで、変数または引数に値を割り当てます。

### <a name="using-the-assign-activity-designer"></a>Assign アクティビティ デザイナーの使用

**割り当てる**アクティビティ デザイナーが記載されて、**プリミティブ**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス** タブ (または、選択**ツールボックス**から、**ビュー**メニューまたは CTRL + ALT + X)。

**割り当てる**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ことで、アクティビティを配置して、このような内に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>します。 削除、**割り当てる**アクティビティ デザイナーを作成、 <xref:System.Activities.Statements.Assign> 、既定値は、アクティビティ**DisplayName**割り当ての。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、**割り当てる**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-assign-properties"></a>Assign のプロパティ

次の表に、<xref:System.Activities.Statements.Assign> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集することができ、その一部は、ワークフロー デザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Assign> アクティビティの表示名。 既定値は Assign です。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.Assign.To%2A>|True|<xref:System.Activities.Statements.Assign.Value%2A> を割り当てる変数または引数。 値は、有効な Visual Basic 識別子である必要があります。 プロパティを設定するには、Visual Basic の式を入力、**に**ボックスに、**割り当てる**アクティビティ デザイナーまたはプロパティ グリッドでします。|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|変数に割り当てられる値。 設定する、 <xref:System.Activities.Statements.Assign.Value%2A>、Visual Basic の式を入力、**値**ボックスに、**割り当てる**アクティビティ デザイナーまたはプロパティ グリッドでします。|

## <a name="see-also"></a>関連項目

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)