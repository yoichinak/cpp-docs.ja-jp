---
description: '詳細情報: continue ステートメント (C)'
title: continue ステートメント (C)
ms.date: 04/14/2021
f1_keywords:
- continue
helpviewer_keywords:
- loop structures, continue keyword
- continue keyword [C]
ms.openlocfilehash: dba5789e52291fbaac4d0b63b5e0d90a9cdcd776
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539306"
---
# <a name="continue-statement-c"></a>`continue` ステートメント (C)

**`continue`** ステートメントは、それを囲む最も近い **`do`** 、 **`for`** 、または **`while`** ステートメントの次の反復処理に制御を渡し、 **`do`** 、 **`for`** 、または **`while`** ステートメント本体の残りのステートメントをバイパスします。

## <a name="syntax"></a>構文

*`jump-statement`*:<br/>
&emsp;**`continue ;`**

**`do`** 、 **`for`** 、または **`while`** ステートメントの次の反復処理は次のように決定されます。

- **`do`** または **`while`** ステートメント内では、次の繰り返しは **`do`** または **`while`** ステートメントの式の再評価によって開始されます。

- **`for`** ステートメントの **`continue`** ステートメントは、 **`for`** ステートメントのループ式を評価します。 次いで、このコードは条件式を再評価します。 その結果によって、ステートメント本体が終了または反復処理されます。 **`for`** ステートメントとその非終端要素の詳細については、「[`for` ステートメント](../c-language/for-statement-c.md)」を参照してください。

**`continue`** ステートメントの例を次に示します。

```C
while ( i-- > 0 )
{
    x = f( i );
    if ( x == 1 )
        continue;
    y += x * x;
}
```

この例では、ステートメント本体は、`i` が 0 を超える場合に実行されます。 最初に、`f(i)` は `x` に割り当てられています。次に、`x` が 1 に等しい場合は、 **`continue`** ステートメントが実行されます。 本体の残りのステートメントは無視されます。 ループ テストの評価がループの先頭から再実行されます。

## <a name="see-also"></a>関連項目

[`continue` ステートメント (C++)](../cpp/continue-statement-cpp.md)
