---
description: '詳細については、次を参照してください: _set_error_mode'
title: _set_error_mode
ms.date: 11/04/2016
api_name:
- _set_error_mode
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_error_mode
- _set_error_mode
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
ms.openlocfilehash: f21983702adb0ae080443e5869485fe581a65f85
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334091"
---
# <a name="_set_error_mode"></a>_set_error_mode

**__Error_mode** を変更して、C ランタイムがプログラムを終了する可能性のあるエラーのエラーメッセージを書き込む既定以外の場所を決定します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _set_error_mode(
   int mode_val
);
```

### <a name="parameters"></a>パラメーター

*mode_val*<br/>
エラー メッセージの書き込み先。

## <a name="return-value"></a>戻り値

エラーが発生した場合、以前の設定または-1 を返します。

## <a name="remarks"></a>解説

**__Error_mode** の値を設定することによって、エラー出力シンクを制御します。 たとえば、出力を標準エラーに転送したり、 **MessageBox** API を使用したりすることができます。

*Mode_val* パラメーターは、次のいずれかの値に設定できます。

|値|説明|
|---------------|-----------------|
|**_OUT_TO_DEFAULT**|エラーシンクは **__app_type** によって決定されます。|
|**_OUT_TO_STDERR**|エラー シンクは、標準エラーです。|
|**_OUT_TO_MSGBOX**|エラー シンクは、メッセージ ボックスです。|
|**_REPORT_ERRMODE**|現在の **__error_mode** 値を報告します。|

リストされている以外の値が渡された場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているように、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、 **_set_error_mode** **errno** を **EINVAL** に設定し、-1 を返します。

[Assert](assert-macro-assert-wassert.md)と共に使用すると、 **_set_error_mode** によってダイアログボックスに失敗したステートメントが表示され、[**無視**] ボタンをクリックすると、プログラムの実行を続行できるようになります。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_set_error_mode**|\<stdlib.h>|

## <a name="example"></a>例

```C
// crt_set_error_mode.c
// compile with: /c
#include <stdlib.h>
#include <assert.h>

int main()
{
   _set_error_mode(_OUT_TO_STDERR);
   assert(2+2==5);
}
```

```Output
Assertion failed: 2+2==5, file crt_set_error_mode.c, line 8

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>関連項目

[assert マクロ、_assert、_wassert](assert-macro-assert-wassert.md)<br/>
