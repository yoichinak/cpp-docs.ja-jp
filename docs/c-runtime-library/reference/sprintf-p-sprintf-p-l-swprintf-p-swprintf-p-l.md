---
description: '詳細については、次を参照してください: _sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l'
title: _sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l
ms.date: 3/9/2021
api_name:
- _sprintf_p
- _swprintf_p_l
- _swprintf_p
- _sprintf_p_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _sprintf_p
- _swprintf_p_l
- _sprintf_p_l
- _swprintf_p
- sprintf_p
- swprint_p_l
- swprintf_p
- swprintf_p_l
helpviewer_keywords:
- sprintf_p_l function
- swprintf_p function
- swprintf_p_l function
- _sprintf_p function
- _sprintf_p_l function
- _swprintf_p function
- sprintf_p function
- _stprintf_p function
- stprintf_p function
- _swprintf_p_l function
- stprintf_p_l function
- formatted text [C++]
- _stprintf_p_l function
ms.openlocfilehash: 2f0b6dad129a8f3f2f91bf1244c77ae5691a679e
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539270"
---
# <a name="_sprintf_p-_sprintf_p_l-_swprintf_p-_swprintf_p_l"></a>`_sprintf_p`, `_sprintf_p_l`, `_swprintf_p`, `_swprintf_p_l`

パラメーターが書式文字列で使用される順序を指定できる文字列に、書式付きデータを書き込みます。

## <a name="syntax"></a>構文

```C
int _sprintf_p(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format [,
   argument_list]
);
int _sprintf_p_l(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   locale_t locale [,
   argument_list]
);
int _swprintf_p(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format [,
   argument_list]
);
int _swprintf_p_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   locale_t locale [,
   argument_list]
);
```

### <a name="parameters"></a>パラメーター

*`buffer`*<br/>
出力の格納場所。

*`sizeOfBuffer`*<br/>
格納する最大文字数。

*`format`*<br/>
書式指定文字列。

*`argument_list`*<br/>
書式指定文字列への省略可能な引数。

*`locale`*<br/>
使用するロケール。

詳細については、[書式の指定](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)に関する記事をご覧ください。

## <a name="return-value"></a>戻り値

書き込まれた文字数。エラーが発生した場合は-1。

## <a name="remarks"></a>注釈

関数は、 **`_sprintf_p`** 一連の文字と値の書式を設定し、に格納し *`buffer`* ます。 内の各引数 *`argument_list`* (存在する場合) は、の対応する書式指定に従って変換され、出力され *`format`* ます。 *Format* 引数は、 [ `printf` `wprintf` 関数と関数の書式指定構文](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)を使用します。 最後に書き込まれる文字の後に NULL 文字が追加されます。 重なり合う文字列間でコピーした場合の動作は未定義です。 との違いは、で **`_sprintf_p`** **`sprintf_s`** は位置指定パラメーターをサポートしています **`_sprintf_p`** 。これにより、書式指定文字列で引数を使用する順序を指定できます。 詳細については、「 [ `printf_p` 位置指定パラメーター](../../c-runtime-library/printf-p-positional-parameters.md)」を参照してください。

**`_swprintf_p`** はのワイド文字バージョンであり、 **`_sprintf_p`** へのポインター引数 **`_swprintf_p`** はワイド文字列です。 でのエンコードエラーの検出 **`_swprintf_p`** は、の場合とは異なる場合があり **`_sprintf_p`** ます。 **`_swprintf_p`** と **`fwprintf_p`** の動作は、が **`_swprintf_p`** 型の出力先ではなく文字列に出力を書き込む点 **`FILE`** と、 **`_swprintf_p`** *`count`* 書き込む最大文字数を指定するパラメーターが必要である点を除いて同じです。 これらの関数のうちサフィックスが付けられたバージョン **`_l`** は、現在のスレッドロケールの代わりに渡されたロケールパラメーターを使用する点を除いて同じです。

