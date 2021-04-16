---
title: fopen_s、_wfopen_s
description: およびの API について説明します。 `fopen_s``_wfopen_s`
ms.date: 2/24/2021
api_name:
- _wfopen_s
- fopen_s
- _o__wfopen_s
- _o_fopen_s
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
- fopen_s
- _tfopen_s
- _wfopen_s
helpviewer_keywords:
- _wfopen_s function
- opening files, for file I/O
- _tfopen_s function
- tfopen_s function
- wfopen_s function
- fopen_s function
- Unicode [C++], creating files
- Unicode [C++], writing files
- files [C++], opening
- Unicode [C++], files
ms.openlocfilehash: e3526df036711d7c6319dfa582dcefcf7b7d0818
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539791"
---
# <a name="fopen_s-_wfopen_s"></a>`fopen_s`, `_wfopen_s`

ファイルを開きます。 これらのバージョン[の `fopen` `_wfopen` では、「](fopen-wfopen.md) [CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されています。

## <a name="syntax"></a>構文

```C
errno_t fopen_s(
   FILE** pFile,
   const char *filename,
   const char *mode
);
errno_t _wfopen_s(
   FILE** pFile,
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>パラメーター

*`pFile`*\
開かれたファイルへのポインターを受け取るファイル ポインターへのポインター。

*`filename`*\
ファイル名。

*`mode`*\
アクセス許可の種類。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。 これらのエラーコードの詳細については、「」、「」、 [ `errno` `_doserrno` `_sys_errlist` および `_sys_nerr` ](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)「」を参照してください。

### <a name="error-conditions"></a>エラー条件

|*`pFile`*|*`filename`*|*`mode`*|戻り値|の内容 *`pFile`*|
|-------------|----------------|------------|------------------|------------------------|
|**`NULL`**|any|any|**`EINVAL`**|変更なし|
|any|**`NULL`**|any|**`EINVAL`**|変更なし|
|any|any|**`NULL`**|**`EINVAL`**|変更なし|

## <a name="remarks"></a>注釈

およびによって開かれたファイルは **`fopen_s`** **`_wfopen_s`** 共有できません。 ファイルを共有可能にする必要がある場合は、適切な共有モード定数 (たとえば、読み取り/書き込み共有) で [ `_fsopen` を `_wfsopen`](fsopen-wfsopen.md)使用し **`_SH_DENYNO`** ます。

関数は、 **`fopen_s`** *filename* によって指定されたファイルを開きます。 **`_wfopen_s`** はのワイド文字バージョンです **`fopen_s`** 。の引数は **`_wfopen_s`** ワイド文字列です。 **`_wfopen_s`****`fopen_s`** それ以外の場合は、との動作は同じです。

**`fopen_s`** は、実行時にファイルシステムで有効なパスを受け入れます。マップされたネットワークドライブを含む UNC パスとパスは、 **`fopen_s`** コードを実行しているシステムが実行時に共有またはマップされたネットワークドライブにアクセスできる限り、によって受け入れられます。 のパスを構築する場合は **`fopen_s`** 、実行環境でのドライブ、パス、またはネットワーク共有の可用性について、想定しないでください。 ディレクトリのパス区切り記号としてスラッシュ (/) または円記号 (\\) のどちらかを使用できます。

これらの関数では、パラメーターの検証が行われます。 *`pFile`*、 *`filename`* 、または *`mode`* が null ポインターの場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーター例外を生成します。

ファイルに対して他の操作を実行する前に、必ず戻り値をチェックして関数が成功したかどうかを確認してください。 エラーが発生した場合は、エラーコードが返され、グローバル変数 **`errno`** が設定されます。 詳細については、「」、「」、 [ `errno` `_doserrno` `_sys_errlist` および `_sys_nerr` ](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)「」を参照してください。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="unicode-support"></a>Unicode のサポート

**`fopen_s`** Unicode ファイルストリームをサポートします。 新規または既存の Unicode ファイルを開くには、目的のエンコーディングを指定する *ccs* フラグをに渡し **`fopen_s`** ます。

**`fopen_s(&fp, "newfile.txt", "rw, ccs=**_encoding_**");`**

*エンコード* に使用できる値は **`UNICODE`** 、、、 **`UTF-8`** および **`UTF-16LE`** です。 に値が指定されていない場合 *`encoding`* 、は **`fopen_s`** ANSI エンコーディングを使用します。

既に存在するファイルを読み取り用または追加用に開く場合は、ファイル内にバイト順マーク (BOM: Byte Order Mark) があれば、それによってエンコーディングが決定されます。 BOM エンコーディングは、フラグで指定されたエンコーディングよりも優先され *`ccs`* ます。 *`ccs`* エンコーディングは、BOM が存在しない場合、またはファイルが新しいファイルの場合にのみ使用されます。

> [!NOTE]
> BOM 検出は、Unicode モードで開かれたファイルにのみ適用されます。つまり、フラグを渡し *`ccs`* ます。

次の表は、 *`ccs`* **`fopen_s`** ファイル内のバイト順マークに対しておよびに対して指定されているさまざまなフラグのモードをまとめたものです。

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>ccs フラグおよび BOM に基づいて使用されるエンコーディング

|ccs フラグ|BOM なし (または新しいファイル)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**`UNICODE`**|**`UTF-16LE`**|**`UTF-8`**|**`UTF-16LE`**|
|**`UTF-8`**|**`UTF-8`**|**`UTF-8`**|**`UTF-16LE`**|
|**`UTF-16LE`**|**`UTF-16LE`**|**`UTF-8`**|**`UTF-16LE`**|

Unicode モードで書き込むように開かれたファイルには、自動的に BOM が書き込まれます。

*`mode`* が **`"a, ccs=` _エン_ コーディング `"`** の場合、は、 **`fopen_s`** まず読み取りアクセスと書き込みアクセスの両方でファイルを開こうとします。 成功すると、この関数は BOM を読み取ってファイルのエンコーディングを決定します。失敗した場合は、ファイルに対して既定のエンコーディングを使用します。 どちらの場合も、は **`fopen_s`** 書き込み専用アクセスでファイルを再度開きます。 (これはモードにのみ適用され、には適用さ **`a`** れません **`a+`** )。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**`_tfopen_s`**|**`fopen_s`**|**`fopen_s`**|**`_wfopen_s`**|

文字列は、次のように、 *`mode`* ファイルに要求されるアクセスの種類を指定します。

|*`mode`*|Access|
|-|-|
| **`"r"`** | 読み取り用に開きます。 ファイルが存在しない場合、または見つからない場合、 **`fopen_s`** 呼び出しは失敗します。 |
| **`"w"`** | 書き込み用に空のファイルを開きます。 指定したファイルが既に存在すると、そのファイルの内容は破棄されます。 |
| **`"a"`** | 末尾に書き込みができるようにファイルを開きます (追加モード)。EOF (end-of-file) マーカーを削除せずにファイルに新しいデータを書き込みます。 ファイルが存在しない場合は、作成します。 |
| **`"r+"`** | 読み取りと書き込みの両方のモードで開きます。 ファイルが存在している必要があります。 |
| **"w +"** | 読み取りと書き込みの両方のモードで空のファイルを開きます。 そのファイルが既に存在すると、そのファイルの内容は破棄されます。 |
| **`"a+"`** | 読み取りと追加の両方のモードでファイルを開きます。 追加操作には、新しいデータをファイルに書き込む前に EOF マーカーを削除することが含まれます。 書き込みが完了した後、EOF マーカーは復元されません。 ファイルが存在しない場合は、作成します。 |

アクセスの種類またはを使用してファイルを開くと **`"a"`** **`"a+"`** 、すべての書き込み操作はファイルの末尾で行われます。 ファイルポインターはまたはを使用して移動できます [`fseek`](fseek-fseeki64.md) [`rewind`](rewind.md) が、既存のデータを上書きできないように、書き込み操作が実行される前に常にファイルの末尾に戻されます。

モードでは、 **`"a"`** ファイルに追加する前に EOF マーカーは削除されません。 追加が行われた後、MS-DOS コマンドは、 `TYPE` ファイルに追加されたデータではなく、元の EOF マーカーまでのデータのみを表示します。 **`"a+"`** モードでは、ファイルに追加する前に EOF マーカーが削除されます。 追加後、MS-DOS `TYPE` コマンドはファイル内のすべてのデータを表示します。 **`"a+"`** **CTRL** + **Z** EOF マーカーで終了するストリームファイルに追加するには、モードが必要です。

**`"r+"`**、 **`"w+"`** 、またはのいずれかのアクセスの種類を指定すると **`"a+"`** 、読み取りと書き込みの両方を行うことができます。 (ファイルは "更新" のために開かれていると言います)。ただし、読み取りから書き込みに切り替えると、入力操作は EOF マーカー経由で行われる必要があります。 EOF マーカーがない場合は、ファイルポジショニング関数に介在する呼び出しを使用する必要があります。 ファイル配置関数は、、 **`fsetpos`** 、 [`fseek`](fseek-fseeki64.md) および [`rewind`](rewind.md) です。 書き込みから読み取りに切り替えると、 **`fflush`** またはファイル配置関数に対して介在する呼び出しを使用する必要があります。

C11 以降で **`"x"`** は、をまたはに追加し **`"w"`** て、ファイルが存在する場合は上書きせずに、関数を失敗させることができ **`"w+"`** ます。

上記の値に加え、に次の文字を追加して、 *`mode`* 改行文字の変換モードを指定できます。

|*`mode`* 変換|変換モード|
|-|-|
| **`t`** | ファイルをテキスト (変換) モードで開きます。 |
| **`b`** | バイナリ (無変換) モードで開く復帰文字と改行文字を含む翻訳は抑制されます。 |

テキスト (変換) モードでは、 **CTRL** + **Z** は入力時にファイルの終端文字として解釈されます。 で読み取り/書き込み用に開かれたファイルでは **`"a+"`** 、が **`fopen_s`** ファイルの末尾に **CTRL** Z があるかどうかを確認 + し、削除できる場合は削除します。 この処理が行われる理由は、 [`fseek`](fseek-fseeki64.md) **`ftell`** **CTRL** Z で終わるファイル内でを使用してを移動すると + 、 [`fseek`](fseek-fseeki64.md) ファイルの末尾付近でが正しく動作しなくなる可能性があるためです。

また、テキストモードでは、キャリッジリターンとラインフィードの組み合わせは入力時に1つの改行に変換され、ラインフィード文字は出力時に復帰と改行の組み合わせに変換されます。 Unicode のストリーム入出力関数が既定のテキスト モードで動作すると、入力元または出力先のストリームはマルチバイト文字のシーケンスと仮定されます。 Unicode ストリーム入力関数は、マルチバイト文字をワイド文字に変換します (関数を呼び出した場合と同様 **`mbtowc`** )。 同様の理由で、Unicode ストリーム出力関数は、関数の呼び出しの場合と同様に、ワイド文字をマルチバイト文字に変換し **`wctomb`** ます。

**`t`** またはが **`b`** に指定されていない場合 *`mode`* 、既定の変換モードは [_fmode](../../c-runtime-library/fmode.md)グローバル変数によって定義されます。 **`t`** または **`b`** が引数の先頭にある場合、関数は失敗し、を返し **`NULL`** ます。

Unicode およびマルチバイトのストリーム入出力におけるテキスト モードおよびバイナリ モードの使い方の詳細については、「[テキスト モードとバイナリ モードのファイル入出力](../../c-runtime-library/text-and-binary-mode-file-i-o.md)」および「[テキスト モードとバイナリ モードの Unicode ストリーム入出力](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)」を参照してください。

|*`mode`* 変換|動作|
|-|-|
| **`c`** | またはが呼び出された場合に、ファイルバッファーの内容がディスクに直接書き込まれるように、関連付けられている *ファイル名* のコミットフラグを有効にし **`fflush`** **`_flushall`** ます。 |
| **`n`** | 関連付けられている *ファイル名* のコミットフラグを "コミットなし" にリセットします。 既定値です。 プログラムを COMMODE.OBJ とリンクする場合は、グローバル コミット フラグもオーバーライドします。 プログラムを明示的に COMMODE.OBJ とリンクしない場合、グローバル コミット フラグの既定の設定は "コミットなし" です (「 [Link Options](../../c-runtime-library/link-options.md)」をご覧ください)。 |
| **`n`** | ファイルが子プロセスによって継承されないことを指定します。 |
| **`S`** | キャッシュがディスクからのシーケンシャル アクセスに最適化されるように指定します。ただし、シーケンシャル アクセスに限定されるわけではありません。 |
| **`R`** | キャッシュがディスクからのランダム アクセスに最適化されるように指定します。ただし、ランダム アクセスに限定されるわけではありません。 |
| **`t`** | ファイルを一時ファイルとして指定します。 可能であれば、ディスクにフラッシュされません。 |
| **`D`** | ファイルを一時ファイルとして指定します。 最後のファイルポインターが閉じられると、削除されます。 |
| **`ccs=`**_暗号化_ | このファイルに使用するエンコードされた文字セット ( **`UTF-8`** 、、またはのいずれか) を指定し **`UTF-16LE`** **`UNICODE`** ます。 何も指定しない場合は、ANSI エンコーディングが使用されます。 |

およびで使用される文字列の有効な文字は、次のように、 *`mode`* **`fopen_s`** [`_fdopen`](fdopen-wfdopen.md) *`oflag`* およびで使用される引数に対応し [`_open`](open-wopen.md) [`_sopen`](sopen-wsopen.md) ます。

|文字列内の文字 *`mode`*|*`oflag`* に相当する値`_open`/`_sopen`|
|-------------------------------|----------------------------------------------------|
|**`a`**|**`_O_WRONLY`** &#124; **`_O_APPEND`** (通常は **`_O_WRONLY`** &#124; **`_O_CREAT`** &#124; **`_O_APPEND`** )|
|**`a+`**|**`_O_RDWR`** &#124; **`_O_APPEND`** (通常は **`_O_RDWR`** &#124; **`_O_APPEND`** &#124; **`_O_CREAT`** )|
|**`R`**|**`_O_RDONLY`**|
|**`r+`**|**`_O_RDWR`**|
|**`w`**|**`_O_WRONLY`** (通常は **`_O_WRONLY`** &#124; **`_O_CREAT`** &#124; **_O_TRUNC**)|
|**`w+`**|**`_O_RDWR`** (通常は **`_O_RDWR`** &#124; **`_O_CREAT`** &#124; **_O_TRUNC**)|
|**`b`**|**`_O_BINARY`**|
|**`t`**|**`_O_TEXT`**|
|**`c`**|なし|
|**`n`**|なし|
|**`S`**|**`_O_SEQUENTIAL`**|
|**`R`**|**`_O_RANDOM`**|
|**`t`**|**`_O_SHORTLIVED`**|
|**`D`**|**`_O_TEMPORARY`**|
|**`ccs=UNICODE`**|**`_O_WTEXT`**|
|**`ccs=UTF-8`**|**`_O_UTF8`**|
|**`ccs=UTF-16LE`**|**`_O_UTF16`**|

モードを使用している場合は、 **`rb`** メモリにマップされた Win32 ファイルが、コードを移植する必要がない場合や、ファイルの大部分を読み取ることが予想される場合、またはネットワークパフォーマンスが気にならない場合にもオプションとなることがあります。

## <a name="requirements"></a>要件

|機能|必須ヘッダー|
|--------------|---------------------|
|**`fopen_s`**|`<stdio.h>`|
|**`_wfopen_s`**|`<stdio.h>` または `<wchar.h>`|

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

**`c`**、 **`n`** 、およびオプションは、 **`t`** *`mode`* およびの Microsoft 拡張機能であり、 **`fopen_s`** ANSI の [`_fdopen`](fdopen-wfdopen.md) 移植性が必要な場所では使用しないでください。

## <a name="example"></a>例

```C
// crt_fopen_s.c
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   errno_t err;

   // Open for read (will fail if file "crt_fopen_s.c" doesn't exist)
   err  = fopen_s( &stream, "crt_fopen_s.c", "r" );
   if( err == 0 )
   {
      printf( "The file 'crt_fopen_s.c' was opened\n" );
   }
   else
   {
      printf( "The file 'crt_fopen_s.c' was not opened\n" );
   }

   // Open for write
   err = fopen_s( &stream2, "data2", "w+" );
   if( err == 0 )
   {
      printf( "The file 'data2' was opened\n" );
   }
   else
   {
      printf( "The file 'data2' was not opened\n" );
   }

   // Close stream if it isn't NULL
   if( stream )
   {
      err = fclose( stream );
      if ( err == 0 )
      {
         printf( "The file 'crt_fopen_s.c' was closed\n" );
      }
      else
      {
         printf( "The file 'crt_fopen_s.c' was not closed\n" );
      }
   }

   // All other files are closed:
   int numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen_s.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)\
[`fclose`, `_fcloseall`](fclose-fcloseall.md)\
[`_fdopen`, `_wfdopen`](fdopen-wfdopen.md)\
[`ferror`](ferror.md)\
[`_fileno`](fileno.md)\
[`freopen`, `_wfreopen`](freopen-wfreopen.md)\
[`_open`, `_wopen`](open-wopen.md)\
[`_setmode`](setmode.md)
