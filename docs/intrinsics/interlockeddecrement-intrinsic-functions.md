---
title: 組み込み関数の _InterlockedDecrement
description: インタロックデクリメントのための Microsoft C/c + + コンパイラ組み込み関数。
ms.date: 09/03/2020
f1_keywords:
- _InterlockedDecrement16_rel_cpp
- _InterlockedDecrement16_acq_cpp
- _InterlockedDecrement16_rel
- _InterlockedDecrement64_acq
- _InterlockedDecrement_nf
- _InterlockedDecrement16_nf
- _InterlockedDecrement64_rel_cpp
- _InterlockedDecrement_rel_cpp
- _InterlockedDecrement16_acq
- _InterlockedDecrement64_acq_cpp
- _InterlockedDecrement_rel
- _InterlockedDecrement64_nf
- _InterlockedDecrement16_cpp
- _InterlockedDecrement64
- _InterlockedDecrement_cpp
- _InterlockedDecrement64_rel
- _InterlockedDecrement16
- _InterlockedDecrement
- _InterlockedDecrement64_cpp
- _InterlockedDecrement_acq
- _InterlockedDecrement_acq_cpp
helpviewer_keywords:
- InterlockedDecrement64_rel intrinsic
- InterlockedDecrement64 intrinsic
- _InterlockedDecrement16 intrinsic
- _InterlockedDecrement16_acq intrinsic
- _InterlockedDecrement intrinsic
- _InterlockedDecrement_nf intrinsic
- _InterlockedDecrement_acq intrinsic
- _InterlockedDecrement64_rel intrinsic
- _InterlockedDecrement16_rel intrinsic
- InterlockedDecrement intrinsic
- InterlockedDecrement16 intrinsic
- _InterlockedDecrement16_nf intrinsic
- InterlockedDecrement64_acq intrinsic
- _InterlockedDecrement_rel intrinsic
- InterlockedDecrement_acq intrinsic
- _InterlockedDecrement64_acq intrinsic
- _InterlockedDecrement64 intrinsic
- _InterlockedDecrement64_nf intrinsic
- InterlockedDecrement_rel intrinsic
ms.assetid: 5268fce3-86b5-4b2b-b96c-2e531a3fb9b5
ms.openlocfilehash: b3ca624ba54f70750ecc303fb44f4fa242b4edc2
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556335"
---
# <a name="_interlockeddecrement-intrinsic-functions"></a>`_InterlockedDecrement` 組み込み関数

Win32 Windows SDK [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement) 関数のコンパイラ組み込みサポートを提供します。 `_InterlockedDecrement`組み込み関数は、 **Microsoft 固有**の関数です。

## <a name="syntax"></a>構文

```C
long _InterlockedDecrement(
   long volatile * lpAddend
);
long _InterlockedDecrement_acq(
   long volatile * lpAddend
);
long _InterlockedDecrement_rel(
   long volatile * lpAddend
);
long _InterlockedDecrement_nf(
   long volatile * lpAddend
);
short _InterlockedDecrement16(
   short volatile * lpAddend
);
short _InterlockedDecrement16_acq(
   short volatile * lpAddend
);
short _InterlockedDecrement16_rel(
   short volatile * lpAddend
);
short _InterlockedDecrement16_nf(
   short volatile * lpAddend
);
__int64 _InterlockedDecrement64(
   __int64 volatile * lpAddend
);
__int64 _InterlockedDecrement64_acq(
   __int64 volatile * lpAddend
);
__int64 _InterlockedDecrement64_rel(
   __int64 volatile * lpAddend
);
__int64 _InterlockedDecrement64_nf(
   __int64 volatile * lpAddend
);
```

### <a name="parameters"></a>パラメーター

*lpAddend*\
[入力、出力]デクリメントする変数への Volatile ポインター。

## <a name="return-value"></a>戻り値

戻り値は、デクリメントして生成された値です。

## <a name="requirements"></a>要件

|Intrinsic|Architecture|
|---------------|------------------|
|`_InterlockedDecrement`, `_InterlockedDecrement16`|x86、ARM、x64、ARM64|
|`_InterlockedDecrement64`|ARM、x64、ARM64|
|`_InterlockedDecrement_acq`, `_InterlockedDecrement_rel`, `_InterlockedDecrement_nf`, `_InterlockedDecrement16_acq`, `_InterlockedDecrement16_rel`, `_InterlockedDecrement16_nf`, `_InterlockedDecrement64_acq`, `_InterlockedDecrement64_rel`, `_InterlockedDecrement64_nf`,|ARM、ARM64|

**ヘッダー ファイル** \<intrin.h>

## <a name="remarks"></a>解説

`_InterlockedDecrement` には、格納するデータ型、およびプロセッサ固有の取得または解放のセマンティクスを使用するかどうかに基づき、異なるいくつかの種類があります。

`_InterlockedDecrement` 関数は 32 ビット整数値で動作しますが、`_InterlockedDecrement16` は 16 ビット整数値および `_InterlockedDecrement64` は 64 ビット整数値で動作します。

ARM プラットフォームでは、クリティカル セクションの最初と最後などで取得と解放のセマンティクスを必要とする場合は、`_acq` および `_rel` サフィックスの付いた組み込みを使用します。 `_nf`("フェンスなし") サフィックスの付いた組み込みは、メモリバリアとしては機能しません。

`lpAddend` パラメーターが指す変数は 32 ビットの境界に合わせて調整する必要があります。そのようにしない場合、この関数はマルチプロセッサの x86 システムおよび x 86 システム以外のシステムで失敗します。 詳細については、「 [align](../cpp/align-cpp.md)」を参照してください。

これらのルーチンは、組み込みとしてのみ使用できます。

## <a name="example"></a>例

```cpp
// compiler_intrinsics_interlocked.cpp
// compile with: /Oi
#define _CRT_RAND_S

#include <cstdlib>
#include <cstdio>
#include <process.h>
#include <windows.h>

// To declare an interlocked function for use as an intrinsic,
// include intrin.h and put the function in a #pragma intrinsic
// statement.
#include <intrin.h>

#pragma intrinsic (_InterlockedIncrement)

// Data to protect with the interlocked functions.
volatile LONG data = 1;

void __cdecl SimpleThread(void* pParam);

const int THREAD_COUNT = 6;

int main() {
   DWORD num;
   HANDLE threads[THREAD_COUNT];
   int args[THREAD_COUNT];
   int i;

   for (i = 0; i < THREAD_COUNT; i++) {
      args[i] = i + 1;
      threads[i] = reinterpret_cast<HANDLE>(_beginthread(SimpleThread, 0,
                           args + i));
      if (threads[i] == reinterpret_cast<HANDLE>(-1))
         // error creating threads
         break;
   }

   WaitForMultipleObjects(i, threads, true, INFINITE);
}

// Code for our simple thread
void __cdecl SimpleThread(void* pParam) {
   int threadNum = *((int*)pParam);
   int counter;
   unsigned int randomValue;
   unsigned int time;
   errno_t err = rand_s(&randomValue);

   if (err == 0) {
      time = (unsigned int) ((double) randomValue / (double) UINT_MAX * 500);
      while (data < 100) {
         if (data < 100) {
            _InterlockedIncrement(&data);
            printf_s("Thread %d: %d\n", threadNum, data);
         }

         Sleep(time);   // wait up to half of a second
      }
   }

   printf_s("Thread %d complete: %d\n", threadNum, data);
}
```

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[Keywords](../cpp/keywords-cpp.md)\
[X86 コンパイラとの競合](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
