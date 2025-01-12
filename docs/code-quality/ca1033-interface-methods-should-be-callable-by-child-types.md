---
title: CA1033:インターフェイス メソッドは、子型によって呼び出し可能でなければなりません
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10db644fe4cf65a7336ef8bd50dcf62e072e1c46
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922952"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033:インターフェイス メソッドは、子型によって呼び出し可能でなければなりません

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Category|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
シールされていない外部から参照できる型によって、パブリック インターフェイスを持つメソッドを明示的に実装しています。また、同じ名前を持つ外部から参照できる代替のメソッドがありません。

## <a name="rule-description"></a>規則の説明
パブリックインターフェイスメソッドを明示的に実装する基本型について考えてみます。 基本型から派生した型は、インターフェイスにキャストされる現在のインスタンス (`this`内C#) への参照によってのみ、継承されたインターフェイスメソッドにアクセスできます。 派生型が継承されたインターフェイスメソッドを再実装 (明示的に) すると、基本実装にアクセスできなくなります。 現在のインスタンス参照を使用して呼び出すと、派生した実装が呼び出されます。これにより、再帰と最終的なスタックオーバーフローが発生します。

この規則は、外部から参照可能<xref:System.IDisposable.Dispose%2A?displayProperty=fullName> `Close()`なまたは`System.IDisposable.Dispose(Boolean)`メソッドが指定されている場合に、の明示的な実装に対する違反を報告しません。

## <a name="how-to-fix-violations"></a>違反の修正方法
この規則違反を修正するには、同じ機能を公開し、派生型から参照できるようにするか、または非明示的な実装に変更する新しいメソッドを実装します。 互換性に影響する変更が許容される場合、別の方法として、型をシールする方法があります。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
外部から参照可能なメソッドが提供されていても、明示的に実装されたメソッドとは異なる名前を持つ場合は、この規則による警告を抑制することが安全です。

## <a name="example"></a>例
次の例は、規則に`ViolatingBase`違反する型と、違反の修正を`FixedBase`示す型を示しています。

[!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>関連項目
[インターフェイス](/dotnet/csharp/programming-guide/interfaces/index)