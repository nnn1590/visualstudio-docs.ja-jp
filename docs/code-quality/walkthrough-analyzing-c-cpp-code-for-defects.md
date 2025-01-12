---
title: 'チュートリアル: C/C++ コード分析による障害の検出'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: acfa1e274b7c0744c2d9968682960b1cd50e0044
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62820338"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>チュートリアル: C/C++ コード分析による障害の検出

このチュートリアルでは、C/C++ コードのコード分析ツールを使用して潜在的なコードの欠陥の C/C++ コードを分析する方法を示します。

- ネイティブ コードに対してコード分析を実行します。
- コード障害の警告を分析します。
- 警告をエラーとして扱う。
- コード障害の分析を向上させるためにソース コードの注釈を設定します。

## <a name="prerequisites"></a>必須コンポーネント

- コピー、[デモ サンプル](../code-quality/demo-sample.md)します。
- C と C++ の基本を理解します。

### <a name="to-run-code-defect-analysis-on-native-code"></a>ネイティブ コードで、コード障害の分析を実行するには

1. デモ ソリューションを開きます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。

     デモ ソリューションを今すぐ設定**ソリューション エクスプ ローラー**します。

2. **[ビルド]** メニューで、**[ソリューションのリビルド]** をクリックします。

     ソリューションは、エラーまたは警告なしでビルドします。

3. **ソリューション エクスプ ローラー**、CodeDefects プロジェクトを選択します。

4. **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

     **プロパティ ページの [CodeDefects** ] ダイアログ ボックスが表示されます。

5. クリックして**コード分析**します。

6. をクリックして、**ビルド時に C/C++ のコード分析を有効にする**チェック ボックスをオンします。

7. CodeDefects プロジェクトをリビルドします。

     コード分析の警告が表示されます、**エラー一覧**します。

### <a name="to-analyze-code-defect-warnings"></a>コード障害の警告を分析するには

1. **ビュー**  メニューのをクリックして**エラー一覧**します。

     選択した開発者プロファイルに応じて[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、 をポイントする必要があります**その他の Windows**上、**ビュー**  メニューをクリック**エラー一覧**します。

2. **エラー一覧**、次の警告をダブルクリックします。

     警告 C6230:意味の異なる型の間の暗黙的なキャスト: HRESULT をブール値のコンテキストを使用しています。

     コード エディターには、関数で、警告の原因となった行が表示されます。`bool ProcessDomain()`します。 この警告は、HRESULT が使用されている 'if' ステートメントのブール型の結果が必要な場合を示します。

3. SUCCEEDED マクロを使用してこの警告を解決します。 コードでは、次のコードをようになります。

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. **エラー一覧**、次の警告をダブルクリックします。

     警告 C6282:不適切な演算子: テストのコンテキストの定数を代入します。 対象の = =」でしょうか。

5. 等しいかどうかをテストして、この警告を解決します。 コードは次のコードのようになります。

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>警告をエラーとして処理するには

1. 次の追加、Bug.cpp ファイル`#pragma`警告 C6001 エラーとして処理するファイルの先頭にステートメント。

   ```cpp
   #pragma warning (error: 6001)
   ```

2. CodeDefects プロジェクトをリビルドします。

     **エラー一覧**C6001 がエラーとして表示されます。

3. 残りの 2 つ C6001 エラーを修正、**エラー一覧**初期化することにより`i`と`j`を 0 にします。

4. CodeDefects プロジェクトをリビルドします。

     プロジェクトは、警告やエラーなしでビルドします。

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Annotation.c でソース コード注釈の警告を修正するには

1. ソリューション エクスプ ローラーでは、注釈のプロジェクトを選択します。

2. **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

     **注釈プロパティ ページ** ダイアログ ボックスが表示されます。

3. クリックして**コード分析**します。

4. 選択、**ビルド時に C/C++ のコード分析を有効にする**チェック ボックスをオンします。

5. 注釈のプロジェクトを再構築します。

6. **エラー一覧**、次の警告をダブルクリックします。

     警告 C6011:NULL ポインター 'newNode' を逆参照します。

     この警告は、戻り値を確認する呼び出し元でエラーを示します。 この場合の呼び出しで**AllocateNode** NULL 値を返す可能性があります (AllocateNode 関数の宣言の annotations.h ヘッダー ファイルを参照してください)。

7. Annotations.cpp ファイルを開きます。

8. この警告を解決するのにには、戻り値をテストするのに 'if' ステートメントを使用します。 コードでは、次のコードをようになります。

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. 注釈のプロジェクトを再構築します。

     プロジェクトは、警告やエラーなしでビルドします。

### <a name="to-use-source-code-annotation"></a>ソース コードの注釈を使用するには

1. 仮パラメーターの注釈を付け、関数の値を返す`AddTail`事前/事後条件でこの例で示すようにします。

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. 注釈のプロジェクトをリビルドします。

3. **エラー一覧**、次の警告をダブルクリックします。

     警告 C6011:'Node' の NULL ポインターの逆参照します。

     この警告は、関数に渡されたノードが、null であることを示し、警告が発生した行番号を示します。

4. この警告を解決するのにには、戻り値をテストするのに 'if' ステートメントを使用します。 コードでは、次のコードをようになります。

   ```cpp
   . . .
   LinkedList *newNode = NULL;
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. 注釈のプロジェクトをリビルドします。

     プロジェクトは、警告やエラーなしでビルドします。

## <a name="see-also"></a>関連項目

[チュートリアル: マネージ コードを分析によるコード障害の](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
[C/C++ のコード分析](../code-quality/code-analysis-for-c-cpp-overview.md)
