---
title: CA2230:可変個の引数のパラメーターを使用します |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8b833f520c574c32f90ff1ec5e20a9671184b78a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685097"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230:可変引数に対して param を使用します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型に使用するパブリックまたはプロテクト メソッドが含まれています、`VarArgs`呼び出し規約。

## <a name="rule-description"></a>規則の説明
 `VarArgs`呼び出し規約は可変個のパラメーターを受け取る特定のメソッド定義で使用します。 メソッドを使用して、`VarArgs`共通言語仕様 (CLS) 準拠でない呼び出し規約、およびプログラミング言語でアクセスできない可能性があります。

 C# で、`VarArgs`呼び出し規約は、メソッドのパラメーター リストが終わるときに使用、`__arglist`キーワード。 Visual Basic がサポートしていません、`VarArgs`呼び出し規約、および Visual C の使用が省略記号ボタンを使用するアンマネージ コードでのみ使用`...`表記します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正する (C#) を使用、 [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012)キーワードの代わりに`__arglist`します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、ルールに違反している使用し、規則に適合するいずれかを使用する、2 つの方法を示します。

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>関連項目
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [Language Independence and Language-independent Components](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
