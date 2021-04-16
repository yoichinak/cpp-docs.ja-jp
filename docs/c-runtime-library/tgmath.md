---
title: ジェネリック型数値演算
description: 引数の型に基づいて、右の数値演算関数を呼び出す C コードを簡単に記述できるようにする <tgmath.h>> のマクロについて説明します。
ms.topic: conceptual
ms.date: 12/10/2020
helpviewer_keywords:
- CRT tgmath.h
ms.openlocfilehash: 38d6e5fba1f2087f692d7b18526f5da43d0683e1
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577219"
---
# <a name="type-generic-math"></a>ジェネリック型数値演算

ISO C Standard 11 (C11) 以降では、 `<tgmath.h>` ヘッダーにやを含めることに加えて、 `<math.h>` `<complex.h>` パラメーターの型に基づいて対応する数学関数を呼び出すマクロが用意されています。

C ランタイムライブラリの数学関数は、実際には複雑なバリアント型になっています。 各バリアントには、引数の型 `float` (、 `double` 、および) に応じて、3つのフレーバーがあり `long double` ます。 C では C++ と同様のオーバーロードがサポートされていないため、各バリアントには異なる名前が付いています。 たとえば、実数の浮動小数点値の絶対値を取得するには、、、のいずれかの `fabsf` `fabs` 値を `fabsl` 渡しているかどうかに応じて、、、またはを呼び出し `float` `double` `long double` ます。 複雑な絶対値を取得するには、、、のいずれかのを、 `cabsf` `cabs` それぞれ、、およびの各 `cabsl` 複合値を渡しているかどうかに応じて呼び出し `float` `double` `long double` ます。 引数が上記のいずれの型とも一致しない場合、関数は、引数が2倍になっているかのように選択されます。

`<tgmath.h>` 呼び出す右の算術関数の選択を簡略化するマクロが含まれています。 マクロは、渡された型を調べてから、right 関数を呼び出します。 たとえば、マクロは `sqrt` にバインドされ `sqrt(9.9f)` `sqrtf()` ますが、 `sqrt(9.9)` にバインドさ `sqrt()` れます。 ジェネリックパラメーターの1つ以上のマクロ引数が複雑な場合、マクロは複合関数にバインドされます。それ以外の場合は、実際の関数を呼び出します。

の型汎用マクロを使用すると、 `<tgmath.h>` 引数の型に応じてキャストを管理したり、異なる関数名を選択したりする必要がないため、移植性の高いコードを記述できます。

これらのマクロは、ヘッダーを使用して記述されたプログラムが中断しないように、独自のヘッダーに含まれてい `<math.h>` ます。 では、常にを含めるように `double x = sin(42);` 動作し \<math.h> ます。 `<tgmath.h>`ただし、またはではなく、ヘッダーが含まれている場合、既存の C プログラムのほとんどは影響を受けませ `<math.h>` `<complex.h>` ん。

次の表に、で使用できるマクロ `<tgmath.h>` とその展開方法を示します。 `modf` は、対応する型汎用マクロを持たないため、このテーブルには含まれません。これは、複雑な型解決を行わずに安全にする方法が明確でないためです。

