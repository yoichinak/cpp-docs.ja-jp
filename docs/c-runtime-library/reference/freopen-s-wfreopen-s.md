---
description: '詳細については、次を参照してください: freopen_s、_wfreopen_s'
title: freopen_s、_wfreopen_s
ms.date: 2/23/2021
api_name:
- _wfreopen_s
- freopen_s
- _o__wfreopen_s
- _o_freopen_s
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
- freopen_s
- _tfreopen_s
- _wfreopen_s
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.openlocfilehash: 410b5fa66c85070bc32a597686627da98fd22ee7
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577379"
---
# <a name="freopen_s-_wfreopen_s"></a>`freopen_s`, `_wfreopen_s`

に現在関連付けられているファイルを閉じ、 `oldStream` `stream` で指定したファイルに再割り当てし `fileName` ます。

これらのバージョンのでは [`freopen, _wfreopen`](freopen-wfreopen.md) 、「CRT の [セキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されています。

## <a name="syntax"></a>構文

```C
errno_t freopen_s(
   FILE ** stream,
   const char * fileName,
   const char * mode,
   FILE* oldStream
);

errno_t _wfreopen_s(
   FILE ** stream,
   const wchar_t * fileName,
   const wchar_t * mode,
   FILE * oldStream
);
```

### <a name="parameters"></a>パラメーター

*`stream`*\
関数がを返したときに、再び開かれたストリームを指す out パラメーター。

*`fileName`*\
再度開くファイルのパス。

*`mode`*\
開かれたストリームのモード。

*`oldStream`*\
再度開くストリーム。 フラッシュされ、関連付けられているすべてのファイルが閉じられます。

## <a name="return-value"></a>戻り値

成功した場合は0それ以外の場合は、エラーコード。 エラーが発生した場合、元のファイルは閉じられ、 **`NULL`** もに書き込まれます。 *`stream`* *`stream`***`NULL`**

エラーコードの詳細については、「」を参照してください [`errno, _doserrno, _sys_errlist, and _sys_nerr`](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。

## <a name="remarks"></a>解説

通常、この **`freopen_s`** 関数は、、、およびに関連付けられているプリオープンストリームを別のファイルにアタッチするために使用され `stdin` `stdout` `stderr` ます。

関数は、 **`freopen_s`** 現在に関連付けられているファイルを閉じ、 *`stream`* *`stream`* *path* によって指定されたファイルに再割り当てします。 **`_wfreopen_s`** はのワイド文字バージョンで **`freopen_s`** あり、の *パス* と *`mode`* 引数 **`_wfreopen_s`** はワイド文字列です。 **`_wfreopen_s`****`freopen_s`** それ以外の場合は、との動作は同じです。

*PFile*、 *path*、、またはのいずれかがの場合、 *`mode`* *`stream`* **`NULL`** または *path* が空の文字列の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は **`errno`** をに設定し、を **`EINVAL`** 返し **`EINVAL`** ます。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|`TCHAR.H` ルーチン|_ `UNICODE & _MBCS` 未定義|`_MBCS` れ|`_UNICODE` れ|
|---------------------|------------------------------------|--------------------|-----------------------|
|**`_tfreopen_s`**|**`freopen_s`**|**`freopen_s`**|**`_wfreopen_s`**|

**`freopen_s`** は通常、事前に開かれたファイル、 **`stdin`** **`stdout`** 、およびを、 **`stderr`** ユーザーが指定したファイルにリダイレクトするために使用されます。 に関連付けられた新しいファイル *`stream`* は、次のように *`mode`* 、ファイルに要求されるアクセスの種類を指定する文字列であるで開かれます。

|*`mode`*|Access|
|-|-|
| **`"r"`** | 読み取り用に開きます。 ファイルが存在しない場合、または見つからない場合、 **`freopen_s`** 呼び出しは失敗します。 |
| **`"w"`** | 書き込み用に空のファイルを開きます。 指定したファイルが既に存在すると、そのファイルの内容は破棄されます。 |
| **`"a"`** | 末尾に書き込みができるようにファイルを開きます (追加モード)。EOF (end-of-file) マーカーを削除せずにファイルに新しいデータを書き込みます。 ファイルが存在しない場合は、作成します。 |
| **`"r+"`** | 読み取りと書き込みの両方のモードで開きます。 ファイルが存在している必要があります。 |
| **`"w+"`** | 読み取りと書き込みの両方のモードで空のファイルを開きます。 そのファイルが既に存在すると、そのファイルの内容は破棄されます。 |
| **`"a+"`** | 読み取りと追加の両方のモードでファイルを開きます。 追加操作には、新しいデータをファイルに書き込む前に EOF マーカーを削除することが含まれます。 書き込みが完了した後、EOF マーカーは復元されません。 ファイルが存在しない場合は、作成します。 |

既存の **`"w"`** **`"w+"`** ファイルが破棄される可能性があるため、およびの型は注意して使用してください。 C11 以降で **`"x"`** は、またはに追加して、ファイルが存在する場合は、 **`"w"`** 上書きするのではなく、関数を失敗させることができ **`"w+"`** ます。

またはアクセスの種類を使用してファイルを開くと **`"a"`** **`"a+"`** 、すべての書き込み操作はファイルの末尾で行われます。 またはを使用してファイルポインターの位置を移動できますが [`fseek`](fseek-fseeki64.md) [`rewind`](rewind.md) 、書き込み操作が実行される前に、ファイルポインターは常にファイルの末尾に戻されます。したがって、既存のデータを上書きすることはできません。

モードでは、 **`"a"`** ファイルに追加する前に EOF マーカーは削除されません。 追加が行われても、MS-DOS TYPE コマンドでは元の EOF マーカーまでのデータしか表示されず、ファイルに追加されたデータは表示されません。 **`"a+"`** モードでは、ファイルに追加する前に EOF マーカーが削除されます。 追加が終了すると、MS-DOS の TYPE コマンドでファイル内すべてのデータが表示されます。 **`"a+"`** CTRL + Z EOF マーカーで終了するストリームファイルに追加するには、モードが必要です。

**`"r+"`**、 **`"w+"`** 、またはのいずれかのアクセスの種類を指定すると **`"a+"`** 、読み取りと書き込みの両方を行うことができます (ファイルは "更新" 用に開かれていると言います)。 ただし、読み取りと書き込みを切り替える場合は、、、のいずれかの操作を行う必要があり [`fsetpos`](fsetpos.md) [`fseek`](fseek-fseeki64.md) [`rewind`](rewind.md) ます。 必要に応じて、または操作に現在の位置を指定でき [`fsetpos`](fsetpos.md) [`fseek`](fseek-fseeki64.md) ます。 上記の値に加えて、 *`mode`* 新しい行の変換モードを指定するために、文字列に次の文字のいずれかが含まれている場合があります。

|*`mode`* 変換|変換モード|
|-|-|
| **`t`** | ファイルをテキスト (変換) モードで開きます。 |
| **`b`** | バイナリ (無変換) モードで開く復帰文字と改行文字を含む翻訳は抑制されます。 |

テキスト (変換) モードでは、キャリッジリターンラインフィード (CR-LF) の組み合わせは入力時に1つの改行 (LF) 文字に変換されます。LF 文字は、出力時に cr-lf の組み合わせに変換されます。 また、Ctrl + Z は入力時に EOF (end-of-file) 文字として解釈されます。 読み取りまたは書き込みのために開かれたファイルでは **`"a+"`** 、ランタイムライブラリがファイル末尾に CTRL + Z があるかどうかをチェックし、可能な場合は削除します。 この処理が行われる理由は、とを使用して [`fseek`](fseek-fseeki64.md) ファイル内を移動すると、 [`ftell`](ftell-ftelli64.md) [`fseek`](fseek-fseeki64.md) ファイルの末尾付近でが正しく動作しなくなる可能性があるためです。 **`t`** ANSI の移植性が必要な場合は、Microsoft の拡張機能であるため、オプションを使用しないでください。

**`t`** またはが **`b`** に指定されていない場合 *`mode`* 、既定の変換モードはグローバル変数によって定義され [`_fmode`](../../c-runtime-library/fmode.md) ます。 **`t`** または **`b`** が引数の先頭にある場合、関数は失敗し、を返し **`NULL`** ます。

テキスト モードとバイナリ モードの詳細については、「[テキスト モードとバイナリ モードのファイル入出力](../../c-runtime-library/text-and-binary-mode-file-i-o.md)」を参照してください。

## <a name="requirements"></a>要件

|機能|必須ヘッダー|
|--------------|---------------------|
|**`freopen_s`**|`<stdio.h>`|
|**`_wfreopen_s`**|`<stdio.h>` または `<wchar.h>`|

コンソールは、ユニバーサル Windows プラットフォーム (UWP) アプリではサポートされていません。 コンソール、、、およびに関連付けられている標準ストリームハンドルは、 **`stdin`** **`stdout`** **`stderr`** C ランタイム関数が UWP アプリで使用できるようになる前にリダイレクトする必要があります。

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="example"></a>例

```C
// crt_freopen_s.c
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.

#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   errno_t err;
   // Reassign "stderr" to "freopen.out":
   err = freopen_s( &stream, "freopen.out", "w", stderr );

   if( err != 0 )
      fprintf( stdout, "error on freopen\n" );
   else
   {
      fprintf( stdout, "successfully reassigned\n" ); 
      fflush( stdout );
      fprintf( stream, "This will go to the file 'freopen.out'\n" );
      fclose( stream );
   }
   system( "type freopen.out" );
}
```

```Output
successfully reassigned
This will go to the file 'freopen.out'
```

## <a name="see-also"></a>関連項目

[`Stream I/O`](../../c-runtime-library/stream-i-o.md)\
[`freopen, _wfreopen`](freopen-wfreopen.md)\
[`fclose, _fcloseall`](fclose-fcloseall.md)\
[`_fdopen, _wfdopen`](fdopen-wfdopen.md)\
[`_fileno`](fileno.md)\
[`fopen, _wfopen`](fopen-wfopen.md)\
[`_open, _wopen`](open-wopen.md)\
[`_setmode`](setmode.md)
