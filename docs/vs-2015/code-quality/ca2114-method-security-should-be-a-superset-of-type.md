---
title: CA2114:メソッドのセキュリティの種類のスーパー セットである必要があります |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b1a360ee4ad35fd48a46f6d866912a05a584a54c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687313"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114:メソッド セキュリティは型のスーパーセットでなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型が宣言型のセキュリティと、同じセキュリティ アクションに対して宣言型セキュリティをそのメソッドのいずれかが、セキュリティ アクションが[リンク確認要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)または[継承確認要求](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)、およびアクセス許可チェックの種類によっては、メソッドによってチェックする権限のサブセットではありません。

## <a name="rule-description"></a>規則の説明
 メソッドは、両方の同じアクション メソッド レベルと型レベルの宣言セキュリティは必要ありません。 2 つのチェックが組み合わされていません。メソッド レベルの要求のみが適用されます。 型のアクセス許可を要求する場合など、 `X`、アクセス許可を要求のメソッドのいずれかと`Y`、コードにアクセス許可がない`X`メソッドを実行します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 両方のアクションが必要であるかどうかを確認するコードを確認します。 両方のアクションが必要な場合は、メソッド レベルのアクションがタイプ レベルで指定されたセキュリティが含まれることを確認します。 種類のアクセス許可を要求する場合など、 `X`、し、そのメソッドは、アクセス許可を要求する必要がありますも`Y`、メソッドが明示的に要求する必要があります`X`と`Y`します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 メソッドは、型で指定されたセキュリティを必要としない場合、この規則による警告を抑制するのには安全です。 ただし、これは通常のシナリオではありません、慎重に設計レビューの必要性を示す可能性があります。

## <a name="example"></a>例
 次の例では、環境のアクセス許可を使用して、この規則に違反する危険性を示します。 この例では、アプリケーション コードは、型に必要な権限を拒否する前にセキュリティで保護された型のインスタンスを作成します。 実際の脅威のシナリオでは、オブジェクトのインスタンスを取得することもできます必要があります。

 次の例では、ライブラリの需要は一種の書き込みアクセス許可と、メソッドに対する読み取りアクセス許可。

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>例
 次のアプリケーション コードでは、型レベルのセキュリティ要件を満たしていない場合でも、メソッドを呼び出すことによって、ライブラリの脆弱性を示します。

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **[すべてのアクセス許可]個人情報:6/16/1964 12時 00分: 00 AM**
 **[書き込み権限 (種類別の要求)] の個人情報。6/16/1964 12時 00分: 00 AM**
 **[読み取り権限 (メソッドによって要求される)] では、個人情報はアクセスできませんでした。要求に失敗しました。**
## <a name="see-also"></a>関連項目
 [安全なコーディングのガイドライン](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[継承確認要求](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)[リンク確認要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[データとモデリング](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
