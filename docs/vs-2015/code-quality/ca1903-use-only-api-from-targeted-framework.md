---
title: CA1903:対象のフレームワークから API のみを使用して、|Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 146563dfa358367e7c22f8ad37564b85d64eaf1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189080"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903:対象のフレームワークから API のみを使用します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio の最新ドキュメントについては、次を参照してください[CA1903:。対象のフレームワークから API のみを使用して、](https://docs.microsoft.com/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework)します。  
  
|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|Category|Microsoft.Portability|  
|互換性に影響する変更点|– の外部から参照できるメンバーまたは型のシグネチャに対して発生した場合。<br /><br /> 改行しない - メソッドの本体で発生したときにします。|  
  
## <a name="cause"></a>原因  
 メンバーまたはないプロジェクトの対象とする framework に含まれていたサービス パックで導入された型、メンバーまたは型を使用します。  
  
## <a name="rule-description"></a>規則の説明  
 新しいメンバーと型は、.NET Framework 2.0 Service Pack 1 および 2、.NET Framework 3.0 Service Pack 1 と 2、および .NET Framework 3.5 Service Pack 1 で追加されました。 .NET Framework のメジャー バージョンを対象とするプロジェクトは、新しい Api でこれらの依存関係を意図せず実行できます。 この依存関係を防ぐためには、この規則は、任意の新しいメンバーとプロジェクトのターゲット フレームワークでは既定で含まれていない型の使用に適用されます。  
  
 **ターゲット フレームワークおよびサービス パックの依存関係**  
  
|||  
|-|-|  
|ターゲット フレームワーク|導入されたメンバーの使用状況で起動されます。|  
|.NET Framework 2.0|.NET framework 2.0 SP1 では、.NET Framework 2.0 SP2|  
|.NET Framework 3.0|.NET framework 2.0 SP1、.NET Framework 2.0 SP2、.NET Framework 3.0 SP1、.NET Framework 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|N/A|  
  
 プロジェクトのターゲット フレームワークを変更するを参照してください。[特定の .NET Framework のバージョンを対象とする](../ide/targeting-a-specific-dotnet-framework-version.md)します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 サービス パックへの依存関係を削除するには、新しいメンバーまたは型のすべての使用状況を削除します。 これが意図的な依存関係の場合は、警告を抑制するか、または、このルールをオフにします。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 これが、指定されたサービス パックに依存関係が意図的でない場合は、この規則による警告を抑制しないでください。 このような状況で、アプリケーションは、この service pack がインストールされていないシステムで実行する失敗可能性があります。 警告を抑制または意図的な依存関係の場合に、このルールをオフにします。  
  
## <a name="example"></a>例  
 次の例では、.NET 2.0 Service Pack 1 で使用できるだけが DateTimeOffset 型を使用するクラスを示します。 この例では、.NET Framework 2.0 がプロジェクトのプロパティでターゲット フレームワーク ドロップダウン リストで選択されている必要があります。  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]  
  
## <a name="example"></a>例  
 次の例は、DateTimeOffset 型の使用状況を DateTime 型に置き換えることにより、前に説明した違反を修正します。  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]  
  
## <a name="see-also"></a>関連項目  
 [移植性に関する警告](../code-quality/portability-warnings.md)   
 [対象となる特定の .NET Framework バージョンの指定](../ide/targeting-a-specific-dotnet-framework-version.md)
