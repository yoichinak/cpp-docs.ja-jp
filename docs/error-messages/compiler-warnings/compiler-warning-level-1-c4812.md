---
description: '詳細情報: コンパイラの警告 (レベル 1) C4812'
title: コンパイラの警告 (レベル 1) C4812
ms.date: 11/04/2016
f1_keywords:
- C4812
helpviewer_keywords:
- C4812
ms.assetid: a7f5721f-2019-44de-ad62-ed30bac8b1f3
ms.openlocfilehash: 3476086d067b98a62ec9d96647a77c109c9a263b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332188"
---
# <a name="compiler-warning-level-1-c4812"></a>コンパイラの警告 (レベル 1) C4812

旧形式の宣言スタイル: 'new_syntax' を使用してください

現在のリリースの Visual C++ では、コンストラクターの明示的な特殊化がサポートされていますが、将来のリリースではサポートされない可能性があります。

次の例では C4812 が生成されます。

```cpp
// C4812.cpp
// compile with: /W1 /c
template <class T>
class MyClass;

template<class T>
class MyClass<T*> {
   MyClass();
};

template<class T>
MyClass<T*>::MyClass<T*>() {}   // C4812
// try the following line instead
// MyClass<T*>::MyClass() {}
```
