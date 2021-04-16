---
description: '詳細情報: &lt; chrono&gt;'
title: '&lt;chrono&gt;'
ms.date: 05/07/2019
f1_keywords:
- <chrono>
- chrono/std::chrono::nanoseconds
- chrono/std::chrono::minutes
- chrono/std::chrono::seconds
- chrono/std::chrono::hours
- chrono/std::chrono::milliseconds
- chrono/std::chrono::microseconds
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
ms.openlocfilehash: 45e59f4c09371398cc5030b78b6378ad12d6a77b
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539503"
---
# `<chrono>`

標準ヘッダーをインクルードして、 `<chrono>` 時間の期間と時間を表すクラスと関数を定義します。

Visual Studio 2015 以降、の実装は、 `steady_clock` 安定性および単調性の C++ 標準要件を満たすように変更されています。 `steady_clock` はに基づいて `QueryPerformanceCounter()` い `high_resolution_clock` ます。これはの typedef です `steady_clock` 。 その結果、Microsoft C++ コンパイラで `steady_clock::time_point` はがになりまし `typedef` た `chrono::time_point<steady_clock>` 。ただし、この規則は、必ずしも他の実装の場合と同じではありません。

## <a name="requirements"></a>要件

**ヘッダー:**`<chrono>`

**名前空間:** std

## <a name="members"></a>メンバー

### <a name="classes"></a>クラス

|名前|Description|
|-|-|
|[`duration` 講義](../standard-library/duration-class.md)|時間間隔を保持する型を表します。|
|[`time_point` 講義](../standard-library/time-point-class.md)|時点を表す型を表します。|

### <a name="structs"></a>構造体

|Name|Description|
|-|-|
|[`common_type` データ](../standard-library/common-type-structure.md)|とのインスタンス化のクラステンプレートの特殊化について説明し [`common_type`](../standard-library/common-type-class.md) `duration` `time_point` ます。|
|[`duration_values` データ](../standard-library/duration-values-structure.md)|`duration` テンプレート パラメーター `Rep` に特定の値を指定します。|
|[`high_resolution_clock` 体型](../standard-library/high-resolution-clock-struct.md)||
|[`steady_clock` 体型](../standard-library/steady-clock-struct.md)|`steady` クロックを表します。|
|[`system_clock` データ](../standard-library/system-clock-structure.md)|*`clock type`* システムのリアルタイムクロックに基づくを表します。|
|[`treat_as_floating_point` データ](../standard-library/treat-as-floating-point-structure.md)|型を浮動小数点型として扱うことができるかどうかを指定します。|

### <a name="functions"></a>関数

