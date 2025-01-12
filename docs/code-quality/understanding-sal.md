---
title: SAL について
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 59c5dfa3d7e1e47fbcd2b0d11a0671b2594125c9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923806"
---
# <a name="understanding-sal"></a>SAL について

Microsoft ソースコード注釈言語 (SAL) は、関数がパラメーターをどのように使用するか、そのパラメーターについての前提条件、および終了時に実行する保証を記述するために使用できる一連の注釈を提供します。 注釈は、ヘッダーファイル`<sal.h>`で定義されています。 の Visual Studio code 分析C++では、SAL 注釈を使用して関数の分析を変更します。 Windows ドライバー開発の SAL 2.0 の詳細については、「 [Windows ドライバーの sal 2.0 注釈](http://go.microsoft.com/fwlink/?LinkId=250979)」を参照してください。

ネイティブでは、 C++ C とは、開発者がインテントと非分散を一貫して表現するための限られた方法のみを提供します。 SAL 注釈を使用すると、関数を使用する開発者がその使用方法について理解を深めることができるように、関数をより詳細に記述できます。

## <a name="what-is-sal-and-why-should-you-use-it"></a>SAL の概要とそれを使用する理由

単純に言うと、SAL は、コンパイラがコードを確認できる安価な方法です。

### <a name="sal-makes-code-more-valuable"></a>SAL でコードの価値を高める

SAL は、人間とコード分析ツールの両方において、コードのデザインを理解しやすくするのに役立ちます。 次の例は、C ランタイム関数`memcpy`を示しています。

```cpp

void * memcpy(
   void *dest,
   const void *src,
   size_t count
);
```

この関数の動作を確認できますか。 関数が実装または呼び出された場合、プログラムの正確性を確保するために、特定のプロパティを維持する必要があります。 例に示すような宣言を調べるだけで、何があるのかわかりません。 SAL 注釈がない場合は、ドキュメントまたはコードのコメントに依存する必要があります。 の MSDN ドキュメントでは、次`memcpy`のことを示しています。

> "Src のバイト数をコピーして dest にコピーします。 コピー元とコピー先が重複する場合、memcpy の動作は未定義です。 重複する領域を処理するには、memmove を使用します。
> **セキュリティに関するメモ:** コピー先のバッファーが、ソース バッファーと同じサイズ、または大きいサイズであることを確認してください。 詳細については、「バッファーオーバーランの回避」を参照してください。

このドキュメントには、プログラムの正確性を確保するために、コードで特定のプロパティを維持する必要があることを提案するいくつかの情報が含まれています。

- `memcpy`コピー元のバッファーからコピー先のバッファーにバイトのをコピーします。`count`

- コピー先のバッファーは、少なくともコピー元のバッファーと同じサイズである必要があります。

ただし、コンパイラはドキュメントや非公式のコメントを読み取ることができません。 2つのバッファーと`count`の間にリレーションシップがあることはわかりません。また、リレーションシップを効果的に推測することもできません。 次に示すように、SAL を使用すると、関数のプロパティと実装についてより明確にすることができます。

```cpp

void * memcpy(
   _Out_writes_bytes_all_(count) void *dest,
   _In_reads_bytes_(count) const void *src,
   size_t count
);
```

これらの注釈は MSDN ドキュメントの情報に似ていますが、より簡潔で、意味のあるパターンに従うことに注意してください。 このコードを読むと、この関数のプロパティをすばやく理解し、バッファーオーバーランのセキュリティ問題を回避する方法を確認できます。 さらに、SAL が提供するセマンティックパターンを使用すると、潜在的なバグを早期に検出する際の自動化されたコード分析ツールの効率と効果を向上させることができます。 次のようなバグの`wmemcpy`ある実装をだれかが書いているとします。

```cpp

wchar_t * wmemcpy(
   _Out_writes_all_(count) wchar_t *dest,
   _In_reads_(count) const wchar_t *src,
   size_t count)
{
   size_t i;
   for (i = 0; i <= count; i++) { // BUG: off-by-one error
      dest[i] = src[i];
   }
   return dest;
}
```

この実装には、一般的な1つずつのエラーが含まれています。 幸いなことに、コード作成者には SAL バッファーサイズ注釈が含まれていました。コード分析ツールでは、この関数だけを分析することでバグをキャッチできます。

### <a name="sal-basics"></a>SAL の基礎
SAL は、使用パターンによって分類される4つの基本的な種類のパラメーターを定義します。

|カテゴリ|パラメーター注釈|説明|
|--------------|--------------------------|-----------------|
|**呼び出された関数への入力**|`_In_`|呼び出された関数にデータが渡され、読み取り専用として扱われます。|
|**呼び出された関数への入力と、呼び出し元への出力**|`_Inout_`|使用可能なデータは関数に渡され、変更される可能性があります。|
|**呼び出し元への出力**|`_Out_`|呼び出し元は、呼び出された関数が書き込み先とする領域のみを提供します。 呼び出された関数は、その領域にデータを書き込みます。|
|**呼び出し元へのポインターの出力**|`_Outptr_`|**呼び出し元への出力に**似ています。 呼び出された関数によって返される値は、ポインターです。|

これら4つの基本的な注釈は、さまざまな方法でより明確にすることができます。 既定では、注釈付きポインターパラメーターは必須であると見なされます。関数が成功するためには、NULL 以外である必要があります。 最も一般的に使用される基本的な注釈のバリエーションは、ポインターパラメーターが省略可能であることを示します。 NULL の場合、関数は処理を成功させることができます。

次の表は、必須パラメーターと省略可能なパラメーターを区別する方法を示しています。

||パラメーターが必要です|パラメーターは省略可能です|
|-|-----------------------------|-----------------------------|
|**呼び出された関数への入力**|`_In_`|`_In_opt_`|
|**呼び出された関数への入力と、呼び出し元への出力**|`_Inout_`|`_Inout_opt_`|
|**呼び出し元への出力**|`_Out_`|`_Out_opt_`|
|**呼び出し元へのポインターの出力**|`_Outptr_`|`_Outptr_opt_`|

これらの注釈は、初期化されていない値を識別するのに役立ちます。また、正しくない正しい方法で null ポインターを使用することもできます。 必須のパラメーターに NULL を渡すとクラッシュが発生する可能性があります。エラーコード "failed" が返される可能性があります。 どちらの場合も、関数はジョブの実行を成功できません。

## <a name="sal-examples"></a>SAL の例
ここでは、基本的な SAL 注釈のコード例を示します。

### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Visual Studio Code 分析ツールを使用して問題を検出する
この例では、Visual Studio Code 分析ツールを SAL 注釈と共に使用して、コードの欠陥を検出します。 その方法を次に示します。

#### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Visual Studio のコード分析ツールと SAL を使用するには

1. Visual Studio で、SAL 注釈C++を含むプロジェクトを開きます。

2. メニューバーで、 **[ビルド]** 、 **[ソリューションでコード分析を実行]** の順に選択します。

     このセクション\_の\_例については、「」を参照してください。 コード分析を実行すると、次の警告が表示されます。

    > **C6387 無効なパラメーター値**' ポイント ' は ' 0 ' である可能性があります。これは、関数 ' InCallee 側 ' の仕様に準拠していません。

### <a name="example-the-_in_-annotation"></a>例:注釈\_内\_の。

注釈`_In_`は、次のことを示します。

- パラメーターは有効である必要があり、変更されません。

- 関数は、単一要素のバッファーからのみを読み取ります。

- 呼び出し元は、バッファーを提供して初期化する必要があります。

- `_In_`"読み取り専用" を指定します。 一般的な誤りは、代わりに`_In_` `_Inout_`注釈を持つ必要があるパラメーターにを適用することです。

- `_In_`は許可されますが、非ポインタースカラーのアナライザーによって無視されます。

```cpp
void InCallee(_In_ int *pInt)
{
   int i = *pInt;
}

void GoodInCaller()
{
   int *pInt = new int;
   *pInt = 5;

   InCallee(pInt);
   delete pInt;
}

void BadInCaller()
{
   int *pInt = NULL;
   InCallee(pInt); // pInt should not be NULL
}
```

この例で Visual Studio Code 分析を使用する場合は、呼び出し元が Null 以外のポインターを用に`pInt`初期化されたバッファーに渡すことを検証します。 この場合、ポインター `pInt`を NULL にすることはできません。

### <a name="example-the-_in_opt_-annotation"></a>例:\_Opt\_注釈の\_

`_In_opt_`はと`_In_`同じですが、入力パラメーターを NULL にすることが許可されている点が異なります。そのため、関数はこのことを確認する必要があります。

```cpp

void GoodInOptCallee(_In_opt_ int *pInt)
{
   if(pInt != NULL) {
      int i = *pInt;
   }
}

void BadInOptCallee(_In_opt_ int *pInt)
{
   int i = *pInt; // Dereferencing NULL pointer 'pInt'
}

void InOptCaller()
{
   int *pInt = NULL;
   GoodInOptCallee(pInt);
   BadInOptCallee(pInt);
}
```

Visual Studio Code の分析では、関数がバッファーにアクセスする前に NULL をチェックするかどうかを検証します。

### <a name="example-the-_out_-annotation"></a>例:\_Out注釈\_

`_Out_`は、要素バッファーを指す NULL 以外のポインターが渡され、関数が要素を初期化する一般的なシナリオをサポートします。 呼び出しの前に、呼び出し元がバッファーを初期化する必要はありません。呼び出された関数は、を返す前に、それを初期化することを約束します。

```cpp
void GoodOutCallee(_Out_ int *pInt)
{
   *pInt = 5;
}

void BadOutCallee(_Out_ int *pInt)
{
   // Did not initialize pInt buffer before returning!
}

void OutCaller()
{
   int *pInt = new int;
   GoodOutCallee(pInt);
   BadOutCallee(pInt);
   delete pInt;
}
```

Visual Studio Code 分析ツールは、呼び出し元が NULL 以外の`pInt`ポインターをバッファーに渡すこと、およびバッファーが返される前に関数によって初期化されることを検証します。

### <a name="example-the-_out_opt_-annotation"></a>例:\_Out\_opt注釈\_

`_Out_opt_`はと`_Out_`同じですが、パラメーターを NULL にすることもできます。したがって、関数はこの点を確認する必要があります。

```cpp
void GoodOutOptCallee(_Out_opt_ int *pInt)
{
   if (pInt != NULL) {
      *pInt = 5;
   }
}

void BadOutOptCallee(_Out_opt_ int *pInt)
{
   *pInt = 5; // Dereferencing NULL pointer 'pInt'
}

void OutOptCaller()
{
   int *pInt = NULL;
   GoodOutOptCallee(pInt);
   BadOutOptCallee(pInt);
}
```

Visual Studio Code の分析では、が逆参照さ`pInt`れる前に、この`pInt`関数が null をチェックし、が null でない場合、バッファーが返される前に関数によって初期化されることを検証します。

### <a name="example-the-_inout_-annotation"></a>例:\_Inout注釈\_

`_Inout_`は、関数によって変更される可能性があるポインターパラメーターに注釈を付けるために使用されます。 ポインターは、呼び出しの前に有効な初期化済みデータをポイントする必要があります。また、ポインターが変更された場合でも、戻り値が有効である必要があります。 注釈は、関数が1つの要素のバッファーから自由に読み取りおよび書き込みを行うことができることを指定します。 呼び出し元は、バッファーを提供して初期化する必要があります。

> [!NOTE]
> と`_Out_`同様`_Inout_`に、は変更可能な値に適用する必要があります。

```cpp
void InOutCallee(_Inout_ int *pInt)
{
   int i = *pInt;
   *pInt = 6;
}

void InOutCaller()
{
   int *pInt = new int;
   *pInt = 5;
   InOutCallee(pInt);
   delete pInt;
}

void BadInOutCaller()
{
   int *pInt = NULL;
   InOutCallee(pInt); // 'pInt' should not be NULL
}
```

Visual Studio Code の分析で`pInt` `pInt`は、呼び出し元が null 以外のポインターを用に初期化されたバッファーに渡すこと、およびが戻る前にが null ではなく、バッファーが初期化されることを検証します。

### <a name="example-the-_inout_opt_-annotation"></a>例:\_Inout\_opt注釈\_

`_Inout_opt_`はと`_Inout_`同じですが、入力パラメーターを NULL にすることが許可されている点が異なります。そのため、関数はこのことを確認する必要があります。

```cpp
void GoodInOutOptCallee(_Inout_opt_ int *pInt)
{
   if(pInt != NULL) {
      int i = *pInt;
      *pInt = 6;
   }
}

void BadInOutOptCallee(_Inout_opt_ int *pInt)
{
   int i = *pInt; // Dereferencing NULL pointer 'pInt'
   *pInt = 6;
}

void InOutOptCaller()
{
   int *pInt = NULL;
   GoodInOutOptCallee(pInt);
   BadInOutOptCallee(pInt);
}
```

Visual Studio Code 分析では、この関数がバッファーにアクセスする前に null をチェック`pInt`するかどうかを検証し、が null でない場合は、バッファーが返される前に関数によって初期化されることを検証します。

### <a name="example-the-_outptr_-annotation"></a>例:Outptr\_注釈\_

`_Outptr_`は、ポインターを返すことを目的としたパラメーターに注釈を付けるために使用されます。  パラメーター自体を NULL にすることはできません。呼び出された関数は NULL 以外のポインターを返し、そのポインターは初期化されたデータを指します。

```cpp
void GoodOutPtrCallee(_Outptr_ int **pInt)
{
   int *pInt2 = new int;
   *pInt2 = 5;

   *pInt = pInt2;
}

void BadOutPtrCallee(_Outptr_ int **pInt)
{
   int *pInt2 = new int;
   // Did not initialize pInt buffer before returning!
   *pInt = pInt2;
}

void OutPtrCaller()
{
   int *pInt = NULL;
   GoodOutPtrCallee(&pInt);
   BadOutPtrCallee(&pInt);
}
```

Visual Studio Code の分析では、呼び出し元がの`*pInt`NULL でないポインターを渡し、バッファーが返される前に関数によって初期化されることを検証します。

### <a name="example-the-_outptr_opt_-annotation"></a>例:Outptr\_opt\_注釈\_

`_Outptr_opt_`はと`_Outptr_`同じですが、パラメーターが省略可能である点が異なります。呼び出し元は、パラメーターの NULL ポインターを渡すことができます。

```cpp
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)
{
   int *pInt2 = new int;
   *pInt2 = 6;

   if(pInt != NULL) {
      *pInt = pInt2;
   }
}

void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)
{
   int *pInt2 = new int;
   *pInt2 = 6;
   *pInt = pInt2; // Dereferencing NULL pointer 'pInt'
}

void OutPtrOptCaller()
{
   int **ppInt = NULL;
   GoodOutPtrOptCallee(ppInt);
   BadOutPtrOptCallee(ppInt);
}
```

Visual Studio Code 分析では、が逆参照される`*pInt`前にこの関数が NULL をチェックすること、およびバッファーが返される前に関数によって初期化されることを検証します。

### <a name="example-the-_success_-annotation-in-combination-with-_out_"></a>例:\_Success注釈\_ と\_Out の組み合わせ\_

注釈は、ほとんどのオブジェクトに適用できます。  特に、関数全体に注釈を付けることができます。  関数の最も明白な特性の1つは、成功または失敗することです。 ただし、バッファーとそのサイズの間の関連付けと同様にC++ 、C/は関数の成功または失敗を表すことができません。 `_Success_`注釈を使用すると、関数の成功がどのようになるかを示すことができます。  注釈の`_Success_`パラメーターは、その関数が成功したことを示す式にすぎません。 式は、注釈パーサーが処理できる任意のものにすることができます。 関数が返された後の注釈の効果は、関数が成功した場合にのみ適用されます。 この例では`_Success_` 、が`_Out_`適切な処理を行うために、とを相互作用させる方法を示します。 キーワード`return`を使用して、戻り値を表すことができます。

```cpp
_Success_(return != false) // Can also be stated as _Success_(return)
bool GetValue(_Out_ int *pInt, bool flag)
{
   if(flag) {
      *pInt = 5;
      return true;
   } else {
      return false;
   }
}
```

注釈によって Visual Studio Code 分析によって、呼び出し元が NULL 以外のポインターをの`pInt`バッファーに渡すこと、およびバッファーが返される前に関数によって初期化されることが検証されます。 `_Out_`

## <a name="sal-best-practice"></a>SAL のベスト プラクティス

### <a name="adding-annotations-to-existing-code"></a>既存のコードに注釈を追加する

SAL は、コードのセキュリティと信頼性を向上させるのに役立つ強力なテクノロジです。 SAL について学習した後は、毎日の作業に新しいスキルを適用できます。 新しいコードでは、SAL ベースの仕様を使用して設計を行うことができます。以前のコードでは、注釈を段階的に追加して、更新するたびに利点を向上させることができます。

Microsoft パブリックヘッダーには既に注釈が付けられています。 したがって、プロジェクトでは、最初に Win32 Api を呼び出すリーフノードの関数と関数に注釈を付けて、最大限の効果を得ることをお勧めします。

### <a name="when-do-i-annotate"></a>注釈を付けるタイミング

いくつかのガイドラインを次に示します。

- すべてのポインターパラメーターに注釈を付けます。

- コード分析でバッファーとポインターの安全性を確保できるように、値範囲注釈に注釈を付けます。

- ロック規則に注釈を付け、副作用をロックします。 詳細については、「[ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)」を参照してください。

- ドライバーのプロパティおよびその他のドメイン固有のプロパティに注釈を設定します。

または、すべてのパラメーターに注釈を付けて、目的を明確にし、注釈が完了したことを簡単に確認できるようにすることもできます。

## <a name="related-resources"></a>関連資料

[コード分析チームのブログ](http://go.microsoft.com/fwlink/p/?LinkId=251197)

## <a name="see-also"></a>関連項目

- [SAL 注釈を使って C/C++ のコード障害を減らす方法](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)
- [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)
- [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)
- [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)
- [注釈を適用するタイミングと場所の指定](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)