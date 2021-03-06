---
description: '詳細情報: towctrans'
title: towctrans
ms.date: 11/04/2016
api_name:
- towctrans
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- towctrans
helpviewer_keywords:
- towctrans function
ms.assetid: 1ed1e70d-7b31-490f-a7d9-42564b5924ca
ms.openlocfilehash: 7b8ecdd38ca45eb658d5e9f61bf05549878228bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318300"
---
# <a name="towctrans"></a>towctrans

文字を変換します。

## <a name="syntax"></a>構文

```C
wint_t towctrans(
   wint_t c,
   wctrans_t category
);
```

### <a name="parameters"></a>パラメーター

*c*<br/>
変換する文字。

*category*<br/>
[wctrans](wctrans.md) の戻り値を含む識別子。

## <a name="return-value"></a>戻り値

**Towctrans** の後の文字 *c* では、*カテゴリ* の変換規則が使用されていました。

## <a name="remarks"></a>解説

*Category* の値は、以前に [wctrans](wctrans.md)の呼び出しが成功したときに返されている必要があります。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**towctrans**|\<wctype.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

**Towctrans** を使用するサンプルについては、「 **wctrans** 」を参照してください。

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
