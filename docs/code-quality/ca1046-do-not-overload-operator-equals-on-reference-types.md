---
title: CA1046:参照型で、演算子 equals をオーバーロードしないでください
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d765bfda87fe184256304b86f145f4f02adb7db6
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922629"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046:参照型で、演算子 equals をオーバーロードしないでください

|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Category|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
パブリックまたは入れ子にされたパブリック参照型は、等値演算子をオーバーロードします。

## <a name="rule-description"></a>規則の説明
参照型の場合、等値演算子は既定の実装でほぼ問題がありません。 既定で、2 つの参照が等値と見なされるのは、同じオブジェクトを参照する場合のみです。

## <a name="how-to-fix-violations"></a>違反の修正方法
この規則違反を修正するには、等値演算子の実装を削除します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
参照型が組み込みの値型のように動作する場合は、この規則からの警告を抑制することが安全です。 型のインスタンスに対して加算または減算を実行するのに意味がある場合は、等値演算子を実装し、違反を抑制することが適切な場合があります。

## <a name="example"></a>例
次の例は、2つの参照を比較する場合の既定の動作を示しています。

[!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>例

次のアプリケーションは、一部の参照を比較します。

[!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

この例を実行すると、次の出力が生成されます。

```txt
a = new (2,2) and b = new (2,2) are equal? No
c and a are equal? Yes
b and a are == ? No
c and a are == ? Yes
```

## <a name="related-rules"></a>関連するルール

[CA1013オーバーロードされた加算と減算で、演算子 equals をオーバーロードします](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>関連項目

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [等値演算子](/dotnet/standard/design-guidelines/equality-operators)