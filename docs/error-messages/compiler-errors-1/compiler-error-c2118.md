---
description: 詳細については、「コンパイラエラー C2118」を参照してください。
title: コンパイラ エラー C2118
ms.date: 11/04/2016
f1_keywords:
- C2118
helpviewer_keywords:
- C2118
ms.assetid: bf4315d0-f085-4323-b813-96ee61a13bde
ms.openlocfilehash: 89ddf355e233e4fb2d6f36a53369d85bf8ea019a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170101"
---
# <a name="compiler-error-c2118"></a>コンパイラ エラー C2118

負の添字

配列のサイズを定義する値が、配列の最大サイズより大きいか、または0より小さい値です。

次の例では、C2118 が生成されます。

```cpp
// C2118.cpp
int main() {
   int array1[-1];   // C2118
   int array2[3];   // OK
}
```
