---
description: 詳細については、「コンパイラエラー C2676」を参照してください。
title: コンパイラ エラー C2676
ms.date: 11/04/2016
f1_keywords:
- C2676
helpviewer_keywords:
- C2676
ms.assetid: 838a5e34-c92f-4f65-a597-e150bf8cf737
ms.openlocfilehash: ff620df72993d5c438e4f670dd63a2de56fea18e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281965"
---
# <a name="compiler-error-c2676"></a>コンパイラ エラー C2676

二項演算子 'operator' : 'type' は、この演算子または定義済の演算子に適切な型への変換の定義を行いません。

この演算子を使うには、型を指定してこの演算子をオーバーロードするか、この演算子が定義された型への変換を定義する必要があります。

## <a name="examples"></a>例

次の例では、C2676 が生成されます。

```cpp
// C2676.cpp
// C2676 expected
struct C {
   C();
} c;

struct D {
   D();
   D operator >>( C& ){return * new D;}
   D operator <<( C& ){return * new D;}
} d;

struct E {
   // operator int();
};

int main() {
   d >> c;
   d << c;
   E e1, e2;
   e1 == e2;   // uncomment operator int in class E, then
               // it is OK even though neither E::operator==(E) nor
               // operator==(E, E) defined. Uses the conversion to int
               // and then the builtin-operator==(int, int)
}
```

C2676 は、参照型のポインターに対してポインター演算を実行しようとした場合にも発生する可能性があり **`this`** ます。

**`this`** ポインターは、参照型のハンドル型です。 詳細については、「 [this ポインターのセマンティクス](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer)」を参照してください。

次の例では、C2676 が生成されます。

```cpp
// C2676_a.cpp
// compile with: /clr
using namespace System;

ref struct A {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }

   A() {
      Console::WriteLine("{0}", this + 3.3);   // C2676
      Console::WriteLine("{0}", this[3.3]);   // OK
   }
};

int main() {
   A ^ mya = gcnew A();
}
```
