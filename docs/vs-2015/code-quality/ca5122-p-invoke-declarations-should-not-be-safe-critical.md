---
title: CA5122 P/invoke 宣言は安全でない重要な |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: eff316ac6f5d73e157e3dbef5126195bd0d62878
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201489"
---
# <a name="ca5122-pinvoke-declarations-should-not-be-safe-critical"></a>CA5122 P/Invoke 宣言をセーフ クリティカルにしないでください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|
|CheckId|CA5122|
|Category|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 P/Invoke 宣言が <xref:System.Security.SecuritySafeCriticalAttribute> でマークされました。

```csharp
[assembly: AllowPartiallyTrustedCallers]

// ...
public class C
{
    [SecuritySafeCritical]
    [DllImport("kernel32.dll")]
    public static extern bool Beep(int frequency, int duration); // CA5122 – safe critical p/invoke
   }
```

 この例では、`C.Beep(...)` がセキュリティ セーフ クリティカルなメソッドとしてマークされています。

## <a name="rule-description"></a>規則の説明
 メソッドは、セキュリティに対する配慮が必要な操作を行うときは SecuritySafeCritical としてマークされますが、透過的なコードによって使用される場合も安全です。 セキュリティ透過性モデルの基本的な規則の 1 つは、透過的なコードが P/Invoke を通じてネイティブ コードを直接呼び出してはいけないということです。 そのため、P/Invoke をセキュリティ セーフ クリティカルとしてマークしても、透過的なコードはそれを呼び出すことができず、セキュリティ分析の際に紛らわしくなります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 透過的なコードで P/Invoke を使用できるようにするには、そのコードのためのセキュリティ セーフ クリティカルなラッパー メソッドを公開します。

```csharp
[assembly: AllowPartiallyTrustedCallers

class C
{
   [SecurityCritical]
   [DllImport(“kernel32.dll”, EntryPoint=”Beep”)]
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke

   [SecuritySafeCritical]
   public static bool Beep(int frequency, int duration)
   {
      return BeepPInvoke(frequency, duration);
   }
}
```

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。
