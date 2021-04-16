---
title: exp、expf、expl
description: Exp、tf、および金の API リファレンス指数を計算します。
ms.date: 1/15/2021
api_name:
- expf
- expl
- exp
- _o_exp
- _o_expf
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
- _expl
- expf
- expl
- exp
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.openlocfilehash: 20a22600d068569468b764ff07519d4292afbfea
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577206"
---
# <a name="exp-expf-expl"></a>`exp`, `expf`, `expl`

指数を計算します。

## <a name="syntax"></a>構文

```C
double exp(
   double x
);
float exp(
   float x
);  // C++ only
long double exp(
   long double x
);  // C++ only
float expf(
   float x
);
long double expl(
   long double x
);
#define exp(z) // Requires C11 or higher
```

### <a name="parameters"></a>パラメーター

*`x`*\
自然対数 *の底を* exponentiate する浮動小数点値。

## <a name="return-value"></a>戻り値

関数は、 **`exp`** 浮動小数点パラメーターの指数値 ( *`x`* 成功した場合) を返します。 つまり、結果は e です <sup>*`x`*</sup> 。ここで、 *e* は自然対数の底です。 オーバーフローの場合、関数は `INF` (無限大) を返し、アンダーフローでは **`exp`** 0 を返します。

|入力|SEH 例外|`Matherr` 例外的|
|-----------|-------------------|-----------------------|
|± Quiet NaN、不確定|なし|`_DOMAIN`|
|±無限大|`INVALID`|`_DOMAIN`|
|x ≥ 7.097827e+002|`INEXACT+OVERFLOW`|`OVERFLOW`|
|X ≤ -7.083964e+002|`INEXACT+UNDERFLOW`|`UNDERFLOW`|

関数には、 **`exp`** ストリーミング SIMD 拡張命令 2 (SSE2) を使用する実装があります。 [`_set_SSE2_enable`](set-sse2-enable.md)SSE2 実装の使用に関する情報と制限については、「」を参照してください。

## <a name="remarks"></a>解説

C++ ではオーバーロードが可能であるため、 **`exp`** または引数を受け取るのオーバーロードを呼び出すことができ **`float`** **`long double`** ます。 C プログラムでは、 `<tgmath.h>` この関数を呼び出すためにマクロを使用している場合を除き、は **`exp`** 常にを受け取り、を返し **`double`** ます。

マクロを使用する場合 `<tgmath.h>` `exp()` 、引数の型によって、どのバージョンの関数が選択されているかが決まります。 詳細については [、「型汎用の算術演算](../../c-runtime-library/tgmath.md) 」を参照してください。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>要件

|機能|必須の C ヘッダー|必須の C++ ヘッダー|
|--------------|---------------------|---|
|**`exp`**, **`expf`**, **`expl`**|`<math.h>`|`<cmath>` または `<math.h>`|
|**`exp`** マクロ| `<tgmath.h>` ||

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="example"></a>例

```C
// crt_exp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.302585093, y;

   y = exp( x );
   printf( "exp( %f ) = %f\n", x, y );
}
```

```Output
exp( 2.302585 ) = 10.000000
```

## <a name="see-also"></a>関連項目

[浮動小数点のサポート](../../c-runtime-library/floating-point-support.md)\
[`log, logf, log10, log10f`](log-logf-log10-log10f.md)\
[`_CIexp`](../../c-runtime-library/ciexp.md)