**`_sprintf_p`** は、に格納されているバイト数を返し *`buffer`* ます。終端の null 文字は含まれません。 **`_swprintf_p`** は、に格納されているワイド文字数を返し *`buffer`* ます。終端の null ワイド文字は含まれません。 またはが null ポインターの場合、または *`buffer`* *`format`* 書式指定文字列に無効な書式指定文字が含まれている場合は、「 [パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は-1 を返し、 **`errno`** をに設定 **`EINVAL`** します。

> [!IMPORTANT]
> Windows 10 バージョン 2004 (ビルド 19041) 以降では、 `printf` 関数ファミリは、丸め処理のために IEEE 754 の規則に従って、正確に表現可能な浮動小数点数を出力します。 以前のバージョンの Windows では、"5" で終わる厳密に表現可能な浮動小数点数は常に切り上げられます。 IEEE 754 では、最も近い偶数 ("銀行型丸め" とも呼ばれます) に丸める必要があることが示されています。 たとえば、との `printf("%1.0f", 1.5)` 両方 `printf("%1.0f", 2.5)` が2に丸められる必要があります。 以前は、1.5 は2に丸められ、2.5 は3に丸められていました。 この変更は、正確に表現できる数値にのみ影響します。 たとえば、2.35 (メモリで表される場合は2.35000000000000008 に近い) は、2.4 に切り上げられます。 これらの関数によって実行される丸め処理は、によって設定された浮動小数点丸めモードにも従い [`fesetround`](fegetround-fesetround2.md) ます。 以前は、常に丸め処理を選択していま `FE_TONEAREST` した。 この変更は、Visual Studio 2019 バージョン16.2 以降を使用してビルドされたプログラムにのみ影響します。 従来の浮動小数点丸め動作を使用するには、 [' legacy_stdio_float_rounding. .obj '](../link-options.md)にリンクします。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|`TCHAR.H` ルーチン|`_UNICODE` & `_MBCS` 未定義|`_MBCS` れ|`_UNICODE` れ|
|---------------------|------------------------------------|--------------------|-----------------------|
|**`_stprintf_p`**|**`_sprintf_p`**|**`_sprintf_p`**|**`_swprintf_p`**|
|**`_stprintf_p_l`**|**`_sprintf_p_l`**|**`_sprintf_p_l`**|**`_swprintf_p_l`**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**`_sprintf_p`**, **`_sprintf_p_l`**|`<stdio.h>`|
|**`_swprintf_p`**, **`_swprintf_p_l`**|`<stdio.h>` または `<wchar.h>`|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example-use-_sprintf_p-to-format-data"></a>例: `_sprintf_p` を使用してデータを書式設定する

```C
// crt_sprintf_p.c
// This program uses _sprintf_p to format various
// data and place them in the string named buffer.
//

#include <stdio.h>

int main( void )
{
    char     buffer[200],
            s[] = "computer", c = 'l';
    int      i = 35,
            j;
    float    fp = 1.7320534f;

    // Format and print various data:
    j  = _sprintf_p( buffer, 200,
                     "   String:    %s\n", s );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Character: %c\n", c );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Integer:   %d\n", i );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Real:      %f\n", fp );

    printf( "Output:\n%s\ncharacter count = %d\n",
            buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example-error-code-handling"></a>例: エラーコードの処理

```C
// crt_swprintf_p.c
// This is the wide character example which
// also demonstrates _swprintf_p returning
// error code.
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    wchar_t buffer[BUFFER_SIZE];
    int     len;

    len = _swprintf_p(buffer, BUFFER_SIZE, L"%2$s %1$d",
                      0, L" marbles in your head.");
    _printf_p( "Wrote %d characters\n", len );

    // _swprintf_p fails because string contains WEOF (\xffff)
    len = _swprintf_p(buffer, BUFFER_SIZE, L"%s",
                      L"Hello\xffff world" );
    _printf_p( "Wrote %d characters\n", len );
}
```

```Output
Wrote 24 characters
Wrote -1 characters
```

## <a name="see-also"></a>こちらもご覧ください

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[`_fprintf_p`, `_fprintf_p_l`, `_fwprintf_p`, `_fwprintf_p_l`](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[`fprintf`, `_fprintf_l`, `fwprintf`, `_fwprintf_l`](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[`_printf_p`, `_printf_p_l`, `_wprintf_p`, `_wprintf_p_l`](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>
[`printf`, `_printf_l`, `wprintf`, `_wprintf_l`](printf-printf-l-wprintf-wprintf-l.md)<br/>
[`sprintf`, `_sprintf_l`, `swprintf`, `_swprintf_l`, `__swprintf_l`](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[`scanf`, `_scanf_l`, `wscanf`, `_wscanf_l`](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[`sscanf`, `_sscanf_l`, `swscanf`, `_swscanf_l`](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[`sscanf_s`, `_sscanf_s_l`, `swscanf_s`, `_swscanf_s_l`](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[`vprintf` 関数](../../c-runtime-library/vprintf-functions.md)<br/>
[`printf_p` 位置指定パラメーター](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
