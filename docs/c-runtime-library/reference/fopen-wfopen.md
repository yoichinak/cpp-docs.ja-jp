---
description: 詳細については、「fopen、_wfopen」を参照してください。
title: fopen、_wfopen
ms.date: 4/2/2020
api_name:
- _wfopen
- fopen
- _o__wfopen
- _o_fopen
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
- fopen
- _wfopen
- _tfopen
- corecrt_wstdio/_wfopen
- stdio/fopen
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
ms.openlocfilehash: d6735d85fbbf3afa72aeb7a21ea1acdd7a5d254b
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539515"
---
# <a name="fopen-_wfopen"></a>`fopen`, `_wfopen`

ファイルを開きます。 追加のパラメーター検証を実行してエラーコードを返す、これらの関数のセキュリティが強化されたバージョンを使用できます。「」 [ `fopen_s` を `_wfopen_s` ](fopen-s-wfopen-s.md)参照してください。

## <a name="syntax"></a>構文

```C
FILE *fopen(
   const char *filename,
   const char *mode
);
FILE *_wfopen(
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>パラメーター

*`filename`*<br/>
ファイル名。

*`mode`*<br/>
有効なアクセス種類。

## <a name="return-value"></a>戻り値

これらの各関数は、開いているファイルへのポインターを返します。 エラーが発生すると、NULL のポインター値を返します。 *Filename* または *mode* が **NULL** または空の文字列の場合、これらの関数は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されている無効なパラメーターハンドラーをトリガーします。 実行の継続が許可された場合、これらの関数は **NULL** を返し、 **errno** を **EINVAL** に設定します。

詳細については、「」、「」、 [ `errno` `_doserrno` `_sys_errlist` および `_sys_nerr` ](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)「」を参照してください。

## <a name="remarks"></a>注釈

関数は、 **`fopen`** *filename* によって指定されたファイルを開きます。 既定では、ナロー *ファイル名* の文字列は、ANSI コードページ () を使用して解釈され `CP_ACP` ます。 Windows デスクトップアプリケーションでは、関数を使用して、これを OEM コードページ () に変更でき `CP_OEMCP` [`SetFileApisToOEM`](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) ます。 関数を使用すると、 [`AreFileApisANSI`](/windows/win32/api/fileapi/nf-fileapi-arefileapisansi) ANSI またはシステムの既定の OEM コードページを使用して *ファイル名* を解釈するかどうかを判断できます。 **`_wfopen`** はのワイド文字バージョンです **`fopen`** 。の引数は **`_wfopen`** ワイド文字列です。 それ以外の場合、とは同じように **`_wfopen`** **`fopen`** 動作します。 を使用するだけで、 **`_wfopen`** ファイルストリームで使用されるコード化された文字セットには影響しません。

**`fopen`** は、実行時にファイルシステムで有効なパスを受け入れます。 **`fopen`** コードを実行するシステムが実行時に共有またはマップされたドライブにアクセスできる限り、マップされたネットワークドライブを含む UNC パスとパスを受け入れます。 のパスを構築するときは **`fopen`** 、ドライブ、パス、またはネットワーク共有を実行環境で使用できるようにする必要があります。 ディレクトリのパス区切り記号としてスラッシュ (/) または円記号 (\\) のどちらかを使用できます。

ファイルでその他の操作を実行する前には、必ず戻り値をチェックしてポインターが NULL かどうかを確認します。 エラーが発生した場合は、グローバル変数が設定され、 **`errno`** 特定のエラー情報を取得するために使用されることがあります。 詳細については、「」、「」、 [ `errno` `_doserrno` `_sys_errlist` および `_sys_nerr` ](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)「」を参照してください。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="unicode-support"></a>Unicode のサポート

**`fopen`** Unicode ファイルストリームをサポートします。 Unicode ファイルを開くには、次のように、目的のエンコーディングを指定する **ccs** フラグをに渡し **`fopen`** ます。

> **ファイル \* fp = fopen ("newfile.txt", "rt +, ccs =**_encoding_**");**

*エンコード* に使用できる値は、 **UNICODE**、 **utf-8**、および **16LE** です。

ファイルが Unicode モードで開かれると、入力関数は、ファイルから読み取られたデータを、型として格納された UTF-16 データに変換し **`wchar_t`** ます。 Unicode モードで開かれたファイルに書き込む関数は、型として格納された UTF-16 データを含むバッファーを想定 **`wchar_t`** します。 ファイルが UTF-8 としてエンコードされている場合、UTF-16 データは書き込まれるときに UTF-8 に変換され、ファイルの UTF-8 でエンコードされた内容は読み取られるときに UTF-16 に変換されます。 Unicode モードで奇数バイトの読み取りまたは書き込みを試みると、 [パラメーター検証](../../c-runtime-library/parameter-validation.md) エラーが発生します。 UTF-8 としてプログラムに格納されたデータを読み取るか書き込む場合は、Unicode モードではなくテキストまたはバイナリ ファイル モードを使用します。 必要なエンコード変換は各自が行う必要があります。

既に存在するファイルを読み取り用または追加用に開く場合は、ファイル内にバイト順マーク (BOM: Byte Order Mark) があれば、それによってエンコーディングが決定されます。 BOM エンコーディングは、 **ccs** フラグによって指定されたエンコーディングよりも優先されます。 **Ccs** encoding は、BOM が存在しない場合、またはファイルが新しいファイルの場合にのみ使用されます。

> [!NOTE]
> BOM 検出は、Unicode モードで開かれたファイル (つまり、 **ccs** フラグを渡すことによって) にのみ適用されます。

次の表は、ファイル内の **fopen** およびバイト順マークに指定されたさまざまな **ccs** フラグに使用されるモードをまとめたものです。

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>ccs フラグおよび BOM に基づいて使用されるエンコーディング

|ccs フラグ|BOM なし (または新しいファイル)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Unicode モードで書き込むように開かれたファイルには、自動的に BOM が書き込まれます。

*モード* が **a, ccs =*_encoding_* * * の場合、 **`fopen`** まず、読み取りと書き込みの両方のアクセス権を使用してファイルを開こうとします。 成功すると、この関数は BOM を読み取ってファイルのエンコーディングを決定します。失敗した場合は、ファイルに対して既定のエンコーディングを使用します。 どちらの場合も、 **`fopen`** は書き込み専用アクセスを使用してファイルを開き直します。 (これは "a **+"** モードではなく **"a"** モードにのみ適用されます)。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**`_tfopen`**|**`fopen`**|**`fopen`**|**`_wfopen`**|

文字文字列 *モード* では、次のように、ファイルに要求されるアクセスの種類を指定します。

|*mode*|Access|
|-|-|
| **\r\n\r\n** | 読み取り用に開きます。 ファイルが存在しないか見つからない場合、呼び出しは **`fopen`** 失敗します。 |
| **リダイレクト** | 書き込み用に空のファイルを開きます。 指定したファイルが既に存在すると、そのファイルの内容は破棄されます。 |
| **ある** | 末尾に書き込みができるようにファイルを開きます (追加モード)。EOF (end-of-file) マーカーを削除せずにファイルに新しいデータを書き込みます。 ファイルが存在しない場合は、作成します。 |
| **"r +"** | 読み取りと書き込みの両方のモードで開きます。 ファイルが存在している必要があります。 |
| **"w +"** | 読み取りと書き込みの両方のモードで空のファイルを開きます。 そのファイルが既に存在すると、そのファイルの内容は破棄されます。 |
| **"a +"** | 読み取りと追加の両方のモードでファイルを開きます。 追加操作には、新しいデータをファイルに書き込む前に EOF マーカーを削除することが含まれます。 書き込みの完了後に、EOF マーカーは復元されません。 ファイルが存在しない場合は、作成します。 |

**"A"** アクセスの種類または **"a +"** アクセスの種類を使用してファイルを開くと、すべての書き込み操作がファイルの末尾で行われます。 ファイルポインターはまたはを使用し [`fseek`](fseek-fseeki64.md) て [`rewind`](rewind.md) 移動できますが、書き込み操作が実行される前に、常にファイルの末尾に戻されます。 したがって、既存のデータは上書きされません。

**"A"** モードでは、ファイルに追加する前に EOF マーカーは削除されません。 追加が行われても、MS-DOS TYPE コマンドでは元の EOF マーカーまでのデータしか表示されず、ファイルに追加されたデータは表示されません。 ファイルに追加する前に、 **"a +"** モードで EOF マーカーが削除されます。 追加が終了すると、MS-DOS の TYPE コマンドでファイル内すべてのデータが表示されます。 CTRL + Z EOF マーカーで終了するストリームファイルに追加するには、 **"a +"** モードが必要です。

**"R +"**、 **"w +"**、または **"a +"** のアクセスの種類が指定されている場合、読み取りと書き込みの両方が有効になります (ファイルは "更新" 用に開かれていると言います)。 ただし、読み取りから書き込みに切り替えると、入力操作は EOF マーカーを検出する必要があります。 EOF がない場合、ファイル ポジショニング関数の中間の呼び出しを使用する必要があります。 ファイルポジショニング関数は、、、 **`fsetpos`** [`fseek`](fseek-fseeki64.md) および [`rewind`](rewind.md) です。 書き込みから読み取りに切り替えると、 **`fflush`** またはファイルポジショニング関数に対して介在する呼び出しを使用する必要があります。

前の値に加えて、次の文字を *モード* に追加して、改行文字の変換モードを指定できます。

|*モード* 修飾子|変換モード|
|-|-|
| **t** | ファイルをテキスト (変換) モードで開きます。 |
| **b** | バイナリ (無変換) モードで開く復帰文字と改行文字を含む翻訳は抑制されます。 |

テキストモードでは、CTRL + Z は入力時に EOF 文字として解釈されます。 **"A +"** を使用して読み取り/書き込み用に開かれたファイルでは、 **fopen** がファイル末尾に CTRL + Z があるかどうかをチェックし、可能な場合は削除します。 これは、と ftell を使用して、 [`fseek`](fseek-fseeki64.md) CTRL + Z で終わるファイル内を移動すると、  [`fseek`](fseek-fseeki64.md) ファイルの末尾付近でが正しく動作しなくなる可能性があるためです。

テキストモードでは、キャリッジリターンラインフィードの組み合わせは入力時に1つの改行に変換され、ラインフィード文字は出力時に復帰と改行の組み合わせに変換されます。 Unicode のストリーム入出力関数が既定のテキスト モードで動作すると、入力元または出力先のストリームはマルチバイト文字のシーケンスと仮定されます。 したがって、Unicode ストリーム入力関数は、マルチバイト文字をワイド文字に変換します (関数を呼び出した場合と同様 **`mbtowc`** )。 同様の理由で、Unicode ストリーム出力関数は、関数の呼び出しの場合と同様に、ワイド文字をマルチバイト文字に変換し **`wctomb`** ます。

**T** または **b** を *モード* で指定しない場合、既定の変換モードはグローバル変数によって定義され [`_fmode`](../../c-runtime-library/fmode.md) ます。 **T** または **b** が引数の前に付加されている場合、関数は失敗し、 **NULL** を返します。

Unicode およびマルチバイトのストリーム入出力でテキスト モードとバイナリ モードを使用する方法について詳しくは、「 [Text and Binary Mode File I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 」および「 [Unicode Stream I/O in Text and Binary Modes](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)」をご覧ください。

次のオプションを *モード* に追加すると、追加の動作を指定できます。

|*モード* 修飾子|動作|
|-|-|
| **x** | *Filename* が既に存在する場合、関数を強制的に失敗させます。 は、"w" または "w +" 指定子と共にのみ使用できます。 |
| **c** | またはが呼び出された場合に、ファイルバッファーの内容がディスクに直接書き込まれるように、関連付けられている *ファイル名* のコミットフラグを有効にし **`fflush`** **`_flushall`** ます。 |
| **n** | 関連付けられている *ファイル名* のコミットフラグを "コミットなし" にリセットします。 既定値です。 プログラムを COMMODE.OBJ とリンクする場合は、グローバル コミット フラグもオーバーライドします。 プログラムを明示的に COMMODE.OBJ とリンクしない場合、グローバル コミット フラグの既定の設定は "コミットなし" です (「 [Link Options](../../c-runtime-library/link-options.md)」をご覧ください)。 |
| **N** | ファイルが子プロセスによって継承されないように指定します。 |
| **S** | キャッシュがディスクからのシーケンシャル アクセスに最適化されるように指定します。ただし、シーケンシャル アクセスに限定されるわけではありません。 |
| **R** | キャッシュがディスクからのランダム アクセスに最適化されるように指定します。ただし、ランダム アクセスに限定されるわけではありません。 |
| **T** | ファイルを一時ファイルとして指定します。 可能な場合、ファイルはディスクにフラッシュされません。 |
| **D** | ファイルを一時ファイルとして指定します。 最後のファイル ポインターが閉じられると、ファイルは削除されます。 |
| **ccs =**_encoding_ | このファイルに使用するエンコードされた文字セット ( **utf-8**、 **Utf 16LE**、 **UNICODE** のいずれか) を指定します。 何も指定しない場合は、ANSI エンコーディングが使用されます。 |

およびで使用される *モード* 文字列の有効な文字は、次のように、 **`fopen`** **`_fdopen`** およびで使用される *oflag* 引数に対応し [`_open`](open-wopen.md) [`_sopen`](sopen-wsopen.md) ます。

|*Mode* 文字列の文字| \_ Open/sopen の同等の oflag 値 \_|
|-------------------------------|----------------------------------------------------|
|**ある**|**\_ O \_ wronly** &#124; **\_ o \_ append** (通常は **\_ o \_ wronly** &#124; **\_ o \_** &#124; **\_ o \_ append**)|
|**+**|**\_ O \_ RDWR** &#124; **\_ o \_ append** (通常は **\_ o \_ RDWR** &#124; **\_ o \_ append** &#124; **\_ o \_** )|
|**r**|**\_O \_ RDONLY**|
|**r +**|**\_O \_ RDWR**|
|**w**|**\_ O \_ wronly** (通常は **\_ o \_ wronly** &#124; **\_ o \_** &#124; **\_ o \_ TRUNC**)|
|**w +**|**\_ O \_ RDWR** (通常は **\_ o \_ RDWR** **&#124; o \_ \_** &#124; **\_ o \_ TRUNC**)|
|**b**|**\_O \_ バイナリ**|
|**t**|**\_O \_ テキスト**|
|**x**|**\_除外する \_**|
|**c**|なし|
|**n**|なし|
|**S**|**\_\_順次**|
|**R**|**\_\_ランダム**|
|**T**|**\_短い有効期間 \_**|
|**D**|**\_O \_ 一時**|
|**ccs = UNICODE**|**\_O \_ WTEXT**|
|**ccs = UTF-8**|**\_O \_ UTF8**|
|**ccs = 16LE**|**\_O \_ UTF16**|

**Rb** モードを使用している場合は、コードを移植する必要はなく、大規模なファイルの大部分を読み取ることが予想される場合や、ネットワークのパフォーマンスに不安がある場合は、オプションとしてメモリマップ Win32 ファイルを使用するかどうかを検討することもできます。

## <a name="requirements"></a>要件

|機能|必須ヘッダー|
|--------------|---------------------|
|**`fopen`**|`<stdio.h>`|
|**`_wfopen`**|`<stdio.h>` または `<wchar.h>`|

**`_wfopen`** は Microsoft の拡張機能です。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

**C**、 **n**、 **t**、 **S**、 **R**、 **t**、および **D** *モード* のオプションは、およびの Microsoft 拡張機能であり、ANSI の **`fopen`** **`_fdopen`** 移植性が必要な場合は使用しないでください。

## <a name="example-1"></a>例 1

次のプログラムは 2 ファイルを開きます。  を使用して **`fclose`** 最初のファイルを閉じ、 **`_fcloseall`** 残りのすべてのファイルを閉じます。

```C
// crt_fopen.c
// compile with: /W3
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   int numclosed;

   // Open for read (will fail if file "crt_fopen.c" does not exist)
   if( (stream  = fopen( "crt_fopen.c", "r" )) == NULL ) // C4996
   // Note: fopen is deprecated; consider using fopen_s instead
      printf( "The file 'crt_fopen.c' was not opened\n" );
   else
      printf( "The file 'crt_fopen.c' was opened\n" );

   // Open for write
   if( (stream2 = fopen( "data2", "w+" )) == NULL ) // C4996
      printf( "The file 'data2' was not opened\n" );
   else
      printf( "The file 'data2' was opened\n" );

   // Close stream if it is not NULL
   if( stream)
   {
      if ( fclose( stream ) )
      {
         printf( "The file 'crt_fopen.c' was not closed\n" );
      }
   }

   // All other files are closed:
   numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="example-2"></a>例 2

