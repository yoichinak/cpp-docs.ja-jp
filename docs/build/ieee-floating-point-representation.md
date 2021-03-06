---
description: '詳細情報: IEEE 浮動小数点表現'
title: IEEE 浮動小数点表現
ms.date: 05/06/2019
helpviewer_keywords:
- float keyword
- real*8 value
- floating-point numbers, IEEE representation
- double data type, floating-point representation
- IEEE floating point representation
- real*10 value
- long double
- real*4 value
ms.assetid: 537833e8-fe05-49fc-8169-55fd0314b195
ms.openlocfilehash: 9de48975ba13fae6117b095565f22265e28edf07
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162652"
---
# <a name="ieee-floating-point-representation"></a>IEEE 浮動小数点表現

Microsoft C++ (MSVC) は、IEEE 数値標準に準拠しています。 IEEE-754 標準では、ハードウェアで実数を表す方法である浮動小数点形式が説明されています。 MSVC コンパイラのターゲットとなるハードウェアで表現可能な浮動小数点数には、少なくとも 5 つの内部形式があります。 コンパイラでは、これらのうち 2 つのみが使用されます。 MSVC では、"*単精度*" (4 バイト) 形式と "*倍精度*" (8 バイト) 形式が使用されます。 単精度は、キーワード **`float`** を使用して宣言されます。 倍精度は、キーワード **`double`** を使用して宣言されます。 また、IEEE 標準では、"*半精度*" (2 バイト) 形式と "*四倍精度*" (16 バイト) 形式に加えて、一部の C および C++ コンパイラで **`long double`** データ型として実装されている "*拡張倍精度*" (10 バイト) 形式も指定されています。 MSVC コンパイラ内では、 **`long double`** データ型は個別の型として扱われますが、ストレージの型は **`double`** にマップされます。 ただし、ハードウェアによってサポートされる拡張倍精度形式など、その他の形式を使用した計算に対する組み込みおよびアセンブリ言語のサポートがあります。

値は次のように格納されます。

|[値]|格納形式|
|-----------|---------------|
|単精度 (single-precision)|符号ビット、8 ビットの指数、23 ビットの仮数|
|倍精度|符号ビット、11 ビットの指数、52 ビットの仮数|

単精度と倍精度の形式では、小数部の先頭が 1 であると仮定されます。 小数部は "*有効桁*" と呼ばれます ("*仮数*" と呼ばれることもあります)。 この先頭の 1 はメモリに格納されないため、1 つ少ないビットが格納されても、有効桁は実際には 24 または 53 ビットです。 拡張倍精度形式では、実際にこのビットが格納されます。

指数は、可能な値の半分でバイアスされます。 つまり、実際の指数を得るためには、格納されている指数からこのバイアスを減算する必要があります。 格納された指数がバイアスより小さい場合、実際には負の指数になります。

指数は次のようにバイアスされます。

|指数|バイアスされる値|
|--------------|---------------|
|8 ビット (単精度)|127|
|11 ビット (倍精度)|1023|

これらの指数は 10 の累乗ではありません。2 の累乗です。 つまり、8 ビット格納された指数は -127 から 127 の範囲になり、0 から 254 として格納されます。 値 2<sup>127</sup> はおよそ 10<sup>38</sup> に等しくなります。これが単精度の実際の制限です。

仮数は、1.XXX という形式の 2 進小数として格納されます。 この分数の値は 1 以上 2 未満です。 実数は、常に "*正規化された形式*" で格納されます。 つまり、有効桁は、有効桁の上位ビットが常に 1 になるように左にシフトされます。 このビットは "*常に*" 1 であるため、単精度と倍精度の形式では仮定として扱われます (格納されません)。 2 進 (10 進ではない) 小数点は、先頭の 1 の右側にあるものと見なされます。

浮動小数点表現の形式は次のとおりです。

