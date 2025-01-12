---
title: 組み込み関数
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 65a5272d74e1987cd7838932182e7e59c9c53f21
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923949"
---
# <a name="intrinsic-functions"></a>組み込み関数
SAL 内の式は、C/C++式にすることができます。これは、副作用のない式であることを示します。たとえば、+ +、--,、関数の呼び出しすべてにこのコンテキストでの副作用があります。  ただし、SAL には、関数に似たオブジェクトや、SAL 式で使用できる予約済みのシンボルがいくつか用意されています。 これらは*組み込み関数*と呼ばれます。

## <a name="general-purpose"></a>General Purpose
次のているか関数注釈は、SAL の一般的なユーティリティを提供します。

|注釈|説明|
|----------------|-----------------|
|`_Curr_`|現在注釈が付けられているオブジェクトのシノニム。  注釈が使用され`_At_`ている`_Curr_`場合、はの最初のパラメーターと同じです。 `_At_`  それ以外の場合は、パラメーター、または注釈が構文的に関連付けられている関数/戻り値全体を指定します。|
|`_Inexpressible_(expr)`|入力データセットをスキャンして選択したメンバーをカウントすることによって計算された場合など、注釈式を使用して、バッファーのサイズが複雑すぎて表すことができない状況を表します。|
|`_Nullterm_length_(param)`|`param`はバッファー内の要素の数ですが、null 終端文字は含まれません。 非集計の非 void 型の任意のバッファーに適用できます。|
|`_Old_(expr)`|前提条件で評価された`_Old_`場合、は入力`expr`値を返します。  事後条件で評価されると、前提条件で評価さ`expr`れた値が返されます。|
|`_Param_(n)`|関数に対する`n` `n` th パラメーター。1からまでをカウントし、はリテラル整数定数です。 `n` パラメーターにという名前が付けられている場合、この注釈は名前によってパラメーターにアクセスするのと同じです。 **注:** `n`は、省略記号で定義された位置指定パラメーターを参照することも、名前が使用されない関数プロトタイプで使用することもできます。|
|`return`|関数の戻りC++値を`return`示すために、SAL 式で C/予約キーワードを使用できます。  この値は post 状態でのみ使用できます。これは、事前状態で使用するための構文エラーです。|

## <a name="string-specific"></a>文字列固有
次の組み込み関数注釈を使用すると、文字列を操作できます。 これらの4つの関数は、null 終端文字の前に見つかった型の要素の数を返すために、同じ目的を果たします。 違いは、参照される要素のデータの種類です。 文字で構成されていない null で終わるバッファーの長さを指定する場合は、前のセクションの`_Nullterm_length_(param)`注釈を使用します。

|注釈|説明|
|----------------|-----------------|
|`_String_length_(param)`|`param`文字列内の要素の数を指定します。 null 終端文字は含まれません。 この注釈は、文字型の文字列用に予約されています。|
|`strlen(param)`|`param`文字列内の要素の数を指定します。 null 終端文字は含まれません。 この注釈は、文字配列で使用するために予約されており、C ランタイム関数[strlen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)に似ています。|
|`wcslen(param)`|`param`は、null 終端文字までの文字列内の要素の数です (ただし、は含まれません)。 この注釈は、ワイド文字配列で使用するために予約されており、C ランタイム関数[wcslen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)に似ています。|

## <a name="see-also"></a>関連項目

- [SAL 注釈を使って C/C++ のコード障害を減らす方法](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [SAL について](../code-quality/understanding-sal.md)
- [関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)
- [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)
- [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)
- [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)
- [注釈を適用するタイミングと場所の指定](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)