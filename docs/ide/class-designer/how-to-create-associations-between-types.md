---
title: '方法: 型の間の関連付けを作成する (クラス デザイナー)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 723d1565dae55852829daf0038201d0c8685b3ce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975386"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>方法: クラス デザイナーで型の間の関連付けを作成する

**クラス デザイナー**の関連行は、ダイアグラムのクラスの関係を示します。 関連行は、プロジェクト内の別のクラスのプロパティまたはフィールドの型であるクラスを表します。 関連行は、一般に、プロジェクト内のクラス間の最も重要な関係を示すために使用されます。

すべてのフィールドとプロパティを関連付けとして表示できますが、ダイアグラムで強調する対象に応じて、重要なメンバーだけを関連付けとして表示する方が有意義です。 重要度の低いメンバーを通常のメンバーとして表示するか、それらのメンバーを完全に非表示にできます。

> [!NOTE]
> **クラス デザイナー**では、一方向の関連付けだけがサポートされます。

## <a name="to-define-an-association-line-in-the-class-diagram"></a>クラス ダイアグラムに関連行を定義するには

1. **クラス デザイナー**のツールボックスで、**[関連]** を選択します。

2. 関連付けでリンクする 2 つの図形間に線を描画します。

     新しいプロパティが最初のクラスに作成されます。 このプロパティは、図形のコンパートメント内のプロパティとしてではなく、既定の名前を持つ関連行として表示されます。 その型は、関連行が指す図形です。

## <a name="to-change-the-name-of-an-association"></a>関連付けの名前を変更するには

ダイアグラム領域で、関連行のラベルをクリックし、編集します。

または、次の手順に従います。

1. 関連付けとして表示されるプロパティを含む図形を選択します。

   図形がフォーカスを取得し、図形のメンバーが **[クラスの詳細]** ウィンドウと **[プロパティ]** ウィンドウに表示されます。

2. **[クラスの詳細]** ウィンドウまたは **[プロパティ]** ウィンドウで、そのプロパティの名前フィールドを編集し、**Enter** キーを押します。

   **[クラスの詳細]** ウィンドウ、関連行、**[プロパティ]** ウィンドウ、およびコード上の名前が更新されます。

## <a name="see-also"></a>関連項目

- [方法: メンバー表記と関連付け表記の間で変更する](how-to-change-between-member-notation-and-association-notation.md)
