---
title: 予想される 16 進数の数字 |Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82f020b5f3b82ab2ce3545102be83a5cd41c6069
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446524"
---
# <a name="expected-hexadecimal-digit"></a>16 進数の数字が必要です。
正しくない Unicode エスケープ シーケンスを作成したとします。 (これ以上を指して) 厳密に 4 つの 16 進数字が続く \u の付いた Unicode エスケープ シーケンスを開始します。 Unicode 16 進数の数字は、0 ~ 9 の数字のみ、大文字 A ~ F、および、小文字アルファベット a ~ f を含めることができます。 次の例では、正しい形式の Unicode エスケープ シーケンスを示します。  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- Unicode 16 進数、\u の付いた開始され、0 ~ 9、A ~ F、小文字アルファベット a ~ f です。 大文字の文字の数値のみを格納してください。4 桁の数字をグループ化されています。  
  
    > [!NOTE]
    > リテラル テキスト \u を使用して文字列に円記号を 2 を使用する場合 (\\\u)-最初の円記号をエスケープする 1 つ。  
  
## <a name="see-also"></a>関連項目  
 [データの種類](../../javascript/data-types-javascript.md)