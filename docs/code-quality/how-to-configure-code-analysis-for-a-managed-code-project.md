---
title: コード分析を構成します。
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a1b09b77eb051d32a3aabb929e9058786215cfb4
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551053"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>方法: マネージコードのレガシ分析を構成する

Visual Studio では、マネージコードプロジェクトに適用するコード分析[規則セット](../code-quality/rule-set-reference.md)の一覧から選択できます。 既定で、 **Microsoft 最小推奨規則**規則セットを選択するが必要な場合は、設定、別の規則を適用できます。 規則セットは、ソリューション内の 1 つまたは複数のプロジェクトに適用できます。

ASP.NET web アプリケーションのルールセットを構成する方法の詳細について[は、「方法:ASP.NET web アプリケーション](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)のコード分析を構成します。

> [!NOTE]
> この記事は、ビルド後にコード分析を実行しない、 [.NET Compiler Platform ベースのコードアナライザー](use-roslyn-analyzers.md)ではなく、レガシ分析に適用されます。

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>.NET Framework プロジェクトの規則セットを構成する

1. 開く、**コード分析**プロジェクトのプロパティ ページのタブ。 これは、次の方法のいずれかで行います。

   - **ソリューション エクスプ ローラー**プロジェクトを選択します。 メニュー バーで選択**分析** > **コード分析を構成する** > **の\<projectname >** します。

   - プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**プロパティ**を選び、**コード分析**タブ。

1. **構成**と**プラットフォーム**一覧で、ビルド構成とターゲット プラットフォームを選択します。

1. 選択した構成を使用して、プロジェクトをビルドするたびに、コード分析を実行するには、選択、**ビルドに対するコード分析を有効にする**チェック ボックスをオンします。 手動では選択してもコード分析を実行することができます**分析** > **コード分析を実行** > **でコード分析を実行\<projectname >** .

1. 既定では、外部ツールによって自動的に生成されたコードからの警告はコード分析では報告されません。 生成されたコードからの警告を表示するには、オフ、**結果生成されたコードを表示しない**チェック ボックスをオンします。

    > [!NOTE]
    > コード分析のエラーおよび警告がフォームやテンプレートで表示される場合、このオプションを使用しても、生成されたコードからこのエラーおよび警告の出力は抑制されません。 表示し、上書きすることがなくフォームまたはテンプレートのソース コードを維持します。

1. **この規則セットを実行**ボックスの一覧で、次のいずれかの操作を行います。

    - 使用する規則セットを選択します。

    - 選択 **\<[参照...] >** 既存のカスタム規則セットを検索するされていないリスト。

    - 定義、[カスタム規則セット](../code-quality/how-to-create-a-custom-rule-set.md)します。

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>ソリューションに複数のプロジェクトに対して規則セットを指定します。

既定では、ソリューションのすべてのマネージ プロジェクトが割り当てられている、 *Microsoft 最小推奨規則*コード分析規則セット。 ソリューションのプロジェクトに割り当てられている規則セットを変更することができます、**プロパティ**ソリューションのダイアログ ボックス。

1. Visual Studio でソリューションを開きます。

2. **分析**メニューの **ソリューションのコード分析を構成する**します。

3. 必要に応じて、展開**共通プロパティ**、し、**コード分析設定**します。

4. 1 つまたは複数のプロジェクトに対して規則セットを指定できます。

    - 個々 のプロジェクトに対して規則セットを指定するには、プロジェクト名を選択します。

    - 押しながら複数のプロジェクトに対して規則セットを指定する**Ctrl**プロジェクト名を選択します。

    - 押しながら、ソリューション内のすべてのプロジェクトを指定する**Shift**プロジェクトの一覧内をクリックします。

5. 選択、**ルール セットの**ルールの名前では、適用する設定、プロジェクトのフィールドと順に選択します。

## <a name="see-also"></a>関連項目

- [コード分析規則セットの参照](../code-quality/rule-set-reference.md)
- [方法: ASP.NET web アプリケーションのコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)
