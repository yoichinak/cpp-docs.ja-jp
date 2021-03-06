---
description: 詳細については、「ftell, _ftelli64」を参照してください。
title: ftell、_ftelli64
ms.date: 4/2/2020
api_name:
- _ftelli64
- ftell
- _o__ftelli64
- _o_ftell
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
- _ftelli64
- ftell
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
ms.openlocfilehash: f3fec98cb9d90c8b63072a8e618f58246a6b0147
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334239"
---
# <a name="ftell-_ftelli64"></a>ftell、_ftelli64

ファイル ポインターの現在の位置を取得します。

## <a name="syntax"></a>構文

```C
long ftell(
   FILE *stream
);
__int64 _ftelli64(
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*一連*<br/>
ターゲット **ファイル** の構造。

## <a name="return-value"></a>戻り値

**ftell** および **_ftelli64** は、現在のファイルの位置を返します。 テキストモードでは復帰と改行の変換が行われるため、 **ftell** と **_ftelli64** によって返される値には、テキストモードで開かれたストリームの物理バイトオフセットが反映されない場合があります。 **Ftell** または **_ftelli64** と共に使用し [て、ファイル](fseek-fseeki64.md)の場所に適切に戻るには、 [_fseeki64](fseek-fseeki64.md)を使用します。 エラーが発生した場合、 **ftell** および **_ftelli64** は、「パラメーターの [検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は-1L を返します。 **errno** には、errno に定義されている2つの定数のいずれかを設定します。 **EBADF** 定数は、*ストリーム* 引数が有効なファイルポインター値ではないか、開いているファイルを参照していないことを意味します。 **EINVAL** は、無効な *ストリーム* 引数が関数に渡されたことを意味します。 (端末やプリンターなどの) シークが不可能なデバイス、または *ストリーム* が開いているファイルを参照していない場合、戻り値は未定義になります。

リターン コードの詳細については、「[_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>解説

**Ftell** 関数と **_ftelli64** 関数は、*ストリーム* に関連付けられたファイルポインター (存在する場合) の現在の位置を取得します。 位置は、ストリームの先頭を基準としたオフセットとして表されます。

データを追加するためにファイルを開く場合、現在のファイルの位置は、次の書き込みが発生する場所ではなく最後の I/O 操作によって決まります。 たとえば、追加のためにファイルが開かれ、最後の操作が読み取りだった場合、ファイルの位置は、次の書き込みが開始される位置ではなく、次の読み取り操作が開始される位置になります  (ファイルを追加するためにファイルを開くと、書き込み操作の前に、ファイルの位置がファイルの末尾に移動します)。追加用に開かれたファイルで i/o 操作がまだ発生していない場合、ファイルの位置はファイルの先頭になります。

テキスト モードでは、Ctrl + Z は入力時に EOF (end-of-file) 文字として解釈されます。 読み取り/書き込み用に開かれたファイルでは、 **fopen** と関連するすべてのルーチンで、ファイルの末尾に CTRL + Z があるかどうかを確認し、可能であれば削除します。 この処理が行われる理由は、 **ftell** と [fseek](fseek-fseeki64.md) または **_ftelli64** と [_fseeki64](fseek-fseeki64.md)の組み合わせを使用して、CTRL + Z で終わるファイル内を移動すると、ファイルの末尾付近で **ftell** または **_ftelli64** が正しく動作しなくなる可能性があるためです。

この関数は実行中に呼び出し元スレッドをロックするため、スレッド セーフです。 ロックしないバージョンについては、「 **_ftell_nolock**」を参照してください。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>要件

|機能|必須ヘッダー|省略可能なヘッダー|
|--------------|---------------------|----------------------|
|**ftell**|\<stdio.h>|\<errno.h>|
|**_ftelli64**|\<stdio.h>|\<errno.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_ftell.c
// This program opens a file named CRT_FTELL.C
// for reading and tries to read 100 characters. It
// then uses ftell to determine the position of the
// file pointer and displays this position.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long position;
   char list[100];
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )
   {
      // Move the pointer by reading data:
      fread( list, sizeof( char ), 100, stream );
      // Get position after read:
      position = ftell( stream );
      printf( "Position after trying to read 100 bytes: %ld\n",
              position );
      fclose( stream );
   }
}
```

```Output
Position after trying to read 100 bytes: 100
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek、_fseeki64](fseek-fseeki64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
