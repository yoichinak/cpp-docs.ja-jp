---
description: '詳細については、次を参照してください: iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l'
title: iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l
ms.date: 4/2/2020
api_name:
- iscntrl
- _iswcntrl_l
- _iscntrl_l
- iswcntrl
- _o_iscntrl
- _o_iswcntrl
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _istcntrl_l
- _iswcntrl_l
- iswcntrl
- _iscntrl_l
- iscntrl
- _istcntrl
helpviewer_keywords:
- iscntrl function
- _iscntrl_l function
- _iswcntrl_l function
- _istcntrl function
- istcntrl function
- iswcntrl function
- _istcntrl_l function
ms.assetid: 616eebf9-aed4-49ba-ba2c-8677c8fe6fb5
ms.openlocfilehash: b4dcba09b139d1ad1c80e495477a6b7b2283e3f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332712"
---
# <a name="iscntrl-iswcntrl-_iscntrl_l-_iswcntrl_l"></a>iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l

整数が制御文字を表すかどうかを判定します。

## <a name="syntax"></a>構文

```C
int iscntrl(
   int c
);
int iswcntrl(
   wint_t c
);
int _iscntrl_l(
   int c,
   _locale_t locale
);
int _iswcntrl_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*c*<br/>
テストする整数

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

これらの各ルーチンは、 *c* が制御文字の特殊表現である場合は0以外の値を返します。 *c* が制御文字 (0X00-0x1f または 0x7f) の場合、 **iscntrl** は0以外の値を返します。 *c* が制御ワイド文字の場合、 **iswcntrl** は0以外の値を返します。 これらの各ルーチンは、 *c* がテスト条件を満たしていない場合は0を返します。

**_L** サフィックスを持つこれらの関数のバージョンでは、現在のロケールの代わりに渡されたロケールパラメーターを使用します。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

*C* が EOF でない場合、または 0 ~ 0xff の範囲内にある場合、 **iscntrl** と **_iscntrl_l** の動作は未定義です。 デバッグ CRT ライブラリが使用され、 *c* がこれらの値のいずれでもない場合、関数はアサーションを発生させます。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istcntrl**|**iscntrl**|**iscntrl**|**iswcntrl**|
|**_istcntrl_l**|**_iscntrl_l**|**_iscntrl_l**|**_iswcntrl_l**|

## <a name="remarks"></a>解説

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**iscntrl**|\<ctype.h>|
|**iswcntrl**|\<ctype.h> または \<wchar.h>|
|**_iscntrl_l**|\<ctype.h>|
|**_iswcntrl_l**|\<ctype.h> または \<wchar.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[文字分類](../../c-runtime-library/character-classification.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[is、isw ルーチン](../../c-runtime-library/is-isw-routines.md)<br/>
