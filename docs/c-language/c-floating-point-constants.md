---
description: '詳細情報: C 浮動小数点定数'
title: C 浮動小数点定数
ms.date: 04/14/2021
helpviewer_keywords:
- types [C], constants
- floating-point numbers, floating-point constants
- constants, floating-point
- floating-point constants
- floating-point constants, about floating-point constants
- double data type, floating-point constants
ms.openlocfilehash: fe4bd00c824af2f2bb1b6e41393c72fc2b30e509
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539335"
---
# <a name="c-floating-point-constants"></a>C 浮動小数点定数

"浮動小数点定数" は符号付き実数を表す 10 進数です。 符号付き実数の表現には、整数部分、小数部分、および指数が含まれます。 変更できない浮動小数点値を表すには、浮動小数点定数を使用します。

## <a name="syntax"></a>構文

*`floating-point-constant`*:<br/>
&emsp; *`fractional-constant`* *`exponent-part`* <sub>opt</sub> *`floating-suffix`* <sub>opt</sub><br/>
&emsp; *`digit-sequence`* *`exponent-part`* *`floating-suffix`* <sub>opt</sub>

*`fractional-constant`*:<br/>
&emsp; *`digit-sequence`* <sub>opt</sub> **.** *`digit-sequence`*<br/>
&emsp;*`digit-sequence`*  **.**

*`exponent-part`*:<br/>
&emsp;**e** *`sign`* <sub>opt</sub> *`digit-sequence`*<br/>
&emsp;**E** *`sign`* <sub>opt</sub> *`digit-sequence`*

*`sign`* : 次のいずれか<br/>
&emsp;**`+`** **`-`**

*`digit-sequence`*:<br/>
&emsp;*`digit`*<br/>
&emsp;*`digit-sequence`* *`digit`*

*`floating-suffix`* : 次のいずれか<br/>
&emsp;**`f`** **`l`** **`F`** **`L`**

小数点の前の桁 (値の整数の部分) または小数点の後の桁 (小数の部分) を省略できますが、両方を省略することはできません。 小数点は、指数を含めた場合にのみ省略できます。 空白文字で定数の数値または文字を分離することはできません。

次の例では、浮動小数点定数と式のフォームをいくつか示します。

```C
15.75
1.575E1   /* = 15.75   */
1575e-2   /* = 15.75   */
-2.5e-3   /* = -0.0025 */
25E-4     /* =  0.0025 */
```

浮動小数点定数は、負符号 ( **`-`** ) が前にない限り、正の値です。 この場合、負符号は単項算術否定演算子として扱われます。 浮動小数点定数には、 **`float`** 、 **`double`** 、または **`long double`** 型があります。

**`f`** 、 **`F`** 、 **`l`** 、または **`L`** のサフィックスのない浮動小数点定数の型は **`double`** になります。 文字 **`f`** または **`F`** がサフィックスの場合、定数の型は **`float`** になります。 末尾に文字 **`l`** または **`L`** が付いている場合、 **`long double`** 型になります。 次に例を示します。

```C
10.0L  /* Has type long double  */
10.0   /* Has type double       */
10.0F  /* Has type float        */
```

Microsoft C コンパイラでは、内部で **`long double`** と **`double`** を同じ型として表します。 ただし、これらの型は異なります。 **`double`** 、 **`float`** 、および **`long double`** 型については、[基本型の格納](../c-language/storage-of-basic-types.md)に関するページを参照してください。

次の例に示すように、浮動小数点定数の整数の部分を省略できます。 数値 0.75 は、次のようなさまざまな方法で表現できます。

```C
.0075e2
0.075e1
.075e1
75e-2
```

## <a name="see-also"></a>関連項目

[C の定数](../c-language/c-constants.md)
