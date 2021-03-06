---
description: '詳細については、次を参照してください: _mm_insert_si64、_mm_inserti_si64'
title: _mm_insert_si64、_mm_inserti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
ms.openlocfilehash: 96ddf9a8836dcb927a09a51e0b2818b2a040c9d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345265"
---
# <a name="_mm_insert_si64-_mm_inserti_si64"></a>_mm_insert_si64、_mm_inserti_si64

**Microsoft 固有の仕様**

`insertq`2 番目のオペランドのビットを最初のオペランドに挿入する命令を生成します。

## <a name="syntax"></a>構文

```C
__m128i _mm_insert_si64(
   __m128i Source1,
   __m128i Source2
);
__m128i _mm_inserti_si64(
   __m128i Source1,
   __m128i Source2
   int Length,
   int Index
);
```

### <a name="parameters"></a>パラメーター

*Source1*\
からフィールドが挿入される、64ビット未満の入力データを持つ128ビットフィールド。

*Source2*\
から下位ビットに挿入するデータを含む128ビットのフィールド。  の場合、には `_mm_insert_si64` 、上位ビットのフィールド記述子も含まれます。

*数*\
から挿入するフィールドの長さを指定する整数定数。

*[インデックス]* \
からデータが挿入されるフィールドの最下位ビットのインデックスを指定する整数定数。

## <a name="return-value"></a>戻り値

128ビットのフィールド。低い64ビットには *Source1* の元の低64ビットが含まれ、指定されたビットフィールドは *Source2* の下位ビットに置き換えられます。 戻り値の上位64ビットは未定義です。

## <a name="requirements"></a>要件

|Intrinsic|アーキテクチャ|
|---------------|------------------|
|`_mm_insert_si64`|SSE4a|
|`_mm_inserti_si64`|SSE4a|

**ヘッダー ファイル** \<intrin.h>

## <a name="remarks"></a>解説

これらの組み込みは、 `insertq` *Source2* から *Source1* にビットを挿入する命令を生成します。 2つのバージョンがあります。 `_mm_inserti_si64` は、直接のバージョンであり、 `_mm_insert_si64` ただちには存在しません。 各バージョンでは、指定された長さのビットフィールドを Source2 から抽出し、Source1 に挿入します。  抽出されたビットは、Source2 の最下位ビットです。  これらのビットが挿入されるフィールド Source1 は、長さと最下位ビットのインデックスによって定義されます。  長さとインデックスの値は mod 64 であるため、-1 と127の両方が63として解釈されます。 (減少した) ビットインデックスと (削減された) フィールド長の合計が64より大きい場合、結果は未定義になります。 フィールド長の値が0の場合は、64と解釈されます。 フィールド長とビットインデックスの両方がゼロの場合は、 *Source2* のビット63:0 が *Source1* に挿入されます。 フィールド長が0でも、ビットインデックスが0以外の場合、結果は未定義になります。

_Mm_insert_si64 の呼び出しでは、フィールド長は Source2 のビット77:72 と、ビット69:64 のインデックスに含まれています。

引数を指定してを呼び出すと、コンパイラが整数定数であると `_mm_inserti_si64` 判断できない場合、コンパイラはそれらの値を XMM register にパッケージ化し、を呼び出すためのコードを生成し `_mm_insert_si64` ます。

命令のハードウェアサポートを確認するには、 `insertq` で組み込みを呼び出し、 `__cpuid` `InfoType=0x80000001` のビット6を確認し `CPUInfo[2] (ECX)` ます。 命令がサポートされている場合、このビットは1になり、それ以外の場合は0になります。 命令をサポートしていないハードウェアに組み込みを使用するコードを実行する場合、 `insertq` 結果は予測できません。

## <a name="example"></a>例

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

union {
    __m128i m;
    unsigned __int64 ui64[2];
} source1, source2, source3, result1, result2, result3;

int
main()
{

    __int64 mask;

    source1.ui64[0] = 0xffffffffffffffffll;
    source2.ui64[0] = 0xfedcba9876543210ll;
    source2.ui64[1] = 0xc10;
    source3.ui64[0] = source2.ui64[0];

    result1.m = _mm_insert_si64 (source1.m, source2.m);
    result2.m = _mm_inserti_si64(source1.m, source3.m, 16, 12);
    mask = 0xffff << 12;
    mask = ~mask;
    result3.ui64[0] = (source1.ui64[0] & mask) |
                      ((source2.ui64[0] & 0xffff) << 12);

    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;
    cout << "result2 = 0x" << result2.ui64[0] << endl;
    cout << "result3 = 0x" << result3.ui64[0] << endl;

}
```

```Output
result1 = 0xfffffffff3210fff
result2 = 0xfffffffff3210fff
result3 = 0xfffffffff3210fff
```

**Microsoft 固有の仕様はここまで**

高度なマイクロデバイス (Inc.) による部分の著作権2007すべての権限が予約されています。 上級マイクロデバイス (Inc.) からのアクセス許可を使用して再現されます。

## <a name="see-also"></a>関連項目

[_mm_extract_si64、_mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
