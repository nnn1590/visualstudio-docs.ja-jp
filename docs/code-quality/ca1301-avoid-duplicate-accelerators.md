---
title: CA1301:重複するアクセラレータを使用しません
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16cd44f00db13027d737b6a6b496877075ac6fa9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922270"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301:重複するアクセラレータを使用しません

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Category|Microsoft のグローバリゼーション|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
型はを<xref:System.Windows.Forms.Control?displayProperty=fullName>拡張し、リソースファイルに格納されているアクセスキーが同じである2つ以上のトップレベルコントロールを含みます。

## <a name="rule-description"></a>規則の説明

アクセスキーは、アクセラレータとも呼ばれ、 **Alt**キーを使用してコントロールにキーボードでアクセスできるようにします。 複数のコントロールが同じアクセスキーを持っている場合は、アクセスキーの動作が適切に定義されていません。 ユーザーは、アクセスキーを使用して目的のコントロールにアクセスできない可能性があります。また、目的のコントロール以外のコントロールが有効になっている可能性があります。

このルールの現在の実装では、メニュー項目が無視されます。 ただし、同じサブメニュー内のメニュー項目は、同じアクセスキーを持つことはできません。

## <a name="how-to-fix-violations"></a>違反の修正方法
この規則違反を修正するには、すべてのコントロールに対して一意のアクセスキーを定義します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
この規則による警告は抑制しないでください。

## <a name="example"></a>例
次の例は、同じアクセスキーを持つ2つのコントロールを含む、最小のフォームを示しています。 キーは、表示されないリソースファイルに格納されます。 ただし、それらの値はコメントアウト`checkBox.Text`された行に表示されます。 重複するアクセラレータの動作は、コメントアウトされ`checkBox.Text`たものと行を交換することによって調べることができます。 ただし、この例では、ルールから警告が生成されません。

[!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>関連項目

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [デスクトップ アプリケーションのリソース](/dotnet/framework/resources/index)