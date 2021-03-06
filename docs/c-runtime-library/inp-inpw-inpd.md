---
title: sct.inp、_inp、inpw、_inpw、_inpd
description: 互換性のために残されている、sct.inp、_inp、inpw、_inpw、および Microsoft C ランタイムライブラリ (CRT) の _inpd 関数について説明します。
ms.date: 12/09/2019
api_name:
- inp
- inpw
- _inp
- _inpw
- _inpd
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- inp
- inpw
- _inp
- _inpw
- _inpd
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
ms.openlocfilehash: aafcd633b2ee04c9ced1520d4ecd1520475d0fea
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556477"
---
# <a name="inp-_inp-inpw-_inpw-_inpd"></a>sct.inp、_inp、inpw、_inpw、_inpd

ポート、バイト ( `inp` 、 `_inp` )、語 ( `inpw` , `_inpw` )、またはダブルワード ( `_inpd` ) からの入力。

> [!IMPORTANT]
> これらは古い関数です。 Visual Studio 2015 以降では、CRT では使用できません。
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```cpp
int _inp(
   unsigned short port
);
unsigned short _inpw(
   unsigned short port
);
unsigned long _inpd(
   unsigned short port
);
```

### <a name="parameters"></a>パラメーター

*ポート*\
I/O ポート番号。

## <a name="return-value"></a>戻り値

これらの関数は、 `port`から読み込んだバイト、ワード、またはダブルワードを返します。 エラーの戻り値はありません。

## <a name="remarks"></a>解説

`_inp`、 `_inpw`、 `_inpd` の各関数は、指定された入力ポートからそれぞれバイト、ワード、ダブルワードを 1 つ読み込みます。 ポート番号として、0 - 65,535 の unsigned short 型整数を入力できます。

これらの関数は I/O ポートから直接読み込まれるため、ユーザー コードで使用できません。

`inp`との `inpw` 名前は、関数および関数の古い名前で、非推奨とされてい `_inp` `_inpw` ます。 詳細については、「 [POSIX 関数名](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|`_inp`|\<conio.h>|
|`_inpw`|\<conio.h>|
|`_inpd`|\<conio.h>|

互換性について詳しくは、「 [Compatibility](../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="see-also"></a>関連項目

[コンソール入出力とポート入出力](../c-runtime-library/console-and-port-i-o.md)\
[outp、outp、_outp、_outpw、_outpd](../c-runtime-library/outp-outpw-outpd.md)
