---
description: '詳細については、次を参照してください: _lseek、_lseeki64'
title: _lseek、_lseeki64
ms.date: 4/2/2020
api_name:
- _lseeki64
- _lseek
- _o__lseek
- _o__lseeki64
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lseeki64
- _lseek
- lseeki64
helpviewer_keywords:
- lseek function
- _lseek function
- _lseeki64 function
- lseeki64 function
- file pointers [C++], moving
- seek file pointers
ms.assetid: aba8a768-d40e-48c3-b38e-473dbd782f93
ms.openlocfilehash: 69a495eda02faa06bd173483d0b292dea11abc13
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539729"
---
# <a name="_lseek-_lseeki64"></a>_lseek、_lseeki64

指定した場所にファイル ポインターを移動します。

## <a name="syntax"></a>構文

```C
long _lseek(
   int fd,
   long offset,
   int origin
);
__int64 _lseeki64(
   int fd,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>パラメーター

*スクリプター*<br/>
開いているファイルを参照するファイル記述子。

*offset*<br/>
*配信元* からのバイト数。

*発行*<br/>
最初の位置。

## <a name="return-value"></a>戻り値

**_lseek** は、ファイルの先頭からの新しい位置のオフセットをバイト単位で返します。 **_lseeki64** は、64ビット整数のオフセットを返します。 この関数は、エラーを示す-1L を返します。 不適切なファイル記述子、*origin* の値が無効、*オフセット* によって指定された位置がファイルの開始より前であるなど、無効なパラメーターが渡された場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」の説明にあるとおり、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は **errno** を **EBADF** に設定し、-1l を返します。 (ターミナルやポインターなどの) シーク非対応のデバイスでは、戻り値は未定義です。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>注釈

**_Lseek** 関数は、 *fd* に関連付けられたファイルポインターを、*原点* から *オフセット* バイトの新しい場所に移動します。 ファイルの次の操作は、新しい場所で行われます。 *origin* 引数は、Stdio.h で定義されている、次の定数のいずれかである必要があります。

|*配信元* の値| Description |
|-|-|
| **SEEK_SET** | ファイルの先頭。 |
| **SEEK_CUR** | ファイル ポインターの現在の位置。 |
| **SEEK_END** | EOF (ファイル終端)。 |

**_Lseek** を使用すると、ファイルの任意の場所またはファイルの末尾を越える位置にポインターを移動できます。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_lseek**|\<io.h>|
|**_lseeki64**|\<io.h>|

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_lseek.c
/* This program first opens a file named lseek.txt.
* It then uses _lseek to find the beginning of the file,
* to find the current position in the file, and to find
* the end of the file.
*/

#include <io.h>
#include <fcntl.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

int main( void )
{
   int fh;
   long pos;               /* Position of file pointer */
   char buffer[10];

   _sopen_s( &fh, "crt_lseek.c_input", _O_RDONLY, _SH_DENYNO, 0 );

   /* Seek the beginning of the file: */
   pos = _lseek( fh, 0L, SEEK_SET );
   if( pos == -1L )
      perror( "_lseek to beginning failed" );
   else
      printf( "Position for beginning of file seek = %ld\n", pos );

   /* Move file pointer a little */
    _read( fh, buffer, 10 );

   /* Find current position: */
   pos = _lseek( fh, 0L, SEEK_CUR );
   if( pos == -1L )
      perror( "_lseek to current position failed" );
   else
      printf( "Position for current position seek = %ld\n", pos );

   /* Set the end of the file: */
   pos = _lseek( fh, 0L, SEEK_END );
   if( pos == -1L )
      perror( "_lseek to end failed" );
   else
      printf( "Position for end of file seek = %ld\n", pos );

   _close( fh );
}
```

### <a name="input-crt_lseekc_input"></a>入力: crt_lseek.c_input

```Input
Line one.
Line two.
Line three.
Line four.
Line five.
```

### <a name="output"></a>出力

```Output
Position for beginning of file seek = 0
Position for current position seek = 10
Position for end of file seek = 57
```

## <a name="see-also"></a>関連項目

[低レベル i/o](../../c-runtime-library/low-level-i-o.md)<br/>
[fseek、_fseeki64](fseek-fseeki64.md)<br/>
[_tell、_telli64](tell-telli64.md)<br/>