|マクロ  |Real</br>`float`  | Real</br>`double` | Real</br>`long double` | 複合</br>`float` | 複合</br>`double` | 複合</br>`long double` |
|---------|---------|---------|---------|---------|---------|---------|
`acos` | [`acosf`](reference/mbsnbicmp-mbsnbicmp-l.md) | [`acos`](reference/mbsnbicmp-mbsnbicmp-l.md) | [`acosl`](reference/mbsnbicmp-mbsnbicmp-l.md) | [`cacosf`](reference/cacos-cacosf-cacosl.md) | [`cacos`](reference/cacos-cacosf-cacosl.md) | [`cacosl`](reference/cacos-cacosf-cacosl.md) |
`acosh` | [`acoshf`](reference/acosh-acoshf-acoshl.md) | [`acosh`](reference/acosh-acoshf-acoshl.md) | [`acoshl`](reference/acosh-acoshf-acoshl.md) | [`cacoshf`](reference/cacosh-cacoshf-cacoshl.md) | [`cacosh`](reference/cacosh-cacoshf-cacoshl.md) | [`cacoshl`](reference/cacosh-cacoshf-cacoshl.md) |
`asin` | [`asinf`](reference/asin-asinf-asinl.md) | [`asin`](reference/asin-asinf-asinl.md) | [`asinl`](reference/asin-asinf-asinl.md) | [`casinf`](reference/casin-casinf-casinl.md) | [`casin`](reference/casin-casinf-casinl.md) | [`casinl`](reference/casin-casinf-casinl.md) |
`asinh` | [`asinhf`](reference/asin-asinf-asinl.md) | [`asinh`](reference/asin-asinf-asinl.md) | [`asinhl`](reference/asin-asinf-asinl.md) | [`casinhf`](reference/casinh-casinhf-casinhl.md) | [`casinh`](reference/casinh-casinhf-casinhl.md) | [`casinhl`](reference/casinh-casinhf-casinhl.md) |
`atan` | [`atanf`](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`atan`](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`atanl`](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`catanf`](reference/catan-catanf-catanl.md) | [`catan`](reference/catan-catanf-catanl.md) | [`catanl`](reference/catan-catanf-catanl.md) |
`atanh` | [`atanhf`](reference/atanh-atanhf-atanhl.md) | [`atanh`](reference/atanh-atanhf-atanhl.md) | [`atanhl`](reference/atanh-atanhf-atanhl.md) | [`catanhf`](reference/catanh-catanhf-catanhl.md) | [`catanh`](reference/catanh-catanhf-catanhl.md) | [`catanhl`](reference/catanh-catanhf-catanhl.md) |
`cos` | [`cosf`](reference/cos-cosf-cosl.md) | [`cos`](reference/cos-cosf-cosl.md) | [`cosl`](reference/cos-cosf-cosl.md) | [`ccosf`](reference/ccos-ccosf-ccosl.md) | [`ccos`](reference/ccos-ccosf-ccosl.md) | [`ccosl`](reference/ccos-ccosf-ccosl.md) |
`cosh` | [`coshf`](reference/cosh-coshf-coshl.md) | [`cosh`](reference/cosh-coshf-coshl.md) | [`coshl`](reference/cosh-coshf-coshl.md) | [`ccoshf`](reference/ccosh-ccoshf-ccoshl.md) | [`ccosh`](reference/ccosh-ccoshf-ccoshl.md) | [`ccoshl`](reference/ccosh-ccoshf-ccoshl.md) |
`exp` | [`expf`](reference/exp-expf.md) | [`exp`](reference/exp-expf.md) | [`expl`](reference/exp-expf.md) | [`cexpf`](reference/cexp-cexpf-cexpl.md) | [`cexp`](reference/cexp-cexpf-cexpl.md) | [`cexpl`](reference/cexp-cexpf-cexpl.md) |
`fabs` | [`fabsf`](reference/fabs-fabsf-fabsl.md) | [`fabs`](reference/fabs-fabsf-fabsl.md) | [`fabsl`](reference/fabs-fabsf-fabsl.md) | [`cabsf`](reference/cabs-cabsf-cabsl.md) | [`cabs`](reference/cabs-cabsf-cabsl.md) | [`cabsl`](reference/cabs-cabsf-cabsl.md) |
`log` | [`logf`](reference/log-logf-log10-log10f.md) | [`log`](reference/log-logf-log10-log10f.md) | [`logl`](reference/log-logf-log10-log10f.md) | [`clogf`](reference/clog-clogf-clogl.md) | [`clog`](reference/clog-clogf-clogl.md) | [`clogl`](reference/clog-clogf-clogl.md) |
`pow` | [`powf`](reference/pow-powf-powl.md) | [`pow`](reference/pow-powf-powl.md) | [`powl`](reference/pow-powf-powl.md) | [`cpowf`](reference/cpow-cpowf-cpowl.md) | [`cpow`](reference/cpow-cpowf-cpowl.md) | [`cpowl`](reference/cpow-cpowf-cpowl.md) |
`sin` | [`sinf`](reference/sin-sinf-sinl.md) | [`sin`](reference/sin-sinf-sinl.md) | [`sinl`](reference/sin-sinf-sinl.md) | [`csinf`](reference/csin-csinf-csinl.md) | [`csin`](reference/csin-csinf-csinl.md) | [`csinl`](reference/csin-csinf-csinl.md) |
`sinh` | [`sinhf`](reference/sinh-sinhf-sinhl.md) | [`sinh`](reference/sinh-sinhf-sinhl.md) | [`sinhl`](reference/sinh-sinhf-sinhl.md) | [`csinhf`](reference/csinh-csinhf-csinhl.md) | [`csinh`](reference/csinh-csinhf-csinhl.md) | [`csinhl`](reference/csinh-csinhf-csinhl.md) |
`sqrt` | [`sqrtf`](reference/sqrt-sqrtf-sqrtl.md) | [`sqrt`](reference/sqrt-sqrtf-sqrtl.md) | [`sqrtl`](reference/sqrt-sqrtf-sqrtl.md) | [`csqrtf`](reference/csqrt-csqrtf-csqrtl.md) | [`csqrt`](reference/csqrt-csqrtf-csqrtl.md) | [`csqrtl`](reference/csqrt-csqrtf-csqrtl.md) |
`tan` | [`tanf`](reference/tan-tanf-tanl.md) | [`tan`](reference/tan-tanf-tanl.md) | [`tanl`](reference/tan-tanf-tanl.md) | [`ctanf`](reference/ctan-ctanf-ctanl.md) | [`ctan`](reference/ctan-ctanf-ctanl.md) | [`ctanl`](reference/ctan-ctanf-ctanl.md) |
`tanh` | [`tanhf`](reference/tanh-tanhf-tanhl.md) | [`tanh`](reference/tanh-tanhf-tanhl.md) | [`tanhl`](reference/tanh-tanhf-tanhl.md) | [`ctanhf`](reference/ctanh-ctanhf-ctanhl.md) | [`ctanh`](reference/ctanh-ctanhf-ctanhl.md) | [`ctanhl`](reference/ctanh-ctanhf-ctanhl.md) |
`atan2` | [`atan2f`](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`atan2`](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`atan2l`](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | - | - | - |
`cbrt` | [`cbrtf`](reference/cbrt-cbrtf-cbrtl.md) | [`cbrt`](reference/cbrt-cbrtf-cbrtl.md) | [`cbrtl`](reference/cbrt-cbrtf-cbrtl.md) | - | - | - |
`ceil` | [`ceilf`](reference/ceil-ceilf-ceill.md) | [`ceil`](reference/ceil-ceilf-ceill.md) | [`ceill`](reference/ceil-ceilf-ceill.md) | - | - | - |
`copysign` | [`copysignf`](reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md) | [`copysign`](reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md) | [`copysignl`](reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md) | - | - | - |
`erf` | [`erff`](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [`erf`](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [`erfl`](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | - | - | - |
`erfc` | [`erfcf`](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [`erfc`](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [`erfcl`](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | - | - | - |
`exp2` | [`exp2f`](reference/exp2-exp2f-exp2l.md) | [`exp2`](reference/exp2-exp2f-exp2l.md) | [`exp2l`](reference/exp2-exp2f-exp2l.md) | - | - | - |
`expm1` | [`expm1f`](reference/expm1-expm1f-expm1l.md) | [`expm1`](reference/expm1-expm1f-expm1l.md) | [`expm1l`](reference/expm1-expm1f-expm1l.md) | - | - | - |
`fdim` | [`fdimf`](reference/fdim-fdimf-fdiml.md) | [`fdim`](reference/fdim-fdimf-fdiml.md) | [`fdiml`](reference/fdim-fdimf-fdiml.md) | - | - | - |
`floor` | [`floorf`](reference/floor-floorf-floorl.md) | [`floor`](reference/floor-floorf-floorl.md) | [`floorl`](reference/floor-floorf-floorl.md) | - | - | - |
`fma` | [`fmaf`](reference/fma-fmaf-fmal.md) | [`fma`](reference/fma-fmaf-fmal.md) | [`fmal`](reference/fma-fmaf-fmal.md) | - | - | - |
`fmax` | [`fmaxf`](reference/fmax-fmaxf-fmaxl.md) | [`fmax`](reference/fmax-fmaxf-fmaxl.md) | [`fmaxl`](reference/fmax-fmaxf-fmaxl.md) | - | - | - |
`fmin` | [`fminf`](reference/fmin-fminf-fminl.md) | [`fmin`](reference/fmin-fminf-fminl.md) | [`fminl`](reference/fmin-fminf-fminl.md) | - | - | - |
`fmod` | [`fmodf`](reference/fmod-fmodf.md) | [`fmod`](reference/fmod-fmodf.md) | [`fmodl`](reference/fmod-fmodf.md) | - | - | - |
`frexp` | [`frexpf`](reference/frexp.md) | [`frexp`](reference/frexp.md) | [`frexpl`](reference/frexp.md) | - | - | - |
`hypot` | [`hypotf`](reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md) | [`hypot`](reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md) | [`hypotl`](reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md) | - | - | - |
`ilogb` | [`ilogbf`](reference/ilogb-ilogbf-ilogbl2.md) | [`ilogb`](reference/ilogb-ilogbf-ilogbl2.md) | [`ilogbl`](reference/ilogb-ilogbf-ilogbl2.md) | - | - | - |
`ldexp` | [`ldexpf`](reference/ldexp.md) | [`ldexp`](reference/ldexp.md) | [`ldexpl`](reference/ldexp.md) | - | - | - |
`lgamma` | [`lgammaf`](reference/lgamma-lgammaf-lgammal.md) | [`lgamma`](reference/lgamma-lgammaf-lgammal.md) | [`lgammal`](reference/lgamma-lgammaf-lgammal.md) | - | - | - |
`llrint` | [`llrintf`](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [`llrint`](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [`llrintl`](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | - | - | - |
`llround` | [`llroundf`](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [`llround`](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [`llroundl`](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | - | - | - |
`log10` | [`log10f`](reference/log-logf-log10-log10f.md) | [`log10`](reference/log-logf-log10-log10f.md) | [`log10l`](reference/log-logf-log10-log10f.md) | - | - | - |
`log1p` | [`log1pf`](reference/log1p-log1pf-log1pl2.md) | [`log1p`](reference/log1p-log1pf-log1pl2.md) | [`log1pl`](reference/log1p-log1pf-log1pl2.md) | - | - | - |
`log2` | [`log2f`](reference/log2-log2f-log2l.md) | [`log2`](reference/log2-log2f-log2l.md) | [`log2l`](reference/log2-log2f-log2l.md) | - | - | - |
`logb` | [`logbf`](reference/logb-logbf-logbl-logb-logbf.md) | [`logb`](reference/logb-logbf-logbl-logb-logbf.md) | [`logbl`](reference/logb-logbf-logbl-logb-logbf.md) | - | - | - |
`lrint` | [`lrintf`](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [`lrint`](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [`lrintl`](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | - | - | - |
`lround` | [`lroundf`](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [`lround`](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [`lroundl`](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | - | - | - |
`nearbyint` | [`nearbyintf`](reference/nearbyint-nearbyintf-nearbyintl1.md) | [`nearbyint`](reference/nearbyint-nearbyintf-nearbyintl1.md) | [`nearbyintl`](reference/nearbyint-nearbyintf-nearbyintl1.md) | - | - | - |
`nextafter` | [`nextafterf`](reference/nextafter-functions.md) | [`nextafter`](reference/nextafter-functions.md) | [`nextafterl`](reference/nextafter-functions.md) | - | - | - |
`nexttoward` | [`nexttowardf`](reference/nextafter-functions.md) | [`nexttoward`](reference/nextafter-functions.md) | [`nexttowardl`](reference/nextafter-functions.md) | - | - | - |
`remainder` | [`remainderf`](reference/remainder-remainderf-remainderl.md) | [`remainder`](reference/remainder-remainderf-remainderl.md) | [`remainderl`](reference/remainder-remainderf-remainderl.md) | - | - | - |
`remquo` | [`remquof`](reference/remquo-remquof-remquol.md) | [`remquo`](reference/remquo-remquof-remquol.md) | [`remquol`](reference/remquo-remquof-remquol.md) | - | - | - |
`rint` | [`rintf`](reference/rint-rintf-rintl.md) | [`rint`](reference/rint-rintf-rintl.md) | [`rintl`](reference/rint-rintf-rintl.md) | - | - | - |
`round` | [`roundf`](reference/round-roundf-roundl.md) | [`round`](reference/round-roundf-roundl.md) | [`roundl`](reference/round-roundf-roundl.md) | - | - | - |
`scalbln` | [`scalblnf`](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [`scalbln`](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [`scalblnl`](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | - | - | - |
`scalbn` | [`scalbnf`](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [`scalbn`](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [`scalbnl`](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | - | - | - |
`tgamma` | [`tgammaf`](reference/tgamma-tgammaf-tgammal.md) | [`tgamma`](reference/tgamma-tgammaf-tgammal.md) | [`tgammal`](reference/tgamma-tgammaf-tgammal.md) | - | - | - |
`trunc` | [`truncf`](reference/trunc-truncf-truncl.md) | [`trunc`](reference/trunc-truncf-truncl.md) | [`truncl`](reference/trunc-truncf-truncl.md) | - | - | - |
`carg` | - | - | - | [`cargf`](reference/carg-cargf-cargl.md) | [`carg`](reference/carg-cargf-cargl.md) | [`cargl`](reference/carg-cargf-cargl.md) |
`conj` | - | - | - | [`conjf`](reference/conj-conjf-conjl.md) | [`conj`](reference/conj-conjf-conjl.md) | [`conjl`](reference/conj-conjf-conjl.md) |
`creal` | - | - | - | [`crealf`](reference/creal-crealf-creall.md) | [`creal`](reference/creal-crealf-creall.md) | [`creall`](reference/creal-crealf-creall.md) |
`cimag` | - | - | - | [`cimagf`](reference/cimag-cimagf-cimagl.md) | [`cimag`](reference/cimag-cimagf-cimagl.md) | [`cimagl`](reference/cimag-cimagf-cimagl.md) |
`cproj` | - | - | - | [`cprojf`](reference/cproj-cprojf-cprojl.md) | [`cproj`](reference/cproj-cprojf-cprojl.md) | [`cprojl`](reference/cproj-cprojf-cprojl.md) |

## <a name="requirements"></a>要件

[std: c++ 11](../build/reference/std-specify-language-standard-version.md) 以降が必要です。

Windows SDK バージョン 10.0.20201.0 以降。 現在、これは Insider ビルドで、 [Windows Insider Preview ダウンロード](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK)からダウンロードできます。 この SDK をインストールして使用する方法については、「 [C11 And C17: はじめに](https://devblogs.microsoft.com/cppblog/c11-and-c17-standard-support-arriving-in-msvc/#c11-and-c17-getting-started) 」を参照してください。

## <a name="see-also"></a>関連項目

[C Run-Time ライブラリリファレンス](c-run-time-library-reference.md)
