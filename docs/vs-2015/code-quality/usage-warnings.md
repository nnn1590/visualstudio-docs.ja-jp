---
title: 使用状況の警告 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 679c12eb99e3cad7486384999a2393e09dbd277f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142111"
---
# <a name="usage-warnings"></a>使用法に関する警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用状況の警告は、.NET Framework の適切な使用をサポートします。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|ルール|説明|  
|----------|-----------------|  
|[CA 1801:未使用のパラメーターをレビューします](../code-quality/ca1801-review-unused-parameters.md)|メソッドのシグネチャに、メソッドの本体で使用されていないパラメーターがあります。|  
|[CA 1806:メソッドの結果を無視しません。](../code-quality/ca1806-do-not-ignore-method-results.md)|新しく作成されたオブジェクトが現在まで使用されていないか、新しい文字列を作成して返すメソッドが呼び出されて作成された新しい文字列が現在まで使用されていません。あるいは、COM または P/Invoke メソッドから返された HRESULT またはエラー コードが現在まで使用されていません。|  
|[CA 1816:GC を呼び出します。SuppressFinalize 正しく](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Dispose の実装であるメソッドでは、GC は呼び出されません。SuppressFinalize;または、Dispose の実装ではないメソッドは、GC を呼び出します。SuppressFinalize;または、GC のメソッド呼び出し。SuppressFinalize およびこの (Visual Basic で Me) 以外は何かのパス。|  
|[CA 2200:スタックの詳細を保持するために再スローします。](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|例外が再スローされ、例外が throw ステートメントで明示的に指定します。 例外が throw ステートメントで例外を指定して再スローされた場合、例外をスローした元のメソッドと、現在のメソッド間のメソッド呼び出しの一覧は失われます。|  
|[CA 2201:予約された例外の種類を発生させません](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|これにより、元のエラーが検出およびデバッグが困難にします。|  
|[CA 2202:オブジェクトを複数回破棄しません](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|メソッドの実装に、同じオブジェクトに対して System.IDisposable.Dispose または Dispose と同等の操作 (たとえば、一部の型に対する Close() メソッドなど) を複数回呼び出すコード パスが含まれています。|  
|[CA2204:リテラルは正しく入力されなければなりません](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|メソッド本体に含まれるリテラル文字列内に Microsoft スペル チェック ライブラリで認識されない語が 1 つ以上あります。|  
|[CA2205:Win32 API に相当するマネージドの使用します。](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|プラットフォーム呼び出しメソッドが定義されているし、.NET Framework クラス ライブラリで同等の機能を持つメソッドが存在します。|  
|[CA 2207:値型の静的フィールドのインラインを初期化します](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|値型で明示的な静的コンストラクターを宣言しています。 この規則違反を修正するには、静的データが宣言されたとき、および静的コンストラクターを削除するときに、静的データをすべて初期化します。|  
|[CA2208:引数の例外を正しくインスタンス化します。](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|ArgumentException またはそのクラスから派生した例外の種類の既定 (パラメーターなし) のコンストラクターに対して呼び出しが行われたか、ArgumentException またはそのクラスから派生した例外の種類のパラメーター付きのコンストラクターに不適切な文字列型の引数が渡されました。|  
|[CA 2211:非定数フィールドを表示することはできません。](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|定数でも読み取り専用でもない静的フィールドは、スレッド セーフではありません。 このようなフィールドへのアクセスは、慎重に管理する必要があり、クラス オブジェクトへのアクセスを同期するための高度なプログラミング手法を必要とします。|  
|[CA2212:サービス コンポーネントを webmethod に設定をマークしないでください。](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|System.EnterpriseServices.ServicedComponent から継承する型のメソッドは、System.Web.Services.WebMethodAttribute でマークされます。 WebMethodAttribute と ServicedComponent メソッドは、コンテキストおよびトランザクション フローの動作および要件が衝突するため、状況によっては正常に動作しません。|  
|[CA2213: 破棄可能なフィールドは破棄されなければなりません](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|System.IDisposable を実装する型が、IDisposable も実装する型を持つフィールドを宣言しています。 このフィールドの Dispose メソッドは、宣言している型の Dispose メソッドから呼び出されていません。|  
|[CA 2214:コンス トラクターのオーバーライド可能なメソッドを呼び出しません](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|コンス トラクターは、仮想メソッドを呼び出し、メソッドを呼び出すインスタンスのコンス トラクターが実行しないことになります。|  
|[CA2215:Dispose メソッドが基底クラス dispose を呼び出す必要があります。](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|型が、破棄できる型から継承している場合、使用している Dispose メソッド内から基本型の Dispose メソッドを呼び出す必要があります。|  
|[CA 2216:破棄可能な型はファイナライザーを宣言する必要があります。](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Object.Finalize での説明に従って、アンマネージ リソースの使用を提案するフィールドであり、System.IDisposable を実装する型はファイナライザーを実装しません。|  
|[CA2217:FlagsAttribute で列挙をマークしないでください。](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|外部から参照できる列挙体が、FlagsAttribute でマークされたあり、2、または列挙型で定義されている他の値の組み合わせの累乗でない 1 つまたは複数の値。|  
|[CA2218:Equals をオーバーライドの GetHashCode をオーバーライドします。](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|GetHashCode は、現在のインスタンスに基づいて、ハッシュ アルゴリズムとデータ構造 (ハッシュ テーブルなど) に適した値を返します。 同じ型で等値の 2 つのオブジェクトによって同じハッシュ コードが返される必要があります。|  
|[CA2219:Exception 句に例外を発生させません](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|finally 句または fault 句で例外が発生すると、アクティブな例外が新しい例外によって隠されます。 filter 句で例外が発生すると、ランタイムがその例外を暗黙的にキャッチします。 これにより、元のエラーが検出およびデバッグが困難にします。|  
|[CA 2220:ファイナライザーは基本クラスのファイナライザーを呼び出す必要があります。](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|終了処理は、継承の階層構造を使用して反映する必要があります。 これを確実に行うには、型が型の Finalize メソッドで基本クラスの Finalize メソッドを呼び出す必要があります。|  
|[CA 2221:ファイナライザーは保護する必要があります。](../code-quality/ca2221-finalizers-should-be-protected.md)|ファイナライザーは、ファミリ アクセス修飾子を使用する必要があります。|  
|[CA 2222:継承されたメンバーの可視性を縮小しません](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|継承メンバーのアクセス修飾子は変更しないでください。 継承メンバーをプライベートに変更しても、呼び出し元はメソッドの基本クラスの実装にアクセスできます。|  
|[CA2223:メンバーが複数の戻り値の型が異なる必要があります。](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|共通言語ランタイムでは、戻り値の型以外は同じであるメンバーの区別に戻り値の型を使用することが許可されていますが、この機能は共通言語仕様ではなく、.NET プログラミング言語の共通機能でもありません。|  
|[CA2224:オーバー ロードする演算子 equals で equals をオーバーライド](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|パブリック型は、等値演算子の実装が、Object.Equals をオーバーライドしません。|  
|[CA2225:演算子のオーバー ロード名前付けされた代替](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|演算子のオーバーロードが検出され、予想される名前の代替メソッドが検出されませんでした。 名前付きの代替メンバーは、演算子と同じ機能にアクセスできるようにおり、オーバー ロードされた演算子をサポートしない言語でプログラミングする開発者向け提供されます。|  
|[CA2226:演算子は対称型オーバー ロードである必要があります。](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|型は、等値演算子または非等値演算子の場合を実装し、反対側の演算子を実装していません。|  
|[CA2227:コレクションのプロパティは読み取り専用にします。](../code-quality/ca2227-collection-properties-should-be-read-only.md)|書き込み可能なコレクション プロパティにより、ユーザーはコレクションを異なるコレクションで置換できます。 読み取り専用プロパティは、コレクションを置換できないようにしますが、個別のメンバーが設定されることは回避できません。|  
|[CA 2228:未公開のリソース形式を出荷しません](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|.NET Framework のプレリリース バージョンを使用してビルドされたリソース ファイルは、サポートされているバージョンの .NET Framework で使用できるしない場合があります。|  
|[CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)|この規則違反を修正するには、シリアル化コンストラクターを実装します。 シールされたクラスの場合、コンストラクターをプライベートにするか、プロテクトにします。|  
|[CA2230:可変個の引数に対して param を使用します。](../code-quality/ca2230-use-params-for-variable-arguments.md)|パブリック型またはプロテクト型に、params キーワードではなく VarArgs 呼び出し規則を使用するパブリック メソッドまたはプロテクト メソッドが含まれています。|  
|[CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|値型は、Object.Equals をオーバーライドしていますが、等値演算子を実装していません。|  
|[CA 2232:Mark の Windows フォームのエントリ ポイントを stathread に設定します](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|STAThreadAttribute は、アプリケーションの COM スレッド処理モデルがシングルスレッド アパートメントであることを示します。 この属性は、Windows フォームを使用するすべてのアプリケーションのエントリ ポイントに指定する必要があります。省略すると、Windows コンポーネントが正常に機能しないことがあります。|  
|[CA 2233:操作はオーバーフローできません。](../code-quality/ca2233-operations-should-not-overflow.md)|最初に関連するデータ型に指定できる値の範囲外操作の結果がないことを確認する、オペランドを検証せず、算術演算を実行できません必要があります。|  
|[CA 2234:文字列の代わりに System.Uri オブジェクトを渡します](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|"uri"、"URI"、"urn"、"URN"、"url"、または "URL" という名前を持つ文字列パラメーターが指定されているメソッドに対して、呼び出しが行われました。  そのメソッドの型宣言に対応するメソッドのオーバーロードが存在し、それに対して System.Uri パラメーターが指定されています。|  
|[CA2235:すべてのシリアル化不可能なフィールドを設定します](../code-quality/ca2235-mark-all-non-serializable-fields.md)|シリアル化できない型のインスタンス フィールドが、シリアル化できる型で宣言されています。|  
|[CA 2236:ISerializable 型の基本クラス メソッドを呼び出す](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|この規則違反を修正するには、基本型の GetObjectData メソッドまたはシリアル化コンストラクターを、対応する派生型のメソッドまたはコンストラクターから呼び出します。|  
|[CA2237:ISerializable 型を serializableattribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|シリアル化可能として共通言語ランタイムによって認識されるは、型が ISerializable インターフェイスの実装を通じてカスタムのシリアル化ルーチンを使用する場合でもに型 SerializableAttribute 属性でマークする必要があります。|  
|[CA 2238:シリアル化メソッドを正しく実装します。](../code-quality/ca2238-implement-serialization-methods-correctly.md)|シリアル化イベントを処理するメソッドに、適切なシグネチャ、戻り値の型、または参照範囲がありません。|  
|[CA2239:オプションのフィールドに逆シリアル化メソッドを提供します。](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|型には、System.Runtime.Serialization.OptionalFieldAttribute 属性でマークされているフィールドがあり、型が逆シリアル化イベント処理メソッドを提供していません。|  
|[CA2240:ISerializable を正しく実装します。](../code-quality/ca2240-implement-iserializable-correctly.md)|このルールの違反を修正するには、GetObjectData メソッドをオーバーライドできるようにし、すべてのインスタンス フィールドをシリアル化プロセスに含まれるまたは NonSerializedAttribute 属性で明示的にマークするかどうかを確認します。|  
|[CA2241:書式指定メソッドに正しい引数を指定します。](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|System.String.Format に渡される書式引数には、各オブジェクトの引数、またはその逆に対応する書式指定項目がありません。|  
|[CA2242:NaN に対して正しくテストします](../code-quality/ca2242-test-for-nan-correctly.md)|この式が Single.Nan または Double.Nan に対して値をテストしています。 値をテストするには、Single.IsNan(Single) または Double.IsNan(Double) を使用します。|  
|[CA 2243:属性文字列リテラルは、正しく解析する必要があります。](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|属性の文字列リテラル パラメーターは、URL、GUID、またはバージョンを正しく解析できません。|