|Name|Description|
|-|-|
|[`duration_cast`](../standard-library/chrono-functions.md#duration_cast)|`duration` オブジェクトを指定した型にキャストします。|
|[`time_point_cast`](../standard-library/chrono-functions.md#time_point_cast)|`time_point` オブジェクトを指定した型にキャストします。|

### <a name="operators"></a>演算子

|Name|Description|
|-|-|
|[`operator-`](../standard-library/chrono-operators.md#operator-)|`duration` オブジェクトおよび `time_point` オブジェクトの減算または否定の演算子。|
|[`operator!=`](../standard-library/chrono-operators.md#op_neq)|`duration` オブジェクトおよび `time_point` オブジェクトで使用される非等値演算子。|
|[`operator modulo`](../standard-library/chrono-operators.md#op_modulo)|`duration` オブジェクトに対するモジュロ演算の演算子。|
|[`operator*`](../standard-library/chrono-operators.md#op_star)|`duration` オブジェクトの乗算演算子。|
|[`operator/`](../standard-library/chrono-operators.md#op_div)|`duration` オブジェクトの除算演算子。|
|[`operator+`](../standard-library/chrono-operators.md#op_add)|`duration` オブジェクトおよび `time_point` オブジェクトを追加します。|
|[`operator<`](../standard-library/chrono-operators.md#op_lt)|一方の `duration` オブジェクトまたは `time_point` オブジェクトの値が、もう一方の `duration` オブジェクトまたは `time_point` オブジェクトの値未満かどうかを判断します。|
|[`operator<=`](../standard-library/chrono-operators.md#op_lt_eq)|一方の `duration` オブジェクトまたは `time_point` オブジェクトの値が、もう一方の `duration` オブジェクトまたは `time_point` オブジェクトの値以下かどうかを判断します。|
|[operator = =](../standard-library/chrono-operators.md#op_eq_eq)|2 つの `duration` オブジェクトが同じ長さの時間間隔を表しているかどうか、または 2 つの `time_point` オブジェクトが同じ時点を表しているかどうかを判断します。|
|[`operator>`](../standard-library/chrono-operators.md#op_gt)|一方の `duration` オブジェクトまたは `time_point` オブジェクトの値が、もう一方の `duration` オブジェクトまたは `time_point` オブジェクトの値より大きいかどうかを判断します。|
|[`operator>=`](../standard-library/chrono-operators.md#op_gt_eq)|一方の `duration` オブジェクトまたは `time_point` オブジェクトの値が、もう一方の `duration` オブジェクトまたは `time_point` オブジェクトの値以上かどうかを判断します。|

### <a name="typedefs-predefined-duration-types"></a>Typedef (定義済みの期間の種類)

次の typedef で使用される比率の種類の詳細については、「」を参照してください [`<ratio>`](../standard-library/ratio.md) 。

|Name|Description|
|-|-|
|`typedef duration<long long, nano> nanoseconds;`|`duration`ティック間隔が1ナノ秒の型のシノニム。|
|`typedef duration<long long, micro> microseconds;`|`duration`ティック間隔が1マイクロ秒の型のシノニム。|
|`typedef duration<long long, milli> milliseconds;`|`duration`ティック間隔が1ミリ秒の型のシノニム。|
|`typedef duration<long long> seconds;`|`duration`ティック間隔が1秒の型のシノニム。|
|`typedef duration<int, ratio<60> > minutes;`|`duration`ティック間隔が1分の型のシノニムです。|
|`typedef duration<int, ratio<3600> > hours;`|`duration`ティック間隔が1時間の型のシノニム。|

### <a name="literals"></a>リテラル

**(C++ 11)** ヘッダーには、 `<chrono>` コードの利便性、タイプセーフ、および保守性を高めるために使用できる、次の [ユーザー定義リテラル](../cpp/user-defined-literals-cpp.md) が定義されています。 これらのリテラルはインライン名前空間で定義され `literals::chrono_literals` 、がスコープ内にある場合はスコープ内にあり `std::chrono` ます。

|宣言|Description|
|-|-|
|`hours operator "" h(unsigned long long Val)`|時間を整数値として指定します。|
|`duration<double, ratio<3600> > operator "" h(long double Val)`|時間を浮動小数点値として指定します。|
|`minutes (operator "" min)(unsigned long long Val)`|分を整数値として指定します。|
|`duration<double, ratio<60> > (operator "" min)( long double Val)`|分を浮動小数点値として指定します。|
|`seconds operator "" s(unsigned long long Val)`|分を整数値として指定します。|
|`duration<double> operator "" s(long double Val)`|秒を浮動小数点値として指定します。|
|`milliseconds operator "" ms(unsigned long long Val)`|ミリ秒を整数値として指定します。|
|`duration<double, milli> operator "" ms(long double Val)`|ミリ秒を浮動小数点値として指定します。|
|`microseconds operator "" us(unsigned long long Val)`|マイクロ秒を整数値として指定します。|
|`duration<double, micro> operator "" us(long double Val)`|マイクロ秒を浮動小数点値として指定します。|
|`nanoseconds operator "" ns(unsigned long long Val)`|ナノ秒を整数値として指定します。|
|`duration<double, nano> operator "" ns(long double Val)`|ナノ秒を浮動小数点値として指定します。|

chrono リテラルを使用する方法の例を次に示します。

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="see-also"></a>こちらもご覧ください

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)
