---
description: pragmaMicrosoft C/c + + での pointers_to_members ディレクティブの詳細については、こちらを参照してください。
title: pointers_to_members pragma
ms.date: 04/13/2021
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragma, pointers_to_members
- members, pointers to
- pointers_to_members pragma
no-loc:
- pragma
ms.openlocfilehash: 287f00dcca5f041fc8c17cc8f14c0274a77f13ea
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107576898"
---
# <a name="pointers_to_members-pragma"></a>`pointers_to_members` pragma

**C++ 固有の仕様**

クラスメンバーへのポインターを、関連付けられているクラス定義の前に宣言できるかどうかを指定します。 ポインターのサイズ、およびポインターを解釈するために必要なコードを制御するために使用されます。

## <a name="syntax"></a>構文

> **`#pragma pointers_to_members( best_case )`**\
> **`#pragma pointers_to_members( full_generality`** [ **`,`** *`most-general-representation`* ] **`)`**

## <a name="remarks"></a>解説

**`pointers_to_members`** pragma [ `/vmb` また `/vmg` は](../build/reference/vmb-vmg-representation-method.md)、、 [ `/vmm` `/vms` 、、 `/vmv`](../build/reference/vmm-vms-vmv-general-purpose-representation.md)コンパイラオプション、または Microsoft 固有の [継承キーワード](../cpp/inheritance-keywords.md)を使用する代わりに、ソースファイルにを配置できます。

ポインター宣言引数は、関連付けられている関数定義の前または後に、メンバーへのポインターを宣言したかどうかを指定します。 *`pointer-declaration`* 引数は、次の2つの記号のいずれかになります。

- **`full_generality`**\
  安全な、場合によっては最適でないコードです。 **`full_generality`** メンバーへのポインターが、関連付けられているクラス定義の前に宣言されている場合は、を使用します。 この引数は常に、引数で指定されたポインター表現を使用し *`most-general-representation`* ます。 と同じ **`/vmg`** です。

- **`best_case`**\
  メンバーへのすべてのポインターに対して最適な表現を使用して、最適なコードを生成します。 メンバーへのポインターを宣言する前に、クラスを定義する必要があります。 既定値は **`best_case`** です。

引数は、 *`most-general-representation`* 変換単位のクラスのメンバーへのポインターを安全に参照するためにコンパイラが使用する最小のポインター表現を指定します。 引数には、次のいずれかの値を指定できます。

- **`single_inheritance`**\
  最も一般的な表現は、メンバー関数への単一継承ポインターです。 と同じ **`/vmg /vms`** です。 クラス定義の継承モデルが複数の場合、または仮想の場合は、エラーが発生します。

- **`multiple_inheritance`**\
  最も一般的な表現は、メンバー関数への多重継承ポインターです。 と同じ **`/vmg /vmm`** です。 クラス定義の継承モデルが仮想の場合、エラーが発生します。

- **`virtual_inheritance`**\
  最も一般的な表現は、メンバー関数への仮想継承ポインターです。 と同じ **`/vmg /vmv`** です。  エラーが発生することはありません。 **`virtual_inheritance`** は、が使用される場合の既定の引数です `#pragma pointers_to_members(full_generality)` 。

> [!CAUTION]
> を **`pointers_to_members`** pragma ソースコードファイルにのみ配置し、すべてのディレクティブの後にのみ含めるようにすることをお勧めし `#include` ます。 これにより、が pragma 他のファイルに影響を与えるリスクが軽減され、同じ変数、関数、またはクラス名に対して複数の定義を誤って指定することになります。

## <a name="example"></a>例

```cpp
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

**END C++ 固有の仕様**

## <a name="see-also"></a>関連項目

[プラグマディレクティブと `__pragma` `_Pragma` キーワードおよびキーワード](./pragma-directives-and-the-pragma-keyword.md)
