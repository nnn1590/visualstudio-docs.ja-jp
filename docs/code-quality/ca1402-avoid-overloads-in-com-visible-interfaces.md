---
title: CA1402:COM 参照可能インターフェイスでのオーバーロードを避けてください
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: aa45a54a994d19b1a04bc0785f21b88dfeef4475
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922125"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402:COM 参照可能インターフェイスでのオーバーロードを避けてください

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Category|Microsoft. 相互運用性|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
コンポーネントオブジェクトモデル (COM) で参照できるインターフェイスが、オーバーロードされたメソッドを宣言しています。

## <a name="rule-description"></a>規則の説明
オーバーロードされたメソッドが COM クライアントに公開されると、最初のメソッド オーバーロードだけが名前を保持します。 後続のオーバーロードは、名前にアンダースコア文字 ' _ '、オーバーロードの宣言の順序に対応する整数を追加することによって、一意の名前に変更されます。 たとえば、次の方法を考えてみます。

```csharp
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

これらのメソッドは、次のように COM クライアントに公開されます。

```csharp
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

Visual Basic 6 COM クライアントは、名前にアンダースコアを使用してインターフェイスメソッドを実装することはできません。

## <a name="how-to-fix-violations"></a>違反の修正方法
この規則違反を修正するには、オーバーロードされたメソッドの名前を変更して、名前が一意になるようにします。 または、アクセシビリティ`internal`を (`Friend`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]は) に変更するか<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 、属性をに`false`設定して、COM でインターフェイスを非表示にします。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
この規則による警告は抑制しないでください。

## <a name="example"></a>例
次の例は、規則に違反するインターフェイスと、規則を満たすインターフェイスを示しています。

[!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
[!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]

## <a name="related-rules"></a>関連するルール
[CA1413COM 参照可能な値型ではパブリックでないフィールドを避けてください](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407COM 参照可能な型で静的メンバーを避けます](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017アセンブリを ComVisibleAttribute にマークします](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>関連項目

- [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)
- [Long データ型](/dotnet/visual-basic/language-reference/data-types/long-data-type)