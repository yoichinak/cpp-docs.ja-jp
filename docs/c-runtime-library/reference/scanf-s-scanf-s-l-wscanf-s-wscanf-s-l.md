---
description: '詳細については、次を参照してください: scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l'
title: scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l
ms.date: 03/26/2019
api_name:
- wscanf_s
- _wscanf_s_l
- scanf_s
- _scanf_s_l
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
- wscanf_s
- _tscanf_s_l
- _wscanf_s_l
- scanf_s
- _tscanf_s
- _scanf_s_l
helpviewer_keywords:
- reading data [C++], from input streams
- buffers [C++], buffer overruns
- _scanf_s_l function
- _wscanf_s_l function
- tscanf_s_l function
- tscanf_s function
- scanf_s function
- data [C++], reading from input stream
- wscanf_s function
- _tscanf_s_l function
- _tscanf_s function
- scanf_s_l function
- formatted data [C++], from input streams
- wscanf_s_l function
- buffers [C++], avoiding overruns
ms.assetid: 42cafcf7-52d6-404a-80e4-b056a7faf2e5
ms.openlocfilehash: 0a23ed2958f29c8027fdd2530cbcb215cbb54ffa
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539352"
---
# <a name="scanf_s-_scanf_s_l-wscanf_s-_wscanf_s_l"></a>`scanf_s`, `_scanf_s_l`, `wscanf_s`, `_wscanf_s_l`

