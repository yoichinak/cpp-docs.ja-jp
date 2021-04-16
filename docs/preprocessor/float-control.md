---
title: float_control pragma
description: Float_control ディレクティブの使用法と効果について説明し pragma ます。 Float_control ディレクティブは、実行時の浮動小数点の正確なセマンティクスと例外セマンティクスの状態を制御します。
ms.date: 04/15/2021
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragma, float_control
no-loc:
- pragma
ms.openlocfilehash: b7a02acf729d04527300454fed6e74e7d06bbfe9
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539758"
---
# <a name="float_control-pragma"></a>`float_control` pragma

関数の浮動小数点動作を指定します。

## <a name="syntax"></a>Syntax

> **`#pragma float_control`**\
> **`#pragma float_control( precise,`** { **`on`** &vert; **`off`** } [ **`, push`** ] **`)`**\
> **`#pragma float_control( except,`** { **`on`** &vert; **`off`** } [ **`, push`** ] **`)`**\
> **`#pragma float_control(`** { **`push`** &vert; **`pop`** } **`)`**

## <a name="options"></a>オプション

**`precise`**, **`on`** | **`off`**, **`push`**\
**`on`** **`off`** 正確な浮動小数点セマンティクスを有効にするかどうかを指定します。 コンパイラオプションの違いについては、「 **`/fp:precise`** 解説」を参照してください。 オプションの **`push`** トークンは、の現在の設定を **`float_control`** 内部コンパイラスタックにプッシュします。

**`except`**, **`on`** | **`off`**, **`push`**\
**`on`** 浮動小数点例外セマンティクスを有効にするかどうかを指定し **`off`** ます。 オプションの **`push`** トークンは、の現在の設定を **`float_control`** 内部コンパイラスタックにプッシュします。

**`except`** をに設定できるの **`on`** は、もに設定されている場合のみ **`precise`** **`on`** です。

**`push`**\
現在の **`float_control`** 設定を内部コンパイラスタックにプッシュします。

**`pop`**\
**`float_control`** 内部コンパイラスタックの一番上から設定を削除し、新しい設定を行い **`float_control`** ます。

## <a name="remarks"></a>注釈

は、 **`float_control`** pragma コンパイラオプションと同じ動作をしません [`/fp`](../build/reference/fp-specify-floating-point-behavior.md) 。 は、 **`float_control`** pragma 浮動小数点動作の一部のみを制御します。 [`fp_contract`](../preprocessor/fp-contract.md) [`fenv_access`](../preprocessor/fenv-access.md) pragma コンパイラオプションを再作成するには、ディレクティブとディレクティブを組み合わせて使用する必要があり **`/fp`** ます。 次の表は、各コンパイラオプションの同等の設定を示してい pragma ます。

| オプション | `float_control(precise, *)` | `float_control(except, *)` | `fp_contract(*)` | `fenv_access(*)` |
|-|-|-|-|-|
| `/fp:strict`             | `on`  | `on`  | `off` | `on`  |
| `/fp:precise`            | `on`  | `off` | `on`  | `off` |
| `/fp:fast`               | `off` | `off` | `on`  | `off` |

つまり、 pragma **`/fp:fast`** 、、およびの各コマンドラインオプションをエミュレートするために、複数のディレクティブを組み合わせて使用することが必要になる場合があり **`/fp:precise`** **`/fp:strict`** ます。

**`float_control`** と **`fenv_access`** 浮動小数点ディレクティブを組み合わせて使用する方法には、次のような制限があり pragma ます。

- **`float_control`** **`except`** **`on`** 正確なセマンティクスが有効になっている場合にのみ、をに設定できます。 正確なセマンティクスは、で有効にすることも、 **`float_control`** pragma **`/fp:precise`** またはコンパイラオプションを使用して有効にすることもでき **`/fp:strict`** ます。

- **`float_control`** **`precise`** **`float_control`** pragma またはコンパイラオプションによって例外のセマンティクスが有効になっている場合は、を使用して無効にすることはできません **`/fp:except`** 。

- **`fenv_access`** **`float_control`** またはコンパイラオプションによって、正確なセマンティクスが有効になっている場合を除き、を有効にすることはできません pragma 。

- **`float_control`** **`precise`** が有効になっている場合は、を使用してオフにすることはできません **`fenv_access`** 。

これらの制限は、一部の浮動小数点ディレクティブの順序が重要であることを意味 pragma します。 ディレクティブを使用して高速モデルから厳密なモデルに移行するには pragma 、次のコードを使用します。

```cpp
#pragma float_control(precise, on)  // enable precise semantics
#pragma fenv_access(on)             // enable environment sensitivity
#pragma float_control(except, on)   // enable exception semantics
#pragma fp_contract(off)            // disable contractions
```

を使用して厳密なモデルから高速モデルに移行するには **`float_control`** pragma 、次のコードを使用します。

```cpp
#pragma float_control(except, off)  // disable exception semantics
#pragma fenv_access(off)            // disable environment sensitivity
#pragma float_control(precise, off) // disable precise semantics
#pragma fp_contract(on)             // enable contractions
```

オプションが指定されていない場合、に **`float_control`** よる影響はありません。

## <a name="example"></a>例

次の例は、を使用してオーバーフロー浮動小数点例外をキャッチする方法を示して pragma **`float_control`** います。

```cpp
// pragma_directive_float_control.cpp
// compile with: /EHa
#include <stdio.h>
#include <float.h>

double func( ) {
   return 1.1e75;
}

#pragma float_control (except, on)

int main( ) {
   float u[1];
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);
   if (err != 0)
      printf_s("_controlfp_s failed!\n");

   try  {
      u[0] = func();
      printf_s ("Fail");
      return(1);
   }

   catch (...)  {
      printf_s ("Pass");
      return(0);
   }
}
```

```Output
Pass
```

## <a name="see-also"></a>こちらもご覧ください

[プラグマディレクティブと `__pragma` `_Pragma` キーワードおよびキーワード](./pragma-directives-and-the-pragma-keyword.md)\
[`fenv_access` pragma](../preprocessor/fenv-access.md)\
[`fp_contract` pragma](../preprocessor/fp-contract.md)
