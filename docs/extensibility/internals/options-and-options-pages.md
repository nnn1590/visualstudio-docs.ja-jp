---
title: オプションと [オプション] ページ |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c336503b80e2af34ac58c7debde16895d7f2585
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314847"
---
# <a name="options-and-options-pages"></a>オプションとオプション ページ
クリックすると**オプション**上、**ツール** メニューが開きます、**オプション** ダイアログ ボックス。 このダイアログ ボックスのオプションを [オプション] ページとしてと総称されます。 すべてのカテゴリが [オプション] ページおよびのツリー コントロール ナビゲーション ウィンドウにはにオプションのカテゴリが含まれます。 ページを選択すると、右側のウィンドウでそのオプションが表示されます。 これらのページを使用して、VSPackage の状態を決定するオプションの値を変更できます。

## <a name="support-for-options-pages"></a>[オプション] ページのサポート
 <xref:Microsoft.VisualStudio.Shell.Package>クラスは、[オプション] ページとオプションのカテゴリを作成するためのサポートを提供します。 <xref:Microsoft.VisualStudio.Shell.DialogPage>クラスは、[オプション] ページを実装します。

 既定の実装<xref:Microsoft.VisualStudio.Shell.DialogPage>プロパティの汎用のグリッド内のユーザーにそのパブリック プロパティを提供しています。 独自のユーザー インターフェイス (UI) を持つカスタム オプション ページを作成するページのさまざまなメソッドをオーバーライドすることで、この動作をカスタマイズできます。 詳細については、次を参照してください。[オプション ページの作成](../../extensibility/creating-an-options-page.md)です。

 <xref:Microsoft.VisualStudio.Shell.DialogPage>クラスが実装する<xref:Microsoft.VisualStudio.Shell.IProfileManager>、[オプション] ページとユーザー設定の永続化を提供します。 既定の実装、<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>と<xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A>と文字列の間に、プロパティを変換できる場合、メソッドは、レジストリのユーザー セクションにプロパティの変更を保持します。

## <a name="options-page-registry-path"></a>オプション ページのレジストリ パス
 既定では、オプション ページによって管理されるプロパティのレジストリ パスは組み合わせで決まります<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>、word DialogPage、およびオプションのページ クラスの型名。 たとえば、次のようにオプション ページ クラスを定義できるかもしれません。

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 場合、 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp、プロパティの名前と値のペアは HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ のサブキーがCompany.OptionsPage.OptionsPageGeneral します。

 オプション ページ自体のレジストリ パスが組み合わせで決まります<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>単語、ToolsOptionsPages、およびオプション ページのカテゴリと名前。 たとえば、カスタム オプション ページには、カテゴリでは、個人用のオプション ページと<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp、オプション ページには、レジストリ キー hkey_local_machine \software\microsoft\ ですがVisualStudio\8.0Exp\ToolsOptionsPages\My オプション Pages\Custom します。

## <a name="toolsoptions-page-attributes-and-layout"></a>ツール/オプション ページの属性とレイアウト
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>属性のカスタム オプション ページのナビゲーション ツリーでのカテゴリにグループ化を指定します、**オプション** ダイアログ ボックス。 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>属性インターフェイスを提供する VSPackage のオプション ページに関連付けます。 次のコードがあるとします。

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 これは、MyPackage が OptionsPageGeneral と OptionsPageCustom、2 つのオプション ページを提供することを宣言します。 **オプション**にダイアログ ボックスで、両方のオプション ページの表示、**マイ オプション ページ**としてカテゴリ**全般**と**カスタム**、それぞれします。

## <a name="option-attributes-and-layout"></a>オプションの属性とレイアウト
 ページを提供するユーザー インターフェイス (UI) は、カスタム オプション ページのオプションの外観を決定します。 レイアウト、ラベル付け、および汎用オプション ページのオプションの説明については、次の属性によって決まります。

- <xref:System.ComponentModel.CategoryAttribute> オプションのカテゴリを決定します。

- <xref:System.ComponentModel.DisplayNameAttribute> オプションの表示名を決定します。

- <xref:System.ComponentModel.DescriptionAttribute> オプションの説明を決定します。

  > [!NOTE]
  > 同等の属性、SRCategory、LocDisplayName、および SRDescription、ローカライズ文字列リソースを使用して、で定義されて、[マネージ プロジェクト サンプル](http://go.microsoft.com/fwlink/?LinkId=122774)します。

  次のコードがあるとします。

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  OptionInteger オプションとして [オプション] ページに表示されます**整数オプション**で、 **My Options**カテゴリ。 オプションが選択されている場合、説明、**マイ整数オプション**、[説明] ボックスに表示されます。

## <a name="accessing-options-pages-from-another-vspackage"></a>別の VSPackage から [オプション] ページにアクセスします。
 ホストしてオプション ページを管理する VSPackage は、別の VSPackage からでプログラムによって、オートメーション モデルを使用してアクセスできます。 たとえば、次のコードでは、VSPackage は、オプション ページをホストとして登録されます。

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 次のコード フラグメントは、MyOptionPage から OptionInteger の値を取得します。

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 ときに、<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>属性は、オプション ページを登録、AutomationProperties キーの場合 の下に、ページが登録されている、`SupportsAutomation`属性の引数が`true`します。 Automation は、関連付けられている VSPackage とオートメーションを検索するには、このレジストリ エントリを検査し、ホストされているオプション ページ、ここでは、個人用のグリッド ページで、プロパティにアクセスします。

 オートメーション プロパティのレジストリ パスが組み合わせで決まります<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>単語、AutomationProperties、およびオプション ページのカテゴリと名前。 たとえば、次のオプション ページには、My Category カテゴリ、個人用のグリッド ページ名、および<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp 後のオートメーション プロパティが、レジストリ キー HKEY_LOCAL_MACHINEMicrosoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My グリッド ページ。

> [!NOTE]
> 正規名、個人用の Category.My グリッド ページでは、このキーの名前のサブキーの値です。