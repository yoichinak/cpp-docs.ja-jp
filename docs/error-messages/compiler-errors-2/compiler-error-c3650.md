---
description: 詳細については、「コンパイラエラー C3650」を参照してください。
title: コンパイラ エラー C3650
ms.date: 11/04/2016
f1_keywords:
- C3650
helpviewer_keywords:
- C3650
ms.assetid: ca4d8de4-b027-4d13-9b9f-03ca62905c33
ms.openlocfilehash: 02230eed0f1e3448bfc91d331611f28a7b6b7531
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203732"
---
# <a name="compiler-error-c3650"></a>コンパイラ エラー C3650

' interface_method ': 明示的なオーバーライドとして使用することはできません。基底クラスの仮想メンバー関数でなければなりません

仮想ではないメンバーに対して明示的なオーバーライドを実行しようとしました。

詳細については、「 [明示的なオーバーライド](../../extensions/explicit-overrides-cpp-component-extensions.md)」を参照してください。

次の例では、C3650 が生成されます。

```cpp
// C3650.cpp
// compile with: /clr
public interface struct I {
   void a();
};

public ref class S {
public:
   static int f() { return 0; }
   static int g() { return 0; }
};

public ref struct T1 : public S, I {
   virtual int f() new sealed = S::f;   // C3650
   virtual int g() { return 0; }   // OK does not override S::g
   virtual void a() new sealed = I::a {}   // OK
};
```
