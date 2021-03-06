---
description: '詳細については、次を参照してください: _aligned_offset_malloc'
title: _aligned_offset_malloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_malloc
- _o__aligned_offset_malloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_offset_malloc
- aligned_offset_malloc
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
ms.openlocfilehash: 0a94a58abde85046e32ca50245e8b9878aeb9b92
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312424"
---
# <a name="_aligned_offset_malloc"></a>_aligned_offset_malloc

指定された配置の境界にメモリを割り当てます。

## <a name="syntax"></a>構文

```C
void * _aligned_offset_malloc(
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>パラメーター

*size*<br/>
要求されたメモリ割り当てのサイズ。

*配置*<br/>
アラインメント値。2 の整数乗である必要があります。

*offset*<br/>
アラインメントを強制するためのメモリ割り当てへのオフセット。

## <a name="return-value"></a>戻り値

割り当てられたメモリブロックへのポインター。操作が失敗した場合は **NULL** 。

## <a name="remarks"></a>解説

**_aligned_offset_malloc** は、入れ子になった要素にアラインメントが必要な場合に役立ちます。たとえば、入れ子になったクラスでアラインメントが必要な場合です。

**_aligned_offset_malloc** は **malloc** に基づいています。詳細については、「 [malloc](malloc.md)」を参照してください。

**_aligned_offset_malloc** はとマークされ `__declspec(noalias)` `__declspec(restrict)` ます。つまり、関数は、グローバル変数を変更せず、返されるポインターがエイリアス化されていないことを保証します。 詳細については、「[noalias](../../cpp/noalias.md)」、および「[restrict](../../cpp/restrict.md)」を参照してください。

メモリ割り当てが失敗した場合、または要求されたサイズが **_HEAP_MAXREQ** より大きい場合、この関数は **errno** を **ENOMEM** に設定します。 **Errno** の詳細については、「 [errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。 また、 **_aligned_offset_malloc** パラメーターを検証します。 *Alignment* が2の累乗でない場合、または *offset* が *size* 以上で0以外の場合、この関数は「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、この関数は **NULL** を返し、 **errno** を **EINVAL** に設定します。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_aligned_offset_malloc**|\<malloc.h>|

## <a name="example"></a>例

詳細については、「[_aligned_malloc](aligned-malloc.md)」を参照してください。

## <a name="see-also"></a>関連項目

[データの配置](../../c-runtime-library/data-alignment.md)<br/>
