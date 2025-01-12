---
title: ClickOnce での COM コンポーネントの配置 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 282945f473f2799b92b24321383190ca38557cbc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422768"
---
# <a name="deploying-com-components-with-clickonce"></a>ClickOnce での COM コンポーネントの配置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

従来の COM コンポーネントのデプロイには、困難な作業がきました。 コンポーネントは、グローバルに登録する必要があるおり、したがって重複しているアプリケーション間では、望ましくない副作用が発生することができます。 このような状況問題には一般に .NET Framework アプリケーションでコンポーネントがアプリケーションに完全に分離されたまたはサイド バイ サイドでの互換性があるのためです。 Visual Studio、Windows XP または以上のオペレーティング システムの分離された COM コンポーネントを配置することができます。  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .NET アプリケーションをデプロイするための簡単で安全なメカニズムを提供します。 ただし、アプリケーションでは、従来の COM コンポーネントを使用する場合は、それらを展開するための追加の手順を実行する必要があります。 このトピックでは、分離された COM コンポーネントをデプロイして (たとえば、Visual Basic 6.0 または Visual C) からのネイティブ コンポーネントを参照する方法について説明します。  
  
 分離された COM コンポーネントの配置の詳細については、次を参照してください。"とアプリの展開を単純化[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]および Registration-free COM"で[ https://msdn.microsoft.com/magazine/msdn-magazine-issues.aspx](https://msdn.microsoft.com/magazine/msdn-magazine-issues.aspx)します。  
  
## <a name="registration-free-com"></a>Registration-free COM  
 登録を必要としない COM は、展開および分離 COM コンポーネントをアクティブ化するための新しいテクノロジです。 でも、すべてのコンポーネントのタイプ ライブラリと、マニフェストと呼ばれる XML ファイルに、システム レジストリに通常インストールされている登録情報を配置することで、アプリケーションと同じフォルダーに格納されています。  
  
 COM コンポーネントを分離するには、開発者のコンピューターに登録することが必要ですが、エンドユーザーのコンピューターに登録することはありません。 その参照を設定して行う必要があるすべてを COM コンポーネントを分離する**Isolated**プロパティを**True**します。 既定では、このプロパティに設定**False**、登録済み COM 参照として扱う必要があることを示します。 このプロパティが場合**True**ビルド時にこのコンポーネントに対して生成されるマニフェストします。 インストール中に、アプリケーションのフォルダーにコピーする、対応するファイルも発生します。  
  
 すべての列挙、マニフェスト ジェネレーターには、分離の COM の参照が検出されると、`CoClass`に対応する登録データ、各エントリに一致して、生成するコンポーネントのタイプ ライブラリ内のエントリはマニフェストのすべての COM の定義タイプ ライブラリ ファイル内のクラス。  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>ClickOnce を使用して Registration-free COM コンポーネントを展開します。  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 配置テクノロジが、分離された COM コンポーネントを展開するために最適ですが両方[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]登録を必要としない COM コンポーネントがある展開するには、マニフェストを必要とします。  
  
 通常、コンポーネントの作成者は、マニフェストを提供する必要があります。 それ以外の場合は、ただし、Visual Studio は自動的に COM コンポーネントのマニフェストを生成できます。 マニフェストの生成の実行中に、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]発行プロセス。 詳細については、次を参照してください。 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)します。 この機能では、Visual Basic 6.0 などの以前の開発環境で作成されたレガシ コンポーネントを活用することもできます。  
  
 2 つの方法を[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]COM コンポーネントを展開します。  
  
- ブートス トラップを使用して、COM コンポーネントを展開するにはこれは、サポートされているすべてのプラットフォームで動作します。  
  
- ネイティブ コンポーネントの分離 (登録無料 COM とも呼ばれます) の展開を使用します。 ただし、この方法は、Windows XP または以上のオペレーティング システムでのみ動作します。  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>分離と単純な COM コンポーネントの展開の例  
 登録のない COM コンポーネントの配置を示すためにこの例は Visual Basic 6.0 を使用して作成された分離ネイティブ COM コンポーネントを参照する Visual Basic では、Windows ベースのアプリケーションを作成および展開を使用して[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]します。  
  
 まず、ネイティブな COM コンポーネントを作成する必要があります。  
  
##### <a name="to-create-a-native-com-component"></a>ネイティブの COM コンポーネントを作成するには  
  
1. Visual Basic 6.0 を使用して、**ファイル** メニューのをクリックして**新規**、し**プロジェクト**します。  
  
2. **新しいプロジェクト**ダイアログ ボックスで、 **Visual Basic**ノード、 **ActiveX DLL**プロジェクト。 **[名前]** ボックスに「 `VB6Hello`」と入力します。  
  
    > [!NOTE]
    > ActiveX の DLL と ActiveX コントロール プロジェクト型は、登録を必要としない COM; でサポートされます。ActiveX 実行可能ファイルと ActiveX ドキュメント プロジェクトの種類がサポートされていません。  
  