標準入力ストリームから書式付きデータを読み取ります。 これらのバージョンの、、 [ `scanf` `_scanf_l` `wscanf` 、 `_wscanf_l` ](scanf-scanf-l-wscanf-wscanf-l.md)には、「CRT の[セキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されています。

## <a name="syntax"></a>構文

```C
int scanf_s(
   const char *format [,
   argument]...
);
int _scanf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wscanf_s(
   const wchar_t *format [,
   argument]...
);
int _wscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>パラメーター

*`format`*<br/>
書式指定文字列。

*`argument`*<br/>
省略可能な引数。

*`locale`*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

正常に変換されて割り当てられたフィールドの数を返します。 戻り値には、読み取られたが割り当てられていないフィールドは含まれません。 戻り値が0の場合は、フィールドが割り当てられていないことを示します。 戻り値は、エラーの場合は **EOF** 、ファイルの終端文字または文字列の末尾の文字が最初に文字を読み取ろうとしたときに見つかった場合はです。 *Format* がポインターの場合は、 **`NULL`** 「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、は **`scanf_s`** **`wscanf_s`** **EOF** を返し、をに設定し **`errno`** **`EINVAL`** ます。

これらのエラーコードの詳細については、「」、「」、 [ `errno` `_doserrno` `_sys_errlist` および `_sys_nerr` ](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)「」を参照してください。

## <a name="remarks"></a>注釈

関数は、 **`scanf_s`** 標準入力ストリームからデータを読み取り、 **`stdin`** に書き込み *`argument`* ます。 各は、 *`argument`* の型指定子に対応する変数型へのポインターである必要があり *`format`* ます。 重なり合う文字列間でコピーした場合の動作は未定義です。

**`wscanf_s`** は、のワイド文字バージョンです **`scanf_s`** 。の *format* 引数は、 **`wscanf_s`** ワイド文字列です。 **`wscanf_s`****`scanf_s`** ストリームが ANSI モードで開かれている場合、との動作は同じです。 **`scanf_s`** は、UNICODE ストリームからの入力を現在サポートしていません。

**_L** サフィックスを持つこれらの関数のバージョンは同じですが、 *`locale`* 現在のスレッドロケールの代わりにパラメーターを使用する点が異なります。

ととは異なり **`scanf`** **`wscanf`** 、およびでは、 **`scanf_s`** **`wscanf_s`** 一部のパラメーターに対してバッファーサイズを指定する必要があります。 すべての、、、 **`c`** 、 **`C`** **`s`** **`S`** または文字列コントロールセットのパラメーター **`[]`** のサイズを指定します。 文字単位のバッファーサイズは、追加のパラメーターとして渡されます。 バッファーまたは変数へのポインターの直後に続きます。 たとえば、文字列を読み取る場合、その文字列のバッファーサイズは次のように渡されます。

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

バッファーサイズには、ターミナルの null が含まれます。 [幅指定] フィールドを使用して、読み取られたトークンがバッファーに確実に収まるようにすることができます。 トークンが大きすぎて収まりきらない場合、幅指定がない限り、バッファーには何も書き込まれません。

> [!NOTE]
> Size パラメーターの型は **`unsigned`** であり、ではありません **`size_t`** 。 **`size_t`** **`unsigned`** 64 ビットのビルド構成の場合は、静的なキャストを使用して値をに変換します。

バッファーサイズのパラメーターは、バイトではなく最大文字数を示します。 この例では、バッファーの種類の幅が書式指定子の幅と一致しません。

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

**`S`** 書式指定子は、関数によってサポートされる既定の幅の "反対" の文字幅を使用することを意味します。 文字幅は1バイトですが、関数は2バイト文字をサポートします。 この例では、最大9つの1バイトワイド文字の文字列を読み取り、2バイト幅の文字バッファーに格納します。 文字は 1 バイト値として処理されます。したがって、最初の 2 文字は `ws[0]` に格納され、次の 2 文字は `ws[1]` に格納され、以降も同様に処理されます。

この例では、1つの文字を読み取ります。

```C
char c;
scanf_s("%c", &c, 1);
```

Null で終わらない文字列に対して複数の文字を読み取る場合、幅指定とバッファーサイズの両方に整数が使用されます。

```C
char c[4];
scanf_s("%4c", c, (unsigned)_countof(c)); // not null terminated
```

詳細については、「 [ `scanf` 幅指定](../../c-runtime-library/scanf-width-specification.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|`TCHAR.H` ルーチン|`_UNICODE` & `_MBCS` 未定義|`_MBCS` れ|`_UNICODE` れ|
|---------------------|------------------------------------|--------------------|-----------------------|
|**`_tscanf_s`**|**`scanf_s`**|**`scanf_s`**|**`wscanf_s`**|
|**`_tscanf_s_l`**|**`_scanf_s_l`**|**`_scanf_s_l`**|**`_wscanf_s_l`**|

詳細については、「 [書式指定フィールド: `scanf` および `wscanf` 関数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**`scanf_s`**, **`_scanf_s_l`**|`<stdio.h>`|
|**`wscanf_s`**, **`_wscanf_s_l`**|`<stdio.h>` または `<wchar.h>`|

コンソールは、ユニバーサル Windows プラットフォーム (UWP) アプリではサポートされていません。 標準ストリームは、 **`stdin`** 、 **`stdout`** 、およびを、 **`stderr`** C ランタイム関数が UWP アプリで使用できるようになる前にリダイレクトする必要があります。 互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_scanf_s.c
// This program uses the scanf_s and wscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int      i,
            result;
   float    fp;
   char     c,
            s[80];
   wchar_t  wc,
            ws[80];

   result = scanf_s( "%d %f %c %C %s %S", &i, &fp, &c, 1,
                     &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   printf( "The number of fields input is %d\n", result );
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c,
           wc, s, ws);
   result = wscanf_s( L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                      &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   wprintf( L"The number of fields input is %d\n", result );
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp,
            c, wc, s, ws);
}
```

この入力を使用すると、このプログラムでは次の出力が生成されます。

```Input
71 98.6 h z Byte characters
36 92.3 y n Wide characters
```

```Output
The number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>こちらもご覧ください

[浮動小数点のサポート](../../c-runtime-library/floating-point-support.md)<br/>
[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[`fscanf`, `_fscanf_l`, `fwscanf`, `_fwscanf_l`](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[`printf`, `_printf_l`, `wprintf`, `_wprintf_l`](printf-printf-l-wprintf-wprintf-l.md)<br/>
[`sprintf`, `_sprintf_l`, `swprintf`, `_swprintf_l`, `__swprintf_l`](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[`sscanf`, `_sscanf_l`, `swscanf`, `_swscanf_l`](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
