---
title: Visual Studio 2019 での C++ 準拠の強化
description: Visual Studio の Microsoft C++ は、C++20 言語標準との完全準拠に向かって進んでいます。
ms.date: 03/10/2021
ms.technology: cpp-language
ms.openlocfilehash: c70b0db4d1d1163556fe746e0078412ae21e71d2
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721447"
---
# <a name="c-conformance-improvements-behavior-changes-and-bug-fixes-in-visual-studio-2019"></a>Visual Studio 2019 での C++ 準拠の強化、動作変更、バグ修正

Visual Studio の Microsoft C/C++ (MSVC) では、リリースごとに準拠の強化とバグ修正が行われます。 この記事では、機能強化をメジャー リリースごと、バージョンごとに一覧で紹介します。 特定のバージョンで行われた変更に直接移動するには、**この記事内** の一覧を使用します。

このドキュメントには、Visual Studio 2019 での変更点が記載されています。 Visual Studio 2017 での変更点のガイドについては、[Visual Studio 2017 での C++ 準拠の強化](cpp-conformance-improvements-2017.md)に関する記事を参照してください。 以前に行われた準拠の強化の完全な一覧については、「[Visual Studio 2003 から 2015 の Visual C++ の新機能](../porting/visual-cpp-what-s-new-2003-through-2015.md)」を参照してください。

## <a name="conformance-improvements-in-visual-studio-2019-rtw-version-160"></a><a name="improvements_160"></a> Visual Studio 2019 RTW (バージョン 16.0) の準拠の強化

Visual Studio 2019 RTW には、Microsoft C++ コンパイラでの以下の準拠強化、バグ修正、動作変更が含まれています。

> [!NOTE]
> C++20 の機能は、コンパイラと IntelliSense の両方で C++20 実装が完了するまで **`/std:c++latest`** モードで利用できます。 その時点で、 **`/std:c++20`** コンパイラ モードが導入されます。

### <a name="improved-modules-support-for-templates-and-error-detection"></a>改善されたモジュールのテンプレート サポートとエラー検出

モジュールは現在、公式に C++20 標準になりました。 改善されたサポートは、Visual Studio 2017 バージョン 15.9 で追加されました。 詳細については、「[Better template support and error detection in C++ Modules with MSVC 2017 version 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/)」 (C++ Modules での、テンプレート サポートとエラー検出に対する MSVC 2017 バージョン 15.9 を使用した改善) を参照してください。

### <a name="modified-specification-of-aggregate-type"></a>集計の種類の変更後の仕様

