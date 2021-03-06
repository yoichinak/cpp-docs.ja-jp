---
description: '詳細については、次を参照してください: _aligned_recalloc_dbg'
title: _aligned_recalloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_recalloc_dbg
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
- _aligned_recalloc_dbg
- aligned_recalloc_dbg
helpviewer_keywords:
- aligned_recalloc_dbg function
- _aligned_recalloc_dbg function
ms.assetid: 55c3c27e-561c-4d6b-9bf9-1e34cc556e4b
ms.openlocfilehash: bfe0450f4a1b63f7451ff148b183c94f59002efc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135734"
---
# <a name="_aligned_recalloc_dbg"></a>_aligned_recalloc_dbg

[_aligned_malloc](aligned-malloc.md) または [_aligned_offset_malloc](aligned-offset-malloc.md) で割り当てられたメモリ ブロックのサイズを変更し、メモリを 0 に初期化します (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
void * _aligned_recalloc_dbg(
   void * memblock,
   size_t num,
   size_t size,
   size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>パラメーター

*memblock*<br/>
現在のメモリ ブロック ポインター。

*number*<br/>
要素の数。

*size*<br/>
各要素のサイズ (バイト単位)。

*配置*<br/>
アラインメント値。2 の整数乗である必要があります。

*filename*<br/>
割り当て操作を要求したソースファイルの名前へのポインターまたは **NULL**。

*linenumber*<br/>
割り当て操作が要求されたソースファイル内の行番号または **NULL**。

## <a name="return-value"></a>戻り値

**_aligned_recalloc_dbg** は、再割り当てされた (移動された可能性がある) メモリブロックへの void ポインターを返します。 サイズが0でバッファー引数が **null** でない場合、またはブロックを指定されたサイズに拡張するのに十分なメモリがない場合、戻り値は **null** になります。 最初の場合には、元のブロックは解放されます。 2 番目の場合には、元のブロックは変更されません。 戻り値は、どの型のオブジェクトを格納する場合でも適切なアラインメントが保証されるストレージ領域を指します。 void 以外の型へのポインターを取得するには、戻り値の型キャストを使用します。

メモリを再割り当てしてブロックのアラインメントを変更すると、エラーになります。

## <a name="remarks"></a>解説

**_aligned_recalloc_dbg** は、 [_aligned_recalloc](aligned-recalloc.md) 関数のデバッグバージョンです。 [_DEBUG](../../c-runtime-library/debug.md)が定義されていない場合、 **_aligned_recalloc_dbg** の各呼び出しは **_aligned_recalloc** への呼び出しに限定されます。 **_Aligned_recalloc** と **_aligned_recalloc_dbg** はどちらもベースヒープ内のメモリブロックを再割り当てしますが、 **_aligned_recalloc_dbg** にはいくつかのデバッグ機能があります。リークをテストするための、ブロックのユーザー部分の両側のバッファーと、  / 割り当て要求の起点を特定するための filename *linenumber* information です。 ブロックの型パラメーターを使用して特定の割り当ての種類を追跡することは、固定された割り当てのデバッグ機能としてサポートされていません。 配置された割り当ては、_NORMAL_BLOCK ブロック型として表示されます。

指定されたメモリブロックを、要求されたサイズ (*数値* サイズ) よりも少し大きい領域で再割り当て **_aligned_recalloc_dbg** 。これは、最初に割り当てられた  *  メモリブロックのサイズよりも大きくなる可能性があります。 追加の領域は、デバッグ メモリ ブロックをリンクし、アプリケーションにデバッグ ヘッダー情報と上書きバッファーを提供するために、デバッグ ヒープ マネージャーによって使用されます。 再割り当てによって、元のメモリ ブロックがヒープ内の別の位置に移動されたり、メモリ ブロックのサイズが変わったりする場合があります。 ブロックのユーザー部分には値 0xCD が設定され、上書きバッファーには 0xFD が設定されます。

**_aligned_recalloc_dbg** は、メモリ割り当てが失敗した場合に **errno** を **ENOMEM** に設定します。必要なメモリの量 (前に説明したオーバーヘッドを含む) が **_HEAP_MAXREQ** を超えた場合は、 **EINVAL** が返されます。 このエラー コードと他のエラーコードの詳細については、「[errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

また、 **_aligned_recalloc_dbg** パラメーターを検証します。 *Alignment* が2の累乗でない場合、この関数は「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、この関数は **NULL** を返し、 **errno** を **EINVAL** に設定します。

デバッグ バージョンのベース ヒープに対するメモリ ブロックの割り当て、初期化、管理方法については、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 割り当てブロックの型とその使用方法については、「 [デバッグヒープ上のブロックの型](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。 標準で呼び出すヒープ関数と、アプリケーションのデバッグ ビルドで呼び出すデバッグ バージョンのヒープ関数との違いの詳細については、「[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_aligned_recalloc_dbg**|\<crtdbg.h>|

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="see-also"></a>関連項目

[デバッグルーチン](../../c-runtime-library/debug-routines.md)<br/>
