---
description: '詳細については、/Zc: rvalueCast (型変換規則の適用) に関するページを参照してください。'
title: /Zc:rvalueCast (型変換規則の適用)
ms.date: 02/18/2020
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
ms.openlocfilehash: f9739f16b12e5e0335f17bb5a56ed1e4aa265e9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269147"
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast (型変換規則の適用)

オプションを指定すると、 **`/Zc:rvalueCast`** コンパイラは、キャスト演算の結果として右辺値参照型を正しく識別します。 その動作は、C++ 11 標準に準拠しています。 オプションが指定されていない場合、コンパイラの動作は Visual Studio 2012 と同じです。

## <a name="syntax"></a>構文

> **`/Zc:rvalueCast`**\
> **`/Zc:rvalueCast-`**

## <a name="remarks"></a>解説

が指定されている場合 **`/Zc:rvalueCast`** 、コンパイラは c++ 11 標準のセクション5.4 に従い、非参照型を結果とするキャスト式だけを処理し、非関数型を右辺値型として返したキャスト式のみを処理します。 既定では、またはが指定されている場合 **`/Zc:rvalueCast-`** 、コンパイラは非準拠であり、右辺値参照になるすべてのキャスト式は右辺値として扱われます。 準拠のために、キャストの使用に関するエラーを回避するために、を使用することをお勧めし **`/Zc:rvalueCast`** ます。

既定で **`/Zc:rvalueCast`** は、は off ( **`/Zc:rvalueCast-`** ) です。 [/Permissive-](permissive-standards-conformance.md)コンパイラオプションはこのオプションを暗黙的に設定しますが、を使用してオーバーライドすることもでき **`/Zc:rvalueCast-`** ます。

**`/Zc:rvalueCast`** 右辺値参照型を受け取る関数に引数としてキャスト式を渡す場合は、を使用します。 既定の動作では、コンパイラがキャスト式の型を誤って判断したときに、コンパイラエラー [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) が発生します。 次の例では、が指定されていない場合に、正しいコードでコンパイラエラーを示して **`/Zc:rvalueCast`** います。

```cpp
// Test of /Zc:rvalueCast
// compile by using:
// cl /c /Zc:rvalueCast- make_thing.cpp
// cl /c /Zc:rvalueCast make_thing.cpp

#include <utility>

template <typename T>
struct Thing {
   // Construct a Thing by using two rvalue reference parameters
   Thing(T&& t1, T&& t2)
      : thing1(t1), thing2(t2) {}

   T& thing1;
   T& thing2;
};

// Create a Thing, using move semantics if possible
template <typename T>
Thing<T> make_thing(T&& t1, T&& t2)
{
   return (Thing<T>(std::forward<T>(t1), std::forward<T>(t2)));
}

struct Test1 {
   long a;
   long b;

   Thing<long> test() {
      // Use identity casts to create rvalues as arguments
      return make_thing(static_cast<long>(a), static_cast<long>(b));
   }
};
```

コンパイラの既定動作では、場合によっては C2102 エラーが報告されないことがあります。 この例では、が指定されていない場合に、id キャストによって作成された右辺値のアドレスが取得されると、コンパイラはエラーを報告しません **`/Zc:rvalueCast`** 。

```cpp
int main() {
   int a = 1;
   int *p = &a;   // Okay, take address of lvalue
                  // Identity cast creates rvalue from lvalue;
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value
}
```

Visual C++ の準拠に関する問題について詳しくは、「 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)」をご覧ください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. [**構成プロパティ**] [  >  **C/c + +**  >  **言語**] プロパティページを選択します。

1. [ **型変換規則を適用** するプロパティをまたはに設定し **`/Zc:rvalueCast`** **`/Zc:rvalueCast-`** ます。 **[OK]** または [**適用**] を選択して、変更を保存します。

## <a name="see-also"></a>関連項目

[/Zc (準拠)](zc-conformance.md)
