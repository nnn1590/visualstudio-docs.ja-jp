---
title: LINQ to XML の動的プロパティ
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 181e9e4fb86a0348c0b5adb1d26a0a4e4e1721bb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62893212"
---
# <a name="linq-to-xml-dynamic-properties"></a>LINQ to XML の動的プロパティ

ここでは、LINQ to XML の動的プロパティに関する参照情報について説明します。 これらのプロパティは、具体的には <xref:System.Xml.Linq.XAttribute> 名前空間の <xref:System.Xml.Linq.XElement> クラスと <xref:System.Xml.Linq> クラスによって公開されます。

「[LINQ to XML による WPF のデータ バインディングの概要](../designers/wpf-data-binding-with-linq-to-xml-overview.md)」のトピックで説明されているように、各動的プロパティには、対応する標準のパブリック プロパティやパブリック メソッドが同じクラスにあります。 ほとんどの用途では、これらの標準のメンバーを使用する必要があります。動的プロパティは、LINQ to XML のデータ バインドのシナリオ専用に用意されています。 これらのクラスの標準のメンバーに関する詳細については、リファレンス トピックの「<xref:System.Xml.Linq.XAttribute>」および「<xref:System.Xml.Linq.XElement>」を参照してください。

このセクションの動的プロパティは、解決される値に関連して次の 2 つのカテゴリに分類されます。

- 1 つの値に解決される単純なプロパティ (`Value` クラスや <xref:System.Xml.Linq.XAttribute> クラスの <xref:System.Xml.Linq.XElement> プロパティなど)。

- インデクサー型に解決されるインデックス値 (<xref:System.Xml.Linq.XElement> の [Elements](../designers/elements-xelement-dynamic-property.md) プロパティや [Descendants](../designers/descendants-xelement-dynamic-property.md) プロパティなど)。 インデクサー型が目的の値やコレクションに解決されるようにするには、拡張名のパラメーターを渡す必要があります。

<xref:System.Collections.Generic.IEnumerable%601> 型のインデックス値を返す動的プロパティはすべて遅延実行を使用します。 遅延実行について詳しくは、「[LINQ クエリの概要 (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)」をご覧ください。

## <a name="reference"></a>関連項目

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>関連項目

- [LINQ to XML による WPF のデータ バインディング](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [LINQ to XML による WPF のデータ バインディングの概要](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [LINQ クエリの概要 (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
