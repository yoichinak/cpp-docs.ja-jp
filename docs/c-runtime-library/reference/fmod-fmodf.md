---
title: fmod、fmodf、fmodl
description: Fmod、fmodf、および fmodl の API リファレンスこれは、浮動小数点の剰余を計算します。
ms.date: 1/15/2021
api_name:
- fmod
- fmodf
- fmodl
- _o_fmod
- _o_fmodf
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fmod
- _fmodl
- fmodf
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.openlocfilehash: 02089e44f1eca66ef5452b73144bfe670e20cd94
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577366"
---
# <a name="fmod-fmodf-fmodl"></a>`fmod`, `fmodf`, `fmodl`

浮動小数点の剰余を計算します。

## <a name="syntax"></a>構文

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);

#define fmod(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>パラメーター

*`x`*, *`y`*\
浮動小数点値。

## <a name="return-value"></a>戻り値

**`fmod`** の浮動小数点の剰余を返し *`x`*  /  *`y`* ます。 の値が0.0 の場合、は簡易 *`y`* **`fmod`** な NaN を返します。 ファミリによる簡易な NaN の表現については **`printf`** 、「 [printf](printf-printf-l-wprintf-wprintf-l.md)」を参照してください。

## <a name="remarks"></a>解説

関数は、 **`fmod`**  *`x`*  /  *`y`* *`x`*  =  *i* \* *`y`*  +  *`f`* ( *`i`* は整数)、は *`f`* と同じ符号を持ち、 *`x`* の絶対値は *`f`* の絶対値よりも小さく *`y`* なるように、の浮動小数点の剰余 f を計算します。

C++ ではオーバーロードが可能であるため、との値を受け取って返すのオーバーロードを呼び出すことができ **`fmod`** **`float`** **`long double`** ます。 C プログラムでは、 `<tgmath.h>` この関数を呼び出すためにマクロを使用している場合を除き、は **`fmod`** 常に2つの引数を受け取り、を **`double`** 返し **`double`** ます。

マクロを使用する場合 `<tgmath.h>` `fmod()` 、引数の型によって、どのバージョンの関数が選択されているかが決まります。 詳細については [、「型汎用の算術演算](../../c-runtime-library/tgmath.md) 」を参照してください。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>要件

|機能|必須ヘッダー|
|--------------|---------------------|
|**`fmod`**, **`fmodf`**, **`fmodl`**|`<math.h>`|
|**`fmod`** マクロ | `<tgmath.h>` |

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="example"></a>例

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>関連項目

[浮動小数点のサポート](../../c-runtime-library/floating-point-support.md)\
[`ceil, ceilf, ceill`](ceil-ceilf-ceill.md)\
[`fabs, fabsf, fabsl`](fabs-fabsf-fabsl.md)\
[`floor, floorf, floorl`](floor-floorf-floorl.md)\
[`_CIfmod`](../../c-runtime-library/cifmod.md)
