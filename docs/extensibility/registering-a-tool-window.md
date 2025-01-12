---
title: ツール ウィンドウの登録 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ae53481b773cfdad5d4ac70f90202fcfd9d1ad4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334324"
---
# <a name="register-a-tool-window"></a>ツール ウィンドウを登録します。
使用して、ツール ウィンドウを登録する<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>と<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>します。

## <a name="example"></a>例

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 上記のコードで、<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>登録、`PersistedWindowPane`と`DynamicWindowPane`ツール ウィンドウが Visual Studio を使用します。 永続化されたツール ウィンドウをドッキングされをタブ付き**ソリューション エクスプ ローラー**と動的のウィンドウで、既定の開始位置とサイズを指定します。 動的なウィンドウが作成された一時的なもので起動時に作成されていないことを示します。 これを書き込みます、`DontForceCreate`値、`ToolWindows`システム レジストリのキー。 詳細については、次を参照してください。[ツール ウィンドウの表示構成](../extensibility/tool-window-display-configuration.md)します。
