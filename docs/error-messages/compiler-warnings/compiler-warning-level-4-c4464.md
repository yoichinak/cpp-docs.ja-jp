---
description: '詳細情報: コンパイラの警告 (レベル 4) C4464'
title: コンパイラの警告 (レベル 4) C4464
ms.date: 03/13/2018
f1_keywords:
- C4464
helpviewer_keywords:
- C4464
ms.openlocfilehash: b104d131cc5dd75c75bdd695b96a7e651c2b24a6
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107723423"
---
# <a name="compiler-warning-level-4-c4464"></a>コンパイラの警告 (レベル 4) C4464

> **相対インクルードパスに '.. ' が含まれています**

`#include`ディレクティブに '.. ' を含むパスが含まれています 親ディレクトリ指定子。

## <a name="remarks"></a>解説

Visual Studio 2015 Update 1 以降では、コンパイラは '.. ' を含む include ディレクティブを検出できます。 パスセグメントを使用して、有効になっている場合は警告を発行します。 この方法で記述されたコードは通常、プロジェクトの相対パスが正しく使用されていないためにプロジェクトの外部に存在するヘッダーをインクルードすることを目的としています。 これにより、プログラマの意図したものとは異なるソースファイルを含めることによってプログラムをコンパイルできるリスクが生じます。また、これらの相対パスを他のビルド環境に移植できないようにすることもできます。 特定の警告はありませんが、プロジェクトのインクルードディレクトリを指定するために親ディレクトリのパスセグメントを使用しないことをお勧めします。

この警告は Visual Studio 2015 Update 1 で新しく追加されたものであり、既定ではオフになっています。 [/Wall](../../build/reference/compiler-option-warning-level.md)を使用して、既定でオフになっているすべての警告を有効にします。または、C4464 をレベル *n* の警告として有効にする場合は __/w__*n*__4464__ を使用します。 詳細については、「 [既定でオフになっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)」を参照してください。 コンパイラのバージョン別の警告を無効にする方法については、「コンパイラの [バージョン別のコンパイラ警告](compiler-warnings-by-compiler-version.md)」を参照してください。

## <a name="example"></a>例

'.. ' を使用するソースコードファイル **/Wall** オプションが指定されている場合、パスセグメントはこの警告をトリガーできます。

```cpp
#include "..\headers\C4426.h"  // emits warning C4464

// To fix this issue, specify only the header file name, and add
// the absolute path to 'headers\' to your project's include directories
#include "C4426.h"
```