3. **ソリューション エクスプ ローラー**、ダブルクリックして**Class1.vb**テキスト エディターを開きます。  
  
4. Class1.vb に対して生成されたコードの後に、次のコードを追加、`New`メソッド。  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5. コンポーネントをビルドします。 **ビルド** メニューのをクリックして**ソリューションのビルド**します。  
  
> [!NOTE]
> COM コントロール プロジェクトの種類を登録しない COM が Dll のみをサポートします。 登録を必要としない COM を Exe を使用することはできません。  
  
 これで、Windows ベースのアプリケーションを作成でき、COM コンポーネントへの参照を追加できます。  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>COM コンポーネントを使用して Windows ベースのアプリケーションを作成するには  
  
1. Visual Basic の場合を使用して、**ファイル** メニューのをクリックして**新規**、し**プロジェクト**します。  
  
2. **新しいプロジェクト**ダイアログ ボックスで、 **Visual Basic**ノード**Windows アプリケーション**します。 **[名前]** ボックスに「 `RegFreeComDemo`」と入力します。  
  
3. **ソリューション エクスプ ローラー**、クリックして、 **すべてのファイル**プロジェクト参照を表示するボタンをクリックします。  
  
4. 右クリックし、**参照**ノード**参照の追加**コンテキスト メニュー。  
  
5. **参照の追加**ダイアログ ボックスで、をクリックして、**参照**タブ、VB6Hello.dll に移動し、それを選択します。  
  
    A **VB6Hello**参照、参照の一覧に表示されます。  
  
6. をポイント、**ツールボックス**を選択、**ボタン**コントロール、ドラッグして、 **Form1**フォーム。  
  
7. **プロパティ**ウィンドウで、設定、ボタンの**テキスト**プロパティを**こんにちは**します。  
  
8. ハンドラーのコードを追加するには、ボタンをダブルクリックし、コード ファイルにできるように、ハンドラーは次のようにコードを追加します。  
  
   ```  
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim VbObj As New VB6Hello.Class1  
       VbObj.SayHello()  
   End Sub  
   ```  
  
9. アプリケーションを実行します。 **[デバッグ]** メニューの **[デバッグ開始]** をクリックします。  
  
   次に、コントロールを分離する必要があります。 アプリケーションで使用される各 COM コンポーネントは、COM 参照としてプロジェクトで表されます。 この参照は、下に表示される、**参照**内のノード、**ソリューション エクスプ ローラー**ウィンドウ。 (追加することに注意を参照して直接を使用して、**参照の追加**コマンドを**プロジェクト**] メニューの [ActiveX コントロールをフォームにドラッグして、直接またはします)。  
  
   次の手順では、COM コンポーネントを分離し、分離のコントロールを含む更新されたアプリケーションを発行する方法を示します。  
  
##### <a name="to-isolate-a-com-component"></a>COM コンポーネントを分離するには  
  
1. **ソリューション エクスプ ローラー**の**参照**ノードを選択、 **VB6Hello**参照。  
  
2. **プロパティ**ウィンドウの値を変更、 **Isolated**プロパティから**False**に**True**します。  
  
3. **ビルド** メニューのをクリックして**ソリューションのビルド**します。  
  
   ここで、ときに予想どおり、アプリケーションは、f5 キーを押してが登録を必要としない COM の下で実行されているようになりました これを証明するために VB6Hello.dll コンポーネントの登録解除して RegFreeComDemo1.exe Visual Studio IDE の外部で実行してみてください。 ボタンがクリックされたとき、この時点でも機能します。 アプリケーション マニフェストを一時的に変更する場合は、もう一度失敗します。  
  