次のプログラムでは、Unicode エンコーディングのテキスト モードで、ファイルを作成します (ファイルが存在する場合は上書きします)。  その後、2 つの文字列をファイルに書き込み、ファイルを閉じます。 出力は *_wfopen_test.xml* という名前のファイルで、出力セクションのデータが含まれています。

```C
// crt__wfopen.c
// compile with: /W3
// This program creates a file (or overwrites one if
// it exists), in text mode using Unicode encoding.
// It then writes two strings into the file
// and then closes the file.

#include <stdio.h>
#include <stddef.h>
#include <stdlib.h>
#include <wchar.h>

#define BUFFER_SIZE 50

int main(int argc, char** argv)
{
    wchar_t str[BUFFER_SIZE];
    size_t  strSize;
    FILE*   fileHandle;

    // Create an the xml file in text and Unicode encoding mode.
    if ((fileHandle = _wfopen( L"_wfopen_test.xml",L"wt+,ccs=UNICODE")) == NULL) // C4996
    // Note: _wfopen is deprecated; consider using _wfopen_s instead
    {
        wprintf(L"_wfopen failed!\n");
        return(0);
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"<xmlTag>\n");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"</xmlTag>");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Close the file.
    if (fclose(fileHandle))
    {
        wprintf(L"fclose failed!\n");
    }
    return 0;
}
```

## <a name="see-also"></a>こちらもご覧ください

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[Multibyte-Character シーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[`fclose`, `_fcloseall`](fclose-fcloseall.md)<br/>
[`_fdopen`, `_wfdopen`](fdopen-wfdopen.md)<br/>
[`ferror`](ferror.md)<br/>
[`_fileno`](fileno.md)<br/>
[`freopen`, `_wfreopen`](freopen-wfreopen.md)<br/>
[`_open`, `_wopen`](open-wopen.md)<br/>
[`_setmode`](setmode.md)<br/>
[`_sopen`, `_wsopen`](sopen-wsopen.md)<br/>
