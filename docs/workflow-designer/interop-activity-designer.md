---
title: ワークフロー デザイナーの Interop アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 688ef92fae5bd0cbaa5ddc653bbaab5692f4827f
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747132"
---
# <a name="interop-activity-designer"></a>Interop アクティビティ デザイナー

**相互運用機能**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.Interop>アクティビティ。

## <a name="the-interop-activity"></a>Interop アクティビティ

<xref:System.Activities.Statements.Interop> アクティビティでは、ワークフロー内の <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> から派生する型の実行を管理します。

### <a name="use-the-interop-activity-designer"></a>Interop アクティビティ デザイナーを使用します。

**相互運用機能**アクティビティ デザイナーが記載されて、**移行**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**タブ。または、選択**ツールボックス**から、**ビュー**メニューのまたはキーを押して**Ctrl**+**Alt** + **X**します。

[移行](../workflow-designer/migration-activity-designers.md)格納しているカテゴリ、<xref:System.Activities.Statements.Interop>でアクティビティにのみ表示されます**ツールボックス**場合、プロジェクトのターゲットが .NET Framework 4 (完全) またはそれ以降。 かどうか、必要に応じて変更できますフレームワークのバージョンをプロジェクトのターゲット。

**相互運用機能**からアクティビティ デザイナーをドラッグできる**ツールボックス**どこにも、アクティビティを通常配置など内に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>します。 削除、**相互運用機能**アクティビティ デザイナーを作成、 <xref:System.Activities.Statements.Interop> 、既定値は、アクティビティ**DisplayName**相互運用機能の。 編集することができます、<xref:System.Activities.Activity.DisplayName%2A>のヘッダーに、**相互運用機能**アクティビティ デザイナー、または、 **DisplayName**プロパティ グリッドのボックスです。

をクリックして、 **参照 をクリックします**内のテキスト、 **ActivityType**ボックスで、いずれかで、**相互運用機能**アクティビティ デザイナーまたはプロパティ グリッドを開く、**参照と.Net の選択の種類** ダイアログ ボックス。 ワークフロー 3.0 またはワークフロー 3.5 のアクティビティの型のみが表示されます。 つまりから派生した型のみ<xref:System.Workflow.ComponentModel.Activity>が表示されます。 このボックスを使用して型を指定する方法の詳細については、次を参照してください。[参照し、.NET の種類 ダイアログ ボックスを選択](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md)します。

### <a name="the-interop-properties"></a>Interop のプロパティ

次の表は、<xref:System.Activities.Statements.Interop>プロパティと、デザイナーでの使用方法について説明します。 プロパティ グリッドで、またはワークフロー デザイナー画面で、これらのプロパティを編集できます。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Interop> アクティビティの表示名。 既定値は**相互運用機能**します。 表示名は必要ありませんが、提供するようにはお勧めします。|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|<xref:System.Activities.Statements.Interop> アクティビティに含まれているアクティビティの型を指定します。 指定されたこの型は、<xref:System.Workflow.ComponentModel.Activity> から派生していることが必要です。|

## <a name="see-also"></a>関連項目

- [移行](../workflow-designer/migration-activity-designers.md)