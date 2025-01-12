---
title: ドキュメントおよび図にユース ケースをリンク |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ee7657b12741cf65583317ba87bd465e15eb02bb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440965"
---
# <a name="link-a-use-case-to-documents-and-diagrams"></a>ユース ケースをドキュメントおよび図にリンクする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ユース ケース図のユース ケースを、別の図またはドキュメントにリンクできます。 たとえば、ユース ケースを次の図やドキュメントにリンクできます。  
  
- ユーザーと、システムまたはその主要なコンポーネント間の相互作用によって、ユース ケースの目標をどのように実現するかを示すシーケンス図。  
  
- ユース ケース実行時に、ユーザー、システム、またはシステムの主要コンポーネントの詳細なアクションを示すアクティビティ図。  
  
- ユース ケースを詳細に記述する OneNote のページまたは段落。  
  
- ユース ケースを詳細に記述する Word 文書または PowerPoint プレゼンテーション。 このようなドキュメントは、ソリューション内、またはチームがアクセスできる場所 (SharePoint サイト) のいずれかで保持できます。  
  
  ユース ケースをドキュメントにリンクするには、ユース ケース図で成果物を作成し、ユース ケースをその成果物に接続します。 成果物のプロパティで、その他の図またはドキュメントのファイル パスを設定します。 成果物をダブルクリックすると、その他の図またはドキュメントが開きます。  
  
  各ユース ケースには、必要な数の成果物を接続することができます。 またユース ケース図では、成果物を他の種類の要素にリンクすることもできます。  
  
### <a name="to-open-a-document-associated-with-an-artifact"></a>成果物に関連付けられているドキュメントを開くには  
  
- ユース ケース図で、成果物の図形をダブルクリックします。  
  
     関連するドキュメントが開きます。  
  
### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>ユース ケースを、同じソリューション内の図またはファイルにリンクするには  
  
1. シーケンス図やアクティビィティ図を描画して、ユース ケースのシナリオを例示します。  
  
2. ユース ケース図に戻ります。  
  
3. 図またはファイルを、ソリューション エクスプローラーからユース ケース図の空白部分にドラッグします。  
  
4. 使用する大文字と小文字を使用して、成果物からの接続、**依存関係**します。  
  
### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Word 文書や PowerPoint プレゼンテーションなどのソリューション ファイルにリンクするには  
  
1. このドキュメントをソリューションに追加します。  
  
    1. Word 文書をソリューションとして、同じ Windows フォルダーに移動します。  
  
    2. ソリューション エクスプ ローラーでソリューションを右クリックして**追加**、 をクリックし、**既存項目の**します。  
  
    3. Word 文書に移動し、をクリックして**追加**します。  
  
         ソリューション エクスプローラーのソリューション フォルダーに、Word 文書が表示されます。  
  
2. Word 文書を、ソリューション エクスプローラーからユース ケース図の空白部分にドラッグします。  
  
     新しい成果物が表示されます。  
  
3. 使用する大文字と小文字を使用して、成果物からの接続、**依存関係**します。  
  
### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>共有ドキュメント、OneNote 要素、または Web ページにリンクを設定するには  
  
1. 共有要素の URL を取得します。 これは、指定できますが、たとえば、ネットワーク ファイルのパスの先頭 '\\\\'、web ページまたは Sharepoint URL 先頭 'http://' OneNote セクションへのリンクは、ページ、または段落の先頭または' onenote:'。  
  
2. ツールボックス、**成果物**ユース ケース図の順にクリックします。  
  
3. 新しい成果物が選択されている次のように入力します。 または、に URL を貼り付け、**ハイパーリンク**プロパティ。  
  
    > [!NOTE]
    > 一般的なワークスペースのいずれかのファイルを選択することをお勧めファイル パスを指定する場合は、(以降では '\\\\')、または Visual Studio ソリューション内のファイル。 これにより、ソリューションが移動された場合でも、ファイル パスは別のチーム メンバーのコンピューター上で有効なままになります。 Word 文書などのドキュメントをソリューションに追加するには、ソリューション エクスプ ローラーでソリューションを右クリックし、 をポイント**追加** をクリックし、**既存項目の**します。  
  
## <a name="see-also"></a>関連項目  
 [UML ユース ケース図: 参照](../modeling/uml-use-case-diagrams-reference.md)   
 [UML ユース ケース図: ガイドライン](../modeling/uml-use-case-diagrams-guidelines.md)   
 [UML モデルおよびダイアグラムを編集します。](../modeling/edit-uml-models-and-diagrams.md)   
 [アプリのモデルを生成する](../modeling/create-models-for-your-app.md)
