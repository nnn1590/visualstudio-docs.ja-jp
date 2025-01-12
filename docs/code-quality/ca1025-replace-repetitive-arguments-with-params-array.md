---
title: CA1025:反復する引数を params 配列で置き換えます
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5014bfe809cb5d56a22e971833128d1f48d77319
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922965"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025:反復する引数を params 配列で置き換えます

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Category|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
パブリック型のパブリックメソッドまたはプロテクトメソッドに3つ以上のパラメーターがあり、その最後の3つのパラメーターが同じ型です。

## <a name="rule-description"></a>規則の説明
引数の正確な数が不明で、可変個の引数が同じ型である場合、または同じ型として渡すことができる場合は、引数を繰り返す代わりにパラメーター配列を使用します。 たとえば、メソッドは<xref:System.Console.WriteLine%2A> 、パラメーター配列を使用して任意の数の<xref:System.Object>引数を受け入れる汎用オーバーロードを提供します。

## <a name="how-to-fix-violations"></a>違反の修正方法
この規則違反を修正するには、繰り返し引数をパラメーター配列に置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
このルールからの警告を抑制するのは常に安全です。ただし、このような設計では、ユーザビリティの問題が発生する可能性があります。

## <a name="example"></a>例
次の例は、この規則に違反する型を示しています。

[!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]