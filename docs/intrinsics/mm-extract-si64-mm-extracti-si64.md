---
description: '詳細については、次を参照してください: _mm_extract_si64、_mm_extracti_si64'
title: _mm_extract_si64、_mm_extracti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
ms.openlocfilehash: 39a07c7310727de8d752c060c3d38481469ff1a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322868"
---
# <a name="_mm_extract_si64-_mm_extracti_si64"></a>_mm_extract_si64、_mm_extracti_si64

**Microsoft 固有の仕様**

最初の `extrq` 引数の下位64ビットから指定されたビットを抽出する命令を生成します。

## <a name="syntax"></a>構文

```C
__m128i _mm_extract_si64(
   __m128i Source,
   __m128i Descriptor
);
__m128i _mm_extracti_si64(
   __m128i Source,
   int Length,
   int Index
);
```

### <a name="parameters"></a>パラメーター

*電源*\
から64ビットの下位に入力データが含まれている128ビットのフィールド。

*ディスクリプタ*\
から抽出するビットフィールドを記述する128ビットフィールド。

*数*\
から抽出するフィールドの長さを指定する整数です。

*[インデックス]* \
から抽出するフィールドのインデックスを指定する整数です。

## <a name="return-value"></a>戻り値

最下位ビットに抽出されたフィールドを含む128ビットのフィールド。

## <a name="requirements"></a>要件

|Intrinsic|アーキテクチャ|
|---------------|------------------|
|`_mm_extract_si64`|SSE4a|
|`_mm_extracti_si64`|SSE4a|

**ヘッダー ファイル** \<intrin.h>

## <a name="remarks"></a>解説

これらの組み込みは、 `extrq` *ソース* からビットを抽出する命令を生成します。 2つのバージョンがあります。は、直接のバージョンであり、 `_mm_extracti_si64` `_mm_extract_si64` ただちには存在しません。 各バージョンでは、 *ソース* からその長さで定義されたビットフィールドと最下位ビットのインデックスを抽出します。 長さとインデックスの値は mod 64 であるため、-1 と127の両方が63として解釈されます。 (減少) インデックスと (削減された) フィールドの長さの合計が64より大きい場合、結果は未定義になります。 フィールド長の値が0の場合は、64と解釈されます。 フィールド長とビットインデックスの両方がゼロの場合、 *ソース* のビット63:0 が抽出されます。 フィールド長が0でも、ビットインデックスが0以外の場合、結果は未定義になります。

の呼び出しでは `_mm_extract_si64` 、 *記述子* にビット13:8 のインデックスと、ビット5:0 で抽出されるデータのフィールド長が含まれています。

引数を指定してを呼び出すと、 `_mm_extracti_si64` コンパイラが整数定数であると判断できない場合、コンパイラはそれらの値を XMM register (*記述子*) にパックしてを呼び出すためのコードを生成し `_mm_extract_si64` ます。

命令のハードウェアサポートを確認するには、 `extrq` で組み込みを呼び出し、 `__cpuid` `InfoType=0x80000001` のビット6を確認し `CPUInfo[2] (ECX)` ます。 命令がサポートされている場合、このビットは1になり、それ以外の場合は0になります。 命令をサポートしていないこの組み込みのハードウェアを使用するコードを実行する場合、 `extrq` 結果は予測できません。

## <a name="example"></a>例

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

union {
    __m128i m;
    unsigned __int64 ui64[2];
} source, descriptor, result1, result2, result3;

int
main()
{
    source.ui64[0] =     0xfedcba9876543210ll;
    descriptor.ui64[0] = 0x0000000000000b1bll;

    result1.m = _mm_extract_si64 (source.m, descriptor.m);
    result2.m = _mm_extracti_si64(source.m, 27, 11);
    result3.ui64[0] = (source.ui64[0] >> 11) & 0x7ffffff;

    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;
    cout << "result2 = 0x" << result2.ui64[0] << endl;
    cout << "result3 = 0x" << result3.ui64[0] << endl;
}
```

```Output
result1 = 0x30eca86
result2 = 0x30eca86
result3 = 0x30eca86
```

**Microsoft 固有の仕様はここまで**

高度なマイクロデバイス (Inc.) による部分の著作権2007すべての権限が予約されています。 上級マイクロデバイス (Inc.) からのアクセス許可を使用して再現されます。

## <a name="see-also"></a>関連項目

[_mm_insert_si64、_mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
