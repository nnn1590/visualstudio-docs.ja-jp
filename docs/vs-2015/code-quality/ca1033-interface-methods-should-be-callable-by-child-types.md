---
title: CA1033:インターフェイス メソッドは、子型によって呼び出し可能でなければなりません。Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bd801e7afc1fa0a4edf043aba560bc4afcdae9de
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682845"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033:インターフェイス メソッドは、子型によって呼び出し可能でなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 シールされていない外部から参照できる型によって、パブリック インターフェイスを持つメソッドを明示的に実装しています。また、同じ名前を持つ外部から参照できる代替のメソッドがありません。

## <a name="rule-description"></a>規則の説明
 パブリック インターフェイスのメソッドを明示的に実装する基本データ型を検討してください。 基本型から派生した型は、現在のインスタンスへの参照を介してのみ継承インターフェイス メソッドにアクセスできます (`this` (C#)) は、インターフェイスにキャストします。 派生型、継承されたインターフェイスのメソッドを再実装 (明示的)、基本の実装がアクセスできなくできます。 現在のインスタンス参照を通じて呼び出しは、派生実装を呼び出しますこれにより、再帰と最終的にスタック オーバーフローします。

 このルールでの明示的な実装の違反が発生しない<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>ときに、外部から参照できる`Close()`または`System.IDisposable.Dispose(Boolean)`メソッドが提供されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則の違反を修正するには、同じ機能を公開し、派生型には、新しいメソッドを実装するか、非明示的な実装を変更します。 重大な変更が許容される場合は、代替策は、型をシールします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を抑制する、外部から参照できるメソッドが明示的に実装されたメソッドとは異なる名前が同じ機能を持つ指定された場合に安全です。

## <a name="example"></a>例
 次の例は、型`ViolatingBase`、ルールと、型に違反する`FixedBase`違反の修正プログラムを表示します。

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]

## <a name="see-also"></a>関連項目
 [インターフェイス](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)
