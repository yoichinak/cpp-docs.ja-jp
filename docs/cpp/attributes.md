---
description: '詳細情報: C++ の属性'
title: C++ の属性
ms.date: 04/18/2021
ms.openlocfilehash: ebf35b7c80a815bd4da605c0a5f8343fe991d5b4
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721122"
---
# <a name="attributes-in-c"></a>C++ の属性

C++ 標準では、共通の属性セットが定義されています。 また、コンパイラベンダーは、ベンダー固有の名前空間内で独自の属性を定義することもできます。 ただし、コンパイラは、標準で定義されている属性を認識するだけで済みます。

場合によっては、標準属性がコンパイラ固有のパラメーターと重複することがあり `__declspec` ます。 Microsoft C++ では、を使用する代わりに属性を使用でき `[[deprecated]]` `__declspec(deprecated)` ます。 この `[[deprecated]]` 属性は、準拠しているコンパイラによって認識されます。 やなどの他のすべてのパラメーターに対し `__declspec` ては `dllimport` 、これまでと `dllexport` 同じ属性が存在しないため、構文を使用し続ける必要があり `__declspec` ます。 属性は型システムに影響を与えず、プログラムの意味を変更しません。 コンパイラは、認識されない属性値を無視します。

**Visual Studio 2017 バージョン15.3 以降** (で使用可能 [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ): 属性リストのスコープで、1つの lambda-introducer を持つすべての名前の名前空間を指定でき **`using`** ます。

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>C++ 標準属性

C++ 11 では、属性は C++ の構造に注釈を付けるための標準化された方法を提供します (クラス、関数、変数、ブロックなどに限定されません)。 属性はベンダー固有のものでもかまいません。 コンパイラは、この情報を使用して情報メッセージを生成したり、属性付きコードをコンパイルするときに特別なロジックを適用したりすることができます。 コンパイラは、認識されない属性を無視します。つまり、この構文を使用して独自のカスタム属性を定義することはできません。 属性は、2つの角かっこで囲まれています。

```cpp
[[deprecated]]
void Foo(int);
```

属性 `#pragma` は、ディレクティブ、 `__declspec()` (Visual C++)、(GNU) などのベンダー固有の拡張機能の代わりに標準化されたものを表し `__attribute__` ます。 ただし、ほとんどの場合、ベンダー固有の構成体を使用する必要があります。 標準では、現在、準拠するコンパイラが認識する必要がある次の属性を指定しています。

- `[[noreturn]]` 関数がを返さないことを指定します。つまり、常に例外がスローされます。 コンパイラは、エンティティのコンパイル規則を調整でき `[[noreturn]]` ます。

- `[[carries_dependency]]` 関数がスレッド同期のデータ依存関係の順序を反映することを指定します。 属性を1つ以上のパラメーターに適用して、渡された引数が関数本体に依存関係を含むことを指定できます。 属性を関数自体に適用して、戻り値が関数からの依存関係を持つことを指定できます。 コンパイラはこの情報を使用して、より効率的なコードを生成できます。

- `[[deprecated]]`**Visual Studio 2015 以降:** 関数を使用するためのものではないことを指定します。 または、ライブラリインターフェイスの将来のバージョンには存在しない可能性があります。 コンパイラは、この属性を使用して、クライアントコードが関数を呼び出そうとしたときに情報メッセージを生成できます。 `[[deprecated]]` クラス、typedef 名、変数、非静的データメンバー、関数、名前空間、列挙型、列挙子、またはテンプレートの特殊化の宣言に適用できます。

- `[[fallthrough]]`**Visual Studio 2017 以降:** (で使用可能 [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ) は、fallthrough の `[[fallthrough]]` [`switch`](switch-statement-cpp.md) 動作が意図されているコンパイラ (またはコードを読み取っているユーザー) へのヒントとして、ステートメントのコンテキストで属性を使用できます。 現在、Microsoft C++ コンパイラでは fallthrough 動作について警告されないため、この属性はコンパイラの動作に影響しません。

- `[[nodiscard]]`**Visual Studio 2017 バージョン15.3 以降:** (で使用可能 [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ) は、関数の戻り値が破棄されることを意図していないことを示します。 次の例に示すように、警告 [C4834](../error-messages/compiler-warnings/c4834.md)を発生させます。

    ```cpp
    [[nodiscard]]
    int foo(int i) { return i * i; }

    int main()
    {
        foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
        return 0;
    }
    ```

- `[[maybe_unused]]`**Visual Studio 2017 バージョン15.3 以降:** (で使用可能 [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ) は、変数、関数、クラス、typedef、非静的データメンバー、列挙型、またはテンプレートの特殊化を意図的に使用しないことを指定します。 とマークされているエンティティが使用されていない場合、コンパイラは警告を表示しません `[[maybe_unused]]` 。 属性を指定せずに宣言されたエンティティは、後で属性で再宣言できます。その逆も可能です。 エンティティは、マークが付けられた最初の宣言の後、現在の翻訳単位の残りの部分に対して *マーク* されていると見なされ `[[maybe_unused]]` ます。

## <a name="microsoft-specific-attributes"></a>Microsoft 固有の属性

- `[[gsl::suppress(rules)]]` この Microsoft 固有の属性は、コードで [ガイドラインサポートライブラリ (GSL)](https://github.com/Microsoft/GSL) の規則を適用するチェッカーからの警告を抑制するために使用されます。 たとえば、次のコードスニペットを考えてみます。

    ```cpp
    int main()
    {
        int arr[10]; // GSL warning C26494 will be fired
        int* p = arr; // GSL warning C26485 will be fired
        [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
        {
            int* q = p + 1; // GSL warning C26481 suppressed
            p = q--; // GSL warning C26481 suppressed
        }
    }
    ```

  この例では、次の警告が発生します。

  - 26494 (型ルール 5: 常にオブジェクトを初期化します。)

  - 26485 (境界規則 3: ポインターがポインターを指す配列がありません。)

  - 26481 (境界規則 1: ポインター演算は使用しません。 代わりに span を使用します。)

  最初の2つの警告は、CppCoreCheck コード分析ツールがインストールおよびアクティブ化された状態でこのコードをコンパイルすると発生します。 ただし、属性が原因で3番目の警告が発生することはありません。 `[[gsl::suppress(bounds)]]`特定の規則番号を含めずに、境界プロファイル全体を作成しないようにすることができます。 C++ Core Guidelines は、より適切で安全なコードを記述できるように設計されています。 抑制属性を使用すると、不要になったときに警告を簡単に無効にすることができます。
