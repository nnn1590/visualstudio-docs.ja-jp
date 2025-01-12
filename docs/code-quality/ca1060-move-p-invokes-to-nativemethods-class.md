---
title: CA1060:P/Invoke を NativeMethods クラスに移動します
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9c05c0b17bc9866edd7c07874be14578ed4cf884
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922558"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060:P/Invoke を NativeMethods クラスに移動します

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

メソッドは、プラットフォーム呼び出しサービスを使用してアンマネージコードにアクセスし、 **NativeMethods**クラスのいずれのメンバーでもありません。

## <a name="rule-description"></a>規則の説明

<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>属性を使用してマークされている、またはの`Declare` [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]キーワードを使用して定義されているメソッドなどのプラットフォーム呼び出しメソッドは、アンマネージコードにアクセスします。 これらのメソッドは、次のいずれかのクラスに含まれている必要があります。

- **NativeMethods** -このクラスは、アンマネージコードのアクセス許可のスタックウォークを抑制しません。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>このクラスに適用することはできません)。このクラスは、スタックウォークが実行されるため、どこからでも使用できるメソッド用です。

- **SafeNativeMethods** -このクラスは、アンマネージコードのアクセス許可のスタックウォークを抑制します。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>は、このクラスに適用されます。)このクラスは、だれもが安全に呼び出すことができるメソッドを対象としています。 これらのメソッドの呼び出し元は、メソッドがどの呼び出し元に対しても無害であるため、完全なセキュリティレビューを実行して、使用方法が安全であることを確認する必要はありません。

- **UnsafeNativeMethods** -このクラスは、アンマネージコードのアクセス許可のスタックウォークを抑制します。 (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>は、このクラスに適用されます。)このクラスは、危険である可能性のあるメソッドを対象としています。 これらのメソッドの呼び出し元は、完全なセキュリティレビューを実行して、スタックウォークが実行されないため、使用状況が安全であることを確認する必要があります。

これらのクラスは、 `internal` (`Friend`Visual Basic の) として宣言され、新しいインスタンスが作成されないようにするためのプライベートコンストラクターを宣言します。 これらのクラスのメソッドは、 `static`と`internal` (`Shared` `Friend` Visual Basic) である必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
この規則違反を修正するには、メソッドを適切な**NativeMethods**クラスに移動します。 ほとんどのアプリケーションでは、P/Invoke を**NativeMethods**という名前の新しいクラスに移動するだけで十分です。

ただし、他のアプリケーションで使用するためのライブラリを開発している場合は、 **SafeNativeMethods**と**UnsafeNativeMethods**という2つのクラスを定義することを検討してください。 これらのクラスは、 **NativeMethods**クラスに似ています。ただし、これらは**SuppressUnmanagedCodeSecurityAttribute**という特殊な属性を使用してマークされます。 この属性が適用されると、ランタイムは完全なスタックウォークを実行せず、すべての呼び出し元に**UnmanagedCode**アクセス許可があることを確認します。 通常、ランタイムは起動時にこのアクセス許可をチェックします。 このチェックは実行されないため、これらのアンマネージメソッドの呼び出しのパフォーマンスを大幅に向上させることができます。また、これらのメソッドを呼び出すためのアクセス許可が制限されているコードを有効にすることもできます。

ただし、この属性は細心の注意を払って使用する必要があります。 正しく実装されていない場合、セキュリティに深刻な影響を及ぼす可能性があります。「」をご覧ください。

メソッドの実装方法の詳細については、 **NativeMethods**の例、 **SafeNativeMethods**の例、および**UnsafeNativeMethods**の例を参照してください。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
この規則による警告は抑制しないでください。

## <a name="example"></a>例
次の例では、この規則に違反するメソッドを宣言しています。 違反を修正するには、 **Removedirectory** p/Invoke を、p/invoke のみを保持するように設計された適切なクラスに移動する必要があります。

[!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
[!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]

## <a name="nativemethods-example"></a>NativeMethods の例

### <a name="description"></a>説明
**NativeMethods**クラスは**SuppressUnmanagedCodeSecurityAttribute**を使用してマークされないようにする必要があるため、このクラスに格納されている P/invoke には**UnmanagedCode**アクセス許可が必要です。 ほとんどのアプリケーションはローカルコンピューターから実行され、完全信頼と共に実行されるため、通常は問題ではありません。 ただし、再利用可能なライブラリを開発している場合は、 **SafeNativeMethods**クラスまたは**UnsafeNativeMethods**クラスを定義することを検討してください。

次の例は、user32.dll から**messagebeep**関数をラップする**ビープ**音のメソッドを示しています。 **Messagebeep** P/Invoke は**NativeMethods**クラスに格納されます。

### <a name="code"></a>コード
[!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
[!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]

## <a name="safenativemethods-example"></a>SafeNativeMethods の例

### <a name="description"></a>説明
P/Invoke メソッドは、任意のアプリケーションに安全に公開でき、副作用がない場合は、 **SafeNativeMethods**という名前のクラスに配置する必要があります。 アクセス許可を要求する必要はなく、どこから呼び出されたかについての注意を払う必要はありません。

次の例は、kernel32.dll から**GetTickCount**関数をラップする**TickCount**プロパティを示しています。

### <a name="code"></a>コード
[!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
[!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]

## <a name="unsafenativemethods-example"></a>UnsafeNativeMethods の例

### <a name="description"></a>説明
安全に呼び出すことができず、副作用を引き起こす可能性のある P/Invoke メソッドは、 **UnsafeNativeMethods**という名前のクラスに配置する必要があります。 これらのメソッドは、意図せずにユーザーに公開されないように厳密にチェックする必要があります。 ルール[CA2118:この問題を](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)解決するには、SuppressUnmanagedCodeSecurityAttribute の使用状況を確認してください。 また、メソッドには、使用時に**UnmanagedCode**の代わりに要求される別のアクセス許可が必要です。

次の例は、user32.dll から**ShowCursor**関数をラップする**Hide**メソッドを示しています。

### <a name="code"></a>コード
[!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
[!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]

## <a name="see-also"></a>関連項目

- [デザインの警告](../code-quality/design-warnings.md)