---
title: CA1903:対象のフレームワークから API のみを使用します
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d972198898dd1a4cafa5280c129db38bb3e4982
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921297"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903:対象のフレームワークから API のみを使用します

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Category|Microsoft. 移植性|
|互換性に影響する変更点|中断-外部から参照できるメンバーまたは型のシグネチャに対して発生した場合。<br /><br /> 非中断-メソッドの本体で発生した場合。|

## <a name="cause"></a>原因
メンバーまたは型が、プロジェクトの対象となるフレームワークに含まれていなかった Service Pack で導入されたメンバーまたは型を使用しています。

## <a name="rule-description"></a>規則の説明
新しいメンバーと型は .NET Framework 2.0 Service Pack 1 および2、.NET Framework 3.0 Service Pack 1 と2、および .NET Framework 3.5 Service Pack 1 に含まれていました。 .NET Framework のメジャーバージョンを対象とするプロジェクトでは、これらの新しい Api に対する依存関係を意図せずに取得できます。 この依存関係を防ぐため、この規則は、プロジェクトのターゲットフレームワークに既定で含まれていない新しいメンバーおよび型の使用時に適用されます。

**ターゲットフレームワークと Service Pack の依存関係**

|||
|-|-|
|ターゲットフレームワークが|で導入されたメンバーの使用時に発生します|
|.NET Framework 2.0|.NET Framework 2.0 SP1、.NET Framework 2.0 SP2|
|.NET Framework 3.0|.NET Framework 2.0 SP1、.NET Framework 2.0 SP2、.NET Framework 3.0 SP1、.NET Framework 3.0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|N/A|

プロジェクトのターゲットフレームワークを変更するには[、「方法:特定の .NET バージョンをターゲットにする](../ide/how-to-target-a-version-of-the-dotnet-framework.md)」を参照してください。

## <a name="how-to-fix-violations"></a>違反の修正方法
Service Pack の依存関係を削除するには、新しいメンバーまたは型のすべての使用を削除します。 これが意図的な依存関係である場合は、警告を抑制するか、この規則を無効にします。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
指定された Service Pack に意図的に依存していない場合は、この規則による警告を抑制しないでください。 このような状況では、この Service Pack インストールされていないシステムでは、アプリケーションの実行が失敗する可能性があります。 意図的な依存関係である場合は、警告を抑制するか、この規則を無効にします。

## <a name="example"></a>例
次の例は、.NET 2.0 Service Pack 1 でのみ使用できる DateTimeOffset 型を使用するクラスを示しています。 この例では、プロジェクトプロパティの [ターゲットフレームワーク] ボックスの一覧で .NET Framework 2.0 が選択されている必要があります。

[!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>例
次の例では、DateTimeOffset 型の使用法を DateTime 型に置き換えることによって、前述の違反を修正します。

[!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>関連項目

- [Portability Warnings](../code-quality/portability-warnings.md)
- [フレームワーク対象設定機能の概要](../ide/visual-studio-multi-targeting-overview.md)