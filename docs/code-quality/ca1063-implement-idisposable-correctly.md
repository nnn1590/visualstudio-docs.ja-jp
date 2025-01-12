---
title: CA1063:IDisposable を正しく実装します
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 837659ca24eb66995626668185500db7bc32bbd7
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547374"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063:IDisposable を正しく実装します

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Category|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

<xref:System.IDisposable?displayProperty=nameWithType>インターフェイスが正しく実装されていません。 これには、次のような原因が考えられます。

- <xref:System.IDisposable>はクラスの再実装です。

- `Finalize`もう一度オーバーライドされます。

- `Dispose()`がオーバーライドされます。

- メソッドが public、 [sealed](/dotnet/csharp/language-reference/keywords/sealed)、または named Dispose ではありません。 `Dispose()`

- `Dispose(bool)`が protected、virtual、または封印されていません。

- シールされて`Dispose()`いない`Dispose(true)`型では、を呼び出す必要があります。

- シールされてい`Finalize`ない型の場合、実装は`Dispose(bool)`またはのいずれかまたは両方の基本クラスのファイナライザーを呼び出しません。

これらのパターンのいずれかに違反すると、警告 CA1063 がトリガーされます。

<xref:System.IDisposable>インターフェイスを宣言して実装するすべての封印されて`protected virtual void Dispose(bool)`いない型は、独自のメソッドを提供する必要があります。 `Dispose()`はを`Dispose(true)`呼び出す必要があり、 `Dispose(false)`ファイナライザーはを呼び出す必要があります。 <xref:System.IDisposable>インターフェイスを宣言して実装する封印されていない型を作成`Dispose(bool)`する場合は、を定義して呼び出す必要があります。 詳細については、「[アンマネージリソースのクリーンアップ (.net ガイド)](/dotnet/standard/garbage-collection/unmanaged) 」および「 [Dispose pattern](/dotnet/standard/design-guidelines/dispose-pattern)」を参照してください。

既定では、この規則は外部から参照できる型のみを参照しますが、これは[構成可能](#configurability)です。

## <a name="rule-description"></a>規則の説明

すべて<xref:System.IDisposable>の型は、 [Dispose パターン](/dotnet/standard/design-guidelines/dispose-pattern)を正しく実装する必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法

コードを調べて、この違反を修正する次の解決策を特定します。

- 型<xref:System.IDisposable>によって実装されているインターフェイスの一覧からを削除し、代わりに基底クラスの Dispose の実装をオーバーライドします。

- 型からファイナライザーを削除し、Dispose (bool disposing) をオーバーライドし、' disposing ' が false であるコードパスに終了ロジックを配置します。

- Dispose (bool disposing) をオーバーライドし、' disposing ' が true であるコードパスに dispose ロジックを配置します。

- Dispose () が public および[sealed](/dotnet/csharp/language-reference/keywords/sealed)として宣言されていることを確認します。

- Dispose メソッドの名前を**dispose**に変更し、public および[sealed](/dotnet/csharp/language-reference/keywords/sealed)として宣言されていることを確認します。

- Dispose (bool) が protected、virtual、およびシールドとして宣言されていることを確認します。

- Dispose () を変更して dispose (true) を呼び出し、現在<xref:System.GC.SuppressFinalize%2A>のオブジェクトインスタンス (`this`、または`Me` Visual Basic) でを呼び出し、を返します。

- Dispose (false) を呼び出すようにファイナライザーを変更し、を返します。

- <xref:System.IDisposable>インターフェイスを宣言して実装する封印されていない型を作成する場合は<xref:System.IDisposable> 、の実装が、このセクションで前に説明したパターンに従っていることを確認してください。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合

この規則による警告は抑制しないでください。

## <a name="configurability"></a>かつ

この規則を[FxCop アナライザー](install-fxcop-analyzers.md) (レガシ分析ではなく) から実行している場合は、ユーザー補助に基づいて、この規則を実行するコードベースの部分を構成できます。 たとえば、パブリックでない API サーフェイスに対してのみルールを実行するように指定するには、プロジェクトの editorconfig ファイルに次のキーと値のペアを追加します。

```ini
dotnet_code_quality.ca1063.api_surface = private, internal
```

このオプションは、この規則、すべての規則、またはこのカテゴリのすべての規則 (デザイン) に対してのみ構成できます。 詳細については、「 [FxCop アナライザーの構成](configure-fxcop-analyzers.md)」を参照してください。

## <a name="pseudo-code-example"></a>擬似コードの例

次の擬似コードは、マネージリソースとネイティブリソースを使用するクラスに Dispose (bool) を実装する方法の一般的な例を示しています。

```csharp
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

    // Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }

    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```

## <a name="see-also"></a>関連項目

- [Dispose パターン (フレームワークデザインガイドライン)](/dotnet/standard/design-guidelines/dispose-pattern)
- [アンマネージリソースのクリーンアップ (.NET ガイド)](/dotnet/standard/garbage-collection/unmanaged)