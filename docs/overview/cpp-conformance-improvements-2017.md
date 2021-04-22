---
title: Visual Studio 2017 の C++ 準拠の強化
description: Visual Studio 2017 の Microsoft C/C++ は、C++20 言語標準との完全準拠に向かって進んでいます。
ms.date: 04/18/2021
ms.technology: cpp-language
ms.openlocfilehash: 6c23b4a1e85253fa304ff4b962958f80523a3416
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721798"
---
# <a name="c-conformance-improvements-behavior-changes-and-bug-fixes-in-visual-studio-2017"></a>Visual Studio 2017 での C++ 準拠の強化、動作変更、バグ修正

Visual Studio の Microsoft C/C++ (MSVC) では、リリースごとに準拠の強化とバグ修正が行われます。 この記事では、機能強化をメジャー リリースごと、バージョンごとに一覧で紹介します。 特定のバージョンで行われた変更に直接移動するには、**この記事内** の一覧を使用します。

このドキュメントには、Visual Studio 2017 での変更点が記載されています。 Visual Studio 2019 での変更点のガイドについては、[Visual Studio 2019 での C++ 準拠の強化](cpp-conformance-improvements.md)に関する記事を参照してください。 以前に行われた準拠の強化の完全な一覧については、「[Visual Studio 2003 から 2015 の Visual C++ の新機能](../porting/visual-cpp-what-s-new-2003-through-2015.md)」を参照してください。

## <a name="conformance-improvements-in-visual-studio-2017-rtw-version-150"></a><a name="improvements_150"></a> Visual Studio 2017 RTW (バージョン 15.0) の準拠の強化

Visual Studio 2017 の MSVC コンパイラは、汎用の **`constexpr`** および集約用の非静的データ メンバーの初期化 (NSDMI) のサポートと共に、C++ 14 標準で追加されたすべての機能に対応するようになりました。 ただし、コンパイラには、C++11 標準および C++98 標準の一部の機能がありません。 コンパイラの現在の状態については、「[Microsoft C++ 言語の準拠表](./visual-cpp-language-conformance.md)」を参照してください。

### <a name="c11-expression-sfinae-support-in-more-libraries"></a>C++11:より多くのライブラリでの SFINAE 式のサポート

