---
description: '詳細情報: コンパイラの警告 (レベル 1) C4080'
title: コンパイラの警告 (レベル 1) C4080
ms.date: 11/04/2016
f1_keywords:
- C4080
helpviewer_keywords:
- C4080
ms.assetid: 964fb3f4-b9fd-450b-aa23-35cece126172
ms.openlocfilehash: 05dcb119d0c028446f038a2cbd796432c688a8c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344290"
---
# <a name="compiler-warning-level-1-c4080"></a>コンパイラの警告 (レベル 1) C4080

セグメント名の識別子が必要です。'symbol' が見つかりました。

[#pragma alloc_text](../../preprocessor/alloc-text.md) 内のセグメントの名前は、文字列または識別子である必要があります。 有効な識別子が見つからない場合、コンパイラはプラグマを無視します。

次の例では C4080 が生成されます。

```cpp
// C4080.cpp
// compile with: /W1
extern "C" void func(void);

#pragma alloc_text()   // C4080

// try this line to resolve the warning
// #pragma alloc_text("mysection", func)

int main() {
}

void func(void) {
}
```
