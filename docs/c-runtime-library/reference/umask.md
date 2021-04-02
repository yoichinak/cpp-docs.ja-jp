---
title: _umask
description: _Umask の API リファレンス既定のファイルアクセス許可マスクを設定します。
ms.date: 4/2/2020
api_name:
- _umask
- _o__umask
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _umask
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
ms.openlocfilehash: 8923e2a9ef489d35d1e7f55b91bfb632c0d22580
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099301"
---
# <a name="_umask"></a>_umask

既定のファイル アクセス許可マスクを設定します。 この関数のセキュリティが強化されたバージョンについては、「 [_umask_s](umask-s.md) 」を参照してください。

## <a name="syntax"></a>構文

```C
int _umask( int pmode );
```

### <a name="parameters"></a>パラメーター

*pmode*<br/>
既定のアクセス許可の設定。

## <a name="return-value"></a>戻り値

**_umask** は、の前の値である *pmode* を返します。 エラーの戻り値はありません。

## <a name="remarks"></a>解説

**_Umask** 関数は、現在のプロセスのファイルアクセス許可マスクを、 *pmode* によって指定されたモードに設定します。 ファイルのアクセス許可マスクは、 **_creat**、 **_open**、または **_sopen** によって作成された新しいファイルのアクセス許可の設定を変更します。 マスクのビットが 1 の場合は、ファイルの要求されたアクセス許可値に対応するビットは 0 (許可しない) に設定されます。 マスクのビットが 0 の場合は、対応するビットは変更されません。 新しいファイルのアクセス許可の設定は、そのファイルが最初に閉じられるまで、設定されません。

整数式 *pmode* には、sysstatで定義されている次のマニフェスト定数のいずれかまたは両方が含まれています。始め

|*pmode*|説明|
|-|-|
| **_S_IWRITE** | 書き込みが許可されます。 |
| **_S_IREAD** | 読み取りが許可されます。 |
| **_S_IREAD** &#124; **_S_IWRITE** | 読み取りと書き込みが許可されます。 |

両方の定数が指定されている場合は、ビットごとの OR 演算子 ( **&#124;** ) と結合されます。 *Pmode* 引数が **_S_IREAD** の場合、読み取りは許可されません (ファイルは書き込み専用です)。 *Pmode* 引数が **_S_IWRITE** の場合、書き込みは許可されません (ファイルは読み取り専用です)。 たとえば、マスクに書き込みビットが設定されている場合、新しいファイルはいずれも読み取り専用となります。 MS-DOS および Windows オペレーティング システムでは、すべてのファイルは読み取り可能です。書き込み専用のアクセス許可を与えることはできません。 このため、読み取りビットを **_umask** に設定しても、ファイルのモードには影響しません。

*Pmode* がマニフェスト定数のいずれかの組み合わせではない場合、または別の定数セットを組み込んでいる場合、関数は単にそれらを無視します。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_umask**|\<io.h>, \<sys/stat.h>, \<sys/types.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_umask.c
// compile with: /W3
// This program uses _umask to set
// the file-permission mask so that all future
// files will be created as read-only files.
// It also displays the old mask.
#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask;

   /* Create read-only files: */
   oldmask = _umask( _S_IWRITE ); // C4996
   // Note: _umask is deprecated; consider using _umask_s instead
   printf( "Oldmask = 0x%.4x\n", oldmask );
}
```

```Output
Oldmask = 0x0000
```

## <a name="see-also"></a>関連項目

[ファイルの処理](../../c-runtime-library/file-handling.md)<br/>
[低レベル i/o](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
