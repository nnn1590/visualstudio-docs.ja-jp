---
title: コード生成と T4 テキスト テンプレート |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
ms.assetid: 74a0a748-5b11-4999-8bea-49572967827d
caps.latest.revision: 84
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4886a23272962d2dee03576504d60d64067faf20
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433408"
---
# <a name="code-generation-and-t4-text-templates"></a>コード生成と T4 テキスト テンプレート
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]では、 *T4 テキスト テンプレート* は、テキスト ファイルを生成できる、テキスト ブロックと制御ロジックが混在するファイルです。 制御ロジックは、 [!INCLUDE[csprcs](../includes/csprcs-md.md)] または [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]のプログラム コードのフラグメントとして記述します。 Visual Studio 2015 Update 2 以降では、T4 テンプレート ディレクティブで C# バージョン 6.0 の機能を使用できます。 Web ページ、リソース ファイル、任意の言語のプログラム ソース コードなど、あらゆる種類のテキスト ファイルを生成できます。  
  
 T4 テキスト テンプレートには、次の 2 種類があります。  
  
 **実行時 T4 テキスト テンプレート** ('前処理された' テンプレート) は、通常、出力の一部として文字列を生成するために、アプリケーションで実行されます。  
 たとえば、次のように HTML ページを定義するテンプレートを作成できます。  
  
```  
<html><body>  
 The date and time now is: <#= DateTime.Now #>  
</body></html>  
```  
  
 このテンプレートは、生成される出力に似ている点にご注目ください。 このように、テンプレートは結果の出力に似ているため、テンプレートを変更する場合に誤りを防ぐことができます。  
  
 また、テンプレートにはプログラム コードのフラグメントも含まれます。 これらのフラグメントを使用して、テキストのセクションの繰り返し、条件付きセクションの作成、アプリケーションのデータの表示を行うことができます。  
  
 出力を生成するには、テンプレートによって生成される関数をアプリケーションで呼び出します。 例えば:  
  
```csharp  
string webResponseText = new MyTemplate().TransformText();  
  
```  
  
 アプリケーションは、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] がインストールされていないコンピューターでも実行できます。  
  
 実行時テンプレートを作成するには、 **前処理されたテキスト テンプレート** ファイルをプロジェクトに追加します。 または、プレーンテキスト ファイルを追加し、 **[カスタム ツール]** プロパティを **TextTemplatingFilePreprocessor**に設定することもできます。  
  
 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md) テンプレートの構文の詳細については、次を参照してください。 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)  
  
 **デザイン時 T4 テキスト テンプレート** は、アプリケーションのソース コードや他のリソースの一部を定義するために、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] で実行されます。  
 通常は、複数のテンプレートを使用して 1 つの入力ファイルまたはデータベースのデータを読み込み、一部の `.cs`ファイル、 `.vb`ファイル、または他のソース ファイルを生成します。 テンプレートごとに 1 つのファイルが生成されます。 テンプレートは、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] または [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]内で実行されます。  
  
 たとえば、入力データが構成データの XML ファイルであるとします。 開発中に XML ファイルを編集するたびに、テキスト テンプレートによって、アプリケーション コードの一部が再生成されます。 テンプレートの例を次に示します。  
  
```  
<#@ output extension=".txt" #>  
<#@ assembly name="System.Xml" #>  
<#  
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.  
#>  
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>  
{  
  ... // More code here.   
}  
  
```  
  
 XML ファイルの値に応じて、次のような `.cs` ファイルが生成されます。  
  
```  
namespace Fabrikam.FirstJob  
{  
  ... // More code here.   
}  
```  
  
 別の例として、入力がビジネス アクティビティのワークフローの図であるとします。 ユーザーがビジネス ワークフローを変更した場合や、別のワークフローを使用する新しいユーザーとの作業を開始する場合は、新しいモデルに合わせてコードを簡単に再生成できます。  
  
 デザイン時テンプレートを使用すると、要件が変わったときに構成をすばやく変更できるようになり、変更の信頼性も高まります。 ワークフローの例のように、ビジネス要件の観点で入力を定義するのが一般的です。 このように定義すると、変更点についてユーザーと共に検討しやすくなります。 そのため、デザイン時テンプレートは、アジャイル開発プロセスにおける有用なツールとなります。  
  
 デザイン時テンプレートを作成するには、 **テキスト テンプレート** ファイルをプロジェクトに追加します。 または、プレーンテキスト ファイルを追加し、 **[カスタム ツール]** プロパティを **TextTemplatingFileGenerator**に設定することもできます。  
  
 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md) テンプレートの構文の詳細については、次を参照してください。 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)  
  
> [!NOTE]
> 1 つ以上のテンプレートで読み込まれるデータを示す際に、 *モデル* という用語を使用する場合があります。 モデルはどのような形式でもかまいません。あらゆる種類のファイルまたはデータベースを使用できます。 必ずしも UML モデルやドメイン固有言語モデルである必要はありません。 'モデル' は、コードのようなものではなく、ビジネス概念の観点でデータを定義できることを示します。  
  
 テキスト テンプレート変換機能は、 *T4*と名付けられています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)  
 プリコンパイルされたテキスト テンプレートは、テキスト ファイルを生成するあらゆるアプリケーションにおいて、テキストを定義する簡単で信頼性の高い方法です。 ただし、この方法では、実行時にテキスト テンプレートを変更することができません。  
  
 [T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
 モデルからコードやその他のリソースを生成すると、モデルを更新してアプリケーションを更新することができます。  
  
 [ビルド処理でのコード生成](../modeling/code-generation-in-a-build-process.md)  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK がインストールされている場合は、生成されるソフトウェアをモデルの変更に合わせて最新の状態に確実に保つことができます。  
  
 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)  
 テキスト テンプレート ファイルの構文。  
  
 [チュートリアル: テキスト テンプレートを使用したコード生成](../modeling/walkthrough-generating-code-by-using-text-templates.md)  
 コード生成を使用する一例のデモ。  
  
 [T4 テキスト テンプレートのデバッグ](../modeling/debugging-a-t4-text-template.md)  
 テキスト テンプレートのデバッグ方法および一般的なテキスト テンプレート エラー。  
  
 [TextTransform ユーティリティを使用したファイルの生成](../modeling/generating-files-with-the-texttransform-utility.md)  
 テキスト テンプレート変換の実行に使用できるコマンド ライン ツール。  
  
 [T4 テキスト変換のカスタマイズ](../modeling/customizing-t4-text-transformation.md)  
 ディレクティブ プロセッサの記述方法および独自のデータ ソース用のカスタム テンプレート ホスト。  
  
## <a name="see-also"></a>関連項目  
 [UML モデルからファイルを生成します。](../modeling/generate-files-from-a-uml-model.md)   
 [ドメイン固有言語からのコード生成](../modeling/generating-code-from-a-domain-specific-language.md)
