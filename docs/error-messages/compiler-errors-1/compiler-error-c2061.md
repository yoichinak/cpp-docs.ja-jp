---
description: 詳細については、「コンパイラエラー C2061」を参照してください。
title: コンパイラエラー C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: e857f4c4de90fadecdd7b7062306391b4222bcf4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328725"
---
# <a name="compiler-error-c2061"></a>コンパイラエラー C2061

構文エラー: 識別子 ' identifier '

コンパイラは、予期されていなかった識別子を検出しました。 を `identifier` 使用する前に、が宣言されていることを確認します。

初期化子は、かっこで囲むことができます。 この問題を回避するには、宣言子をかっこで囲むか、をに設定し **`typedef`** ます。

このエラーは、コンパイラがクラステンプレート引数として式を検出した場合にも発生する可能性があります。型であることをコンパイラに通知するには、 [typename](../../cpp/typename.md) を使用します。

次の例では、C2061 が生成されます。

```cpp
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

C2061 は、インスタンス名を [typeid](../../extensions/typeid-cpp-component-extensions.md)に渡すと発生する可能性があります。

```cpp
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```
