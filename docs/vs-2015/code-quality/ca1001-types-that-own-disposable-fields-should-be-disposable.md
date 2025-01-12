---
title: CA1001:破棄可能なフィールドは破棄可能にする必要がありますを所有する型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 98be3bafb582e4d48560108625be911e53acf664
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562316"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001:破棄可能なフィールドを所有する型は、破棄可能でなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|CheckId|CA1001|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|改行の種類が、アセンブリの外部に表示されない場合。<br /><br /> – 型は、アセンブリ外部から参照できる場合。|  
  
## <a name="cause"></a>原因  
 クラスの宣言およびインスタンス フィールドの実装を<xref:System.IDisposable?displayProperty=fullName>型とクラスを実装しません<xref:System.IDisposable>します。  
  
## <a name="rule-description"></a>規則の説明  
 クラスを実装する、<xref:System.IDisposable>を所有しているアンマネージ リソースを破棄するインターフェイス。 あるインスタンス フィールド、<xref:System.IDisposable>型では、フィールドがアンマネージ リソースを所有していることを示します。 宣言するクラス、<xref:System.IDisposable>フィールドは間接的にアンマネージ リソースを所有し、実装する必要があります、<xref:System.IDisposable>インターフェイス。 クラスは、アンマネージ リソースを直接所有していない、ファイナライザーを実装する必要があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 このルールの違反を修正するには、実装<xref:System.IDisposable>との間、<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>メソッドの呼び出し、<xref:System.IDisposable.Dispose%2A>フィールドのメソッド。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例は、規則に違反するクラスとクラスを実装することで、ルールを満たす<xref:System.IDisposable>します。 クラスは、クラスがアンマネージ リソースを直接所有していないために、ファイナライザーを実装しません。  
  
 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]  
  
## <a name="related-rules"></a>関連規則  
 [CA2213: 破棄可能なフィールドは破棄されなければなりません](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA 2216:破棄可能な型はファイナライザーを宣言する必要があります。](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215:Dispose メソッドが基底クラス dispose を呼び出す必要があります。](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA 1049:ネイティブ リソースを所有する型は、破棄可能でなければなりません](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