> [!NOTE]
> COM コンポーネントの休暇をシミュレートするには、一時的に登録を解除すること。 コマンド プロンプトを開き、」と入力して、[システム] フォルダーに移動して`cd /d %windir%\system32`、」と入力して、コンポーネントの登録を解除`regsvr32 /u VB6Hello.dll`します。 」と入力してもう一度登録できます`regsvr32 VB6Hello.dll`します。  
  
 最後の手順は、使用して、アプリケーションを発行する[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>分離の COM コンポーネントとアプリケーションの更新プログラムを発行するには  
  
1. **ビルド** メニューのをクリックして**発行 RegFreeComDemo**します。  
  
    発行ウィザードが表示されます。  
  
2. 発行ウィザードでは、ローカル コンピューターのディスクにアクセスして、発行されたファイルを調査できますの場所を指定します。  
  
3. **[完了]** をクリックして、アプリケーションを発行します。  
  
   発行されたファイルを確認することは sysmon.ocx ファイルが含まれることがわかります。 コントロールがエンドユーザーのコンピューターに、コントロールのさまざまなバージョンを使用して別のアプリケーションがある場合でも、このアプリケーションに干渉ことはできませんが、つまり、このアプリケーションに完全に分離されています。  
  
## <a name="referencing-native-assemblies"></a>ネイティブ アセンブリを参照します。  
 Visual Studio は、ネイティブの Visual Basic 6.0 または C++ アセンブリへの参照をサポートしています。このような参照は、ネイティブ参照と呼ばれます。 確認して、参照がネイティブかどうかを伝えることができます、**ファイルの種類**プロパティに設定されて**ネイティブ**または**ActiveX**します。  
  
 ネイティブ参照を追加するには、使用、**参照の追加**コマンドを使用し、マニフェストを参照します。 一部のコンポーネントは、DLL 内のマニフェストを配置します。 この場合、DLL 自体を選択するだけと Visual Studio は参照として追加するネイティブ コンポーネントに埋め込まれたマニフェストが含まれていることが検出された場合。 Visual Studio には、依存ファイルまたはアセンブリの参照先のコンポーネントと同じフォルダー内にある場合に、マニフェストに示されたすべてがも自動的に含まれます。  
  
 COM コントロールの分離を簡単にマニフェストがまだない COM コンポーネントを展開します。 ただし、コンポーネントは、マニフェストで指定した場合、マニフェストを直接参照できます。 使用せずに可能な限り、コンポーネントの作成者によって提供されたマニフェストを使用するは常に実際には、 **Isolated**プロパティ。  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Registration-free COM コンポーネントの配置の制限事項  
 登録を必要としない COM では、従来の展開手法にクリアの利点を提供します。 ただしは、いくつかの制限事項と注意すも指摘しました。最大の制限は、のみ動作する Windows XP またはそれ以上です。 登録を必要としない COM の実装には、コア オペレーティング システムのコンポーネントが読み込まれる方法の変更が必要です。 残念ながら、登録を必要としない COM のレイヤーを下位レベルのサポートはありません。  
  
 すべてのコンポーネントが登録を必要としない COM の適切な候補 コンポーネントでは、次のいずれかに該当する場合、適切です。  
  
- コンポーネントは、アウト プロセス サーバーです。 EXE サーバーはサポートされていません。Dll のみがサポートされています。  
  
- コンポーネントは、オペレーティング システムの一部であるまたは XML、Internet Explorer、Microsoft Data Access Components (MDAC) などのシステム コンポーネントです。 コンポーネント作成者; の再配布ポリシーに従う必要があります。ベンダーに確認します。  
  
- コンポーネントには、Microsoft Office などのアプリケーションの一部です。 たとえば、Microsoft Excel オブジェクト モデルを分離しない必要があります。 Office の一部は、この完全な Office 製品がインストールされていると、コンピューターでのみ使用します。  
  
- アドインまたはスナップインをたとえば Office アドインまたは Web ブラウザーでのコントロールとして使用されるコンポーネント。 このようなコンポーネントには、通常、ある種のマニフェスト自体の範囲を超えているホスティング環境で定義されている登録スキームが必要です。  
  
- コンポーネントは、システムでは、印刷スプーラのデバイス ドライバーなどの物理または仮想デバイスを管理します。  
  
- コンポーネントは、再頒布可能パッケージのデータ アクセスです。 データ アプリケーションでは、別のデータへのアクセスを再頒布可能パッケージを実行する前にインストールする一般的に必要です。 Microsoft ADO データ コントロール、Microsoft OLE DB、または Microsoft Data Access Components (MDAC) などのコンポーネントを分離しようとする必要があります。 代わりに、アプリケーションでは、MDAC または SQL Server Express を使用する場合として設定の前提条件参照してください[方法。ClickOnce アプリケーションと共に必須コンポーネントをインストール](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)します。  
  
  場合によっては、コンポーネントの開発者に登録を必要としない COM の再設計可能な場合があります。 それができない場合でもビルドし、ブートス トラップを使用して標準の登録スキームを通じてそれらに依存するアプリケーションを発行します。 詳細については、次を参照してください。[ブートス トラップ パッケージを作成する](../deployment/creating-bootstrapper-packages.md)します。  
  
  COM コンポーネントはアプリケーションごとに 1 回分けできるだけです。 たとえばから 2 つの異なる同じ COM コンポーネントを分離することはできません**クラス ライブラリ**プロジェクトは、同じアプリケーションの一部であります。 これによりビルドの警告が発生し、アプリケーションの実行時に読み込みが失敗します。 この問題を回避するには、1 つのクラス ライブラリ内の COM コンポーネントをカプセル化することをお勧めします。  
  
  開発者のコンピューターには、com 登録が必要ないくつかのシナリオがある場合でも、アプリケーションの配置には、登録は不要です。 `Isolated`プロパティは、ビルド中に、マニフェストを自動生成するために開発者のコンピューターで COM コンポーネントが登録することが必要です。 登録キャプチャ機能、ビルド時に自己登録を呼び出すことはありません。 また、タイプ ライブラリで明示的に定義されているすべてのクラスは、マニフェストには反映されません。 ネイティブ参照などの既存のマニフェストを COM コンポーネントを使用する場合、コンポーネントが開発時に登録する必要はありません。 ただし、登録が必要なコンポーネントが ActiveX コントロールに追加する場合、**ツールボックス**および Windows フォーム デザイナー。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)
