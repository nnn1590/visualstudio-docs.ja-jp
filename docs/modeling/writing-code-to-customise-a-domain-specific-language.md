---
title: ドメイン固有言語をカスタマイズします。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e62fa58d3f0678c8784cb8584a95d8475238ce0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945441"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>ドメイン固有言語をカスタマイズするコードを記述する

このセクションでは、カスタム コードを使用して、アクセス、変更、またはドメイン固有言語でモデルを作成する方法を示します。

これには、DSL で動作するコードを記述できるいくつかのコンテキストがあります。

- **カスタム コマンド。** ダイアグラムで、右クリックしてユーザーが呼び出すことができます、モデルを変更するコマンドを作成できます。 詳細については、「[方法 :ショートカット メニューにコマンドを追加](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)します。

- **検証。** モデルが適切な状態であることを検証するコードを記述することができます。 詳細については、次を参照してください。[ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)です。

- **既定の動作をオーバーライドします。** DslDefinition.dsl から生成されるコードの多くの側面を変更することができます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)します。

- **テキスト変換です。** モデルにアクセスし、プログラム コードを生成する例については、テキスト ファイルを生成するコードが含まれるテキスト テンプレートを作成できます。 詳細については、次を参照してください。[ドメイン固有言語からコードを生成する](../modeling/generating-code-from-a-domain-specific-language.md)します。

- **他の Visual Studio 拡張機能。** 読み取りおよびモデルの変更を別の VSIX 拡張機能を記述することができます。 詳細については、「[方法 :プログラム コード内のファイルからモデルを開く](../modeling/how-to-open-a-model-from-file-in-program-code.md)

DslDefinition.dsl で定義するクラスのインスタンスと呼ばれるデータ構造に保存しておく、*インメモリ ストア*(IMS) または*ストア*します。 常に、DSL で定義したクラスは、コンス トラクターに引数として、ストアを受け取ります。 たとえば、DSL の例と呼ばれるクラスを定義するとします。

`Example element = new Example (theStore);`

(単に通常のオブジェクト) ではなく、ストア内のオブジェクトを管理するには、いくつかの利点が提供します。

- **Transactions**。 一連のトランザクションに関連する変更をグループ化できます。

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     最終的な Commit() が実行されないように、変更中に例外が発生する場合、ストアが以前の状態にリセットされます。 これにより、エラー、モデルに置かないでが不整合な状態になっていることを確認できます。 詳細については、次を参照してください。[を移動すると、プログラム コードでのモデルを更新する](../modeling/navigating-and-updating-a-model-in-program-code.md)します。

- **2 項リレーションシップ**します。 2 つのクラス間のリレーションシップを定義する場合、両方の end にあるインスタンスは、もう一方の end に移動するプロパティを持ちます。 2 つの端は、常に同期します。 たとえば、親と子という名前の役割を持つ親リレーションシップを定義する場合は、次の可能性がありますに記述します。

     `John.Children.Add(Mary)`

     次の式の両方が該当するようになりました。

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     記述することで、同じ効果を得ることができますも。

     `Mary.Parents.Add(John)`

     詳細については、次を参照してください。[を移動すると、プログラム コードでのモデルを更新する](../modeling/navigating-and-updating-a-model-in-program-code.md)します。

- **ルールとイベント**します。 指定された変更が加えられるたびを起動するルールを定義することができます。 ルールは、たとえば、ダイアグラム上の図形、モデル要素を持つ最新の状態に保つを使用します。 詳細については、次を参照してください。[への対応および変更の反映](../modeling/responding-to-and-propagating-changes.md)します。

- **シリアル化**します。 ストアでは、ファイルに含まれるオブジェクトをシリアル化する標準的な方法を提供します。 シリアル化と逆シリアル化規則をカスタマイズできます。 詳細については、次を参照してください。[ファイル記憶域のカスタマイズと XML シリアル化](../modeling/customizing-file-storage-and-xml-serialization.md)します。

## <a name="see-also"></a>関連項目

- [ドメイン固有言語のカスタマイズおよび拡張](../modeling/customizing-and-extending-a-domain-specific-language.md)