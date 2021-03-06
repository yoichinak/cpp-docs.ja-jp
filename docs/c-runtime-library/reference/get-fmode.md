---
description: '詳細については、次を参照してください: _get_fmode'
title: _get_fmode
ms.date: 4/2/2020
api_name:
- _get_fmode
- _o__get_fmode
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
- get_fmode
- _get_fmode
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
ms.openlocfilehash: 56716b7e8c12c5a3de79098a8227be31148ae386
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97303649"
---
# <a name="_get_fmode"></a>_get_fmode

ファイル I/O 操作の既定のファイル変換モードを取得します。

## <a name="syntax"></a>構文

```C
errno_t _get_fmode(
   int * pmode
);
```

### <a name="parameters"></a>パラメーター

*pmode*<br/>
現在の既定のモード ( **_O_TEXT** または **_O_BINARY** に格納される整数へのポインター。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。 *Pmode* が **NULL** の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、 **errno** は **einval** に設定され、関数は **einval** を返します。

## <a name="remarks"></a>解説

この関数は、[_fmode](../../c-runtime-library/fmode.md) グローバル変数の値を取得します。 この変数は、 **_open**、 **_pipe**、 **fopen**、 [freopen](freopen-wfreopen.md)など、低レベルのファイル i/o 操作とストリームファイル i/o 操作の両方について、既定のファイル変換モードを指定します。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="example"></a>例

[_set_fmode](set-fmode.md) の例を参照してください。

## <a name="see-also"></a>関連項目

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[テキストモードとバイナリモードのファイル入出力](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