集計の種類の仕様が C++20 で変更されました (「[Prohibit aggregates with user-declared constructors](https://wg21.link/p1008r1)」 (ユーザー宣言コンストラクターの集計を禁止) を参照してください)。 Visual Studio 2019 の **`/std:c++latest`** では、ユーザー宣言コンストラクター (たとえば、コンストラクター宣言の `= default` や `= delete` を含む) を含むクラスは集約ではありません。 以前は、ユーザー指定のコンストラクターのみで、集計になる資格がクラスから剥奪されました。 今回の変更により、このような種類の初期化方法に対する制約が追加されました。

次のコードは Visual Studio 2017 ではエラーなくコンパイルされますが、Visual Studio 2019 の **`/std:c++latest`** では、C2280 エラーや C2440 エラーが発生します。

```cpp
struct A
{
    A() = delete; // user-declared ctor
};

struct B
{
    B() = default; // user-declared ctor
    int i = 0;
};

A a{}; // ill-formed in C++20, previously well-formed
B b = { 1 }; // ill-formed in C++20, previously well-formed
```

### <a name="partial-support-for-operator-"></a>`operator <=>` の部分的なサポート

[P0515R3](https://wg21.link/p0515r3) C++20 では、3 方向の比較演算子 `<=>` が導入されました。これは "宇宙船演算子" とも呼ばれています。 **`/std:c++latest`** モードの Visual Studio 2019 では、現在許可されていない構文に対してエラーを発生させることで、この演算子が部分的にサポートされています。 たとえば、次のコードは Visual Studio 2017 ではエラーなくコンパイルされますが、Visual Studio 2019 の **`/std:c++latest`** では、複数のエラーが発生します。

```cpp
struct S
{
    bool operator<=(const S&) const { return true; }
};

template <bool (S::*)(const S&) const>
struct U { };

int main(int argc, char** argv)
{
    U<&S::operator<=> u; // In Visual Studio 2019 raises C2039, 2065, 2146.
}
```

エラーを回避するには、`U<&S::operator<= > u;` のように、最後の山かっこの前でエラーを出す行にスペースを挿入します。

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>cv 修飾子が一致しない型の参照

MSVC では以前、最上位より下で、cv 修飾子が一致しない型から参照を直接バインドすることが許可されました。 このバインドにより、参照により指示されると思われる const データを変更できる場合がありました。 このコンパイラでは現在、標準で要求されるとおり、temporary が作成されます。 Visual Studio 2017 の場合、次のコードは警告なしでコンパイルされます。 Visual Studio 2019 では、コンパイラによって警告 C4172 が発生します。

```cpp
struct X
{
    const void* const& PData() const
    {
        return _pv;
    }

    void* _pv;
};

int main()
{
    X x;
    auto p = x.PData(); // C4172 <func:#1 "?PData@X@@QBEABQBXXZ"> returning address of local variable or temporary
}
```

### <a name="reinterpret_cast-from-an-overloaded-function"></a>オーバー ロードした関数からの `reinterpret_cast`

**`reinterpret_cast`** の引数は、オーバーロードした関数のアドレスが許可されるコンテキストの 1 つではありません。 次のコードは Visual Studio 2017 ではエラーなくコンパイルされますが、Visual Studio 2019 ではエラー C2440 が発生します。

```cpp
int f(int) { return 1; }
int f(float) { return .1f; }
using fp = int(*)(int);

int main()
{
    fp r = reinterpret_cast<fp>(&f); // C2440: cannot convert from 'overloaded-function' to 'fp'
}
```

このエラーを回避するには、このシナリオで許可されるキャストを使用します。

```cpp
int f(int);
int f(float);
using fp = int(*)(int);

int main()
{
    fp r = static_cast<fp>(&f); // or just &f;
}
```

### <a name="lambda-closures"></a>ラムダ クロージャ

C++ 14 では、ラムダ クロージャの型はリテラルではありません。 このルールの最も重要な影響は、ラムダが **`constexpr`** 変数に割り当てられない可能性があるということです。 次のコードは Visual Studio 2017 ではエラーなくコンパイルされますが、Visual Studio 2019 ではエラー C2127 が発生します。

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 'l': illegal initialization of 'constexpr' entity with a non-constant expression
}
```

エラーを回避するには、 **`constexpr`** 修飾子を削除するか、準拠モードを **`/std:c++17`** に変更します。

### <a name="stdcreate_directory-failure-codes"></a>`std::create_directory` エラー コード

無条件で C++20 から [P1164](https://wg21.link/p1164r1) が実装されました。 これにより、エラー時、ターゲットが既にディレクトリであったかどうかを確認するように `std::create_directory` が変更されます。 以前は、ERROR_ALREADY_EXISTS タイプのエラーはすべて、success-but-directory-not-created コードに変換されました。

### `operator<<(std::ostream, nullptr_t)`

[LWG 2221](https://cplusplus.github.io/LWG/issue2221) に基づき、 **`nullptr`** をストリームに書き込むための `operator<<(std::ostream, nullptr_t)` が追加されました。

### <a name="more-parallel-algorithms"></a>追加の並列アルゴリズム

`is_sorted`、`is_sorted_until`、`is_partitioned`、`set_difference`、`set_intersection`、`is_heap`、`is_heap_until` の新しい並列バージョン。

### <a name="atomic-initialization"></a>アトミック初期化

[P0883 "Fixing atomic initialization"](https://wg21.link/p0883r1) により、含まれる `T` を既定初期化せず、値初期化するように `std::atomic` が変更されます。 Clang/LLVM と Microsoft 標準ライブラリが使用されるとき、修正は有効になります。 Microsoft C++ コンパイラでは、 **`constexpr`** 処理のバグに対する回避策としてこれは現在、無効になっています。

### <a name="remove_cvref-and-remove_cvref_t"></a>`remove_cvref` および `remove_cvref_t`

[P0550](https://wg21.link/p0550r2) から型の特徴、`remove_cvref` と `remove_cvref_t` を実装しました。 それにより、(`std::decay` や `std::decay_t` とは異なり) 関数や配列をポインターに減衰させることなく、reference-ness と cv 修飾が型から削除されます。

### <a name="feature-test-macros"></a>機能テストのマクロ

[P0941R2 - 機能テスト マクロ](https://wg21.link/p0941r2)は完全であり、`__has_cpp_attribute` がサポートされています。 機能テスト マクロはすべての標準モードでサポートされています。

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>ユーザー宣言コンストラクターによる集計の禁止

C++20 [P1008R1 - ユーザー宣言コンストラクターによる集約の禁止](https://wg21.link/p1008r1)は完全です。

### <a name="reinterpret_cast-in-a-constexpr-function"></a>`constexpr` 関数での `reinterpret_cast`

**`constexpr`** 関数では **`reinterpret_cast`** は無効です。 これまでは、Microsoft C++ コンパイラによって **`reinterpret_cast`** は **`constexpr`** のコンテキストで使用される場合に限り拒否されていました。 Visual Studio 2019 では、すべての言語標準モードで、コンパイラにより **`constexpr`** 関数の定義で **`reinterpret_cast`** が正しく診断されます。 次のコードでは、C3615 が生成されるようになりました。

```cpp
long long i = 0;
constexpr void f() {
    int* a = reinterpret_cast<int*>(i); // C3615: constexpr function 'f' cannot result in a constant expression
}
```

このエラーを回避するには、関数宣言から **`constexpr`** 修飾子を削除します。

### <a name="correct-diagnostics-for-basic_string-range-constructor"></a>basic_string 範囲コンストラクターの正しい診断

Visual Studio 2019 では、`basic_string` 範囲コンストラクターで **`static_cast`** を含むコンパイラ診断が非表示になることがなくなりました。 次のコードは Visual Studio 2017 では、`out` の初期化時、データが失われ、 **`wchar_t`** が **`char`** になる可能性がありますが、警告なくコンパイルされます。

```cpp
std::wstring ws = /* . . . */;
std::string out(ws.begin(), ws.end()); // VS2019 C4244: 'argument': conversion from 'wchar_t' to 'const _Elem', possible loss of data.
```

Visual Studio 2019 では、警告 C4244 が正しく生成されます。 この計画を回避するには、この例のように `std::string` を初期化できます。

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>`/clr` または `/ZW` での `+=` や `-=` の誤った呼び出しが正しく検出されるようになった

Visual Studio 2017 では、 **`/clr`** または **`/ZW`** での **`+=`** や **`-=`** の無効な呼び出しに対して、コンパイラで何も表示されずにエラーが無視され、何のコードも生成されないというバグが発生しました。 次のコードは Visual Studio 2017 ではエラーなくコンパイルされますが、Visual Studio 2019 の場合、error C2845:

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // in VS2019 C2845: 'System::String ^': pointer arithmetic not allowed on this type.
}
```

この例のエラーを回避するには、`s += E::e.ToString();` のように、`ToString()` メソッドで **`+=`** 演算子を使用します。

### <a name="initializers-for-inline-static-data-members"></a>インライン静的データ メンバーの初期化子

**`inline`** 初期化子と **`static constexpr`** 初期化子内の無効なメンバー アクセスが、正しく検出されるようになりました。 次の例は Visual Studio 2017 ではエラーなくコンパイルされますが、 **`/std:c++17`** モードの Visual Studio 2019 では、エラー C2248 が発生します。

```cpp
struct X
{
    private:
        static inline const int c = 1000;
};

struct Y : X
{
    static inline int d = c; // VS2019 C2248: cannot access private member declared in class 'X'.
};
```

このエラーを回避するには、メンバー `X::c` を protected として宣言します。

```cpp
struct X
{
    protected:
        static inline const int c = 1000;
};
```

### <a name="c4800-reinstated"></a>C4800 の復帰

MSVC には以前、 **`bool`** への暗黙的変換に関するパフォーマンス警告 C4800 がありました。 これは煩わしく、かつ非表示にできなかったため、Visual Studio 2017 で削除されました。 しかしながら、Visual Studio 2017 が使用されている間、この警告が役に立った事例についてたくさんのフィードバックがありました。 Visual Studio 2019 では、慎重に調整された C4800 とそれに付属する C4165 を復帰させました。 いずれの警告も、簡単に非表示にできます。それには、明示的な型変換を使用するか、該当する型の 0 と比較します。 C4800 は既定でオフのレベル 4 警告であり、C4165 は既定でオフのレベル 3 警告です。 いずれも **`/Wall`** コンパイラ オプションで検出できます。

次の例では、 **`/Wall`** で C4800 と C4165 が発生します。

```cpp
bool test(IUnknown* p)
{
    bool valid = p; // warning C4800: Implicit conversion from 'IUnknown*' to bool. Possible information loss
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return hr; // warning C4165: 'HRESULT' is being converted to 'bool'; are you sure this is what you want?
}
```

前の例の警告を回避する目的で、コードを次のように記述できます。

```cpp
bool test(IUnknown* p)
{
    bool valid = p != nullptr; // OK
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return SUCCEEDED(hr);  // OK
}
```

### <a name="local-class-member-function-doesnt-have-a-body"></a>ローカル クラスのメンバー関数に本体がない

Visual Studio 2017 では、警告 C4822 は、コンパイラ オプション **`/w14822`** が明示的に設定されている場合にのみ発生します。 これは **`/Wall`** では表示されません。 Visual Studio 2019 では、C4822 は既定でオフの警告であり、 **`/w14822`** を明示的に設定しなくても **`/Wall`** で検出できるようになります。

```cpp
void example()
{
    struct A
        {
            int boo(); // warning C4822: Local class member function doesn't have a body
        };
}
```

### <a name="function-template-bodies-containing-if-constexpr-statements"></a>`if constexpr` ステートメントを含む関数テンプレートの本体

**`if constexpr`** ステートメントが含まれるテンプレート関数の本体では、一部の [`/permissive-`](../build/reference/permissive-standards-conformance.md) 解析関連チェックが有効になっています。 たとえば、Visual Studio 2017 では、次のコードで C7510 が生成されるのは **`/permissive-`** オプションが設定されていない場合のみです。 Visual Studio 2019 の場合、 **`/permissive-`** オプションが設定されていても、同じコードでエラーが発生します。

```cpp
template <typename T>

int f()
{
    T::Type a; // error C7510: 'Type': use of dependent type name must be prefixed with 'typename'

    if constexpr (T::val)
    {
        return 1;
    }
    else
    {
        return 2;
    }
}

struct X
{
    using Type = X;
    constexpr static int val = 1;
};

int main()
{
    return f<X>();
}
```

このエラーを回避するには、`typename T::Type a;` のように、 **`typename`** キーワードを `a` の宣言に追加します。

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>インライン アセンブリ コードがラムダ式でサポートされない

Microsoft C++ チームは最近、ラムダ内のインライン アセンブラーが実行時、`ebp` (リターン アドレス レジスタ) の破損につながる可能性があるセキュリティ上の問題を発見しました。 悪意のある攻撃者は、このシナリオを活用できる可能性があります。 インライン アセンブラーは x86 でのみサポートされており、インライン アセンブラーとコンパイラのその他の部分との間の相互作用は貧弱でした。 これらの事実と問題の性質を考えると、この問題の最も安全な解決策は、ラムダ式内のインライン アセンブラーを許可しないことでした。

ラムダ式内でのインライン アセンブラーの唯一の使い方として出回っていたのは、リターン アドレスをキャプチャすることを目的としたものでした。 このシナリオでは、コンパイラ固有の `_ReturnAddress()` を使用し、すべてのプラットフォームでリターン アドレスをキャプチャできます。

次のコードでは、Visual Studio 2017 15.9 と Visual Studio 2019 の両方で C7552 が発生します。

```cpp
#include <cstdio>

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;

    auto lambda = [&]
    {
        __asm {  // C7552: inline assembler is not supported in a lambda

            mov eax, x
            mov y, eax
        }
    };

    lambda();
    return y;
}
```

このエラーを回避するには、次の例のように、名前付きの関数にアセンブリ コードを移動します。

```cpp
#include <cstdio>

void g(int& x, int& y)
{
    __asm {
        mov eax, x
        mov y, eax
    }
}

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;
    auto lambda = [&]
    {
        g(x, y);
    };
    lambda();
    return y;
}

int main()
{
    std::printf("%d\n", f());
}
```

### <a name="iterator-debugging-and-stdmove_iterator"></a>反復子のデバッグと `std::move_iterator`

`std::move_iterator` のラッピングを正しく解除する目的で反復子のデバッグ機能が導入されました。 たとえば、`std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` では、`memcpy` 高速パスを作動させることができるようになりました。

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>\<xkeycheck.h> キーワード強制の修正

キーワードを置き換えるマクロに対する \<xkeycheck.h> での標準ライブラリの強制が修正されました。 ライブラリでは、汎用メッセージではなく、検出された実際の問題のキーワードが生成されるようになりました。 また、C++ 20 キーワード対応となり、IntelliSense でランダムのキーワードがマクロであるととらえられることがなくなりました。

### <a name="allocator-types-no-longer-deprecated"></a>非推奨でなくなったアロケーター型

`std::allocator<void>`、`std::allocator::size_type`、および `std::allocator::difference_type` が非推奨でなくなりました。

### <a name="correct-warning-for-narrowing-string-conversions"></a>文字列変換を絞り込むための正しい警告

標準では呼び出されず、C4244 絞り込み警告を誤って非表示にしていた不適切な **`static_cast`** が `std::string` から削除されました。 `std::string::string(const wchar_t*, const wchar_t*)` を呼び出そうとすると、`char` への `wchar_t` の縮小に関する C4244 が正しく生成されるようになりました。

### <a name="various-fixes-for-filesystem-correctness"></a>\<filesystem> の正確性に関するさまざまな修正

- ディレクトリの最後の書き込み時刻を変更しようとすると失敗する `std::filesystem::last_write_time` が修正されました。
- `std::filesystem::directory_entry` コンストラクターには、存在しないターゲット パスが指定されたとき、例外をスローせず、エラー結果が格納されるようになりました。
- `existing_p` がシンボリック リンクのとき、基礎となる `CreateDirectoryExW` 関数で `copy_symlink` が使用されるため、`std::filesystem::create_directory` の 2 パラメーター バージョンが 1 パラメーター バージョンを呼び出すように変更されました。
- 壊れたシンボリック リンクが見つかっても `std::filesystem::directory_iterator` ではエラーを出さなくなりました。
- `std::filesystem::space` で相対パスを受け取るようになりました。
- [LWG 3096](https://cplusplus.github.io/LWG/issue3096) で報告されていた末尾のスラッシュと `std::filesystem::path::lexically_relative` が混同されることがなくなりました。
- `std::filesystem::create_symlink` にスラッシュを含むパスを拒否する `CreateSymbolicLinkW` の回避策が考案されました。
- Windows 10 LTSB 1609 に存在していたが、実際にはファイルを削除できなかった POSIX 削除モード `delete` 関数の回避策が考案されました。
- `std::boyer_moore_searcher` と `std::boyer_moore_horspool_searcher` のコピー コンストラクターとコピー代入演算子で、実際にコピーできるようになりました。

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Windows 8 以降の並列アルゴリズム

並列アルゴリズム ライブラリでは、Windows 7 以前のフェイク バージョンを常時使用せず、Windows 8 以降の実際の `WaitOnAddress` ファミリが正しく使用されるようになりました。

### <a name="stdsystem_categorymessage-whitespace"></a>`std::system_category::message()` のスペース

`std::system_category::message()` では、返されたメッセージから末尾のスペースが削除されるようになりました。

### <a name="stdlinear_congruential_engine-divide-by-zero"></a>`std::linear_congruential_engine` のゼロ除算

`std::linear_congruential_engine` のゼロ除算を誘発していたいくつかの条件が修正されました。

### <a name="fixes-for-iterator-unwrapping"></a>反復子ラッピング解除の修正

一部の反復子ラッピング解除機構は、プログラマとユーザーの統合を目的として、Visual Studio 2017 15.8 で最初に公開されました。 これについては、C++ チームのブログ記事「[VS 2017 15.8 での STL の機能と修正](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/)」で説明されていました。 この機構では、標準ライブラリ反復子から派生する反復子のラッピングが解除されなくなりました。 たとえば、`std::vector<int>::iterator` から派生し、動作をカスタマイズしようとするユーザーには、標準ライブラリ アルゴリズムを呼び出すとき、ポインターの動作ではなく、カスタマイズされた動作が与えられるようになりました。

順序付けられていないコンテナー `reserve` 関数は、[LWG 2156](https://cplusplus.github.io/LWG/issue2156) に説明があるように、N 要素に予約されるようになりました。

### <a name="time-handling"></a>時間の処理

- 以前は、`condition_variable::wait_for(seconds::max())` など、同時実行ライブラリに渡されていた一部の時間値がオーバーフローしていました。 このようなオーバーフローが解消され、うわべではランダムの 29 日周期で動作が変わりました (基礎となる Win32 API で受け取られる uint32_t ミリ秒がオーバーフローしたとき)。

- \<ctime> ヘッダーでは、`timespec` と `timespec_get` が名前空間 `std` で正しく宣言されるようになり、グローバル名前空間でも宣言されています。

### <a name="various-fixes-for-containers"></a>コンテナーのさまざまな修正

- 標準ライブラリのさまざまな内部コンテナー関数が `private` になり、IntelliSense が使いやすくなりました。 MSVC の今後のリリースでは、メンバーを `private` にする修正が追加される予定です。

- `list`、`map`、`unordered_map` のようなノードベース コンテナーが破損する原因となっていた、例外の安全性における正確性の問題が修正されました。 `propagate_on_container_copy_assignment` または `propagate_on_container_move_assignment` の再代入演算の間、古いアロケーターを持つコンテナーのセンチネル ノードを解放し、古いアロケーターで POCCA/POCMA 代入を行い、新しいアロケーターからセンチネル ノードの取得を試みました。 この割り当てが失敗した場合、コンテナーは破損しました。 センチネル ノードを持つとハード データ構造不変であるため、破棄さえできなくなります。 このコードは、既存のセンチネル ノードを破棄する前に、ソース コンテナーのアロケーターを使用して新しいセンチネル ノードを作成するように修正されました。

- `is_always_equal` が宣言されたアロケーターの場合でも、常に `propagate_on_container_copy_assignment`、`propagate_on_container_move_assignment`、`propagate_on_container_swap` に基づいてアロケーターをコピー、移動、スワップするようにコンテナーが修正されました。

- rvalue コンテナーを受け取るコンテナー結合関数およびメンバー抽出関数に対してオーバーロードが追加されました 詳細については、[P0083 「マップと設定のスプライス」](https://wg21.link/p0083r3)を参照してください

### <a name="stdbasic_istreamread-processing-of-rn-n"></a>`std::basic_istream::read` での `\r\n`` =>`\n` の処理

`\r\n` から `\n` への処理の一環として、与えられたバッファーの一部を一時的に書き込まないよう、`std::basic_istream::read` が修正されました。 この変更により、Visual Studio 2017 15.8 において 4K を超える読み込みで得られるパフォーマンス上のいくつかの長所を放棄することになります。 ただし、文字ごとに 3 つの仮想呼び出しを回避することから得られる効率性の改善が残されています。

### <a name="stdbitset-constructor"></a>`std::bitset` コンストラクター

`std::bitset` のコンストラクターで、大きなビットセットの 1 と 0 が逆の順序で読み取られることがなくなりました。

### <a name="stdpairoperator-regression"></a>`std::pair::operator=` 回帰

[LWG 2729 "Missing SFINAE on `std::pair::operator=`";](https://cplusplus.github.io/LWG/issue2729) の実装時に見つかった `std::pair` 代入演算子の回帰が修正されました。 再び `std::pair` に変換できる型を正しく受け取るようになりました。

### <a name="non-deduced-contexts-for-add_const_t"></a>`add_const_t` の非推定コンテキスト

`add_const_t` や関連関数が非推定コンテキストであることが求められる、型の特徴の軽微なバグが修正されました。 言い換えると、`add_const_t` は `const T` ではなく、`typename add_const<T>::type` のエイリアスにする必要があります。

## <a name="conformance-improvements-in-161"></a><a name="improvements_161"></a> 16.1 の準拠の強化

### <a name="char8_t"></a>char8_t

[P0482r6](https://wg21.link/p0482r6)。 C++20 では、UTF-8 コード単位を表すための新しい文字型が追加されます。 C++20 の `u8` 文字列リテラルには、以前の `const char[N]` に代わり、型 `const char8_t[N]` が与えられます。 [N2231](https://wg14.link/n2231) では、C 標準に同様の変更が提案されています。 **`char8_t`** 下位互換性改善の提案が [P1423r3](https://wg21.link/p1423r3) に記載されています。 **`/Zc:char8_t`** コンパイラ オプションを指定すると、Microsoft C++ コンパイラでは、Visual Studio 2019 バージョン 16.1 の **`char8_t`** のサポートが追加されます。 将来的にこれは [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) でサポートされます。これは、 **`/Zc:char8_t-`** 経由で C++17 の動作に戻すことができます。 IntelliSense に機能を提供する EDG コンパイラでは、それはまだサポートされていません。 IntelliSense のみの誤ったエラーが表示される場合がありますが、実際のコンパイルには影響ありません。

#### <a name="example"></a>例

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtype_identity-metafunction-and-stdidentity-function-object"></a>`std::type_identity` メタ関数と `std::identity` 関数オブジェクト

[P0887R1 type_identity](https://wg21.link/p0887r1). 非推奨 `std::identity` クラス テンプレート拡張が削除され、C++20 `std::type_identity` メタ関数と `std::identity` 関数オブジェクトに置換されました。 いずれも [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) でのみ利用できます。

次の例では、Visual Studio 2017 の `std::identity` (\<type_traits> で定義) に対して非推奨警告 C4996 が生成されます。

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

次の例では、新しい `std::type_identity` と共に新しい `std::identity` (\<functional> で定義) を使用する方法を確認できます。

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>汎用ラムダの構文チェック

新しいラムダ プロセッサにより、[`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) で、または **`/experimental:newLambdaProcessor`** を使用する他のに似の言語モードで、汎用ラムダの一部の準拠モード構文チェックが有効になります。

Visual Studio 2017 の場合、このコードは警告なくコンパイルされますが、Visual Studio 2019 ではエラー C2760 が発生します。

```cpp
void f() {
    auto a = [](auto arg) {
        decltype(arg)::Type t; // C2760 syntax error: unexpected token 'identifier', expected ';'
    };
}
```

次の例では、コンパイラから強制されるようになった正しい構文を確認できます。

```cpp
void f() {
    auto a = [](auto arg) {
        typename decltype(arg)::Type t;
    };
}
```

### <a name="argument-dependent-lookup-for-function-calls"></a>関数呼び出しの引数依存検索

[P0846R0](https://wg21.link/p0846r0) (C++20) 明示的なテンプレート引数を含む関数呼び出し式の引数依存照合を使用する、関数テンプレートの検索機能が強化されました。 **`/std:c++latest`** が必要です。

### <a name="designated-initialization"></a>初期化の指定

[P0329R4](https://wg21.link/p0329r4) (C++20) "*初期化の指定*" により、集計初期化で `Type t { .member = expr }` 構文を使用して、特定のメンバーを選択できます。 **`/std:c++latest`** が必要です。

### <a name="new-and-updated-standard-library-functions-c20"></a>新規および更新された標準ライブラリ関数 (C++20)

- `basic_string` と `basic_string_view` 向けの `starts_with()` と `ends_with()`。
- 連想コンテナーの `contains()`。
- `list` と `forward_list` の `remove()`、`remove_if()`、および `unique()` で `size_type` が返されるようになりました。
- `shift_left()` および `shift_right()` が \<algorithm> に追加されました。

## <a name="conformance-improvements-in-162"></a><a name="improvements_162"></a> 16.2 の準拠の強化

### <a name="noexcept-constexpr-functions"></a>`noexcept` `constexpr` 関数

定数式で使用する場合、 **`constexpr`** 関数は既定では **`noexcept`** と見なされなくなりました。 この動作変更は、Core Working Group (CWG) [1351](https://wg21.link/cwg1351) の解決によるものであり、[`/permissive-`](../build/reference/permissive-standards-conformance.md) で有効になります。 次の例は、Visual Studio 2019 バージョン 16.1 以前ではコンパイルされますが、Visual Studio 2019 バージョン 16.2 では C2338 が生成されます。

```cpp
constexpr int f() { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept"); // C2338 in 16.2
}
```

このエラーを修正するには、 **`noexcept`** 式を関数宣言に追加します。

```cpp
constexpr int f() noexcept { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept");
}
```

### <a name="binary-expressions-with-different-enum-types"></a>異なる列挙型を持つバイナリ式

C++ 20 では、次の両方が当てはまる場合、オペランドでの通常の算術変換は非推奨になりました。

- 1 つのオペランドは列挙型である。

- もう 1 つは、別の列挙型または浮動小数点型である。

詳細については、[P1120R0](https://wg21.link/p1120r0) を参照してください。

Visual Studio 2019 バージョン 16.2 以降では、[`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) コンパイラ オプションが有効になっていると、次のコードでレベル 4 の警告が生成されます。

```cpp
enum E1 { a };
enum E2 { b };
int main() {
    int i = a | b; // warning C5054: operator '|': deprecated between enumerations of different types
}
```

この警告を回避するには、[`static_cast`](../cpp/static-cast-operator.md) を使用して 2 番目のオペランドを変換します。

```cpp
enum E1 { a };
enum E2 { b };
int main() {
  int i = a | static_cast<int>(b);
}
```

列挙型と浮動小数点型の間で二項演算を使用すると、[`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) コンパイラ オプションが有効になっているときに警告が発生するようになりました。

```cpp
enum E1 { a };
int main() {
  double i = a * 1.1;
}
```

この警告を回避するには、[`static_cast`](../cpp/static-cast-operator.md) を使用して 2 番目のオペランドを変換します。

```cpp
enum E1 { a };
int main() {
   double i = static_cast<int>(a) * 1.1;
}
```

### <a name="equality-and-relational-comparisons-of-arrays"></a>配列の等価比較と関係比較

C++20 ([P1120R0](https://wg21.link/p1120r0)) では、配列型の 2 つのオペランドの等価比較と関係比較は非推奨とされます。 言い換えると、2 つの配列間の比較演算を使用すると (ランクと範囲の類似性に関係なく) 警告が発生するようになりました。 Visual Studio 2019 バージョン 16.2 以降では、[`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) コンパイラ オプションが有効になっている場合、次のコードでは C5056 が生成されます。

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (a == b) { return 1; } // warning C5056: operator '==': deprecated for array types
}
```

この警告を回避するには、最初の要素のアドレスを比較します。

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (&a[0] == &b[0]) { return 1; }
}
```

2 つの配列の内容が等しいかどうかを判断するには、[`std::equal`](../standard-library/algorithm-functions.md#equal) 関数を使用します。

```cpp
std::equal(std::begin(a), std::end(a), std::begin(b), std::end(b));
```

### <a name="effect-of-defining-spaceship-operator-on--and-"></a>`==` と `!=` で宇宙船演算子を定義した場合の効果

宇宙船演算子 ( **`<=>`** ) のみを定義しても、宇宙船演算子が **`= default`** ([P1185R2](https://wg21.link/p1185r2)) とマークされていなければ、 **`==`** または **`!=`** を伴う式は書き換えられなくなります。 次の例は、Visual Studio 2019 RTW およびバージョン 16.1 ではコンパイルされますが、Visual Studio 2019 バージョン 16.2 では C2678 が生成されます。

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs; // error C2676
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs; // error C2676
}
```

このエラーを回避するには、`operator==` を定義するか、これを既定値として宣言します。

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
  bool operator==(const S&) const = default;
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

### <a name="standard-library-improvements"></a>標準ライブラリの機能強化

- \<charconv> `to_chars()` (固定/科学的表記)。 (16.4 では一般的表記が計画されています。)
- [P0020R6](https://wg21.link/p0020r6): `atomic<float>`、`atomic<double>`、`atomic<long double>`
- [P0463R1](https://wg21.link/p0463r1): エンディアン
- [P0482R6](https://wg21.link/p0482r6): `char8_t` のライブラリ サポート
- [P0600R1](https://wg21.link/p0600r1): `[[nodiscard]]` (STL、Part 1)
- [P0653R2](https://wg21.link/p0653r2): `to_address()`
- [P0754R2](https://wg21.link/p0754r2): \<version>
- [P0771R1](https://wg21.link/p0771r1): `std::function` の移動コンストラクター用の `noexcept`

### <a name="const-comparators-for-associative-containers"></a>連想コンテナーの const 比較子

[`set`](../standard-library/set-class.md)、[`map`](../standard-library/map-class.md)、[`multiset`](../standard-library/multiset-class.md)、[`multimap`](../standard-library/multimap-class.md) の検索と挿入のコードは、コード サイズの削減のためにマージされました。 検索操作で以前に実行されたのと同じように、挿入操作によって **`const`** 比較ファンクターで小なり比較が呼び出されるようになりました。 次のコードは、Visual Studio 2019 バージョン 16.1 以前ではコンパイルされますが、Visual Studio 2019 バージョン 16.2 では C3848 が生成されます。

```cpp
#include <iostream>
#include <map>

using namespace std;

struct K
{
   int a;
   string b = "label";
};

struct Comparer  {
   bool operator() (K a, K b) {
      return a.a < b.a;
   }
};

map<K, double, Comparer> m;

K const s1{1};
K const s2{2};
K const s3{3};

int main() {

   m.emplace(s1, 1.08);
   m.emplace(s2, 3.14);
   m.emplace(s3, 5.21);

}
```

このエラーを回避するには、次のように比較演算子 **`const`** を使用します。

```cpp
struct Comparer  {
   bool operator() (K a, K b) const {
      return a.a < b.a;
   }
};

```

## <a name="conformance-improvements-in-visual-studio-2019-version-163"></a><a name="improvements_163"></a> Visual Studio 2019 バージョン 16.3 の準拠の強化

### <a name="stream-extraction-operators-for-char-removed"></a>`char*` のストリーム抽出演算子が削除されました

ポインターから文字へのストリーム抽出演算子が削除され、文字配列の抽出演算子に置き換えられました ([P0487R1](https://wg21.link/p0487r1) による)。 WG21 では、削除されたオーバーロードは安全でないと見なされます。 [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) モードでは、次の例で C2679 が生成されるようになりました。

```cpp
// stream_extraction.cpp
// compile by using: cl /std:c++latest stream_extraction.cpp

#include <iostream>
#include <iomanip>

int main() {
    char x[42];
    char* p = x;
    std::cin >> std::setw(42);
    std::cin >> p;  // C2679: binary '>>': no operator found which takes a right-hand operand of type 'char *' (or there is no acceptable conversion)
}
```

このエラーを回避するには、抽出演算子を `char[]` 変数と共に使用します。

```cpp
#include <iostream>
#include <iomanip>

int main() {
    char x[42];
    std::cin >> std::setw(42);
    std::cin >> x;  // OK
}
```

### <a name="new-keywords-requires-and-concept"></a>新しいキーワード `requires` と `concept`

Microsoft C++ コンパイラに新しいキーワード **`requires`** と **`concept`** が追加されました。 [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) モードでそのいずれかを識別子として使用しようとすると、コンパイラで C2059: "構文エラー" が発生します。

### <a name="constructors-as-type-names-disallowed"></a>型名としてのコンストラクターが許可されない

コンストラクター名は、クラス テンプレート特殊化のエイリアスの後に修飾名で表示される場合、コンパイラでは挿入されたクラス名と見なされなくなりました。 これまでは、他のエンティティを宣言するための型名として、コンストラクターを使用できました。 次の例では、C3646:

```cpp
#include <chrono>

class Foo {
   std::chrono::milliseconds::duration TotalDuration{}; // C3646: 'TotalDuration': unknown override specifier
};
```

このエラーを回避するには、次に示すように `TotalDuration` を宣言します。

```cpp
#include <chrono>

class Foo {
  std::chrono::milliseconds TotalDuration {};
};
```

### <a name="stricter-checking-of-extern-c-functions"></a>`extern "C"` 関数のより厳密なチェック

異なる名前空間で **`extern "C"`** 関数が宣言されている場合、以前のバージョンの Microsoft C++ コンパイラでは、宣言に互換性があるかどうかがチェックされませんでした。 Visual Studio 2019 バージョン 16.3 以降では、コンパイラによって互換性がチェックされます。 [`/permissive-`](../build/reference/permissive-standards-conformance.md) モードでは、次のコードによってエラー C2371 と C2733 が生成されます。

```cpp
using BOOL = int;

namespace N
{
   extern "C" void f(int, int, int, bool);
}

void g()
{
   N::f(0, 1, 2, false);
}

extern "C" void f(int, int, int, BOOL){}
    // C2116: 'N::f': function parameter lists do not match between declarations
    // C2733: 'f': you cannot overload a function with 'extern "C"' linkage
```

前の例のエラーを回避するには、`f` の両方の宣言で `BOOL` ではなく **`bool`** を一貫して使用します。

### <a name="standard-library-improvements"></a>標準ライブラリの機能強化

非標準ヘッダーの \<stdexcpt.h> と \<typeinfo.h> が削除されました。 これらが含まれるコードには、代わりに標準ヘッダー \<exception> と \<typeinfo> をそれぞれ含める必要があります。

## <a name="conformance-improvements-in-visual-studio-2019-version-164"></a><a name="improvements_164"></a> Visual Studio 2019 バージョン 16.4 の準拠の強化

### <a name="better-enforcement-of-two-phase-name-lookup-for-qualified-ids-in-permissive-"></a>`/permissive-` での修飾 ID に対する 2 フェーズの名前参照の適用の強化

2 フェーズの名前参照では、テンプレートの本文で使用される非依存名が定義時にテンプレートに表示されている必要があります。 以前は、テンプレートがインスタンス化されるときにそのような名前が検索される場合がありました。 この変更により、[`/permissive-`](../build/reference/permissive-standards-conformance.md) フラグを使用した MSVC で、移植性が高く準拠したコードを記述しやすくなります。

Visual Studio 2019 バージョン 16.4 で **`/permissive-`** フラグが設定されている場合、次の例ではエラーが発生します。`f<T>` のテンプレートを定義するときに、`N::f` を参照できないためです。

```cpp
template <class T>
int f() {
    return N::f() + T{}; // error C2039: 'f': is not a member of 'N'
}

namespace N {
    int f() { return 42; }
}
```

通常、このエラーは、次の例に示すように、不足しているヘッダーを追加するか、関数または変数を前方宣言することで修正できます。

```cpp
namespace N {
    int f();
}

template <class T>
int f() {
    return N::f() + T{};
}

namespace N {
    int f() { return 42; }
}
```

### <a name="implicit-conversion-of-integral-constant-expressions-to-null-pointer"></a>整数定数式から Null ポインターへの暗黙的な変換

MSVC コンパイラの準拠モード ( **`/permissive-`** ) において、[CWG イシュー 903](https://wg21.link/cwg903) が実装されるようになりました。 このルールにより、整数定数式 (整数リテラル '0' を除く) を Null ポインター定数に暗黙的に変換することが許可されなくなります。 次の例では、準拠モードで C2440 が生成されます。

```cpp
int* f(bool* p) {
    p = false; // error C2440: '=': cannot convert from 'bool' to 'bool *'
    p = 0; // OK
    return false; // error C2440: 'return': cannot convert from 'bool' to 'int *'
}
```

エラーを解決するには、 **`false`** ではなく **`nullptr`** を使用します。 リテラル 0 は引き続き許可されます。

```cpp
int* f(bool* p) {
    p = nullptr; // OK
    p = 0; // OK
    return nullptr; // OK
}
```

### <a name="standard-rules-for-types-of-integer-literals"></a>整数リテラルの型に関する標準ルール

MSVC の準拠モード ([`/permissive-`](../build/reference/permissive-standards-conformance.md) で有効) では、整数リテラルの型に対して標準ルールが使用されます。 以前は、大きすぎて **`signed int`** に収まらない 10 進リテラルは **`unsigned int`** 型になりました。 そのようなリテラルは、2 番目に大きな **`signed`** 整数型である **`long long`** になるようになりました。 また、'll' というサフィックスが付いたリテラルで、大きすぎて **`signed`** 型に収まらないものは、 **`unsigned long long`** 型になります。

この変更により、異なる警告の診断が生成され、リテラルに対する算術演算で異なる動作が発生する可能性があります。

次の例は、Visual Studio 2019 バージョン 16.4 での新しい動作を示しています。 `i` 変数は **`unsigned int`** 型になります。 これが原因で、警告が発生します。 変数 `j` の上位ビットは 0 に設定されます。

```cpp
void f(int r) {
    int i = 2964557531; // warning C4309: truncation of constant value
    long long j = 0x8000000000000000ll >> r; // literal is now unsigned, shift will fill high-order bits with 0
}
```

次の例は、以前の動作を維持し、警告と実行時の動作の変更を回避する方法を示しています。

```cpp
void f(int r) {
int i = 2964557531u; // OK
long long j = (long long)0x8000000000000000ll >> r; // shift will keep high-order bits
}
```

### <a name="function-parameters-that-shadow-template-parameters"></a>テンプレート パラメーターをシャドウする関数パラメーター

MSVC コンパイラでは、関数パラメーターによってテンプレート パラメーターがシャドウされるとエラーが発生するようになりました。

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T(&buffer)[Size], int& Size) // error C7576: declaration of 'Size' shadows a template parameter
{
    return f(buffer, Size, Size);
}
```

このエラーを修正するには、いずれかのパラメーターの名前を変更します。

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T (&buffer)[Size], int& size_read)
{
    return f(buffer, Size, size_read);
}
```

### <a name="user-provided-specializations-of-type-traits"></a>型特性のユーザー指定の特殊化

MSVC コンパイラでは、標準の *meta.rqmts* サブ句に準拠して、`std` 名前空間で指定された `type_traits` テンプレートのいずれかに対するユーザー定義の特殊化が検出されると、エラーが発生するようになりました。 特に指定しない限り、このような特殊化によって未定義の動作が発生します。 次の例はこのルールに違反しているため、未定義の動作が発生します。また、 **`static_assert`** はエラー C2338 によって失敗します。

```cpp
#include <type_traits>
struct S;

template<>
struct std::is_fundamental<S> : std::true_type {};

static_assert(std::is_fundamental<S>::value, "fail");
```

このエラーを回避するには、優先する `type_trait` から継承する構造体を定義し、それを特殊化します。

```cpp
#include <type_traits>

struct S;

template<typename T>
struct my_is_fundamental : std::is_fundamental<T> {};

template<>
struct my_is_fundamental<S> : std::true_type { };

static_assert(my_is_fundamental<S>::value, "fail");
```

### <a name="changes-to-compiler-provided-comparison-operators"></a>コンパイラによって提供される比較演算子の変更点

MSVC コンパイラでは、[`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) オプションが有効になっている場合に、[P1630R1](https://wg21.link/p1630r1) によって比較演算子に対する次の変更点が実装されるようになりました。

式で **`bool`** ではない戻り値の型が含まれる場合、その式がコンパイラによって `operator==` を利用して書き換えられることがなくなりました。 次のコードでは、エラー C2088 が生成されるようになりました。

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;  // C2088: '!=': illegal for struct
}
```

このエラーを回避するには、必要な演算子を明示的に定義する必要があります。

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
    U operator!=(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

既定化された比較演算子が union-like クラスのメンバーである場合、それがコンパイラによって定義されることはなくなりました。 次の例では、エラー C2120 が生成されるようになりました。

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const = default;
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

このエラーを回避するには、演算子の本体を定義します。

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const { ... }
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

クラスに参照メンバーが含まれている場合、既定化された比較演算子がコンパイラによって定義されることはなくなりました。 次のコードでは、エラー C2120 が生成されるようになりました。

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const = default;
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

このエラーを回避するには、演算子の本体を定義します。

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const { ... };
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

## <a name="conformance-improvements-in-visual-studio-2019-version-165"></a><a name="improvements_165"></a> Visual Studio 2019 バージョン 16.5 の準拠の強化

### <a name="explicit-specialization-declaration-without-an-initializer-isnt-a-definition"></a>初期化子のない明示的な特殊化の宣言は定義ではない

`/permissive-` の下では、初期化子のない明示的な特殊化は定義ではないという標準規則が MSVC で適用されるようになりました。 以前は、宣言は既定の初期化子による定義と見なされることがありました。 その効果はリンク時に観察できます。このビヘイビアーに依存するプログラムには、未解決のシンボルを与えることができるようになったためです。 この例ではエラーが出るようになります。

```cpp
template <typename> struct S {
    static int a;
};

// In permissive-, this declaration isn't a definition, and the program won't link.
template <> int S<char>::a;

int main() {
    return S<char>::a;
}
```

```Output
error LNK2019: unresolved external symbol "public: static int S<char>::a" (?a@?$S@D@@2HA) referenced in function _main at link time.
```

この問題を解決するには、初期化子を追加します。

```cpp
template <typename> struct S {
    static int a;
};

// Add an initializer for the declaration to be a definition.
template <> int S<char>::a{};

int main() {
    return S<char>::a;
}
```

### <a name="preprocessor-output-preserves-newlines"></a>プリプロセッサ出力によって改行が維持される

実験用のプリプロセッサでは、 **`/experimental:preprocessor`** と共に **`/P`** または **`/E`** を使用するとき、改行と空白が維持されるようになりました。

このようなサンプル ソースがあります。

```cpp
#define m()
line m(
) line
```

**`/E`** の以前の出力は次のようになっていました。

```Output
line line
#line 2
```

**`/E`** の新しい出力は次のようになります。

```Output
line
 line
```

### <a name="import-and-module-keywords-are-context-dependent"></a>`import` と `module` キーワードがコンテキスト依存になる

[P1857R1](https://wg21.link/P1857R1) に基づき、`import` および `module` プリプロセッサ ディレクティブの構文に制約が追加されました。 次の例はコンパイルされなくなります。

```cpp
import // Invalid
m;     // error C2146: syntax error: missing ';' before identifier 'm'
```

この問題を解決するには、同じ行でインポートを続けます。

```cpp
import m; // OK
```

### <a name="removal-of-stdweak_equality-and-stdstrong_equality"></a>`std::weak_equality` と `std::strong_equality` の削除

[P1959R0](https://wg21.link/P1959R0) を結合するには、ビヘイビアーと、`std::weak_equality` 型と `std::strong_equality` 型の参照を削除することがコンパイラに求められます。

この例のコードはコンパイルされなくなります。

```cpp
#include <compare>

struct S {
    std::strong_equality operator<=>(const S&) const = default;
};

void f() {
    nullptr<=>nullptr;
    &f <=> &f;
    &S::operator<=> <=> &S::operator<=>;
}
```

この例では次のようなエラーが発生します。

```Output
error C2039: 'strong_equality': is not a member of 'std'
error C2143: syntax error: missing ';' before '<=>'
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C7546: binary operator '<=>': unsupported operand types 'nullptr' and 'nullptr'
error C7546: binary operator '<=>': unsupported operand types 'void (__cdecl *)(void)' and 'void (__cdecl *)(void)'
error C7546: binary operator '<=>': unsupported operand types 'int (__thiscall S::* )(const S &) const' and 'int (__thiscall S::* )(const S &) const'
```

この問題を解決するには、組み込み関係演算子を優先し、削除された型を置換するように更新します。

```cpp
#include <compare>

struct S {
    std::strong_ordering operator<=>(const S&) const = default; // prefer 'std::strong_ordering'
};

void f() {
    nullptr != nullptr; // use pre-existing builtin operator != or ==.
    &f != &f;
    &S::operator<=> != &S::operator<=>;
}
```

### <a name="tls-guard-changes"></a>TLS ガードの変更

以前は、DLL のスレッドローカル変数が正しく初期化されていませんでした。 DLL を読み込んだスレッド以外では、DLL が読み込まれる前に存在したスレッドで最初に使用されるまで、正しく初期化されませんでした。 この欠陥が修正されました。 このような DLL のスレッドローカル変数は、そのようなスレッドで最初に使用される直前に初期化されます。

スレッドローカル変数の使用時に初期化するためのこの新しいテスト ビヘイビアーは、 **`/Zc:tlsGuards-`** コンパイラ スイッチを使用して無効にできます。 あるいは、特定のスレッドローカル変数に `[[msvc:no_tls_guard]]` 属性を追加するという方法もあります。

### <a name="better-diagnosis-of-call-to-deleted-functions"></a>削除された関数の呼び出しの診断機能向上

以前は、削除された関数の呼び出しについては、コンパイラにあまり制限がありませんでした。 たとえば、テンプレートの本文に関して呼び出しがあっても、呼び出しが診断されることはなかったでしょう。 また、削除された関数が複数回呼び出された場合、診断を 1 回だけ発行したでしょう。 これからは呼び出しごとに診断が発行されます。

新しいビヘイビアーの結果として、小規模の破壊的変更が行われる可能性があります。削除された関数を呼び出したコードは、コード生成に不要であった場合、診断されることはなかったでしょう。 それがあらかじめ診断されるようになりました。

この例のコードからはエラーが生成されるようになりました。

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s{};
};

U u{ 0 };
```

```Output
error C2280: 'S::S(void)': attempting to reference a deleted function
note: see declaration of 'S::S'
note: 'S::S(void)': function was explicitly deleted
```

この問題を解決するには、削除された関数の呼び出しを削除します。

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s;  // Do not call the deleted ctor of 'S'.
};

U u{ 0 };
```

## <a name="conformance-improvements-in-visual-studio-2019-version-166"></a><a name="improvements_166"></a> Visual Studio 2019 バージョン 16.6 の準拠の強化

### <a name="standard-library-streams-reject-insertions-of-mis-encoded-character-types"></a>標準ライブラリのストリームで不適切にエンコードされた文字型の挿入が拒否される

従来、 **`wchar_t`** を `std::ostream` に挿入したり、 **`char16_t`** または **`char32_t`** を `std::ostream` または `std::wostream` に挿入したりすると、その整数値が出力されます。 これらの文字型にポインターを挿入すると、ポインター値が出力されます。 どちらのケースも、プログラマにとって直感的ではありません。 多くの場合は、代わりに標準ライブラリによって文字または null で終わる文字列がトランスコードされ、その結果が出力されることが期待されます。

C++20 の提案 [P1423R3](https://wg21.link/p1423r3) では、このようなストリームと文字または文字のポインター型の組み合わせに対して、削除されたストリーム挿入演算子のオーバーロードが追加されます。 **`/std:c++latest`** では、予期しない方法で動作するのではなく、オーバーロードによってこれらの挿入が不適切な形式となります。 これが検出されると、コンパイラでエラー C2280 が発生します。 "脱出ハッチ" マクロ `_HAS_STREAM_INSERTION_OPERATORS_DELETED_IN_CXX20` を `1` に定義して、以前の動作を復元することができます。 (提案では、 **`char8_t`** のストリーム挿入演算子も削除されます。 標準ライブラリでは **`char8_t`** のサポートを追加したときに同様のオーバーロードが実装されているため、 **`char8_t`** に対して "間違った" 動作を使用できることはありません。)

次のサンプルでは、この変更を含む動作が示されます。

```cpp
#include <iostream>
int main() {
    const wchar_t cw = L'x', *pw = L"meow";
    const char16_t c16 = u'x', *p16 = u"meow";
    const char32_t c32 = U'x', *p32 = U"meow";
    std::cout << cw << ' ' << pw << '\n';
    std::cout << c16 << ' ' << p16 << '\n';
    std::cout << c32 << ' ' << p32 << '\n';
    std::wcout << c16 << ' ' << p16 << '\n';
    std::wcout << c32 << ' ' << p32 << '\n';
}
```

このコードでは、次の診断メッセージが生成されるようになりました。

```Output
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,wchar_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,char16_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,char32_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::<<<std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char16_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::<<<std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char32_t)': attempting to reference a deleted function
```

文字型を **`unsigned int`** に変更するか、文字へのポインター型から `const void*` に変換することで、すべての言語モードで以前の動作の効果を実現できます。

```c++
#include <iostream>
int main() {
    const wchar_t cw = L'x', *pw = L"meow";
    const char16_t c16 = u'x', *p16 = u"meow";
    const char32_t c32 = U'x', *p32 = U"meow";
    std::cout << (unsigned)cw << ' ' << (const void*)pw << '\n'; // Outputs "120 0052B1C0"
    std::cout << (unsigned)c16 << ' ' << (const void*)p16 << '\n'; // Outputs "120 0052B1CC"
    std::cout << (unsigned)c32 << ' ' << (const void*)p32 << '\n'; // Outputs "120 0052B1D8"
    std::wcout << (unsigned)c16 << ' ' << (const void*)p16 << '\n'; // Outputs "120 0052B1CC"
    std::wcout << (unsigned)c32 << ' ' << (const void*)p32 << '\n'; // Outputs "120 0052B1D8"
}
```

### <a name="changed-return-type-of-stdpow-for-stdcomplex"></a>`std::complex` に対する `std::pow()` の戻り値の型の変更

以前は、関数テンプレート `std::pow()` の戻り値の型に対する昇格規則の MSVC 実装は正しくありませんでした。 たとえば、以前は `pow(complex<float>, int)` によって `complex<float>` が返されました。 現在は、`complex<double>` が正しく返されるようになりました。 この修正プログラムは、Visual Studio 2019 バージョン 16.6 のすべての標準モードで無条件に実装されています。

この変更によって、コンパイラ エラーが発生する可能性があります。 たとえば、以前は `pow(complex<float>, int)` を **`float`** で乗算することができました。 `complex<T> operator*` では同じ型の引数が想定されるため、次の例ではコンパイラ エラー C2676 が発生するようになりました。

```cpp
// pow_error.cpp
// compile by using: cl /EHsc /nologo /W4 pow_error.cpp
#include <complex>

int main() {
    std::complex<float> cf(2.0f, 0.0f);
    (void) (std::pow(cf, -1) * 3.0f);
}
```

```Output
pow_error.cpp(7): error C2676: binary '*': 'std::complex<double>' does not define this operator or a conversion to a type acceptable to the predefined operator
```

さまざまな修正が考えられます。

- **`float`** 被乗数の型を **`double`** に変更する。 この引数は、`pow` から返される型と一致するように `complex<double>` に直接変換できます。

- `complex<float>{pow(ARG, ARG)}` と記述することで `pow` の結果を `complex<float>` に絞り込む。 これにより、引き続き **`float`** 値で乗算できます。

- **`int`** の代わりに **`float`** を `pow` に渡す。 この操作は速度が低下する可能性があります。

- 場合によっては、`pow` を完全に回避できます。 たとえば、`pow(cf, -1)` を除算に置き換えることができます。

### <a name="switch-related-warnings-for-c"></a>C の switch 関連の警告

Visual Studio 2019 バージョン 16.6 以降では、C としてコンパイルされたコードに対する既存の C++ の警告がいくつかコンパイラに実装されています。次の警告がさまざまなレベルで有効になりました:C4060、C4061、C4062、C4063、C4064、C4065、C4808、および C4809。 C では、警告 C4065 と C4060 は既定で無効になっています。

この警告は、 **`case`** ステートメントの不足、未定義の **`enum`** 、不適切な **`bool`** の switch (つまり、含むケースが多すぎるもの) に対してトリガーされます。 次に例を示します。

```c
#include <stdbool.h>

int main() {
    bool b = true;
    switch (b) {
        case true: break;
        case false: break;
        default: break; // C4809: switch statement has redundant 'default' label;
                        // all possible 'case' labels are given
    }
}
```

このコードを修正するには、冗長な **`default`** ケースを削除します。

```c
#include <stdbool.h>

int main() {
    bool b = true;
    switch (b) {
        case true: break;
        case false: break;
    }
}
```

### <a name="unnamed-classes-in-typedef-declarations"></a>`typedef` 宣言内の名前のないクラス

Visual Studio 2019 バージョン 16.6 以降では、 **`typedef`** 宣言の動作が [P1766R1](https://wg21.link/P1766R1) に準拠するように制限されています。 この更新により、 **`typedef`** 宣言内の名前のないクラスは、次を除くメンバーを持つことができません。

- 既定のメンバー初期化子を持たない非静的データ メンバー、
- メンバー クラス、または
- メンバー列挙型。

入れ子になった各クラスに対しても、同じ制限が再帰的に適用されます。 この制限は、リンケージのために **`typedef`** 名を持つ構造体の単純さを確保することを目的としています。 それらは、コンパイラがリンケージの **`typedef`** 名に達する前にリンケージ計算が必要となることがないように、単純である必要があります。

この変更は、コンパイラのすべての標準モードに影響します。 既定 ( **`/std:c++14`** ) と **`/std:c++17`** モードの場合、コンパイラでは非準拠コードに対して警告 C5208 が出力されます。 **`/permissive-`** を指定した場合、コンパイラでは、 **`/std:c++14`** でのエラーとして警告 C5208 が出力され、 **`/std:c++17`** ではエラー C7626 が出力されます。 **`/std:c++latest`** を指定した場合、コンパイラでは非準拠コードに対してエラー C7626 が出力されます。

次の例は、名前のない構造体では使用できなくなったコンストラクトを示しています。 指定された標準モードに応じて、C5208 または C7626 エラー、または警告が出力されます。

```cpp
struct B { };
typedef struct : B { // inheriting from 'B'; ill-formed
    void f(); // ill-formed
    static int i; // ill-formed
    struct U {
        void f(); // nested class has non-data member; ill-formed
    };
    int j = 10; // default member initializer; ill-formed
} S;
```

上記のコードは、名前のないクラスに名前を付けることで修正できます。

```cpp
struct B { };
typedef struct S_ : B {
    void f();
    static int i;
    struct U {
        void f();
    };
    int j = 10;
} S;
```

### <a name="default-argument-import-in-ccli"></a>C++/CLIでの既定の引数のインポート

.NET Core では、既定の引数を持つ API の数が増えています。 そのため、C++/CLI で既定の引数のインポートがサポートされるようになりました。 この変更により、次の例のように、複数のオーバーロードが宣言されている既存のコードが破損する可能性があります。

```cpp
public class R {
    public void Func(string s) {}   // overload 1
    public void Func(string s, string s2 = "") {} // overload 2;
}
```

このクラスが C++/CLI にインポートされると、いずれかのオーバーロードの呼び出しによってエラーが発生します。

```cpp
    (gcnew R)->Func("abc"); // error C2668: 'R::Func' ambiguous call to overloaded function
```

両方のオーバーロードがこの引数リストと一致しているため、コンパイラによってエラー C2668 が出力されます。 2 番目のオーバーロードでは、2 番目の引数は既定の引数によって設定されます。 この問題を回避するには、冗長なオーバーロード (1) を削除します。 または、完全な引数リストを使用し、既定の引数を明示的に指定します。

## <a name="conformance-improvements-in-visual-studio-2019-version-167"></a><a name="improvements_167"></a> Visual Studio 2019 バージョン 16.7 の準拠の強化

### <a name="is-trivially-copyable-definition"></a>"*トリビアルにコピー可能である*" の定義

C++20 では、"*トリビアルにコピー可能である*" の定義が変更されました。 クラスに **`volatile`** 修飾型の非静的データ メンバーが含まれている場合、それにより、コンパイラによって生成されたコピーまたは移動コンストラクター、あるいはコピーまたは移動代入演算子は非トリビアルである、ということは意味されなくなりました。 この変更は、C++ 標準化委員会により障害レポートとしてさかのぼって適用されました。 MSVC では、 **`/std:c++14`** や **`/std:c++latest`** などの異なる言語モードでは、コンパイラの動作は変更されません。

新しい動作の例を次に示します。

```cpp
#include <type_traits>

struct S
{
    volatile int m;
};

static_assert(std::is_trivially_copyable_v<S>, "Meow!");
```

このコードは、Visual Studio 2019 バージョン 16.7 より前のバージョンの MSVC ではコンパイルされません。 この変更を検出するために使用できる、既定でオフ コンパイラ警告があります。 **`cl /W4 /w45220`** を使用して上記のコードをコンパイルすると、次の警告が表示されます。

```Output
warning C5220: `'S::m': a non-static data member with a volatile qualified type no longer implies that compiler generated copy/move constructors and copy/move assignment operators are non trivial`
```

### <a name="pointer-to-member-and-string-literal-conversions-to-bool-are-narrowing"></a>メンバーへのポインターおよび文字列リテラルの `bool` への変換は縮小変換である

C++ 標準化委員会で最近採用された障害レポート [P1957R2](https://wg21.link/p1957r2) では、`T*` から **`bool`** は縮小変換と見なされています。 MSVC の実装のバグが修正されました。これにより、以前は `T*` から **`bool`** は縮小変換として診断されましたが、文字列リテラルの **`bool`** への変換、またはメンバーへのポインターの **`bool`** への変換は診断されませんでした。

次のプログラムは、Visual Studio 2019 バージョン16.7 では不適切な形式になります。

```cpp
struct X { bool b; };
void f(X);

int main() {
    f(X { "whoops?" }); // error: conversion from 'const char [8]' to 'bool' requires a narrowing conversion

    int (X::* p) = nullptr;
    f(X { p }); // error: conversion from 'int X::*' to 'bool' requires a narrowing conversion
}
```

このコードを修正するには、 **`nullptr`** に対する明示的な比較を追加するか、縮小変換の形式が正しくなくなるようなコンテキストを回避します。

```cpp
struct X { bool b; };
void f(X);

int main() {
    f(X { "whoops?" != nullptr }); // Absurd, but OK

    int (X::* p) = nullptr;
    f(X { p != nullptr }); // OK
}
```

### <a name="nullptr_t-is-only-convertible-to-bool-as-a-direct-initialization"></a>`nullptr_t` は、直接的な初期化として `bool` にのみ変換可能である

C++11 では、 **`nullptr`** は "*直接変換*" として **`bool`** にのみ変換可能です。たとえば、中かっこで囲まれた初期化子リストを使用して **`bool`** を初期化するときなどです。 この制限は、MSVC では適用されませんでした。 現在の MSVC では、[`/permissive-`](../build/reference/permissive-standards-conformance.md) でルールが実装されています。 暗黙的な変換は、不正な形式として診断されるようになりました。 直接初期化 `bool b(nullptr)` が有効であるため、 **`bool`** へのコンテキスト変換は引き続き許可されます。

ほとんどの場合、次の例に示すように、このエラーは **`nullptr`** を **`false`** に置き換えることによって解決できます。

```cpp
struct S { bool b; };
void g(bool);
bool h() { return nullptr; } // error, should be 'return false;'

int main() {
    bool b1 = nullptr; // error: cannot convert from 'nullptr' to 'bool'
    S s { nullptr }; // error: cannot convert from 'nullptr' to 'bool'
    g(nullptr); // error: cannot convert argument 1 from 'nullptr' to 'bool'

    bool b2 { nullptr }; // OK: Direct-initialization
    if (!nullptr) {} // OK: Contextual conversion to bool
}
```

### <a name="conforming-initialization-behavior-for-array-initializations-with-missing-initializers"></a>初期化子がない配列の初期化に対する初期化動作への準拠

以前は、初期化子がない配列の初期化について、MSVC の動作は準拠していませんでした。 MSVC では、初期化子がない各配列要素に対して常に既定のコンストラクターが呼び出されていました。 標準の動作では、空の中かっこで囲まれた初期化子リスト ( **`{}`** ) を使用して各要素を初期化します。 空の中かっこで囲まれた初期化子リストの初期化コンテキストはコピー初期化であり、明示的なコンストラクターの呼び出しは許可されません。 また、初期化に `{}` を使用すると、既定のコンストラクターではなく `std::initializer_list` を受け取るコンストラクターが呼び出される可能性があるため、ランタイムにも違いがあります。 準拠動作は、[`/permissive-`](../build/reference/permissive-standards-conformance.md) で有効にされます。

変更された動作の例を次に示します。

```cpp
struct B {
    explicit B() {}
};

void f() {
    B b1[1]{}; // Error in /permissive-, because aggregate init calls explicit ctor
    B b2[1]; // OK: calls default ctor for each array element
}
```

### <a name="initialization-of-class-members-with-overloaded-names-is-correctly-sequenced"></a>オーバーロードされた名前を持つクラス メンバーの初期化が正しい順序で行われる

型名もデータ メンバーの名前としてオーバーロードされているときの、クラス データ メンバーの内部表現で、バグが見つかりました。 このバグにより、集約の初期化とメンバーの初期化の順序で不整合が発生しました。 正しい初期化コードが生成されるようになりました。 ただし、この変更により、次の例のように正しくない順序のメンバーに誤って依存しているソースで、エラーまたは警告が発生する可能性があります。

```cpp
// Compiling with /w15038 now gives:
// warning C5038: data member 'Outer::Inner' will be initialized after data member 'Outer::v'
struct Outer {
    Outer(int i, int j) : Inner{ i }, v{ j } {}

    struct Inner { int x; };
    int v;
    Inner Inner; // 'Inner' is both a type name and data member name in the same scope
};
```

以前のバージョンのコンストラクターでは、データ メンバー `v` より前に、データ メンバー `Inner` が誤って初期化されていました。 (C++ の標準では、初期化の順序は、メンバーの宣言の順序と同じである必要があります)。 生成されたコードが標準に従うようになったので、メンバー初期化リストは順不同になります。 この例では、コンパイラによって警告が生成されます。 この問題を解決するには、宣言の順序を反映するように、メンバー初期化子リストの順序を変更します。

### <a name="overload-resolution-involving-integral-overloads-and-long-arguments"></a>整数オーバーロードと `long` 引数を含むオーバーロードの解決

C++ 標準では、標準変換として **`long`** から **`int`** への変換を優先度付けする必要があります。 以前の MSVC コンパイラでは、それが整数の上位変換として不適切に優先度付けされ、オーバーロードの解決に対して上位に優先度付けされます。 この優先度付けによって、あいまいであると見なす必要がある場合に、オーバーロードの解決が正常に解決される可能性があります。

コンパイラにより、[`/permissive-`](../build/reference/permissive-standards-conformance.md) モードで優先度付けが正しく考慮されるようになりました。 次の例のように、無効なコードが適切に診断されます。

```cpp
void f(long long);
void f(int);

int main() {
    long x {};
    f(x); // error: 'f': ambiguous call to overloaded function
    f(static_cast<int>(x)); // OK
}
```

この問題を解決するには、いくつかの方法があります。

- 呼び出しサイトで、渡す引数の型を **`int`** に変更します。 変数の型を変更することも、キャストすることもできます。

- 呼び出しサイトが多い場合は、 **`long`** 引数を受け取る別のオーバーロードを追加できます。 この関数では、引数をキャストして **`int`** オーバーロードに転送します。

### <a name="use-of-undefined-variable-with-internal-linkage"></a>内部リンケージでの未定義の変数の使用

Visual Studio 2019 バージョン16.7 より前のバージョンの MSVC では、内部リンケージがあり、定義されていない **`extern`** と宣言された変数の使用が認められていました。 このような変数は他の翻訳単位で定義できず、有効なプログラムを作成することもできません。 コンパイラで、コンパイル時にこのケースが診断されるようになりました。 エラーは、未定義の静的関数に対するエラーに似ています。

```cpp
namespace {
    extern int x; // Not a definition, but has internal linkage because of the anonymous namespace
}

int main()
{
    return x; // Use of 'x' that no other translation unit can possibly define.
}
```

このプログラムは、以前は誤ってコンパイルおよびリンクされましたが、現在はエラー C7631 が出力されます。

```Output
error C7631: '`anonymous-namespace'::x': variable with internal linkage declared but not defined
```

このような変数は、使用されるのと同じ翻訳単位で定義する必要があります。 たとえば、明示的な初期化子または別の定義を指定できます。

### <a name="type-completeness-and-derived-to-base-pointer-conversions"></a>型の完全性と派生から基底へのポインターの変換

C++20 より前の C++ 標準での、派生クラスから基底クラスへの変換では、派生クラスが完全なクラス型である必要はありませんでした。 C++標準化委員会において、すべてのバージョンの C++ 言語に適用される遡及効果のある障害レポートの変更が承認されました。 この変更により、変換プロセスは `std::is_base_of` などの型の特徴と一致するようになり、派生クラスは完全なクラス型であることが必要になります。

次に例を示します。

```cpp
template<typename A, typename B>
struct check_derived_from
{
    static A a;
    static constexpr B* p = &a;
};

struct W { };
struct X { };
struct Y { };

// With this change this code will fail as Z1 is not a complete class type
struct Z1 : X, check_derived_from<Z1, X>
{
};

// This code failed before and it will still fail after this change
struct Z2 : check_derived_from<Z2, Y>, Y
{
};

// With this change this code will fail as Z3 is not a complete class type
struct Z3 : W
{
    check_derived_from<Z3, W> cdf;
};
```

この動作変更は、 **`/std:c++latest`** だけでなく、MSVC のすべての C++ 言語モードに適用されます。

### <a name="narrowing-conversions-are-more-consistently-diagnosed"></a>縮小変換がより一貫して診断される

MSVC では、中かっこで囲まれたリスト初期化子での縮小変換に関する警告が出力されます。 以前のコンパイラでは、基になる大きな **`enum`** 型から、より狭い整数型への縮小変換が診断されませんでした。 (コンパイラでは、変換ではなく、整数の上位変換であると誤って見なされました)。 縮小変換が意図的なものである場合は、初期化子の引数で **`static_cast`** を使用することによって警告を回避できます。 または、より大きな変換先の整数型を選択します。

次に、明示的な **`static_cast`** を使用して警告に対応する例を示します。

```cpp
enum E : long long { e1 };
struct S { int i; };

void f(E e) {
    S s = { e }; // warning: conversion from 'E' to 'int' requires a narrowing conversion
    S s1 = { static_cast<int>(e) }; // Suppress warning with explicit conversion
}
```

## <a name="conformance-improvements-in-visual-studio-2019-version-168"></a><a name="improvements_168"></a> Visual Studio 2019 バージョン 16.8 の準拠の強化

### <a name="class-rvalue-used-as-lvalue-extension"></a>"lvalue として使用されるクラス rvalue" 拡張機能

MSVC には、クラスの rvalue を lvalue として使用できるようにする拡張機能があります。 この拡張機能を使用すると、クラスの rvalue の有効期間が延びることはなく、実行時に未定義の動作が発生する可能性があります。 これについて、標準の規則が適用されるようになり、 **`/permissive-`** でこの拡張機能は禁止されます。
**`/permissive-`** をまだ使用できない場合は、 **`/we4238`** を使用して、拡張機能を明示的に無効にすることができます。 次に例を示します。

```cpp
// Compiling with /permissive- now gives:
// error C2102: '&' requires l-value
struct S {};

S f();

void g()
{
    auto p1 = &(f()); // The temporary returned by 'f' is destructed after this statement. So 'p1' points to an invalid object.

    const auto &r = f(); // This extends the lifetime of the temporary returned by 'f'
    auto p2 = &r; // 'p2' points to a valid object
}
```

### <a name="explicit-specialization-in-non-namespace-scope-extension"></a>"名前空間ではないスコープでの明示的特殊化" 拡張機能

MSVC には、名前空間ではないスコープでの明示的特殊化を許可する拡張機能がありました。 これは、CWG 727 の解決の後、標準の一部になっています。 ただし、動作の違いがあります。 標準に合わせてコンパイラの動作を調整しました。

```cpp
// Compiling with 'cl a.cpp b.cpp /permissive-' now gives:
//   error LNK2005: "public: void __thiscall S::f<int>(int)" (??$f@H@S@@QAEXH@Z) already defined in a.obj
// To fix the linker error,
// 1. Mark the explicit specialization with 'inline' explicitly. Or,
// 2. Move its definition to a source file.

// common.h
struct S {
    template<typename T> void f(T);
    template<> void f(int);
};

// This explicit specialization is implicitly inline in the default mode.
template<> void S::f(int) {}

// a.cpp
#include "common.h"

int main() {}

// b.cpp
#include "common.h"
```

### <a name="checking-for-abstract-class-types"></a>抽象クラス型のチェック

C++20 標準では、関数パラメーターとしての抽象クラス型の使用を検出するためにコンパイラによって使用されるプロセスが変更されました。 具体的には、これは SFINAE エラーではなくなりました。 以前は、関数テンプレートの特殊化に、関数パラメーターとしての抽象クラス型のインスタンスがあることがコンパイラによって検出された場合、その特殊化は不適切な形式と見なされました。 それは、実行可能な候補関数のセットに追加されませんでした。 C++20 では、抽象クラス型のパラメーターのチェックは、関数が呼び出されるまで行われません。 結果として、コンパイルに使用されるコードによってエラーが発生しなくなります。 次に例を示します。

```cpp
class Node {
public:
    int index() const;
};

class String : public Node {
public:
    virtual int size() const = 0;
};

class Identifier : public Node {
public:
    const String& string() const;
};

template<typename T>
int compare(T x, T y)
{
    return x < y ? -1 : (x > y ? 1 : 0);
}

int compare(const Node& x, const Node& y)
{
    return compare(x.index(), y.index());
}

int f(const Identifier& x, const String& y)
{
    return compare(x.string(), y);
}
```

以前は、`compare` を呼び出すと、`T` に `String` テンプレート引数を使用することで、関数テンプレート `compare` の特殊化が試みられました。 `String` が抽象クラスであるため、有効な特殊化を生成できません。 実行可能な唯一の候補は `compare(const Node&, const Node&)` でした。 しかし、C++20 では、抽象クラス型のチェックは、関数が呼び出されるまで行われません。 したがって、特殊化 `compare(String, String)` が実行可能な候補のセットに追加され、`const String&` から `String` への変換は、`const String&` から `const Node&` への変換より優れた変換シーケンスなので、それが最適な候補として選択されます。

C++20 でこの例の場合に可能な修正の 1 つは、概念を使用することです。つまり、`compare` の定義を次のように変更します。

```cpp
template<typename T>
int compare(T x, T y) requires !std::is_abstract_v<T>
{
    return x < y ? -1 : (x > y ? 1 : 0);
}
```

または、C++ の概念を使用できない場合は、SFINAE にフォールバックすることができます。

```cpp
template<typename T, std::enable_if_t<!std::is_abstract_v<T>, int> = 0>
int compare(T x, T y)
{
    return x < y ? -1 : (x > y ? 1 : 0);
}
```

### <a name="support-for-p0960r3---allow-initializing-aggregates-from-a-parenthesized-list-of-values"></a>P0960R3 のサポート - かっこで囲まれた値のリストからの集計の初期化を許可する

C++20 [P0960R3](https://wg21.link/P0960R3) では、かっこで囲まれた初期化子リストを使用する集約の初期化のサポートが追加されています。 たとえば、C++20 では次のようなコードが有効です。

```cpp
struct S {
    int i;
    int j;
};

S s(1, 2);
```

この機能のほとんどは付加的なものです。つまり、以前はコンパイルされなかったコードが、コンパイルされるようになります。 ただし、`std::is_constructible` の動作が変更されます。 C++17 モードではこの **`static_assert`** は失敗しますが、C++20 モードでは成功します。

```cpp
static_assert(std::is_constructible_v<S, int, int>, "Assertion failed!");
```

この型の特徴を使用してオーバーロードの解決を制御する場合、C++17 と C++20 で動作が変わる可能性があります。

### <a name="overload-resolution-involving-function-templates"></a>関数テンプレートが関係するオーバーロードの解決

以前は、コンパイルしてはならない一部のコードを **`/permissive-`** でコンパイルすることが、コンパイラによって許可されていました。 結果として、コンパイラにより、実行時の動作が変わってしまう間違った関数が呼び出されていました。

```cpp
int f(int);

namespace N
{
    using ::f;
    template<typename T>
    T f(T);
}

template<typename T>
void g(T&& t)
{
}

void h()
{
    using namespace N;
    g(f);
}
```

`g` を呼び出すと、2 つの関数 `::f` と `N::f` を含むオーバーロード セットが使用されます。 `N::f` は関数テンプレートであるため、関数の引数はコンパイラによって "*非推定コンテキスト*" として処理される必要があります。 この場合、それはコンパイラでテンプレート パラメーター `T` の型を推定できないため、`g` の呼び出しが失敗しなければならないことを意味します。 残念ながら、コンパイラによって、`::f` が関数呼び出しに適していると既に判断された事実が破棄されていませんでした。 エラーを生成する代わりに、引数として `::f` を使用して `g` を呼び出すコードが、コンパイラによって生成されました。

多くの場合、関数の引数として `::f` を使用するのはユーザーが意図することであるため、コードが **`/permissive-`** でコンパイルされる場合は、エラーの出力のみを行います。

### <a name="migrating-from-await-to-c20-coroutines"></a>`/await` から C++20 のコルーチンへの移行

**`/std:c++latest`** を使用すると、C++20 標準のコルーチンが既定でオンになります。 これらは、コルーチン TS および **`/await`** スイッチでのサポートとは異なります。 **`/await`** から標準のコルーチンに移行するには、ソースの変更が必要になる場合があります。

#### <a name="non-standard-keywords"></a>標準以外のキーワード

古い **`await`** キーワードと **`yield`** キーワードは、C++20 モードではサポートされていません。 代わりに、 **`co_await`** と **`co_yield`** をコードで使用する必要があります。 標準モードでは、コルーチンで `return` を使用することもできません。 コルーチン内のすべての **`return`** では、 **`co_return`** を使用する必要があります。

```cpp
// /await
task f_legacy() {
    ...
    await g();
    return n;
}
// /std:c++latest
task f() {
    ...
    co_await g();
    co_return n;
}
```

#### <a name="types-of-initial_suspendfinal_suspend"></a>initial_suspend と final_suspend の型

**`/await`** においては、promise initial 関数と suspend 関数を、 **`bool`** を返すように宣言することができます。 この動作は標準ではありません。 C++20 では、これらの関数は待機可能なクラス型、通常は次のトリビアルで待機可能な型のいずれかを返す必要があります: 関数で以前に **`true`** を返していた場合は `std::suspend_always`、 **`false`** を返していた場合は `std::suspend_never`。

```cpp
// /await
struct promise_type_legacy {
    bool initial_suspend() noexcept { return false; }
    bool final_suspend() noexcept { return true; }
    ...
};

// /std:c++latest
struct promise_type {
    auto initial_suspend() noexcept { return std::suspend_never{}; }
    auto final_suspend() noexcept { return std::suspend_always{}; }
    ...
};
```

#### <a name="type-of-yield_value"></a>`yield_value` の型

C++20 では、Promise `yield_value` 関数は待機可能を返す必要があります。 **`/await`** モードでは、`yield_value` 関数は **`void`** を返すことが許可されており、常に中断しました。 そのような関数は、`std::suspend_always` を返す関数に置き換えることができます。

```cpp
// /await
struct promise_type_legacy {
    ...
    void yield_value(int x) { next = x; };
};

// /std:c++latest
struct promise_type {
    ...
    auto yield_value(int x) { next = x; return std::suspend_always{}; }
};
```

#### <a name="exception-handling-function"></a>例外処理関数

**`/await`** を使用すると、例外処理関数のない Promise 型、または `std::exception_ptr` を受け取る `set_exception` という名前の例外処理関数のある Promise 型がサポートされます。 C++20 では、Promise 型には、引数を受け取らない `unhandled_exception` という名前の関数が必要です。 必要に応じて、`std::current_exception` から例外オブジェクトを取得できます。

```cpp
// /await
struct promise_type_legacy {
    void set_exception(std::exception_ptr e) { saved_exception = e; }
    ...
};
// /std:c++latest
struct promise_type {
    void unhandled_exception() { saved_exception = std::current_exception(); }
    ...
};
```

#### <a name="deduced-return-types-of-coroutines-not-supported"></a>コルーチンの戻り値の型の推定はサポートされない

C++20 では、 **`auto`** などのプレースホルダー型が含まれる戻り値の型を使用するコルーチンはサポートされていません。 コルーチンの戻り値の型は、明示的に宣言する必要があります。 **`/await`** では、これらの推定される型には常に実験的な型が含まれ、必要な型を定義するヘッダーを含める必要があります: `std::experimental::task<T>`、`std::experimental::generator<T>`、`std::experimental::async_stream<T>` のいずれか。

```cpp
// /await
auto my_generator() {
    ...
    co_yield next;
};

// /std:c++latest
#include <experimental/generator>
std::experimental::generator<int> my_generator() {
    ...
    co_yield next;
};
```

#### <a name="return-type-of-return_value"></a>`return_value` の戻り値の型

Promise `return_value` 関数の戻り値の型は、 **`void`** である必要があります。 **`/await`** モードでは、戻り値の型は何でもかまわず、無視されます。 この診断は、`return_value` の戻り値が呼び出し元に返されると作成者が誤って想定している場合などの、微妙なエラーを検出するのに役立ちます。

```cpp
// /await
struct promise_type_legacy {
    ...
    int return_value(int x) { return x; } // incorrect, the return value of this function is unused and the value is lost.
};

// /std:c++latest
struct promise_type {
    ...
    void return_value(int x) { value = x; }; // save return value
};
```

#### <a name="return-object-conversion-behavior"></a>戻されるオブジェクトの変換動作

コルーチンの宣言された戻り値の型が、Promise `get_return_object` 関数の戻り値の型と一致しない場合、`get_return_object` から戻されるオブジェクトは、コルーチンの戻り値の型に変換されます。 **`/await`** の場合、この変換は、コルーチンの本体が実行される可能性がまだない、早い段階で行われます。 **`/std:c++latest`** の場合、この変換は、値が呼び出し元に戻されたときに実行されます。 これにより、初期中断ポイントで中断していないコルーチンは、`get_return_object` によって返されるオブジェクトをコルーチン本体内で使用できます。

#### <a name="coroutine-promise-parameters"></a>コルーチンの Promise のパラメーター

C++20 では、コンパイラにより、コルーチンのパラメーター (存在する場合) を Promise 型のコンストラクターに渡すことが試みられます。 それが失敗した場合は、既定のコンストラクターで再試行されます。 **`/await`** モードでは、既定のコンストラクターのみが使用されました。 この変更により、Promise に複数のコンストラクターがある場合に、動作の違いが生じる可能性があります。 または、コルーチンのパラメーターから Promise 型への変換がある場合です。

```cpp
struct coro {
    struct promise_type {
        promise_type() { ... }
        promise_type(int x) { ... }
        ...
    };
};

coro f1(int x);

// Under /await the promise gets constructed using the default constructor.
// Under /std:c++latest the promise gets constructed using the 1-argument constructor.
f1(0);

struct Object {
template <typename T> operator T() { ... } // Converts to anything!
};

coro f2(Object o);

// Under /await the promise gets constructed using the default constructor
// Under /std:c++latest the promise gets copy- or move-constructed from the result of
// Object::operator coro::promise_type().
f2(Object{});
```

### <a name="permissive--and-c20-modules-are-on-by-default-under-stdclatest"></a>`/std:c++latest` では `/permissive-` と C++20 モジュールが既定でオンになる

**`/std:c++latest`** を指定すると、C++20 モジュールのサポートが既定でオンになります。 この変更の詳細と、 **`module`** および **`import`** が条件付きでキーワードとして処理されるシナリオについては、「[Visual Studio 2019 バージョン 16.8 における MSVC での標準 C++20 モジュールのサポート](https://devblogs.microsoft.com/cppblog/standard-c20-modules-support-with-msvc-in-visual-studio-2019-version-16-8/)」を参照してください。

モジュールをサポートする前提条件として、 **`/std:c++latest`** が指定されているときは、 **`permissive-`** が有効になるようになりました。 詳細については、[`/permissive-`](../build/reference/permissive-standards-conformance.md) をご覧ください。

以前に **`/std:c++latest`** でコンパイルされていて、コンパイラの非準拠動作を必要とするコードの場合は、 **`permissive`** を指定することにより、コンパイラでの厳密準拠モードを無効にすることができます。 このコンパイラ オプションは、コマンド ライン引数リストで **`/std:c++latest`** の後に指定する必要があります。 ただし、モジュールの使用が検出された場合、 **`permissive`** はエラーになります。

> エラー C1214: Modules conflict with non-standard behavior requested via '*option*' (モジュールは 'オプション' で要求された非標準動作と競合します)

"*オプション*" の最も一般的な値は次のとおりです。

| オプション | 説明 |
|--|--|
| **`/Zc:twoPhase-`** | 2 つのフェーズ名参照が C++20 モジュールには必要であり、 **`permissive-`** によって暗黙的に指定されます。 |
| **`/Zc:hiddenFriend-`** | 標準の非表示フレンド名参照規則が C++ 20 モジュールに必要であり、 **`permissive-`** によって暗黙的に指定されます。 |
| **`/Zc:preprocessor-`** | 準拠プリプロセッサは、C++20 ヘッダー ユニットの使用と作成のみに必要です。 名前付きモジュールには、このオプションは必要ありません。 |

Visual Studio に付属している *`std.*`* モジュールはまだ標準化されていないため、それを使用するには [`/experimental:module`](../build/reference/experimental-module.md) オプションがやはり必要です。

**`/experimental:module`** オプションを指定すると、 **`/Zc:twoPhase`** と **`/Zc:hiddenFriend`** も暗黙的に使用されます。 以前は、モジュールを使用してコンパイルされるコードは、モジュールだけが使用されている場合は、 **`/Zc:twoPhase-`** でコンパイルされることがありました。 この動作はサポートされなくなりました。

## <a name="conformance-improvements-in-visual-studio-2019-version-169"></a><a name="improvements_169"></a> Visual Studio 2019 バージョン 16.9 の準拠の強化

### <a name="copy-initialization-of-temporary-in-reference-direct-initialization"></a>参照の直接初期化でのテンポラリのコピー初期化

Core Working Group のイシュー [CWG 2267](https://wg21.link/cwg2267) では、かっこで囲まれた初期化子リストと中かっこで囲まれた初期化子リストとの間の不一致が取り上げられています。 解決策では 2 つの形式の釣り合いが取られています。

Visual Studio 2019 バージョン 16.9 では、すべての **`/std`** コンパイラ モードで変更された動作が実装されています。 ただし、これはソースの破壊的変更となる可能性があるため、 **`/permissive-`** を使用してコードがコンパイルされている場合にのみサポートされます。

次のサンプルでは、動作の変更が示されています。

```cpp
struct A { };

struct B {
    explicit B(const A&);
};

void f()
{
    A a;
    const B& b1(a);     // Always an error
    const B& b2{ a };   // Allowed before resolution to CWG 2267 was adopted: now an error
}
```

### <a name="destructor-characteristics-and-potentially-constructed-subobjects"></a>デストラクターの特性と作成される可能性のあるサブオブジェクト

Core Working Group のイシュー [CWG 2336](https://wg21.link/cwg2336) では、仮想基底クラスを持つクラスのデストラクターの暗黙的な例外指定に関する省略が取り上げられています。 この省略は、派生クラスのデストラクターでは、基底クラスが抽象で `virtual` 基底があった場合に、基底クラスよりも弱い例外指定を持つことができたことを意味しました。

Visual Studio 2019 バージョン 16.9 では、すべての **`/std`** コンパイラ モードで変更された動作が実装されています。

次のサンプルは、解釈がどのように変更されたかを示しています。

```cpp
class V {
public:
    virtual ~V() noexcept(false);
};

class B : virtual V {
    virtual void foo () = 0;
    // BEFORE: implicitly defined virtual ~B() noexcept(true);
    // AFTER: implicitly defined virtual ~B() noexcept(false);
};

class D : B {
    virtual void foo ();
    // implicitly defined virtual ~D () noexcept(false);
};
```

この変更以前は、`B` の暗黙的に定義されたデストラクターは `noexcept` でした。作成される可能性のあるサブオブジェクトだけが考慮されるためです。 また、基底クラス `V` は、`virtual` 基底であり、`B` が抽象であるため、作成される可能性のあるサブオブジェクトではありません。 ただし、基底クラス `V` はクラス `D` の作成される可能性のあるサブオブジェクトであるため、`D::~D` は `noexcept(false)` であると判断され、その基底よりも弱い例外指定を持つ派生クラスになります。 この解釈は安全ではありません。 B から派生したクラスのデストラクターから例外がスローされた場合、正しくないランタイムの動作が生じる可能性があります。

この変更により、デストラクターでも、仮想デストラクターを持つ場合スローされる可能性があり、すべての仮想基底クラスが、スローする可能性のあるデストラクターを持ちます。

### <a name="similar-types-and-reference-binding"></a>類似した型と参照バインディング

Core Working Group のイシュー [CWG 2352](https://wg21.link/cwg2352) では、参照バインディング規則と型の類似に対する変更内容との間の不一致が取り上げられています。 この不一致は、以前の不具合報告 ([CWG 330](https://wg21.link/cwg330) など) で報告されました。 この変更により、以前に参照をテンポラリにバインディングしていたコードで、関連する型が cv 修飾子によってのみ異なる場合に、直接バインドできるようになりました。

Visual Studio 2019 バージョン 16.9 では、すべての **`/std`** コンパイラ モードで変更された動作が実装されています。 これはソースの破壊的変更となる可能性があります。

次のサンプルは、変更された動作を示しています。

```cpp
int *ptr;
const int *const &f() {
    return ptr; // Now returns a reference to 'ptr' directly.
    // Previously returned a reference to a temporary and emitted C4172
}
```

この更新によって、紹介されたテンポラリに依存していたプログラムの動作が変更される場合があります。

```cpp
int func() {
    int i1 = 13;
    int i2 = 23;
    
    int* iptr = &i1;
    int const * const&  iptrcref = iptr;

    // iptrcref is a reference to a pointer to i1 with value 13.
    if (*iptrcref != 13)
    {
        return 1;
    }
    
    // Now change what iptr points to.

    // Prior to CWG 2352 iptrcref should be bound to a temporary and still points to the value 13.
    // After CWG 2352 it is bound directly to iptr and now points to the value 23.
    iptr = &i2;
    if (*iptrcref != 23)
    {
        return 1;
    }

    return 0;
}
```

### <a name="zctwophase-and-zctwophase--switch-behavior-change"></a>`/Zc:twoPhase` および `/Zc:twoPhase-` スイッチの動作変更

通常、MSVC コンパイラのスイッチは、最後の 1 つが優先されるという原則で動作します。 残念ながら、これは **`/Zc:twoPhase`** と **`/Zc:twoPhase-`** スイッチについては当てはまりませんでした。 これらのスイッチは "固定" であったため、後のスイッチでオーバーライドできませんでした。 次に例を示します。

`cl /Zc:twoPhase /permissive a.cpp`

この場合、最初の **`/Zc:twoPhase`** スイッチにより、厳密な 2 フェーズの名前参照が有効になります。 2 番目のスイッチは、厳密な準拠モードを無効にすること ( **`/permissive-`** の逆) を目的としていますが、 **`/Zc:twoPhase`** を無効にできませんでした。

Visual Studio 2019 バージョン 16.9 では、すべての **`/std`** コンパイラ モードでこの動作が変更されています。 **`/Zc:twoPhase`** と **`/Zc:twoPhase-`** は "固定" されなくなり、後のスイッチでオーバーライドできます。

### <a name="explicit-noexcept-specifiers-on-destructor-templates"></a>デストラクター テンプレートでの明示的な noexcept 指定子

以前は、非スロー例外指定を使用して宣言されるが、明示的な noexcept 指定なしで定義されるデストラクター テンプレートがコンパイラに受け入れられていました。 デストラクターの暗黙的な例外指定は、クラスのプロパティに依存します。つまり、テンプレートを定義する時点では認識されない可能性があるプロパティです。 また、C++ 標準では次の動作も要求されます: デストラクターが noexcept 指定子なしで宣言されている場合、それは暗黙的な例外指定を持ち、関数の他の宣言が noexcept 指定子を持つことはできません。

Visual Studio 2019 バージョン 16.9 では、すべての **`/std`** コンパイラ モードで準拠動作が変更されています。

次のサンプルは、コンパイラの動作の変更点を示しています。

```cpp
template <typename T>
class B {
    virtual ~B() noexcept; // or throw()
};

template <typename T>
B<T>::~B() { /* ... */ } // Before: no diagnostic.
// Now diagnoses a definition mismatch. To fix, define the implementation by 
// using the same noexcept-specifier. For example,
// B<T>::~B() noexcept { /* ... */ }
```

### <a name="rewritten-expressions-in-c20"></a>C++20 で書き換えられる式

Visual Studio 2019 バージョン 16.2 以降では、 **`/std:c++latest`** で、コンパイラにより次の例のようなコードが受け入れられていました。

```cpp
#include <compare>

struct S {
    auto operator<=>(const S&) const = default;
    operator bool() const;
};

bool f(S a, S b) {
    return a < b;
}
```

しかし、作成者が期待する比較関数がコンパイラによって呼び出されることはありません。 上記のコードでは、`a < b` が `(a <=> b) < 0` として書き換えられる必要がありました。 代わりに、コンパイラではユーザー定義の変換関数 `operator bool()` が使用され、`bool(a) < bool(b)` が比較されました。 Visual Studio 2019 バージョン 16.9 以降では、コンパイラによって、期待される宇宙船演算子の式を使用して式が書き直されます。

#### <a name="source-breaking-change"></a>ソースの破壊的変更

書き換えられた式に変換を適切に適用すると、別の効果が発生します。つまりコンパイラによって、式を書き直そうとする操作から、あいまいさも正しく診断されます。 次の例について考えます。

```cpp
struct Base {
    bool operator==(const Base&) const;
};

struct Derived : Base {
    Derived();
    Derived(const Base&);
    bool operator==(const Derived& rhs) const;
};

bool b = Base{} == Derived{};
```

C++17 では、式の右辺にある `Derived` の派生から基底への変換のため、このコードは受け入れられました。 C++20 では、合成された式の候補も追加されます: `Derived{} == Base{}`。 変換に基づいてどの関数が優先されるかについての標準の規則により、`Base::operator==` と `Derived::operator==` のどちらを選択するかは決定不可能であることがわかります。 これは、2 つの式の変換シーケンスに優先順位をつけられないためであり、このコード例ではあいまいさが発生します。

このあいまいさを解決するには、2 つの変換シーケンスに影響されない新しい候補を追加します。

```cpp
bool operator==(const Derived&, const Base&);
```

#### <a name="runtime-breaking-change"></a>ランタイムの破壊的変更

C++20 の演算子書き換え規則が原因で、オーバーロードの解決によって、より低い言語モードでは見つからなかった新しい候補が見つかる可能性があります。 さらに、その新しい候補は、古い候補よりも適切な一致である可能性があります。 次の例について考えます。

```cpp
struct iterator;
struct const_iterator {
  const_iterator(const iterator&);
  bool operator==(const const_iterator &ci) const;
};

struct iterator {
  bool operator==(const const_iterator &ci) const { return ci == *this; }
};
```

C++17 では、`ci == *this` の唯一の候補は `const_iterator::operator==` です。 これが一致と見なされるのは、`*this` に派生から基底への変換が適用され、`const_iterator` に至るためです。 C++20 では、もう 1 つの書き換えられた候補 `*this == ci` が追加されます。これは `iterator::operator==` を呼び出します。 この候補には変換が必要ないため、`const_iterator::operator==` よりも適切な一致です。 新しい候補の問題は、それが現在定義中の関数であるため、関数の新しいセマンティクスによって、`iterator::operator==` の無限に再帰する定義が発生するという点です。

例のようなコードで役立つように、コンパイラによって新しい警告が実装されます。

```cmd
$ cl /std:c++latest /c t.cpp
t.cpp
t.cpp(8): warning C5232: in C++20 this comparison calls 'bool iterator::operator ==(const const_iterator &) const' recursively
```

コードを修正するには、使用する変換を明示的に指定します。

```cpp
struct iterator {
  bool operator==(const const_iterator &ci) const { return ci == static_cast<const const_iterator&>(*this); }
};
```

## <a name="see-also"></a>関連項目

[Microsoft C++ 言語の準拠表](visual-cpp-language-conformance.md)
