---
description: '詳細については、次を参照してください: strcpy_s、wcscpy_s、_mbscpy_s、_mbscpy_s_l'
title: strcpy_s、wcscpy_s、_mbscpy_s、_mbscpy_s_l
ms.date: 5/28/2020
api_name:
- wcscpy_s
- _mbscpy_s
- _mbscpy_s_l
- strcpy_s
- _o__mbscpy_s
- _o__mbscpy_s_l
- _o_strcpy_s
- _o_wcscpy_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strcpy_s
- _mbscpy_s
- _mbscpy_s_l
- _tcscpy_s
- wcscpy_s
helpviewer_keywords:
- strcpy_s function
- _tcscpy_s function
- _mbscpy_s function
- _mbscpy_s_l function
- copying strings
- strings [C++], copying
- tcscpy_s function
- wcscpy_s function
ms.assetid: 611326f3-7929-4a5d-a465-a4683af3b053
ms.openlocfilehash: 3cbfa2b2f8450adf07b2040fb2be0932377c9e37
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539563"
---
# <a name="strcpy_s-wcscpy_s-_mbscpy_s-_mbscpy_s_l"></a>`strcpy_s`、 `wcscpy_` 、、 `_mbscpy_s``_mbscpy_s_l`

文字列をコピーします。 これらのバージョン[ `strcpy` `wcscpy` `_mbscpy` のでは](strcpy-wcscpy-mbscpy.md)、「 [CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されています。

> [!IMPORTANT]
> **`_mbscpy_s`** およびは **`_mbscpy_s_l`** 、Windows ランタイムで実行されるアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
errno_t strcpy_s(
   char *dest,
   rsize_t dest_size,
   const char *src
);
errno_t wcscpy_s(
   wchar_t *dest,
   rsize_t dest_size,
   const wchar_t *src
);
errno_t _mbscpy_s(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src
);
errno_t _mbscpy_s_l(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src,
   _locale_t locale
);
```

```cpp
// Template functions are C++ only:
template <size_t size>
errno_t strcpy_s(
   char (&dest)[size],
   const char *src
); // C++ only
template <size_t size>
errno_t wcscpy_s(
   wchar_t (&dest)[size],
   const wchar_t *src
); // C++ only
template <size_t size>
errno_t _mbscpy_s(
   unsigned char (&dest)[size],
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbscpy_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>パラメーター

*`dest`*<br/>
追加先の文字列バッファーの場所。

*`dest_size`*<br/>
ナロー関数とマルチバイト関数の場合は、ターゲット文字列バッファーのサイズ **`char`** (単位)、 **`wchar_t`** ワイド関数の場合は単位です。 この値は0より大きく、を超えることはできません **`RSIZE_MAX`** 。 このサイズのアカウントで、文字列の後に続くが使用されていることを確認し `NULL` ます。

*`src`*<br/>
null で終わる元の文字列バッファー。

*`locale`*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

正常に終了した場合は 0 を返し、それ以外の場合はエラーを返します。

### <a name="error-conditions"></a>エラー条件

|*`dest`*|*`dest_size`*|*`src`*|戻り値|の内容 *`dest`*|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**`NULL`**|any|any|**`EINVAL`**|変更されない|
|any|any|**`NULL`**|**`EINVAL`**|*`dest[0]`* 0に設定|
|any|0 または小さすぎる|any|**`ERANGE`**|*`dest[0]`* 0に設定|

## <a name="remarks"></a>注釈

関数は、 **`strcpy_s`** 終端の null 文字を含むのアドレスの内容を、 *`src`* で指定した場所にコピーし *`dest`* ます。 コピー先の文字列には、コピー元の文字列とその終端の NULL 文字を保持できるサイズが必要です。 **`strcpy_s`** コピー元とコピー先の文字列が重なり合っている場合、の動作は未定義です。

**`wcscpy_s`** はのワイド文字バージョンであり、 **`strcpy_s`** **`_mbscpy_s`** はマルチバイト文字バージョンです。 の引数は **`wcscpy_s`** ワイド文字列で、およびの引数は **`_mbscpy_s`** **`_mbscpy_s_l`** マルチバイト文字列です。 それ以外では、これらの関数の動作は同じです。 **`_mbscpy_s_l`** はと同じですが、 **`_mbscpy_s`** 現在のロケールの代わりに渡されたロケールパラメーターを使用する点が異なります。 詳細については、「[`locale`](../../c-runtime-library/locale.md)」を参照してください。

またはが null ポインターの場合、または *`dest`* *`src`* コピー先の文字列サイズ *`dest_size`* が小さすぎる場合は、「 [パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、またはが null ポインターの場合、これらの関数はを返し、を **`EINVAL`** **`errno`** に設定 **`EINVAL`** *`dest`* *`src`* し **`ERANGE`** **`errno`** **`ERANGE`** ます。コピー先の文字列が小さすぎる場合、はを返し、をに設定します。

正常に実行されると、コピー先の文字列は常に NULL で終わります。

C++ では、これらの関数をより簡単に使用できます。これはバッファー長を自動的に推論できるテンプレートのオーバーロードにより可能です。その結果、サイズの引数を指定する必要がなくなります。また、セキュリティが万全ではない以前の関数は、セキュリティが強化された新しい関数に自動的に置き換わります。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

これらの関数のデバッグライブラリバージョンは、最初にバッファーを0xFE で埋めます。 この動作を無効にするには、を使用し [`_CrtSetDebugFillThreshold`](crtsetdebugfillthreshold.md) ます。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|`TCHAR.H` ルーチン|`_UNICODE` & `_MBCS` 未定義|`_MBCS` れ|`_UNICODE` れ|
|---------------------|------------------------------------|--------------------|-----------------------|
|**`_tcscpy_s`**|**`strcpy_s`**|**`_mbscpy_s`**|**`wcscpy_s`**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**`strcpy_s`**|`<string.h>`|
|**`wcscpy_s`**|`<string.h>` または `<wchar.h>`|
|**`_mbscpy_s`**|`<mbstring.h>`|

これらの関数は、Microsoft 固有の関数です。 互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

実稼働品質コードとは異なり、このサンプルでは、エラーをチェックせずに、セキュリティで保護された文字列関数を呼び出します。

```C
// crt_strcpy_s.c
// Compile by using: cl /W4 crt_strcpy_s.c
// This program uses strcpy_s and strcat_s
// to build a phrase.

#include <string.h>     // for strcpy_s, strcat_s
#include <stdlib.h>     // for _countof
#include <stdio.h>      // for printf
#include <errno.h>      // for return values

int main(void)
{
    char stringBuffer[80];

    strcpy_s(stringBuffer, _countof(stringBuffer), "Hello world from ");
    strcat_s(stringBuffer, _countof(stringBuffer), "strcpy_s ");
    strcat_s(stringBuffer, _countof(stringBuffer), "and ");
    strcat_s(stringBuffer, _countof(stringBuffer), "strcat_s!");

    printf("stringBuffer = %s\n", stringBuffer);
}
```

```Output
stringBuffer = Hello world from strcpy_s and strcat_s!
```

C++ コードをビルドするときに、テンプレートのバージョンを使いやすくすることができます。

```cpp
// crt_wcscpy_s.cpp
// Compile by using: cl /EHsc /W4 crt_wcscpy_s.cpp
// This program uses wcscpy_s and wcscat_s
// to build a phrase.

#include <cstring>  // for wcscpy_s, wcscat_s
#include <cstdlib>  // for _countof
#include <iostream> // for cout, includes <cstdlib>, <cstring>
#include <errno.h>  // for return values

int main(void)
{
    wchar_t stringBuffer[80];
    // using template versions of wcscpy_s and wcscat_s:
    wcscpy_s(stringBuffer, L"Hello world from ");
    wcscat_s(stringBuffer, L"wcscpy_s ");
    wcscat_s(stringBuffer, L"and ");
    // of course we can supply the size explicitly if we want to:
    wcscat_s(stringBuffer, _countof(stringBuffer), L"wcscat_s!");

    std::wcout << L"stringBuffer = " << stringBuffer << std::endl;
}
```

```Output
stringBuffer = Hello world from wcscpy_s and wcscat_s!
```

## <a name="see-also"></a>こちらもご覧ください

[文字列操作](../../c-runtime-library/string-manipulation-crt.md) <br/>
[`strcat`, `wcscat`, `_mbscat`, `_mbscat_l`](strcat-wcscat-mbscat.md) <br/>
[`strcmp`, `wcscmp`, `_mbscmp`, `_mbscmp_l`](strcmp-wcscmp-mbscmp.md) <br/>
[`strncat_s`, `_strncat_s_l`, `wcsncat_s`, `_wcsncat_s_l`, `_mbsncat_s`, `_mbsncat_s_l`](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md) <br/>
[`strncmp`, `wcsncmp`, `_mbsncmp`, `_mbsncmp_l`](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md) <br/>
[`strncpy_s`, `_strncpy_s_l`, `wcsncpy_s`, `_wcsncpy_s_l`, `_mbsncpy_s`, `_mbsncpy_s_l`](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md) <br/>
[`_strnicmp`, `_wcsnicmp`, `_mbsnicmp`, `_strnicmp_l`, `_wcsnicmp_l`, `_mbsnicmp_l`](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md) <br/>
[`strrchr`, `wcsrchr`, `_mbsrchr`, `_mbsrchr_l`](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md) <br/>
[`strspn`, `wcsspn`, `_mbsspn`, `_mbsspn_l`](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
