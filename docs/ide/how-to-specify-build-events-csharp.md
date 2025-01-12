---
title: '方法: ビルド イベントを指定する (C#)'
ms.date: 03/21/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9484d6977c6896253197215ce185579518448da8
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483704"
---
# <a name="how-to-specify-build-events-c"></a>方法: ビルド イベントを指定する (C#)

ビルド開始前またはビルド終了後に実行するコマンドを指定するには、ビルド イベントを使います。 ビルド イベントは、ビルド プロセスにおいてビルドがこれらのポイントに正常に達した場合にのみ実行されます。

プロジェクトのビルド時に、ビルド前イベントは *PreBuildEvent.bat* という名前のファイルに追加され、ビルド後イベントは *PostBuildEvent.bat* という名前のファイルに追加されます。 エラー チェックを行う場合は、独自のエラー チェック コマンドをビルド ステップに追加します。

## <a name="specify-a-build-event"></a>ビルド イベントを指定する

1. **ソリューション エクスプローラー**で、ビルド イベントを指定するプロジェクトを選択します。

2. **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

3. **[ビルド イベント]** タブを選択します。

4. **[ビルド前に実行するコマンド ライン]** ボックスで、ビルド イベントの構文を指定します。

   > [!NOTE]
   > プロジェクトが最新の状態で、ビルドがトリガーされない場合、ビルド前イベントは実行されません。

5. **[ビルド後に実行するコマンド ライン]** ボックスで、ビルド イベントの構文を指定します。

   > [!NOTE]
   > *.bat* ファイルを実行するすべてのビルド後コマンドの前に `call` ステートメントを追加します。 たとえば、`call C:\MyFile.bat` または `call C:\MyFile.bat call C:\MyFile2.bat` のようにします。

6. **[ビルド後イベントの実行]** ボックスで、ビルド後イベントを実行する条件を指定します。

   > [!NOTE]
   > 長い構文を追加する場合、または [[ビルド前に実行するコマンド ライン]/[ビルド後に実行するコマンド ライン] ダイアログ ボックス](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)でビルド マクロを選択する場合は、省略記号 **[...]** ボタンをクリックして編集ボックスを表示します。

   ビルド イベントの構文では、コマンド プロンプトまたは *.bat* ファイルで有効な任意のコマンドを使うことができます。 後続のすべてのコマンドが確実に実行されるように、バッチ ファイルの名前の前には `call` を記述する必要があります。

   > [!NOTE]
   > ビルド前またはビルド後イベントが正常に完了しない場合は、アクションの成功を示すゼロ (0) 以外のコードでイベント アクションを終了させて、ビルドを強制終了することができます。

## <a name="example"></a>例

次の手順は、ビルド後イベントから呼び出される *.exe* コマンドを使って、アプリケーション マニフェスト (プロジェクト ディレクトリ内の *.exe.manifest* ファイル) 内にオペレーティング システムの最小バージョンを設定する方法を示しています。 オペレーティング システムの最小バージョンは、4.10.0.0 などの 4 つの部分に分かれた数字です。 オペレーティング システムの最小バージョンを設定するには、コマンドによってマニフェストの `<dependentOS>` セクションを変更します。

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>アプリケーション マニフェストを変更する .exe コマンドを作成する

1. コマンド用の新しい**コンソール アプリ** プロジェクトを作成します。 プロジェクトに **ChangeOSVersionCS** という名前を付けます。

2. *Program.cs* で、ファイルの先頭にある他の `using` ステートメントに次の行を追加します。

   ```csharp
   using System.Xml;
   ```

3. `ChangeOSVersionCS` 名前空間で、`Program` クラスの実装を次のコードに置き換えます。

   ```csharp
   class Program
   {
      /// <summary>
      /// This function sets the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest)
      /// 1 - Version of OS
      ///</param>
      static void Main(string[] args)
      {
         string applicationManifestPath = args[0];
         Console.WriteLine("Application Manifest Path: " + applicationManifestPath);

         // Get version name.
         Version osVersion = null;
         if (args.Length >=2 ){
            osVersion = new Version(args[1]);
         }else{
            throw new ArgumentException("OS Version not specified.");
         }
         Console.WriteLine("Desired OS Version: " + osVersion.ToString());

         XmlDocument document;
         XmlNamespaceManager namespaceManager;
         namespaceManager = new XmlNamespaceManager(new NameTable());
         namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");
         namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");

         document = new XmlDocument();
         document.Load(applicationManifestPath);

         string baseXPath;
         baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";

         // Change minimum required operating system version.
         XmlNode node;
         node = document.SelectSingleNode(baseXPath, namespaceManager);
         node.Attributes["majorVersion"].Value = osVersion.Major.ToString();
         node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();
         node.Attributes["buildNumber"].Value = osVersion.Build.ToString();
         node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();

         document.Save(applicationManifestPath);
      }
   }
   ```

   このコマンドは、2 つの引数を受け取ります。1 つはアプリケーション マニフェストへのパス (つまり、ビルド処理でマニフェストが作成されるフォルダーであり、通常は *Projectname.publish*)、もう 1 つは新しいオペレーティング システムのバージョンです。

4. プロジェクトをビルドします。

5. *.exe* ファイルを *C:\TEMP\ChangeOSVersionVB.exe* などのディレクトリにコピーします。

次に、ビルド後のイベントでこのコマンドを呼び出して、アプリケーション マニフェストを変更します。

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>ビルド後のイベントを呼び出してアプリケーション マニフェストを変更する

1. 新しい **Windows フォーム アプリ** プロジェクトを作成し、それに **CSWinApp** という名前を付けます。

2. **ソリューション エクスプローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** を選択します。

3. **プロジェクト デザイナー**で、 **[発行]** ページに移動し、 **[発行場所]** を *C:\TEMP* に設定します。

4. **[今すぐ発行]** をクリックして、プロジェクトを発行します。

   マニフェスト ファイルがビルドされ、*C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest* に保存されます。 マニフェストを表示するには、ファイルを右クリックし、 **[プログラムから開く]** 、 **[一覧からプログラムを選択する]** 、 **[メモ帳]** の順にクリックします。

   ファイルで `<osVersionInfo>` 要素を探します。 たとえば、バージョンは次のように記述されています。

   ```xml
   <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   ```

5. **プロジェクト デザイナー**に戻り、 **[ビルド イベント]** タブをクリックし、 **[ビルド後の編集]** をクリックします。

6. **[ビルド後に実行するコマンド ライン]** ボックスに次のコマンドを入力します。

   `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

   プロジェクトをビルドすると、このコマンドでアプリケーション マニフェストのオペレーティング システムの最小バージョンが 5.1.2600.0 に変更されます。

   `$(TargetPath)` マクロは作成される実行可能ファイルの完全なパスを表すので、`$(TargetPath).manifest` では *bin* ディレクトリに作成されるアプリケーション マニフェストが指定されます。 発行することにより、前に設定した発行場所にこのマニフェストがコピーされます。

7. プロジェクトを再び発行します。

   マニフェストのバージョンは次のように表示されます。

   ```xml
   <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
   ```

## <a name="see-also"></a>関連項目

- [[ビルド イベント] ページ (プロジェクト デザイナー) (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [[ビルド前に実行するコマンド ライン] / [ビルド後に実行するコマンド ライン] ダイアログ ボックス](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [方法: ビルド イベントを指定する (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [コンパイルとビルド](../ide/compiling-and-building-in-visual-studio.md)