コンパイラでは、SFINAE 式のサポートが継続的に改善されています。 これは、 **`decltype`** および **`constexpr`** 式がテンプレート パラメーターとして使用されるテンプレート引数の演繹と代替のために必要です。 詳細については、「[Expression SFINAE improvements in Visual Studio 2017 RC](https://devblogs.microsoft.com/cppblog/expression-sfinae-improvements-in-vs-2015-update-3/)」 (Visual Studio 2017 RC での SFINAE 式の機能拡張) を参照してください。

### <a name="c14-nsdmi-for-aggregates"></a>C++14: 集約用の NSDMI

"*集約*" は、配列またはクラスであり、ユーザー指定のコンストラクターがなく、プライベートまたは保護された非静的データ メンバーを持たず、基底クラスや仮想関数もありません。 C++ 14 以降では、集約にメンバーの初期化子を含めることができます。 詳細については、「[Member initializers and aggregates](https://wg21.link/n3605)」 (メンバー初期化子と集計) を参照してください。

### <a name="c14-extended-constexpr"></a>C++14:拡張された `constexpr`

**`constexpr`** として宣言された式には、特定の種類の宣言、if および switch ステートメント、loop ステートメント、 **`constexpr`** 式の評価内で有効期間が開始されたオブジェクトの変異を含めることができます。 さらに、 **`constexpr`** の非静的メンバー関数を暗黙的に **`const`** しなければならないという要件はなくなりました。 詳細については、「[`constexpr` 関数に対する制約の緩和](https://wg21.link/n3652)」を参照してください。

### <a name="c17-terse-static_assert"></a>C++17:簡易 `static_assert`

**`static_assert`** のメッセージ パラメーターは省略可能です。 詳細については、[N3928: 「static_assert の拡張 v2」](https://wg21.link/n3928)を参照してください。

### <a name="c17-fallthrough-attribute"></a>C++17: `[[fallthrough]]` 属性

**`/std:c++17`** モードで、`[[fallthrough]]` 属性は、フォールスルー動作を意図するコンパイラに対するヒントとして switch ステートメントのコンテキスト内で使用できます。 この属性により、コンパイラがこのような場合に警告を発行することを防止できます。 詳細については、[P0188R0 - 「`[[fallthrough]]` 属性の表現方法」](https://wg21.link/p0188r0)を参照してください。

### <a name="generalized-range-based-for-loops"></a>範囲ベースの `for` ループ (汎用)

範囲ベースの `for` ループでは、`begin()` および `end()` が同じ型のオブジェクトを返す必要はなくなりました。 この変更により、`end()` で [`range-v3`](https://github.com/ericniebler/range-v3) および completed-but-not-quite-published 範囲の技術仕様で使用される sentinel を返すことができます。 詳細については、[P0184R0 - 「範囲ベースの `for` ループの汎用化」](https://wg21.link/p0184r0)を参照してください。

### <a name="copy-list-initialization"></a>Copy-list-initialization

Visual Studio 2017 では、初期化子リストを使用したオブジェクトの作成に関連するコンパイラ エラーが正しく発生します。 これらのエラーは、Visual Studio 2015 ではキャッチされなかったため、クラッシュまたは未定義の実行時の動作を引き起こす可能性がありました。 [N4594 13.3.1.7p1](https://wg21.link/n4594) のとおり、 *`copy-list-initialization`* で、コンパイラは、オーバーロードの解決のために明示的なコンストラクターを考慮する必要があります。 ただし、その特定のオーバーロードが選択された場合、エラーを発生させる必要があります。

次の 2 つの例は、Visual Studio 2017 ではなく Visual Studio 2015 でコンパイルします。

```cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 }; // error C3445: copy-list-initialization of 'A' cannot use an explicit constructor
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot convert from 'int' to 'const A &'

}
```

このエラーを修正するには、直接の初期化を使用します。

```cpp
A a1{ 1 };
const A& a2{ 1 };
```

Visual Studio 2015 では、コンパイラは、誤って copy-list-initialization を通常の copy-initialization と同じ方法で処理しました。これは、単なるオーバーロードの解決のためのコンストラクターの変換と見なされます。 次の例では、Visual Studio 2015 で `MyInt(23)` を選択しています。 Visual Studio 2017 ではエラーが正しく発生します。

```cpp
// From http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html#1228
struct MyStore {
    explicit MyStore(int initialCapacity);
};

struct MyInt {
    MyInt(int i);
};

struct Printer {
    void operator()(MyStore const& s);
    void operator()(MyInt const& i);
};

void f() {
    Printer p;
    p({ 23 }); // C3066: there are multiple ways that an object
        // of this type can be called with these arguments
}
```

この例は、前に似ていますが、別のエラーを発生させます。 Visual Studio 2015 では成功し、Visual Studio 2017 と C2668 では失敗します。

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```

### <a name="deprecated-typedefs"></a>非推奨の typedef

Visual Studio 2017 は、クラスまたは構造体で宣言されている非推奨の typedef に関する正しい警告を発行するようになりました。 次の Visual Studio 2015 の例では、警告なしでコンパイルされます。 Visual Studio 2017 では C4996 が生成されます。

```cpp
struct A
{
    // also for __declspec(deprecated)
    [[deprecated]] typedef int inttype;
};

int main()
{
    A::inttype a = 0; // C4996 'A::inttype': was declared deprecated
}
```

### `constexpr`

Visual Studio 2017 では、条件付きで評価する演算の左のオペランドが `constexpr` コンテキストで無効である場合、正しくエラーが発生します。 次のコードは、Visual Studio 2015 ではコンパイルされますが、Visual Studio 2017 ではコンパイルされず、C3615 が発生します。

```cpp
template<int N>
struct array
{
    int size() const { return N; }
};

constexpr bool f(const array<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615 constexpr function 'f' cannot result in a constant expression
}
```

エラーを修正するには、`array::size()` 関数を **`constexpr`** として宣言するか、`f` から **`constexpr`** 修飾子を削除します。

### <a name="class-types-passed-to-variadic-functions"></a>可変個引数関数に渡されるクラス型

Visual Studio 2017 では、`printf` などの可変個引数関数に渡されるクラスまたは構造体は、普通にコピー可能である必要があります。 このようなオブジェクトを渡すときには、コンパイラは単にビットごとのコピーを作成し、コンストラクターまたはデストラクターを呼び出しません。

```cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function.
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```

エラーを解決するために、普通にコピー可能な型を返すメンバー関数を呼び出すことができます。

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

または、オブジェクトを渡す前にオブジェクトを変換するための静的キャストを実行します。

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

`CString` を使用して構築および管理される文字列の場合、指定されている `operator LPCTSTR()` を使用して、書式設定文字列によって予期されている C ポインターに `CString` オブジェクトをキャストする必要があります。

```cpp
CString str1;
CString str2 = _T("hello!");
str1.Format(_T("%s"), static_cast<LPCTSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>クラス コンストラクションの cv 修飾子

Visual Studio 2015 では、コンストラクターを呼び出してクラス オブジェクトを生成するときに、コンパイラが誤って cv 修飾子を無視することがあります。 この問題により、クラッシュまたは予期しない実行時動作が発生する可能性があります。 次の例は、Visual Studio 2015 ではコンパイルされますが、Visual Studio 2017 ではコンパイラ エラーが発生します。

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

このエラーを解決するには、`operator int()` を **`const`** として宣言します。

### <a name="access-checking-on-qualified-names-in-templates"></a>テンプレートの修飾名のアクセス確認

以前のバージョンのコンパイラでは、一部のテンプレートのコンテキストで修飾名へのアクセスが確認されませんでした。 この問題により、名前にアクセスできないために置換が失敗すると予想される場合に、予期される SFINAE の動作に干渉する可能性があります。 コンパイラが演算子の誤ったオーバーロードを不適切に呼び出すために、これが原因でクラッシュまたは実行時に予期しない動作が発生する可能性があります。 Visual Studio 2017 年では、コンパイラ エラーが発生します。 具体的なエラーは異なる場合がありますが、典型的なエラーは、C2672: "一致するオーバーロードされた関数が見つかりませんでした" です。 次のコードは、Visual Studio 2015 ではコンパイルされますが、Visual Studio 2017 ではエラーが発生します。

```cpp
#include <type_traits>

template <class T> class S {
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x);

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```

### <a name="missing-template-argument-lists"></a>見つからないテンプレート引数リスト

Visual Studio 2015 以前のコンパイラでは、不足しているすべてのテンプレート引数リストが診断されませんでした。 テンプレート パラメーター リストに不足しているテンプレートが含まれている場合、たとえば既定のテンプレート引数または非型テンプレート パラメーターの一部が見つからなかった場合、注意されませんでした。 この問題により、コンパイラのクラッシュや実行時の予期しない動作などの予期しない動作が発生する可能性があります。 次のコードは、Visual Studio 2015 ではコンパイルされますが、Visual Studio 2017 ではエラーが発生します。

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>SFINAE 式

SFINAE 式をサポートするために、コンパイラは、テンプレートがインスタンス化されるときではなく宣言されるときに、 **`decltype`** 引数を解析するようになりました。 そのため、decltype 引数に非依存の特殊化が見つかった場合、インスタンス化時まで遅延されません。 すぐに処理され、結果として発生したエラーは、その時点で診断されます。

次の例は、宣言時に発生するこのようなコンパイラ エラーを示しています。

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT>
class IsCallable
{
public:
    struct BadType {};

    template <class U>
    static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>

    template <class U>
    static BadType Test(...);

    static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

### <a name="classes-declared-in-anonymous-namespaces"></a>匿名の名前空間で宣言されたクラス

C++ 標準によると、匿名の名前空間内で宣言されたクラスは内部リンケージがあるため、エクスポートすることができません。 Visual Studio 2015 以前のバージョンでは、この規則は適用されませんでした。 Visual Studio 2017 では、この規則は部分的に適用されます。 Visual Studio 2017 では、次の例によりエラー C2201:  が発生します

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} };
  // C2201 const anonymous namespace::S1::vftable: must have external linkage
  // in order to be exported/imported.
```

### <a name="default-initializers-for-value-class-members-ccli"></a>値クラス メンバー (C++/CLI) の既定の初期化子

Visual Studio 2015 以前では、コンパイラは、値クラスのメンバーの既定のメンバーの初期化子を許可しました (ただし無視しました)。 値クラスの既定の初期化子は、常にメンバーを 0 に初期化します。 既定のコンストラクターは許可されません。 Visual Studio 2017 年では、この例に示すように、既定メンバー初期化子は、コンパイラ エラーを発生させます。

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // isn't allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>既定のインデクサー (C++/CLI)

Visual Studio 2015 以前では、場合によっては、コンパイラは、既定のプロパティを誤って既定のインデクサーとして識別します。 識別子 **`default`** を使用してプロパティにアクセスすることで、この問題を回避できました。 C++ 11 で **`default`** がキーワードとして導入された後は、この回避策自体が問題になりました。 Visual Studio 2017 では、この回避策を必要としたバグが修正されました。 コンパイラでは、 **`default`** を使用してクラスの既定のプロパティにアクセスしたときにエラーが発生するようになりました。

```cpp
//class1.cs

using System.Reflection;
using System.Runtime.InteropServices;

namespace ClassLibrary1
{
    [DefaultMember("Value")]
    public class Class1
    {
        public int Value
        {
            // using attribute on the return type triggers the compiler bug
            [return: MarshalAs(UnmanagedType.I4)]
            get;
        }
    }
    [DefaultMember("Value")]
    public class Class2
    {
        public int Value
        {
            get;
        }
    }
}

// code.cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value; // error
       r1->default;
       r2->Value;
       r2->default; // error
}
```

Visual Studio 2017 年では、名前を指定して両方の Value プロパティにアクセスできます。

```cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="conformance-improvements-in-153"></a><a name="improvements_153"></a> 15.3 の準拠の強化

### <a name="constexpr-lambdas"></a>`constexpr` ラムダ

定数式でラムダ式を使用できるようになりました。 詳細については、「[C++ での `constexpr` ラムダ式](../cpp/lambda-expressions-constexpr.md)」を参照してください。

### <a name="if-constexpr-in-function-templates"></a>関数テンプレートでの `if constexpr`

関数テンプレートに、 **`if constexpr`** ステートメントを含めてコンパイル時の分岐を有効にできます。 詳細については、「[`if constexpr` ステートメント](../cpp/if-else-statement-cpp.md#if_constexpr)」を参照してください。

### <a name="selection-statements-with-initializers"></a>初期化子を含む選択ステートメント

**`if`** ステートメントには、ステートメント自体のブロック スコープで変数を導入する初期化子を含めることができます。 詳細については、「[初期化子を含む `if` 式](../cpp/if-else-statement-cpp.md#if_with_init)」を参照してください。

### <a name="maybe_unused-and-nodiscard-attributes"></a>`[[maybe_unused]]` 属性および `[[nodiscard]]` 属性

新しい属性 `[[maybe_unused]]` は、エンティティが使用されていない場合に警告を発生させません。 `[[nodiscard]]` 属性は、関数呼び出しの戻り値が破棄された場合に警告を発生させます。 詳しくは、「[Attributes in C++ (C++ における属性)](../cpp/attributes.md)」をご覧ください。

### <a name="using-attribute-namespaces-without-repetition"></a>繰り返しのない属性名前空間の使用

1 つの属性リストで 1 つの名前空間の識別子のみを有効にする新しい構文です。 詳しくは、「[Attributes in C++ (C++ における属性)](../cpp/attributes.md)」をご覧ください。

### <a name="structured-bindings"></a>構造化バインド

値が、配列、`std::tuple`、`std::pair` のいずれかであるか、すべてのパブリックの非静的データ メンバーを持つときに、1 つの宣言で、そのコンポーネントの個別の名前を持つ値を格納できるようになりました。 詳細については、[P0144R0 - 「構造化バインド」](https://wg21.link/p0144r0)と「[関数から複数の値を返す](../cpp/functions-cpp.md#multi_val)」を参照してください。

### <a name="construction-rules-for-enum-class-values"></a>`enum class` の値の構築ルール

非縮小のスコープ列挙に対して暗黙的な変換を使用できるようになりました。 スコープ列挙の基になる型から列挙型自体に変換されます。 この変換は、その定義で列挙子を導入せず、ソースでリスト初期化構文を使用している場合に使用できます。 詳細については、[P0138R2 - 「`enum class` の値の構築ルール」](https://wg21.link/p0138r2)と[列挙型](../cpp/enumerations-cpp.md#no_enumerators)に関する記事を参照してください。

### <a name="capturing-this-by-value"></a>`*this` の値によるキャプチャ

ラムダ式の **`*this`** オブジェクトが値でキャプチャできるようになりました。 この変更により、特に新しいコンピューター アーキテクチャで、並列で非同期の操作でラムダが呼び出されるシナリオを実現できます。 詳細については、[P0018R3 - 「\*this の \[=,\*this\] としての値によるラムダ キャプチャ」](https://wg21.link/p0018r3)を参照してください。

### <a name="removing-operator-for-bool"></a>`bool` の `operator++` の削除

`operator++` は **`bool`** 型でサポートされなくなりました。 詳細については、[P0002R1 - 「非推奨の operator++(bool) の削除」](https://wg21.link/p0002r1)を参照してください。

### <a name="removing-deprecated-register-keyword"></a>非推奨の `register` キーワードの削除

**`register`** キーワードは、以前は非推奨でしたが (コンパイラでは無視される)、言語から削除されました。 詳細については、[P0001R1 - 「`register` キーワードの非推奨の使用の削除」](https://wg21.link/p0001r1)を参照してください。

### <a name="calls-to-deleted-member-templates"></a>削除されたメンバー テンプレートへの呼び出し

Visual Studio の以前のバージョンでは、削除されたメンバー テンプレートの不適切な形式の呼び出しに対して、コンパイラがエラーの生成に失敗する場合がありました。 このような呼び出しは、実行時のクラッシュの原因になる可能性がありました。 次のコードでは、C2280 が生成されるようになりました。

```cpp
template<typename T>
struct S {
   template<typename U> static int f() = delete;
};

void g()
{
   decltype(S<int>::f<int>()) i; // this should fail with
// C2280: 'int S<int>::f<int>(void)': attempting to reference a deleted function
}
```

このエラーを解決するには、`i` を **`int`** として宣言します。

### <a name="pre-condition-checks-for-type-traits"></a>型の特徴に対する前提条件の確認

Visual Studio 2017 バージョン 15.3 では、型の特徴の前提条件の確認が向上し、標準にいっそう厳密に準拠するようになりました。 そのような確認の 1 つは割り当て可能に関するものです。 Visual Studio 2017 バージョン 15.3 では、次のコードに対して C2139 が生成されます。

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>コンパイラの新しい警告と、ネイティブからマネージへのマーシャリングの実行時チェック

マネージド関数からネイティブ関数を呼び出すには、マーシャリングが必要です。 CLR はマーシャリングを実行しますが、C++ のセマンティクスを理解していません。 ネイティブ オブジェクトを値で渡した場合、CLR はオブジェクトのコピー コンストラクターを呼び出すか、または `BitBlt` を使いますが、それによって実行時に未定義の動作が発生する可能性があります。

コンパイラでは、コンパイル時に、削除されたコピー コンストラクターを含むネイティブ オブジェクトがネイティブとマネージドの境界を越えて値で渡されるエラーが検出されると、警告が生成されるようになりました。 コンパイル時に認識できない場合のためには、実行時チェックが挿入されて、不適切な形式のマーシャリングが発生すると直ちにプログラムが `std::terminate` を呼び出せるようにします。 Visual Studio 2017 バージョン 15.3 では、次のコードに対して警告 C4606 が生成されます

```cpp
class A
{
public:
   A() : p_(new int) {}
   ~A() { delete p_; }

   A(A const &) = delete;
   A(A &&rhs) {
   p_ = rhs.p_;
}

private:
   int *p_;
};

#pragma unmanaged

void f(A a)
{
}

#pragma managed

int main()
{
    // This call from managed to native requires marshaling. The CLR doesn't
    // understand C++ and uses BitBlt, which results in a double-free later.
    f(A()); // C4606 'A': passing argument by value across native and managed
    // boundary requires valid copy constructor. Otherwise, the runtime
    // behavior is undefined.`
}
```

このエラーを解決するには、`#pragma managed` ディレクティブを削除し、呼び出し元をネイティブとしてマークして、マーシャリングを回避します。

### <a name="experimental-api-warning-for-winrt"></a>WinRT に対する実験用 API の警告

実験とフィードバックのためにリリースされている WinRT API は、`Windows.Foundation.Metadata.ExperimentalAttribute` で修飾されます。 Visual Studio 2017 バージョン 15.3 のコンパイラは、この属性に対して警告 | [C4698](../error-messages/compiler-warnings/c4698.md) を生成します。 以前のバージョンの Windows SDK に含まれる一部の API は、この属性で既に修飾されており、これらの API を呼び出すとこのコンパイラ警告がトリガーされるようになりました。 新しい Windows SDK では、付属するすべての型からこの属性が削除されています。 古い SDK を使っている場合は、付属する型のすべての呼び出しでこの警告を抑制する必要があります。

次のコードでは、警告 C4698 が生成されます。

```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); // C4698
// 'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' is for
// evaluation purposes only and is subject to change or removal in future updates
```

警告を無効にするには、#pragma を追加します。

```cpp
#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>テンプレート メンバー関数のアウトオブライン定義

Visual Studio 2017 バージョン 15.3 では、クラスで宣言されていないテンプレート メンバー関数のアウトオブライン定義に対してエラーが生成されます。 次のコードでは、エラー C2039 が生成されるようになりました。

```cpp
struct S {};

template <typename T>
void S::f(T t) {} // C2039: 'f': is not a member of 'S'
```

このエラーを解決するには、次の宣言をクラスに追加します。

```cpp
struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>`this` ポインターのアドレスを取得する試み

C++ では、 **`this`** は X へのポインター型の prvalue です。 **`this`** のアドレスを取得すること、または lvalue 参照にバインドすることはできません。 前のバージョンの Visual Studio では、キャストを使用することにより、この制限を回避できました。 Visual Studio 2017 バージョン 15.3 では、コンパイラはエラー C2664 を生成します。

### <a name="conversion-to-an-inaccessible-base-class"></a>アクセスできない基底クラスへの変換

Visual Studio 2017 バージョン 15.3 では、アクセスできない基底クラスに型を変換しようとすると、エラーになります。 次のコードは形式が不適切であり、実行時にクラッシュが発生する可能性があります。 コンパイラでは、次のようなコードが検出されると、C2243 が生成されるようになりました。

```cpp
#include <memory>

class B { };
class D : B { }; // C2243: 'type cast': conversion from 'D *' to 'B *' exists, but is inaccessible

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-arent-allowed-on-out-of-line-definitions-of-member-functions"></a>メンバー関数のアウトオブライン定義で既定の引数が許可されない

テンプレート クラスのメンバー関数のアウトオブライン定義では、既定の引数が許可されません。 コンパイラでは、 **`/permissive`** では警告が発生し、[`/permissive-`](../build/reference/permissive-standards-conformance.md) ではハード エラーが発生します。

Visual Studio の以前のバージョンでは、形式が間違っている次のコードでランタイム クラッシュが発生する可能性がありました。 Visual Studio 2017 バージョン 15.3 は、警告 [C5037](../error-messages/compiler-warnings/c5037.md) を生成します。

```cpp
template <typename T>
struct A {
    T f(T t, bool b = false);
};

template <typename T>
T A<T>::f(T t, bool b = false) // C5037: 'A<T>::f': an out-of-line definition of a member of a class template cannot have default arguments
{
    // ...
}
```

このエラーを解決するには、既定の引数 `= false` を削除します。

### <a name="use-of-offsetof-with-compound-member-designator"></a>複合メンバー指定子での `offsetof` の使用

Visual Studio 2017 バージョン 15.3 では、*m* が "複合メンバー指定子" である `offsetof(T, m)` を使用して、 **`/Wall`** オプションを指定してコンパイルすると、警告が発生します。 次のコードは形式が不適切であり、実行時にクラッシュが発生する可能性があります。 Visual Studio 2017 バージョン 15.3 では、警告 C4841 が発生します。

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

コードを修正するには、プラグマで警告を無効にするか、`offsetof` を使わないようにコードを変更します。

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>静的なデータ メンバーまたはメンバー関数での `offsetof` の使用

Visual Studio 2017 バージョン 15.3 では、*m* が静的なデータ メンバーまたはメンバー関数である `offsetof(T, m)` を使うと、エラーになります。 次のコードでは、エラー C4597 が生成されます。

```cpp
#include <cstddef>

struct A {
   int ten() { return 10; }
   static constexpr int two = 2;
};

constexpr auto off = offsetof(A, ten);  // C4597: undefined behavior: offsetof applied to member function 'A::ten'
constexpr auto off2 = offsetof(A, two); // C4597: undefined behavior: offsetof applied to static data member 'A::two'
```

このコードは形式が不適切であり、実行時にクラッシュが発生する可能性があります。 このエラーを解決するには、定義されていない動作を呼び出さないようにコードを変更します。 これは、C++ 標準で許可されていない移植性のないコードです。

### <a name="new-warning-on-__declspec-attributes"></a><a name="declspec"></a>`__declspec` 属性についての新しい警告

Visual Studio 2017 バージョン 15.3 では、`extern "C"` リンケージ指定の前に `__declspec(...)` を適用した場合、コンパイラは属性を無視しないようになりました。 以前のコンパイラは属性を無視し、実行時に影響する可能性がありました。 **`/Wall`** および **`/WX`** オプションが設定されている場合、次のコードでは警告 C4768 が生成されます。

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall // C4768: __declspec attributes before linkage specification are ignored
```

この警告を解決するには、`extern "C"` を先頭に配置します。

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

15.3 では既定でこの警告はオフになっており (15.5 では既定でオン)、 **`/Wall`** **`/WX`** を指定してコンパイルされたコードにのみ影響します。

### <a name="decltype-and-calls-to-deleted-destructors"></a>`decltype` と削除されたデストラクターの呼び出し

以前のバージョンの Visual Studio では、 **`decltype`** と関連付けられた式での削除されたデストラクターの呼び出しがコンパイラで検出されませんでした。 Visual Studio 2017 バージョン 15.3 では、次のコードではエラー C2280 が発生します。

```cpp
template<typename T>
struct A
{
   ~A() = delete;
};

template<typename T>
auto f() -> A<T>;

template<typename T>
auto g(T) -> decltype((f<T>()));

void h()
{
   g(42); // C2280: 'A<T>::~A(void)': attempting to reference a deleted function
}
```

### <a name="uninitialized-const-variables"></a>初期化されていない const 変数

Visual Studio 2017 RTW リリースには、初期化されていない **`const`** 変数に対して C++ コンパイラにより診断が生成されないという回帰がありました。 この回帰は、Visual Studio 2017 バージョン 15.3 で修正されました。 次のコードでは、警告 C4132 が生成されるようになりました。

```cpp
const int Value; // C4132: 'Value': const object should be initialized
```

このエラーを解決するに、`Value` に値を割り当てます。

### <a name="empty-declarations"></a>空の宣言

Visual Studio 2017 バージョン 15.3 では、組み込み型だけでなくすべての型で、空の宣言が警告されるようになりました。 次のコードでは、4 つの宣言すべてに対し、レベル 2 の警告 C4091 が生成されます。

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

警告を解決するには、空の宣言をコメントにするか、削除します。 名前のないオブジェクトが副作用 (RAII など) を意図したものである場合、名前を指定する必要があります。

警告は、 **`/Wv:18`** では除外され、警告レベル W2 では既定で有効になります。

### <a name="stdis_convertible-for-array-types"></a>配列型の `std::is_convertible`

以前のバージョンのコンパイラでは、配列型の [`std::is_convertible`](../standard-library/is-convertible-class.md) で正しい結果が得られませんでした。 そのため、ライブラリの作成者は `std::is_convertible<...>` 型の特徴を使用する場合に、Microsoft C++ コンパイラを特例処理する必要がありました。 次の例では、静的アサートは以前のバージョンの Visual Studio では成功しますが、Visual Studio 2017 バージョン 15.3 では失敗します。

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>` は、以下のように、虚数関数定義の形式が適切であるかどうかを確認して計算されます。

```cpp
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdis_constructible"></a>プライベート デストラクターと `std::is_constructible`

以前のバージョンのコンパイラでは、[`std::is_constructible`](../standard-library/is-constructible-class.md) の結果の判定時にデストラクターがプライベートかどうかは無視されていました。 ここではこれについて考えます。 次の例では、静的アサートは以前のバージョンの Visual Studio では成功しますが、Visual Studio 2017 バージョン 15.3 では失敗します。

```cpp
#include <type_traits>

class PrivateDtor {
   PrivateDtor(int) { }
private:
   ~PrivateDtor() { }
};

// This assertion used to succeed. It now correctly fails.
static_assert(std::is_constructible<PrivateDtor, int>::value);
```

プライベート デストラクターの場合、型が構成不可となります。 `std::is_constructible<T, Args...>` は、以下の宣言が書き込まれているかのように計算されます。

```cpp
   T obj(std::declval<Args>()...)
```

この呼び出しはデストラクターの呼び出しを意味します。

### <a name="c2668-ambiguous-overload-resolution"></a>C2668: あいまいなオーバーロードの解決

以前のバージョンのコンパイラでは、宣言と引数依存の参照の両方を使用して、複数の候補が見つかったときに、あいまいさを検出できない場合がありました。 この問題により、誤ったオーバーロードが選択され、ランタイムが予期しない動作になることがあります。 次の例では、Visual Studio 2017 バージョン 15.3 で C2668 が正しく発生します。

```cpp
namespace N {
   template<class T>
   void f(T&, T&);

   template<class T>
   void f();
}

template<class T>
void f(T&, T&);

struct S {};
void f()
{
   using N::f;

   S s1, s2;
   f(s1, s2); // C2668: 'f': ambiguous call to overloaded function
}
```

このコードを修正するには、`::f()` の呼び出しを意図していた場合は using `N::f` ステートメントを削除します。

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660: ローカル関数宣言と引数依存の参照

ローカル関数宣言では、外側のスコープ内の関数が非表示になり、引数依存の参照が無効になります。 以前のバージョンのコンパイラでは、このケースで引数依存の参照が常に行われました。 コンパイラによって間違ったオーバーロードが選択された場合、予期しない実行時の動作につながる可能性がありました。 通常、このエラーは、ローカル関数宣言のシグネチャが正しくないことが原因で発生します。 次の例では、Visual Studio 2017 バージョン 15.3 で C2660 が正しく発生します。

```cpp
struct S {};
void f(S, int);

void g()
{
   void f(S); // C2660 'f': function does not take 2 arguments:
   // or void f(S, int);
   S s;
   f(s, 0);
}
```

問題を修正するには、`f(S)` シグネチャを変更するか、削除します。

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038: 初期化子リストの初期化の順序

クラス メンバーは、初期化子リストに表示される順序ではなく、宣言される順序で初期化されます。 以前のバージョンのコンパイラでは、初期化子リストの順序が宣言の順序と異なる場合に警告されませんでした。 この問題により、あるメンバーの初期化が、リスト内の既に初期化されている別のメンバーに依存していた場合に、未定義の実行時の動作が発生することがありました。 次の例では、Visual Studio 2017 バージョン 15.3 ( **`/Wall`** を指定) で警告 C5038 が発生します。

```cpp
struct A
{    // Initialized in reverse, y reused
    A(int a) : y(a), x(y) {} // C5038: data member 'A::y' will be initialized after data member 'A::x'
    int x;
    int y;
};
```

この問題を解決するには、宣言と同じ順序になるように初期化子リストを整列します。 初期化子のいずれかまたは両方で基底クラス メンバーが参照される場合に同様の警告が発生します。

この警告は既定ではオフになっており、 **`/Wall`** を指定してコンパイルされたコードにのみ影響します。

## <a name="conformance-improvements-in-155"></a><a name="improvements_155"></a> 15.5 の準拠の強化

\[14] でマークされた機能は、 **`/std:c++14`** モードでも無条件で使用できます。

### <a name="new-compiler-switch-for-extern-constexpr"></a>`extern constexpr` の新しいコンパイラ スイッチ

Visual Studio の以前のバージョンでは、変数が **`extern`** としてマークされている場合でも、コンパイラは常に **`constexpr`** 変数を提供しました。 Visual Studio 2017 バージョン 15.5 では、新しいコンパイラ スイッチ ([`/Zc:externConstexpr`](../build/reference/zc-externconstexpr.md)) により、正しい標準準拠の動作が可能になります。 詳細については、「[`extern constexpr` リンケージ](#extern_linkage)」を参照してください。

### <a name="removing-dynamic-exception-specifications"></a>動的例外指定の削除

[P0003R5](https://wg21.link/p0003r5) C++11 では動的な例外の指定は非推奨となりました。 C++17 から機能が削除されますが、(引き続き) `noexcept(true)` のエイリアスとして非推奨の `throw()` 仕様が維持されます。 詳細については、「[動的例外指定の削除と `noexcept`](#noexcept_removal)」を参照してください。

### `not_fn()`

[P0005R4](https://wg21.link/p0005r4) `not_fn` は `not1` と `not2` の置き換えです。

### <a name="rewording-enable_shared_from_this"></a>`enable_shared_from_this` の新しい表現

[P0033R1](https://wg21.link/p0033r1) C++ 11 で `enable_shared_from_this` が追加されました。 C++ 17 標準では、特殊なケースの処理を改善するために仕様を更新します。 \[14]

### <a name="splicing-maps-and-sets"></a>マップと設定のスプライス

[P0083R3](https://wg21.link/p0083r3) この機能により、ノードを連想コンテナー (たとえば、`map`、`set`、`unordered_map`、`unordered_set`) から抽出し、それを変更して同じコンテナーまたは同じノード型を使用する別のコンテナーに挿入することができます (一般的なユース ケースでは、`std::map` からノードを抽出し、キーを変更して再挿入します)。

### <a name="deprecating-vestigial-library-parts"></a>残留ライブラリ パーツの廃止

[P0174R2](https://wg21.link/p0174r2) C++ 標準ライブラリのいくつかの機能は、長年にわたって新しい機能で置き換えられました。そうでないものは、あまり便利ではないか、または問題があることがわかっています。 これらの機能は、c++ 17 で正式に非推奨とされます。

### <a name="removing-allocator-support-in-stdfunction"></a>`std::function` のアロケーター サポートの削除

[P0302R1](https://wg21.link/p0302r1) C++17 の前には、クラス テンプレート `std::function` に、アロケーター引数を取るいくつかのコンストラクターがありました。 ただし、このコンテキストでのアロケーターの使用には問題があり、セマンティクスが不明確でした。 問題のコントラクターは削除されました。

### <a name="fixes-for-not_fn"></a>`not_fn()` の修正

[P0358R1](https://wg21.link/p0358r1)`std::not_fn` の新しい表現は、ラッパー呼び出し時の値のカテゴリの伝達をサポートします。

### <a name="shared_ptrt-shared_ptrtn"></a>`shared_ptr<T[]>`, `shared_ptr<T[N]>`

[P0414R2](https://wg21.link/p0414r2) ライブラリ基盤から C++ 17 への `shared_ptr` の変更のマージ。 \[14]

### <a name="fixing-shared_ptr-for-arrays"></a>配列の `shared_ptr` の修正

[P0497R0](https://wg21.link/p0497r0) 配列の shared_ptr のサポートを修正します。 \[14]

### <a name="clarifying-insert_return_type"></a>`insert_return_type` の明確化

[P0508R0](https://wg21.link/p0508r0) 固有のキーを持つ関連するコンテナー、固有ではないキーを持つ順序付けられていないコンテナーには、入れ子になった型 `insert_return_type` を返すメンバー関数 `insert` があります。 戻りの型は、コンテナーの反復子と NodeType でパラメーター化された型の特殊な形式として定義されるようになりました。

### <a name="inline-variables-for-the-standard-library"></a>標準ライブラリのインライン変数

[P0607R0](https://wg21.link/p0607r0) では、標準ライブラリで宣言されるいくつかの共通変数がインラインで宣言されるようになりました。

### <a name="annex-d-features-deprecated"></a>非推奨になった Annex D 機能

C++ 標準の Annex D は、`shared_ptr::unique()`、`<codecvt>`、`namespace std::tr1` を含む非推奨になったすべての機能を含んでいます。 **`/std:c++17`** コンパイラ スイッチが設定されている場合、Annex D のほとんどすべての標準ライブラリの機能は非推奨としてマークされます。 詳細については、「[非推奨としてマークされた Annex D の標準ライブラリの機能](#annex_d)」を参照してください。

`<experimental/filesystem>` の `std::tr2::sys` 名前空間は、 **`/std:c++14`** の下では既定で非推奨の警告を出力し、 **`/std:c++17`** では既定で削除されました。

非標準の拡張 (クラス内の明示的な特殊化) を回避することで `<iostream>` の適合性を向上させます。

標準ライブラリでは、変数テンプレートを内部で使用するようになりました。

標準ライブラリは、C++17 コンパイラの変更に応じて更新されました。 更新には、型システムへの **`noexcept`** の追加と、dynamic-exception-specifications の削除が含まれます。

### <a name="partial-ordering-change"></a>部分的な順序の変更

コンパイラは次のコードを正しく拒否し、正しいエラー メッセージを表示するようになりました。

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(const T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);    // C2668
}
```

```Output
t161.cpp
t161.cpp(16): error C2668: 'f': ambiguous call to overloaded function
t161.cpp(8): note: could be 'int f<int*>(const T &)'
        with
        [
            T=int*
        ]
t161.cpp(2): note: or       'int f<int>(int*)'
t161.cpp(16): note: while trying to match the argument list '(int*)'
```

上記の例での問題は型の 2 つの違い (定数と否定数およびパックと非パック) があることです。 コンパイラ エラーを回避するには、相違点の 1 つを削除します。 そうすると、コンパイラが関数を明確に順序付けることができます。

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);
}
```

### <a name="exception-handlers"></a>例外ハンドラー

配列または関数型への参照のハンドラーは、どの例外オブジェクトとも一致することはできません。 コンパイラは、このルールを正しく優先し、レベル 4 の警告を発生させるようになりました。 **`/Zc:strictStrings`** を使用するときに `char*` または `wchar_t*` のハンドラーを文字列リテラルと一致させることもできなくなりました。

```cpp
int main()
{
    try {
        throw "";
    }
    catch (int (&)[1]) {} // C4843 (This should always be dead code.)
    catch (void (&)()) {} // C4843 (This should always be dead code.)
    catch (char*) {} // This should not be a match under /Zc:strictStrings
}
```

```Output
warning C4843: 'int (&)[1]': An exception handler of reference to array or function type is unreachable, use 'int*' instead
warning C4843: 'void (__cdecl &)(void)': An exception handler of reference to array or function type is unreachable, use 'void (__cdecl*)(void)' instead
```

次のコードでは、エラーが回避されます。

```cpp
catch (int (*)[1]) {}
```

### <a name="stdtr1-namespace-is-deprecated"></a><a name="tr1"></a>非推奨となった `std::tr1` 名前空間

非標準 `std::tr1` 名前空間は、c++ 14 と c++ 17 の両方のモードで非推奨とマークされるようになりました。 Visual Studio 2017 バージョン 15.5 では、次のコードは C4996: を発生させます。

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::tr1::function<int (int, int)> f = std::plus<int>(); //C4996
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

```Output
warning C4996: 'std::tr1': warning STL4002: The non-standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
```

エラーを解決するには、`tr1` 名前空間への参照を削除します。

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::function<int (int, int)> f = std::plus<int>();
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

### <a name="standard-library-features-in-annex-d-are-marked-as-deprecated"></a><a name="annex_d"></a>非推奨としてマークされた Annex D の標準ライブラリの機能

**`/std:c++17`** モード コンパイラ スイッチが設定されている場合、Annex D のほとんどすべての標準ライブラリの機能は非推奨としてマークされます。

Visual Studio 2017 バージョン 15.5 では、次のコードは C4996: を発生させます。

```cpp
#include <iterator>

class MyIter : public std::iterator<std::random_access_iterator_tag, int> {
public:
    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

```Output
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
```

エラーを解決するには、次のコードに示すように、警告テキストの指示に従います。

```cpp
#include <iterator>

class MyIter {
public:
    typedef std::random_access_iterator_tag iterator_category;
    typedef int value_type;
    typedef ptrdiff_t difference_type;
    typedef int* pointer;
    typedef int& reference;

    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

### <a name="unreferenced-local-variables"></a>参照されていないローカル変数

Visual Studio 15.5 では、次のコードに示すように、多くの場合、警告 C4189 が生成されます。

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}
```

```Output
warning C4189: 's': local variable is initialized but not referenced
```

このエラーを解決するには、使用されていない変数を削除します。

### <a name="single-line-comments"></a>単一行コメント

Visual Studio 2017 バージョン 15.5 では、警告 C4001 と C4179 が、C コンパイラで生成されなくなりました。 以前は、それらは **`/Za`** コンパイラ スイッチでのみ生成されていました。  C99 以降、単一行のコメントが C 標準の一部になったため、警告は必要なくなりました。

```cpp
/* C only */
#pragma warning(disable:4001) // C4619
#pragma warning(disable:4179)
// single line comment
//* single line comment */
```

```Output
warning C4619: #pragma warning: there is no warning number '4001'
```

コードに下位互換性が必要ではない場合、C4001 と C4179 の抑制を削除することで警告を回避します。 コードに下位互換性が必要な場合は、C4619 のみを抑制します。

```C
/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="__declspec-attributes-with-extern-c-linkage"></a>`extern "C"` リンケージを持つ `__declspec` 属性

Visual Studio の以前のバージョンでは、`extern "C"` リンケージの指定の前に `__declspec(...)`が適用された場合、コンパイラは `__declspec(...)` を無視しました。 この動作によりユーザーが意図しないコードが生成され、ランタイムに影響する可能性がありました。 Visual Studio バージョン 15.3 で警告が追加されましたが、既定でオフになっていました。 Visual Studio 2017 バージョン 15.5 では、警告は既定で有効になっています。

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall // C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

エラーを解決するには、__declspec 属性の前に、リンケージの指定を配置します。

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

この新しい警告 C4768 は、Visual Studio 2017 15.3 以前 (たとえば、バージョン 10.0.15063.0、RS2 SDK とも呼ばれます) に付属していたいくつかの Windows SDK ヘッダーで指定されます。 ただし、この警告を生成しないように以降のバージョンの Windows SDK のヘッダー (具体的には、ShlObj.h および ShlObj_core.h) が修正されました。 Windows SDK のヘッダーからこの警告が表示される場合は、次の操作を実行できます。

1. Visual Studio 2017 バージョン 15.5 リリースに付属している最新の Windows SDK に切り替えます。

1. Windows SDK のヘッダー ステートメントの #include に関する警告をオフにします。

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern-constexpr-linkage"></a><a name="extern_linkage"></a> `extern constexpr` リンケージ

Visual Studio の以前のバージョンでは、変数が **`extern`** としてマークされている場合でも、コンパイラは常に **`constexpr`** 変数を提供しました。 Visual Studio 2017 バージョン 15.5 では、新しいコンパイラ スイッチ ( **`/Zc:externConstexpr`** ) により、正しい標準準拠の動作が可能になります。 最終的にこの動作は既定値になります。

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

ヘッダー ファイルには、宣言された変数 **`extern constexpr`** が含まれている場合、重複する宣言を正しく組み合わせるために、`__declspec(selectany)` のマークを付ける必要があります。

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>不完全なクラス型で `typeid` を使用できない

Visual Studio の以前のバージョンでは、コンパイラ誤って次のコードを許可し、その結果正しくない型情報になる可能性がありました。 Visual Studio 2017 バージョン 15.5 では、コンパイラは正しくエラーを生成します。

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdis_convertible-target-type"></a>`std::is_convertible` のターゲットの型

`std::is_convertible` では、ターゲットの型が有効な戻り値の型になっている必要があります。 Visual Studio の以前のバージョンでは、コンパイラが誤って抽象型を許可し、そのために、正しくないオーバーロードの解決や意図しない実行時の動作につながる可能性がありました。  次のコードは、C2338 を正しく発生させるようになりました。

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5
```

1 つの型が抽象型の場合、non-pointer-type の比較が失敗する場合があるので、エラー回避するには、`is_convertible` を使用するときにポインター型を比較する必要があります。

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");
```

### <a name="dynamic-exception-specification-removal-and-noexcept"></a><a name="noexcept_removal"></a>動的例外指定の削除と `noexcept`

C++ 17 では、`throw()` は **`noexcept`** のエイリアスで、`throw(<type list>)` と `throw(...)` は削除されているので、特定の型に **`noexcept`** が含まれる場合があります。 この変更により、C++14 またはそれ以前に準拠したコードのソース互換性の問題が生じる可能性があります。 **`/Zc:noexceptTypes-`** スイッチを利用すれば、全般的に C++17 モードを使用しながら、C++14 バージョンの **`noexcept`** に戻すことができます。 これでソース コードを更新し、C++17 に準拠できます。すべての `throw()` コードを同時に書き直す必要がありません。

コンパイラでは、C++ 17 モードの宣言で、または新しい警告 C5043 と [`/permissive-`](../build/reference/permissive-standards-conformance.md) を使用して、より多くの一致しない例外の指定を診断するようになりました。

次のコードでは、Visual Studio 2017 バージョン 15.5 で **`/std:c++17`** スイッチを適用するときに、C5043 および C5040 が生成されます。

```cpp
void f() throw(); // equivalent to void f() noexcept;
void f() {} // warning C5043
void g() throw(); // warning C5040

struct A {
    virtual void f() throw();
};

struct B : A {
    virtual void f() { } // error C2694
};
```

**`/std:c++17`** の使用中にエラーを削除するには、 **`/Zc:noexceptTypes-`** スイッチをコマンド ラインに追加するか、次の例のように、 **`noexcept`** を使用するようにコードを更新します。

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A {
    virtual void f() noexcept;
};

struct B : A {
    virtual void f() noexcept { }
};
```

### <a name="inline-variables"></a>インライン変数

静的 **`constexpr`** データ メンバーは、暗黙的に **`inline`** になり、クラス内でその宣言がそれらの定義になるようになりました。 **`static constexpr`** データ メンバーのアウトオブライン定義は、冗長であり、現在は非推奨とされます。 Visual Studio 2017 バージョン 15.5 では、 **`/std:c++17`** スイッチが適用されると、次のコードによって警告 C5041 が生成されるようになりました。

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041: 'size': out-of-line definition for constexpr static data member is not needed and is deprecated in C++17
```

### <a name="extern-c-__declspec-warning-c4768-now-on-by-default"></a>`extern "C" __declspec(...)` の警告 C4768 が既定でオンになる

Visual Studio 2017 バージョン 15.3 で警告が追加されましたが、既定でオフになっていました。 Visual Studio 2017 バージョン 15.5 では、警告は既定でオンになっています。 詳細については、「[`__declspec` 属性についての新しい警告](#declspec)」を参照してください。

### <a name="defaulted-functions-and-__declspecnothrow"></a>既定の関数と `__declspec(nothrow)`

コンパイラは以前、対応する base/member 関数で例外が許可されている場合、`__declspec(nothrow)` を使用した既定の関数の宣言を許可していました。 この動作は、C++ 標準に反しており、実行時に未定義の動作が発生することがあります。 標準では、例外の指定の不一致がある場合、そのような関数は削除済みとして定義する必要があります。  **`/std:c++17`** では、次のコードによって C2280 が発生します。

```cpp
struct A {
    A& operator=(const A& other) { // No exception specification; this function may throw.
        ...
    }
};

struct B : public A {
    __declspec(nothrow) B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1; // error C2280: attempting to reference a deleted function.
             // Function was implicitly deleted because the explicit exception
             // specification is incompatible with that of the implicit declaration.
}
```

このコードを修正するには、__declspec(nothrow) を既定値の関数から削除するか、`= default` を削除して、必要な例外処理と共に関数の定義を提供します。

```cpp
struct A {
    A& operator=(const A& other) {
        // ...
    }
};

struct B : public A {
    B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1;
}
```

### <a name="noexcept-and-partial-specializations"></a>`noexcept` と部分的な特殊化

型システムで **`noexcept`** を使用すると、特定の "呼び出し可能な" 型と一致させるための部分的な特殊化がコンパイルされなかったり、プライマリ テンプレートの選択に失敗したりすることがあります。これは、pointers-to-noexcept-functions の部分的な特殊化がないためです。

このような場合は、 **`noexcept`** 関数ポインターおよびメンバー関数への **`noexcept`** ポインターを処理するために、部分的な特殊化をさらに追加する必要があります。 これらのオーバーロードは、 **`/std:c++17`** モードでのみ有効です。 C++ 14 との下位互換性を維持する必要があるときに、他のユーザーが使用するコードを記述している場合、`#ifdef` ディレクティブ内でこれらの新しいオーバーロードを保護する必要があります。 自己完結型のモジュールを使用している場合、`#ifdef` ガードを使用する代わりに、 **`/Zc:noexceptTypes-`** スイッチを使用してコンパイルすることができます。

次のコードは **`/std:c++14`** ではコンパイルされますが、 **`/std:c++17`** ではエラー C2027 で失敗します。

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // C2027: use of undefined type 'A<T>'
}
```

次のコードは、 **`/std:c++17`** で成功します。コンパイラによって新しい部分的な特殊化 `A<void (*)() noexcept>` が選択されるためです。

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <>
struct A<void(*)() noexcept>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // OK
}
```

## <a name="conformance-improvements-in-156"></a><a name="improvements_156"></a> 15.6 の準拠の強化

### <a name="c17-library-fundamentals-v1"></a>C++17: ライブラリ基礎 V1

[P0220R1](https://wg21.link/p0220r1): C++17 用のライブラリ基礎技術仕様が標準に組み込まれています。 \<experimental/tuple>、\<experimental/optional>、\<experimental/functional>、\<experimental/any>、\<experimental/string_view>、\<experimental/memory>、\<experimental/memory_resource>、\<experimental/algorithm> の更新が含まれています。

### <a name="c17-improving-class-template-argument-deduction-for-the-standard-library"></a>C++17:標準ライブラリのクラス テンプレート引数の推論の機能強化

[P0739R0](https://wg21.link/p0739r0): `scoped_lock` を一貫して使用できるように、`adopt_lock_t` を `scoped_lock` のパラメーター リストの先頭に移動します。 コピー割り当てを有効にするために、`std::variant` コンストラクターがオーバーロードの解決法に関与することを許可します。

## <a name="conformance-improvements-in-157"></a><a name="improvements_157"></a> 15.7 の準拠の強化

### <a name="c17-rewording-inheriting-constructors"></a>C++17:コンストラクター継承の新しい表現

[P0136R1](https://wg21.link/p0136r1): コンストラクターに名前を命名する **`using`** 宣言では、追加の派生クラス コンストラクターを宣言するのでなく、派生クラスの初期化において対応する基底クラスのコンストラクターを表示できるようにしました。 この新しい表現は、C++14 からの変更です。 Visual Studio 2017 バージョン 15.7 以降の **`/std:c++17`** モードでは、C++14 において有効であり、かつ継承コンストラクターを使用するコードが、無効である場合もあれば、異なるセマンティクスを持つ場合もあります。

次の例では C++14 のビヘイビアーを示します。

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n) = delete; // Error C2280
};

B b(42L); // Calls B<long>(long), which calls A(int)
          //  due to substitution failure in A<long>(long).
```

次の例では、Visual Studio 15.7 での **`/std:c++17`** のビヘイビアーを示します。

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n)
    {
        //do something
    }
};

B b(42L); // now calls B(int)
```

詳細については、「[コンストラクター](../cpp/constructors-cpp.md#inheriting_constructors)」を参照してください。

### <a name="c17-extended-aggregate-initialization"></a>C++17:集約の初期化 (拡張)

[P0017R1](https://wg21.link/p0017r1)

基底クラスのコンストラクターがパブリックではないが、派生クラスからアクセスできる場合、Visual Studio 2017 バージョン 15.7 の **`/std:c++17`** モードでは、空のかっこを使用して派生型のオブジェクトを初期化することができなくなりました。
次の例では、C++14 の準拠動作を示します。

```cpp
struct Derived;
struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};
Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

C++17 で、`Derived` は集約型と見なされるようになりました。 つまり、既定のプライベート コンストラクターによる `Base` の初期化は、集約初期化ルールの一部として直接実行されます。 以前、`Base` プライベート コンストラクターは `Derived` コンストラクターを介して呼び出され、friend 宣言があるために成功していました。
次の例は、Visual Studio バージョン 15.7 の **`/std:c++17`** モードでの C++17 のビヘイビアーを示しています。

```cpp
struct Derived;
struct Base {
    friend struct Derived;
private:
    Base() {}
};
struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};
Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C++17:auto による非型テンプレート パラメーターの宣言

[P0127R2](https://wg21.link/p0127r2)

**`/std:c++17`** モードで、コンパイラは、 **`auto`** によって宣言されている非型テンプレート引数の型を推測できるようになりました。

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

この新しい機能の効果の 1 つとして、有効な C++14 コードが無効になったり、異なるセマンティクスを持つようになったりする場合があることが挙げられます。 たとえば、以前は無効であったオーバーロードの一部が有効になりました。 次の例では、`example(p)` の呼び出しが `example(void*);` にバインドされているためにコンパイルされる C++14 コードを示します。 Visual Studio 2017 バージョン 15.7 の **`/std:c++17`** モードでは、`example` 関数テンプレートが最も適しています。

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*) = delete;

void example(void *);

void sample(A<0> *p)
{
    example(p); // OK in C++14
}
```

次の例は、Visual Studio 15.7 の **`/std:c++17`** モードでの C++17 コードを示しています。

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*);

void example(void *);

void sample(A<0> *p)
{
    example(p); // C2280: 'int example<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C++17:基本文字列変換 (部分的)

[P0067R5](https://wg21.link/p0067r5): 整数と文字列の間、および浮動小数点数と文字列の間の変換ためのロケールに依存しない低レベルの機能

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C++20:不要な decay の回避 (部分的)

[P0777R1](https://wg21.link/p0777r1): "decay" の概念と const 修飾子または reference 修飾子の単純な削除の概念との区別を追加します。  一部のコンテキストでは、新しい型の特性 `remove_reference_t` が `decay_t` に置き換えられます。 `remove_cvref_t` のサポートは Visual Studio 2019 で実装されます。

### <a name="c17-parallel-algorithms"></a>C++17:並列アルゴリズム

[P0024R2](https://wg21.link/p0024r2): 並列 TS は、若干の変更が加えられて、標準に組み込まれます。

### <a name="c17-hypotx-y-z"></a>C++17: `hypot(x, y, z)`

[P0030R1:](https://wg21.link/p0030r1) 型 **`float`** 、 **`double`** 、および **`long double`** について、`std::hypot` に 3 つの新しいオーバーロードを追加します。それぞれが 3 つの入力パラメーターを持っています。

### <a name="c17-filesystem"></a>C++17: \<filesystem>

[P0218R1](https://wg21.link/p0218r1): ファイル システム TS を、表現に少し変更を加えて、標準に採用します。

### <a name="c17-mathematical-special-functions"></a>C++17:数学的特殊関数

[P0226R1](https://wg21.link/p0220r1): 数学的特殊関数に関する以前の技術仕様を標準的な \<cmath> ヘッダーに採用します。

### <a name="c17-deduction-guides-for-the-standard-library"></a>C++17:標準ライブラリの推論ガイド

[P0433R2](https://wg21.link/p0433r2): [P0091R3](https://wg21.link/p0091r3) (クラス テンプレート引数の推論に対するサポートを追加) の C++17 採用の利点を活用するための、STL の更新。

### <a name="c17-repairing-elementary-string-conversions"></a>C++17:基本文字列変換の修正

[P0682R1](https://wg21.link/p0682r1): 基本文字列変換の新しい関数を P0067R5 から新しいヘッダー \<charconv> に移動します。さらに、`std::error_code` ではなく `std::errc` を使用するようにエラー処理を変更するなど、他の機能強化も行います。

### <a name="c17-constexpr-for-char_traits-partial"></a>C++ 17: `char_traits` の `constexpr` (部分的)

[P0426R1](https://wg21.link/p0426r1): `std::string_view` を定数式で使用できるようにするために、`std::traits_type` のメンバー関数である `length`、`compare`、`find` に変更します。 (Visual Studio 2017 バージョン 15.6 では、Clang/LLVM のみがサポートされました。 バージョン 15.7 Preview 2 では、ClXX についてもサポートはほぼ完全です。)

### <a name="c17-default-argument-in-the-primary-class-template"></a>C++17:プライマリ クラス テンプレートでの既定の引数

この動作変更は、[P0091R3 - クラス テンプレートのテンプレート引数の推論](https://wg21.link/p0091r3)の前提条件です。

以前、コンパイラでは、プライマリ クラス テンプレート内の既定の引数は無視されていました。

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

Visual Studio 2017 バージョン 15.7 の **`/std:c++17`** モードでは、既定の引数は無視されません。

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>依存名の解決

この動作変更は、[P0091R3 - クラス テンプレートのテンプレート引数の推論](https://wg21.link/p0091r3)の前提条件です。

次の例では、Visual Studio 15.6 以前のコンパイラが、プライマリ クラス テンプレート内で `D::type` を `B<T>::type` に変換しています。

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = B<T*>::type;
};
```

Visual Studio 2017 バージョン 15.7 の **`/std:c++17`** モードでは、D の **`using`** ステートメントにキーワード **`typename`** が必要です。 **`typename`** がないと、コンパイラで警告 C4346: `'B<T*>::type': dependent name is not a type` とエラー C2061: `syntax error: identifier 'type'` が生成されます。

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = typename B<T*>::type;
};
```

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C++ 17 `[[nodiscard]]` 属性 - 警告レベルの引き上げ

Visual Studio 2017 バージョン 15.7 の **`/std:c++17`** モードでは、[C4834](../error-messages/compiler-warnings/c4834.md) の警告レベルは W3 から W1 に引き上げられます。 この警告は、 **`void`** へのキャストにより、または **`/wd:4834`** をコンパイラに渡すことにより無効にできます。

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning C4834: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>可変個引数テンプレート コンストラクター ベース クラス初期化リスト

Visual Studio の以前のエディションでは、テンプレート引数のない可変個引数テンプレート コンストラクター ベース クラス初期化リストが誤ってエラーなしで許可されていました。 Visual Studio 2017 バージョン 15.7 では、コンパイラ エラーが発生します。

Visual Studio 2017 バージョン 15.7 の次のコード例では、エラー C2614: 

```cpp
template<typename T>
struct B {};

template<typename T>
struct D : B<T>
{

    template<typename ...C>
    D() : B() {} // C2614: D<int>: illegal member initialization: 'B' is not a base or member
};

D<int> d;
```

このエラーを解決するには、B() 式を B\<T>() に変更します。

### <a name="constexpr-aggregate-initialization"></a>`constexpr` の集約の初期化

以前のバージョンの C++ コンパイラでは、 **`constexpr`** の集約の初期化が誤って処理されていました。 コンパイラによって、集約初期化リストの要素が多すぎる無効なコードが受け入れられ、不適切なオブジェクト コードが生成されました。 次にそのようなコードの例を示します。

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = { // C2078: too many initializers
        { 1, 2 },
        { 3, 4 }
    };
    return 0;
}
```

Visual Studio 2017 バージョン 15.7 Update 3 以降では、前の例に対して C2078 が発生するようになりました。 次に、コードを修正する方法の例を示します。 入れ子になった中かっこの初期化リストを使用して `std::array` を初期化する場合、内側の配列に独自の中かっこのリストを指定します。

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {{ // note double braces
        { 1, 2 },
        { 3, 4 }
    }}; // note double braces
    return 0;
}
```

## <a name="conformance-improvements-in-158"></a><a name="update_158"></a> 15.8 の準拠の強化

### <a name="typename-on-unqualified-identifiers"></a>非限定識別子の `typename`

[`/permissive-`](../build/reference/permissive-standards-conformance.md) モードでは、エイリアス テンプレート定義の非限定識別子に使用される疑似の **`typename`** キーワードがコンパイラで受け入れられなくなりました。 次のコードでは、C7511 が生成されるようになりました。

```cpp
template <typename T>
using  X = typename T; // C7511: 'T': 'typename' keyword must be 
                       // followed by a qualified name
```

このエラーを解決するには、2 行目を `using  X = T;` に変更します。

### <a name="__declspec-on-right-side-of-alias-template-definitions"></a>エイリアス テンプレート定義の右側の `__declspec()`

[`__declspec`](../cpp/declspec.md) はエイリアス テンプレート定義の右側で使用できなくなりました。 以前は、コンパイラによりこのコードは受け入れられましたが、無視されました。 エイリアスが使用されたときに、非推奨の警告が発生することはありませんでした。

標準の C++ 属性 [`[[deprecated]]`](../cpp/attributes.md) を代わりに使用できますが、適用されるのは Visual Studio 2017 バージョン 15.6 以降です。 次のコードでは、C2760 が生成されるようになりました。

```cpp
template <typename T>
using X = __declspec(deprecated("msg")) T; // C2760: syntax error:
                                           // unexpected token '__declspec',
                                           // expected 'type specifier'`
```

このエラーを解決するには、コードを次のように変更します (属性はエイリアス定義の '=' の前に置く)。

```cpp
template <typename T>
using  X [[deprecated("msg")]] = T;
```

### <a name="two-phase-name-lookup-diagnostics"></a>2 フェーズの名前参照の診断

2 フェーズの名前参照では、テンプレートの本文で使用される非依存名が定義時にテンプレートに表示されている必要があります。 以前の Microsoft C++ コンパイラでは、インスタンス化されるまで、見つからない名前は参照対象外のままになっていました。 現在は、非依存名がテンプレートの本文にバインドされている必要があります。

これにより、マニフェストで依存する基底クラスを参照できるようになります。 以前は、依存する基底クラスで定義されている名前を使用することがコンパイラにより許可されていました。 これは、インスタンス化中にすべての型が解決されると、それらが参照されるためです。 現在は、そのようなコードはエラーとして扱われます。 このような場合、変数を基底クラス型で修飾するか、`this->` ポインターを使用するなどして依存させることで、インスタンス化のときに変数が参照されるように強制できます。

[`/permissive-`](../build/reference/permissive-standards-conformance.md) モードでは、次のコードに対して C3861 が発生するようになりました。

```cpp
template <class T>
struct Base {
    int base_value = 42;
};

template <class T>
struct S : Base<T> {
    int f() {
        return base_value; // C3861: 'base_value': identifier not found
    }
};
```

このエラーを解決するには、 **`return`** ステートメントを `return this->base_value;` に変更します。

> [!NOTE]
> バージョン 1.70 より前の Boost.Python ライブラリの [`unwind_type.hpp`](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp) には、テンプレートの事前宣言のための MSVC 固有の回避策がありました。 Visual Studio 2017 バージョン 15.8 以降の [`/permissive-`](../build/reference/permissive-standards-conformance.md) モード (`_MSC_VER==1915`) では、MSVC コンパイラによって引数依存の名前検索 (ADL) が正しく実行されます。 これは他のコンパイラと一貫性があるため、この回避策のガードは不要になります。 エラー C3861: `'unwind_type': identifier not found` を回避するには、Boost.Python ライブラリを更新します。

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>名前空間 `std` での事前宣言と定義

C++ 標準では、ユーザーが事前宣言または定義を名前空間 `std` に追加することができません。 名前空間 `std` または名前空間 `std` 内の名前空間に宣言または定義を追加すると、定義されていない動作が発生するようになりました。

Microsoft は今後どこかの時点で、一部の標準ライブラリ型を定義する場所を移動します。 この変更が行われると、名前空間 `std` に事前宣言を追加する既存のコードが破損します。 新しい警告 C4643 は、このようなソースの問題の特定に役立ちます。 この警告は **`/default`** モードでは有効に、既定では無効になっています。 これは、 **`/Wall`** または **`/WX`** を指定してコンパイルされたプログラムに影響します。

次のコードで C4643: 

```cpp
namespace std {
    template<typename T> class vector;  // C4643: Forward declaring 'vector'
                                        // in namespace std is not permitted
                                        // by the C++ Standard`
}
```

このエラーを解決するには、事前宣言ではなく **`#include`** ディレクティブを使用します。

```cpp
#include <vector>
```

### <a name="constructors-that-delegate-to-themselves"></a>それ自体にデリゲートするコンストラクター

C++ 標準では、コンストラクターがそれ自体にデリゲートするときにはコンパイラで診断を出力することを提案しています。 Microsoft C++ コンパイラの [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) モードと [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) モードでは、C7535 が発生するようになりました。

このエラーがないと、次のプログラムでコンパイルされますが、無限ループが生成されます。

```cpp
class X {
public:
    X(int, int);
    X(int v) : X(v){} // C7535: 'X::X': delegating constructor calls itself
};
```

無限ループを避けるには、別のコンストラクターにデリゲートしてください。

```cpp
class X {
public:

    X(int, int);
    X(int v) : X(v, 0) {}
};
```

### <a name="offsetof-with-constant-expressions"></a>定数式を含む `offsetof`

[`offsetof`](../c-runtime-library/reference/offsetof-macro.md) は従来から [`reinterpret_cast`](../cpp/reinterpret-cast-operator.md) を必要とするマクロを使用して実装されています。 この用法は、定数式を必要とするコンテキストでは正しくありませんが、Microsoft C++ コンパイラではこれまで許可されていました。 標準ライブラリの一部としてリリースされている `offsetof` マクロはコンパイラ組み込み型 ( **`__builtin_offsetof`** ) が正しく使用されますが、多くのユーザーはマクロのトリックを使用して独自の `offsetof` を定義しています。

Visual Studio 2017 バージョン 15.8 では、コードが標準の C++ の動作に準拠するように、これらの **`reinterpret_cast`** 演算子が既定のモードで表示される領域がコンパイラにより制約されます。 [`/permissive-`](../build/reference/permissive-standards-conformance.md) の下では、制約がさらに厳しくなります。 定数式を必要とする場所で `offsetof` の結果を使用すると、警告 C4644 または C2975 を発生させるコードが生成される場合があります。

次のコードでは、 **`/default`** モードと **`/std:c++17`** モードでは C4644 が、[`/permissive-`](../build/reference/permissive-standards-conformance.md) モードでは C2975 が発生します。

```cpp
struct Data {
    int x;
};

// Common pattern of user-defined offsetof
#define MY_OFFSET(T, m) (unsigned long long)(&(((T*)nullptr)->m))

int main()

{
    switch (0) {
    case MY_OFFSET(Data, x): return 0; // C4644: usage of the
        // macro-based offsetof pattern in constant expressions
        // is non-standard; use offsetof defined in the C++
        // standard library instead
        // OR
        // C2975: invalid template argument, expected
        // compile-time constant expression

    default: return 1;
    }
}
```

このエラーを解決するには、\<cstddef> を使用して定義された `offsetof` を使用します。

```cpp
#include <cstddef>

struct Data {
    int x;
};

int main()
{
    switch (0) {
    case offsetof(Data, x): return 0;
    default: return 1;
    }
}
```

### <a name="cv-qualifiers-on-base-classes-subject-to-pack-expansion"></a>パック拡張の対象になっている基底クラスの cv 修飾子

以前のバージョンの Microsoft C++ コンパイラでは、基底クラスがパック拡張の対象でもあった場合、cv 修飾子が含まれることを検出しませんでした。

Visual Studio 2017 バージョン 15.8 の [`/permissive-`](../build/reference/permissive-standards-conformance.md) モードでは、次のコードにより C3770 が発生します。

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x; // C3770: 'const S': is not a valid base class
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>`template` キーワードと nested-name-specifier

[`/permissive-`](../build/reference/permissive-standards-conformance.md) モードでは、コンパイラが依存する nested-name-specifier の後にある場合にテンプレート名が優先されるためには、コンパイラで **`template`** キーワードが必要になりました。

[`/permissive-`](../build/reference/permissive-standards-conformance.md) モードでは、次のコードによって C7510 が発生するようになりました。

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        Base<T>::example<int>(); // C7510: 'example': use of dependent
            // template name must be prefixed with 'template'
            // note: see reference to class template instantiation
            // 'X<T>' being compiled
    }
};
```

このエラーを解決するには、次の例で示すように、 **`template`** キーワードを `Base<T>::example<int>();` ステートメントに追加します。

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        // Add template keyword here:
        Base<T>::template example<int>();
    }
};
```

## <a name="conformance-improvements-in-159"></a><a name="improvements_159"></a> 15.9 の準拠の強化

### <a name="left-to-right-evaluation-order-for-operators-----and-"></a>演算子 `->*`、`[]`、`>>`、`<<` での左から右の評価順序

C++ 17 以降、演算子`->*`、`[]`、`>>`、`<<` のオペランドは必ず左から右の順序で評価されます。 コンパイラでこの順序を保証できないケースが 2 つあります。

- オペランド式の 1 つが値渡しされるオブジェクトであるか、値渡しされるオブジェクトを含んでいる場合、または

- **`/clr`** を使ってコンパイルされ、かつオペランドの 1 つがオブジェクトのフィールドか配列要素である場合。

コンパイラで左から右の評価を保証できない場合、警告 [C4866](../error-messages/compiler-warnings/c4866.md) が生成されます。 これらの演算子に対する左から右の順序の要件は C++ 17 で導入されたため、コンパイラでこの警告が生成されるのは **`/std:c++17`** 以降を指定した場合のみです。

この警告を解決するには、まず、オペランドを左から右に評価する必要があるかどうかを検討します。 たとえば、オペランドの評価によって順序に依存する副作用が発生する可能性がある場合は、必要になることがあります。 多くの場合、オペランドが評価される順序によって、目に見える影響が生じることはありません。 必ず左から右の順序で評価する必要がある場合は、代わりに定数参照でオペランドを渡すことができるかどうかを検討します。 この変更により、次のコード サンプルにおける警告がなくなります。

```cpp
// C4866.cpp
// compile with: /w14866 /std:c++17

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x) : x(x) {}
    HasCopyConstructor(const HasCopyConstructor& h) : x(h.x) { }
};

int operator>>(HasCopyConstructor a, HasCopyConstructor b) { return a.x >> b.x; }

// This version of operator>> does not trigger the warning:
// int operator>>(const HasCopyConstructor& a, const HasCopyConstructor& b) { return a.x >> b.x; }

int main()
{
    HasCopyConstructor a{ 1 };
    HasCopyConstructor b{ 2 };

    a>>b;        // C4866 for call to operator>>
};
```

### <a name="identifiers-in-member-alias-templates"></a>メンバーのエイリアス テンプレート内の識別子

メンバーのエイリアス テンプレート定義で使用される識別子は、使用前に宣言する必要があります。

以前のバージョンのコンパイラでは、次のコードが許可されていました。 Visual Studio 2017 バージョン 15.9 の [`/permissive-`](../build/reference/permissive-standards-conformance.md) モードでは、コンパイラによって C3861 が発生します。

```cpp
template <typename... Ts>
struct A
{
  public:
    template <typename U>
    using from_template_t = decltype(from_template(A<U>{})); // C3861:
        // 'from_template': identifier not found

  private:
    template <template <typename...> typename Type, typename... Args>
    static constexpr A<Args...> from_template(A<Type<Args...>>);
};

A<>::from_template_t<A<int>> a;
```

このエラーを解決するには、`from_template_t` の前に `from_template` を宣言します。

### <a name="modules-changes"></a>モジュールの変更

Visual Studio 2017 のバージョン 15.9 では、モジュールのコマンド ライン オプションがモジュールの作成側とモジュールの使用側で一貫していない場合に必ず、コンパイラで C5050 が発生します。 次の例には、2 つの問題があります。

- 使用側 (main.cpp) で、オプション **`/EHsc`** が指定されていません。

- C++ のバージョンは、作成側が **`/std:c++17`** で、使用側が **`/std:c++14`** です。

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

このどちらの場合でも、コンパイラによって C5050 が発生します。

```Output
warning C5050: Possible incompatible environment while
importing module 'm': mismatched C++ versions.
Current "201402" module version "201703"`.
```

*`.ifc`* ファイルが改ざんされている場合には必ずコンパイラで C7536 が発生します。 モジュール インターフェイスのヘッダーの下には、コンテンツの SHA2 ハッシュが含まれています。 インポート時に *`.ifc`* ファイルがハッシュされ、ヘッダーに指定されたハッシュと照合されます。 これらが一致しない場合は、エラー C7536 が発生します。

```Output
error C7536: ifc failed integrity checks.
Expected SHA2: '66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6'
```

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>別名と非推定コンテキストが含まれる部分的な順序付け

非推定コンテキストに別名が含まれる部分的な順序付けルールには実装方法に違いがあります。 次の例では、GCC と Microsoft C++ コンパイラ ([`/permissive-`](../build/reference/permissive-standards-conformance.md) モード) ではエラーが発生しますが、Clang ではコードが受け入れられます。

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <class T, class Alloc>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

前述の例では、C2668 が発生します。

```Output
partial_alias.cpp(32): error C2668: 'f': ambiguous call to overloaded function
partial_alias.cpp(18): note: could be 'int f<Alloc,void>(A<void> &,const AlignedBuffer<10,4> &)'
partial_alias.cpp(12): note: or       'int f<Alloc,A<void>>(Alloc &,const AlignedBuffer<10,4> &)'
        with
        [
            Alloc=A<void>
        ]
partial_alias.cpp(32): note: while trying to match the argument list '(A<void>, AlignedBuffer<10,4>)'
```

実装方法が異なる原因は、C++ 標準の表現の回帰です。 核となる問題 2235 の解決により、これらのオーバーロードの順序付けを許可する一部のテキストが削除されました。 現在の C++ 標準ではこれらの関数を部分的に並べ替えるメカニズムを提供していないため、関数があいまいであると見なされます。

回避策として、部分的な順序付けに頼らずにこの問題を解決することをお勧めします。 または、SFINAE を使用して特定のオーバーロードを削除します。 次の例では、`Alloc` が `A` の特殊化である場合にヘルパー クラス `IsA` を使用して最初のオーバーロードを削除しています。

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <typename T> struct IsA : std::false_type {};
template <typename T> struct IsA<A<T>> : std::true_type {};

template <class T, class Alloc, typename = std::enable_if_t<!IsA<Alloc>::value>>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

### <a name="illegal-expressions-and-non-literal-types-in-templated-function-definitions"></a>テンプレート関数定義の不正な式と非リテラルの型

不正な式と非リテラルの型が、明示的に特化されているテンプレート関数の定義で正しく診断されるようになりました。 以前は、このようなエラーは関数定義で発生しませんでした。 ただし、定数式の一部として評価される場合は、不正な式も非リテラルの型も診断されることがありました。

前のバージョンの Visual Studio では、次のコードが警告なしでコンパイルされます。

```cpp
void g();

template<typename T>
struct S
{
    constexpr void f();
};

template<>
constexpr void S<int>::f()
{
    g(); // C3615 in 15.9
}
```

Visual Studio 2017 バージョン 15.9 では、このコードは次のエラーを発生させます。

```Output
error C3615: constexpr function 'S<int>::f' cannot result in a constant expression.
note: failure was caused by call of undefined function or one not declared 'constexpr'
note: see usage of 'g'.
```

このエラーを回避するには、関数 `f()` の明示的なインスタンス化から **`constexpr`** 修飾子を削除します。

## <a name="see-also"></a>関連項目

[Microsoft C++ 言語の準拠表](visual-cpp-language-conformance.md)
