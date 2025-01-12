---
title: FxCop アナライザーの構成オプション
ms.date: 03/11/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3c7050cbb80b1b79009a23a2d9bfedc40204fede
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816715"
---
# <a name="configuration-options-for-fxcop-analyzers"></a>FxCop アナライザーの構成オプション

このページには、使用可能な構成オプション、使用可能な値、および各オプションの構成可能なルールが一覧表示されます。

## <a name="apisurface"></a>api_surface

| 説明 | 使用できる値 | 既定値 | 構成可能なルール |
| - | - | - | - |
| 分析する API サーフェイスのどの部分 | `public`<br/>`internal` または `friend`<br/>`private`<br/>`all`<br/><br/>複数の値をコンマ (,) で区切ります | `public` | [CA1000](ca1000-do-not-declare-static-members-on-generic-types.md)<br/>[CA 1003](ca1003-use-generic-event-handler-instances.md)<br/>[CA1008](ca1008-enums-should-have-zero-value.md)<br/>[CA 1010](ca1010-collections-should-implement-generic-interface.md)<br/>[CA 1012](ca1012-abstract-types-should-not-have-constructors.md)<br/>[CA 1024](ca1024-use-properties-where-appropriate.md)<br/>[CA1027](ca1027-mark-enums-with-flagsattribute.md)<br/>[CA1028](ca1028-enum-storage-should-be-int32.md)<br/>[CA1030](ca1030-use-events-where-appropriate.md)<br/>[CA1036](ca1036-override-methods-on-comparable-types.md)<br/>[CA1040](ca1040-avoid-empty-interfaces.md)<br/>[CA1041](ca1041-provide-obsoleteattribute-message.md)<br/>[CA 1043](ca1043-use-integral-or-string-argument-for-indexers.md)<br/>[CA 1044](ca1044-properties-should-not-be-write-only.md)<br/>[CA 1051](ca1051-do-not-declare-visible-instance-fields.md)<br/>[CA1052](ca1052-static-holder-types-should-be-sealed.md)<br/>[CA1054](ca1054-uri-parameters-should-not-be-strings.md)<br/>[CA 1055](ca1055-uri-return-values-should-not-be-strings.md)<br/>[CA 1056](ca1056-uri-properties-should-not-be-strings.md)<br/>[CA1058](ca1058-types-should-not-extend-certain-base-types.md)<br/>[CA1063](ca1063-implement-idisposable-correctly.md)<br/>[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md)<br/>[CA1710](ca1710-identifiers-should-have-correct-suffix.md)<br/>[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md)<br/>[CA1714](ca1714-flags-enums-should-have-plural-names.md)<br/>[CA1715](ca1715-identifiers-should-have-correct-prefix.md)<br/>[CA1716](ca1716-identifiers-should-not-match-keywords.md)<br/>[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md)<br/>[CA 1720](ca1720-identifiers-should-not-contain-type-names.md)<br/>[CA1721](ca1721-property-names-should-not-match-get-methods.md)<br/>[CA1725](ca1725-parameter-names-should-match-base-declaration.md)<br/>[CA 1802](ca1802-use-literals-where-appropriate.md)<br/>[CA1815](ca1815-override-equals-and-operator-equals-on-value-types.md)<br/>[CA 1819](ca1819-properties-should-not-return-arrays.md)<br/>[CA2217](ca2217-do-not-mark-enums-with-flagsattribute.md)<br/>[CA2225](ca2225-operator-overloads-have-named-alternates.md)<br/>[CA2226](ca2226-operators-should-have-symmetrical-overloads.md)<br/>[CA2231](ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)<br/>[CA2234](ca2234-pass-system-uri-objects-instead-of-strings.md) |

## <a name="excludeasyncvoidmethods"></a>exclude_async_void_methods

| 説明 | 使用できる値 | 既定値 | 構成可能なルール |
| - | - | - | - |
| 値を返さない非同期メソッドを無視するかどうか | `true`<br/>`false` | `false` | [CA2007](ca2007-do-not-directly-await-task.md) |

> [!NOTE]
> このオプションの名前が 2.6.3 のバージョンでと、以前のアナライザー パッケージ`skip_async_void_methods`します。

## <a name="excludesinglelettertypeparameters"></a>exclude_single_letter_type_parameters

| 説明 | 使用できる値 | 既定値 | 構成可能なルール |
| - | - | - | - |
| 単一の文字を除外するかどうか[パラメーター入力](/dotnet/csharp/programming-guide/generics/generic-type-parameters)、ルールから`S`で `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715-identifiers-should-have-correct-prefix.md) |

> [!NOTE]
> このオプションの名前が 2.6.3 のバージョンでと、以前のアナライザー パッケージ`allow_single_letter_type_parameters`します。

## <a name="outputkind"></a>output_kind

| 説明 | 使用できる値 | 既定値 | 構成可能なルール |
| - | - | - | - |
| この種類のアセンブリを生成するプロジェクトでコードを分析することを指定します。 | 1 つまたは複数のフィールド、<xref:Microsoft.CodeAnalysis.OutputKind>列挙型<br/><br/>複数の値をコンマ (,) で区切ります | すべての出力の種類 | [CA2007](ca2007-do-not-directly-await-task.md) |