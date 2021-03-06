---
description: '詳細については、次を参照してください: _CrtMemDumpAllObjectsSince'
title: _CrtMemDumpAllObjectsSince
ms.date: 11/04/2016
api_name:
- _CrtMemDumpAllObjectsSince
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
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
ms.openlocfilehash: e833543d3119b39a21b596af412a97f6991e4ef0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319639"
---
# <a name="_crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince

プログラムの実行開始時以降または指定されたヒープ状態以降のヒープ内のオブジェクトについての情報をダンプします (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
void _CrtMemDumpAllObjectsSince(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>パラメーター

*state*<br/>
ダンプの開始点となるヒープ状態へのポインターまたは **NULL**。

## <a name="remarks"></a>解説

**_CrtMemDumpAllObjectsSince** 関数は、ヒープに割り当てられたオブジェクトのデバッグヘッダー情報をユーザーが判読できる形式でダンプします。 ダンプ情報は、割り当ての追跡とメモリの問題の検出のためにアプリケーションで使用できます。 [_DEBUG](../../c-runtime-library/debug.md)が定義されていない場合、 **_CrtMemDumpAllObjectsSince** の呼び出しはプリプロセス中に削除されます。

**_CrtMemDumpAllObjectsSince** は、 *state* パラメーターの値を使用して、ダンプ操作を開始する場所を決定します。 指定されたヒープ状態からのダンプを開始するには、 *state* パラメーターに、 **_CrtMemDumpAllObjectsSince** が呼び出される前に [_CrtMemCheckpoint](crtmemcheckpoint.md)によって入力された **_CrtMemState** 構造体へのポインターを指定する必要があります。 *State* が **NULL** の場合、関数はプログラムの実行開始時からダンプを開始します。

アプリケーションが [_CrtSetDumpClient](crtsetdumpclient.md)を呼び出すことによってダンプフック関数をインストールした場合は、 **_CLIENT_BLOCK** 型のブロックに関する情報を **_CrtMemDumpAllObjectsSince** ダンプするたびに、アプリケーションによって提供されるダンプ関数も呼び出されます。 既定では、内部 C ランタイムブロック (**_CRT_BLOCK**) はメモリダンプ操作に含まれません。 [_CrtSetDbgFlag](crtsetdbgflag.md)関数を使用すると、 **_crtDbgFlag** の **_CRTDBG_CHECK_CRT_DF** ビットをオンにして、これらのブロックを含めることができます。 また、解放済みまたは無視としてマークされているブロック (**_FREE_BLOCK**、**_IGNORE_BLOCK**) は、メモリ ダンプに含まれません。

ヒープ状態関数と **_CrtMemState** 構造体の詳細については、「 [ヒープ状態レポート関数](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。 デバッグ バージョンのベース ヒープでのメモリ ブロックの割り当て、初期化、管理の方法について詳しくは、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**以降の _CrtMemDumpAll**|\<crtdbg.h>|

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="example"></a>例

**_CrtMemDumpAllObjectsSince** の使用方法の例については、「 [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)」を参照してください。

## <a name="see-also"></a>関連項目

[デバッグルーチン](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
