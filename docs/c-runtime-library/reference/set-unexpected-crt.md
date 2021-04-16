---
description: 詳細については、「set_unexpected (CRT)」を参照してください。
title: set_unexpected (CRT)
ms.date: 1/14/2021
api_name:
- set_unexpected
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_unexpected
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
ms.openlocfilehash: f5922cb5fb6b06cc809818fcfd324b6fc825c5a6
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577107"
---
# <a name="set_unexpected-crt"></a>`set_unexpected` .CRT

によって呼び出される独自の終了関数をインストール **`unexpected`** します。

## <a name="syntax"></a>構文

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>パラメーター

*`unexpFunction`*\
関数を置き換えるために記述する関数へのポインター **`unexpected`** 。

## <a name="return-value"></a>戻り値

**`_set_unexpected`** 前の関数を後で復元できるように、によって登録された前の終了関数へのポインターを返します。 前の関数が設定されていない場合は、戻り値を使用して既定の動作を復元できます。この値はでもかまい **`NULL`** ません。

## <a name="remarks"></a>解説

関数は、 **`set_unexpected`** によって呼び出される関数として *関数* をインストールし **`unexpected`** ます。 **`unexpected`** は、現在の C++ 例外処理の実装では使用されません。 **`unexpected_function`** 型は EH で定義されています。ユーザー定義の予期しない関数へのポインターとしての H。を返す *関数* **`void`** 。 *カスタム関数関数は*、呼び出し元に戻らないようにする必要があります。

```cpp
typedef void ( *unexpected_function )( );
```

既定では、はを **`unexpected`** 呼び出し **`terminate`** ます。 この既定の動作を変更するには、独自の終了関数を作成し、 **`set_unexpected`** その引数として関数の名前を指定してを呼び出します。 **`unexpected`** の引数として渡された最後の関数を呼び出し **`set_unexpected`** ます。

の呼び出しによってインストールされるカスタムの終了関数とは異なり **`set_terminate`** 、内から例外がスローされる可能性があり **`unexpFunction`** ます。

マルチ スレッド環境では、予期しない関数はスレッドごとに別々に管理されます。 新しいスレッドは各々、それぞれの予期しない関数をインストールする必要があります。 したがって、各スレッドがそれぞれの予期しない処理を担当します。

現在の C++ 例外処理の実装では、 **`unexpected`** は **`terminate`** 既定でを呼び出し、例外処理ランタイムライブラリによって呼び出されることはありません。 ではなくを呼び出すことには、特に利点はありません **`unexpected`** **`terminate`** 。

動的にリンクされた **`set_unexpected`** すべての dll または exe に対して1つのハンドラーがあります。ハンドラーを呼び出しても別のハンドラー **`set_unexpected`** に置き換えられるか、または別の dll または EXE で設定されたハンドラーを置き換えることができます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**`set_unexpected`**|`<eh.h>`|

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[例外処理ルーチン](../../c-runtime-library/exception-handling-routines.md)\
[`abort`](abort.md)\
[`_get_unexpected`](get-unexpected.md)\
[`set_terminate`](set-terminate-crt.md)\
[`terminate`](terminate-crt.md)\
[`unexpected`](unexpected-crt.md)\