|形式|バイト 1|バイト 2|バイト 3|バイト 4|...|バイト n|
|------------|------------|------------|------------|------------|---------|------------|
|単精度 (single-precision)| `SXXXXXXX`|`XMMMMMMM`|`MMMMMMMM`|`MMMMMMMM`|||
|倍精度|`SXXXXXXX`|`XXXXMMMM`|`MMMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|

`S` は符号ビットを表し、`X` はバイアスされた指数ビット、`M` は仮数ビットです。 左端のビットは、単精度と倍精度の形式では仮定として扱われます

2 進小数点を適切にシフトするには、最初に指数のバイアスを除外してから、適切なビット数だけ右か左にその 2 進小数点を動かします。

## <a name="special-values"></a>特殊な値

浮動小数点形式には、特別に処理されるいくつかの値が含まれます。

### <a name="zero"></a>ゼロ

0 を正規化することはできないため、これを単精度または倍精度の値の正規化された形式で表現することはできません。 すべてゼロの特殊なビット パターンが 0 を表します。 符号ビットが設定されたゼロとして -0 を表すこともできますが、-0 と 0 は常に等しいと見なされます。

### <a name="infinities"></a>無限大

+∞ と −∞ の値は、すべて 1 の指数とすべてゼロの有効桁によって表されます。 正と負は、符号ビットを使用して表されます。

### <a name="subnormals"></a>非正規化

正規化された形式の最小値よりも絶対値の小さい数値を表すことができます。 これらは "*非正規化*" または "*非正規*" 数と呼ばれます。 指数がすべてゼロで、仮数がゼロでない場合、仮数の暗黙的な先頭ビットは、1 ではなくゼロであると見なされます。 仮数の先頭のゼロの数が増えると、非正規化数の精度が低下します。

### <a name="nan---not-a-number"></a>NaN - 非数

IEEE 浮動小数点形式では、0 / 0 などの実数でない値を表すことができます。 この種類の値は *NaN* と呼ばれます。 NaN は、すべて 1 の指数と 0 でない仮数で表されます。 NaN には 2 種類があります。*quiet* NaN または QNaN と、*signaling* NaN または SNaN です。 Quiet NaN の仮数の先頭は 1 であり、式を通じて伝達されます。 これらは、無限大で除算した結果や、無限大をゼロで乗算した結果など、不確定な値を表します。 signaling NaN の仮数の先頭は 0 です。 これらは有効でない操作のために使用され、浮動小数点のハードウェア例外が通知されます。

## <a name="examples"></a>使用例

単精度形式のいくつかの例を次に示します。

- 値 2 の場合、符号ビットは 0 です。 格納されている指数は 128 またはバイナリで 1000 0000 です。これは 127 に 1 を加えた値です。 格納された 2 進数の仮数は (1.)000 0000 0000 0000 0000 0000 です。これには暗黙的な先頭の 1 と 2 進小数点が含まれるため、実際の仮数は 1 になります。

   |[値]|計算式|2 進数表現|16 進数|
   |-|-|-|-|
   |2|1 * 2<sup>1</sup>|0100 0000 0000 0000 0000 0000 0000 0000|0x40000000|

- 値 -2。 符号ビットが設定されている点を除いて、+2 と同じです。 すべての IEEE 形式の浮動小数点数の負の値についても、同じことが当てはまります。

   |[値]|計算式|2 進数表現|16 進数|
   |-|-|-|-|
   |-2|-1 * 2<sup>1</sup>|1100 0000 0000 0000 0000 0000 0000 0000|0xC0000000|

- 値 4。 同じ仮数で、指数は 1 増加します (バイアスされた値は 129、または 2 進数で 100 0000 1 です。

   |[値]|計算式|2 進数表現|16 進数|
   |-|-|-|-|
   |4|1 * 2<sup>2</sup>|0100 0000 1000 0000 0000 0000 0000 0000|0x40800000|

- 値 6。 同じ指数で、有効桁が半分大きくなります。 これは (1.)100 0000 ...0000 0000 です。これは、2 進小数であるため、1 1/2 になります。小数部の値は 1/2、1/4、1/8 などになるためです。

   |[値]|計算式|2 進数表現|16 進数|
   |-|-|-|-|
   |6|1.5 * 2<sup>2</sup>|0100 0000 1100 0000 0000 0000 0000 0000|0x40C00000|

- 値 1。 他の 2 の累乗と同じ仮数で、バイアスされた指数は、127、または 2 進数の 011 1111 1 で、2 よりも 1 小さくなります。

   |[値]|計算式|2 進数表現|16 進数|
   |-|-|-|-|
   |1|1 * 2<sup>0</sup>|0011 1111 1000 0000 0000 0000 0000 0000|0x3F800000|

- 値 0.75。 バイアスされた指数は 126 (2 進数の 011 1111 0) で、仮数は (1.)100 0000 ...0000 0000 です。これは 1 1/2 です。

   |[値]|計算式|2 進数表現|16 進数|
   |-|-|-|-|
   |0.75|1.5 * 2<sup>-1</sup>|0011 1111 0100 0000 0000 0000 0000 0000|0x3F400000|

- 値 2.5。 仮数に 1/4 を表すビットが設定される以外は、2 とまったく同じです。

   |[値]|計算式|2 進数表現|16 進数|
   |-|-|-|-|
   |2.5|1.25 * 2<sup>1</sup>|0100 0000 0010 0000 0000 0000 0000 0000|0x40200000|

- 1/10 は、2 進数では繰り返しになる分数です。 有効桁は 1.6 よりも少し小さくなり、バイアスされた指数によって 1.6 が 16 で除算されることが示されます。 (これはバイナリでは 011 1101 1、10 進数では 123 です。)実際の指数は 123 - 127 = -4 です。これは、乗算に使用する係数が 2<sup>-4</sup> = 1/16 であることを意味します。 格納された仮数は、表現できない数値を可能な限り正確に表現しようとするために、最後のビットで切り上げられます。 (1/10 と 1/100 を 2 進数で正確に表現できない理由は、1/3 を 10 進数で正確に表現できない理由と似ています。)

   |[値]|計算式|2 進数表現|16 進数|
   |-|-|-|-|
   |0.1|1.6 * 2<sup>-4</sup>|0011 1101 1100 1100 1100 1100 1100 1101|0x3DCCCCCD|

- 0 は特殊なケースです。 表現可能な正の最小値の式 (すべてゼロ) が使用されます。

   |[値]|計算式|2 進数表現|16 進数|
   |-|-|-|-|
   |0|1 * 2<sup>-128</sup>|0000 0000 0000 0000 0000 0000 0000 0000|0x00000000|

## <a name="see-also"></a>関連項目

[浮動小数点数の精度の低下](why-floating-point-numbers-may-lose-precision.md)
