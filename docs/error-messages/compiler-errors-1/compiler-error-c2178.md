---
description: 詳細については、「コンパイラエラー C2178」を参照してください。
title: コンパイラエラー C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: 7a93293fdb87f30827b8b9c3c6d38066b0c76798
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322163"
---
# <a name="compiler-error-c2178"></a>コンパイラエラー C2178

'*identifier*' を '*指定* 子 ' 指定子と共に宣言することはできません

**`mutable`** 宣言で指定子が使用されましたが、このコンテキストでは指定子は許可されていません。

**`mutable`** 指定子は、クラスのデータメンバーの名前にのみ適用できます。また、またはと宣言された名前には適用できません **`const`** **`static`** 。また、参照メンバーには適用できません。

## <a name="example"></a>例

次の例では、C2178 の発生方法とその修正方法を示しています。

```cpp
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
