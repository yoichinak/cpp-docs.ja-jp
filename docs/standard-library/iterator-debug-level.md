---
description: '詳細については、次を参照してください: _ITERATOR_DEBUG_LEVEL'
title: _ITERATOR_DEBUG_LEVEL
ms.date: 11/04/2016
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
ms.openlocfilehash: a496bdd18856f2862a1e0d5660cb329cf576e6cc
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721148"
---
# `_ITERATOR_DEBUG_LEVEL`

`_ITERATOR_DEBUG_LEVEL` マクロは、[チェックを行う反復子](../standard-library/checked-iterators.md)および[反復子のデバッグのサポート](../standard-library/debug-iterator-support.md)が有効かどうかを制御します。 このマクロは、以前の `_SECURE_SCL` および `_HAS_ITERATOR_DEBUGGING` マクロを置き換え、組み合わせたものです。

## <a name="macro-values"></a>マクロの値

`_ITERATOR_DEBUG_LEVEL` マクロの有効値を次の表に示します。

|コンパイル モード|マクロの値|Description|
|----------------------|----------------|-----------------|
|**デバッグ**|||
||0|チェックを行う反復子を無効にし、反復子のデバッグを無効にします。|
||1|チェックを行う反復子を有効にし、反復子のデバッグを無効にします。|
||2 (既定値)|反復子のデバッグを有効にします。チェックを行う反復子は関連しません。|
|**リリース**|||
||0 (既定値)|チェックを行う反復子を無効にします。|
||1|チェックを行う反復子を有効にします。反復子のデバッグは関連しません。|

リリース モードでは、`_ITERATOR_DEBUG_LEVEL` に 2 を指定するとコンパイラはエラーを生成します。

## <a name="remarks"></a>解説

`_ITERATOR_DEBUG_LEVEL` マクロは、[チェックを行う反復子](../standard-library/checked-iterators.md)が有効かどうか、およびデバッグ モードで[反復子のデバッグのサポート](../standard-library/debug-iterator-support.md)が有効かどうかを制御します。 `_ITERATOR_DEBUG_LEVEL` が 1 または 2 と定義されている場合、チェックを行う反復子は、コンテナーの境界が上書きされないようにします。 `_ITERATOR_DEBUG_LEVEL` が 0 の場合、反復子はチェックされません。 `_ITERATOR_DEBUG_LEVEL` が 1 と定義されている場合、反復子の安全でない使用によってランタイム エラーが発生し、プログラムが終了します。 `_ITERATOR_DEBUG_LEVEL` が 2 と定義されている場合、反復子の安全でない使用によってアサートが発生し、ランタイム エラー ダイアログによってデバッガーに侵入できます。

`_ITERATOR_DEBUG_LEVEL` マクロでは、`_SECURE_SCL` および `_HAS_ITERATOR_DEBUGGING` マクロと同様の機能がサポートされるため、特定の状況で使用するマクロおよびマクロ値を判断できない場合があります。 混乱を回避するために、`_ITERATOR_DEBUG_LEVEL` マクロのみを使用することをお勧めします。 次の表では、既存のコードの `_SECURE_SCL` および `_HAS_ITERATOR_DEBUGGING` のさまざまな値に使用する `_ITERATOR_DEBUG_LEVEL` マクロの同等の値を示します。

|**`_ITERATOR_DEBUG_LEVEL`** |**`_SECURE_SCL`** |**`_HAS_ITERATOR_DEBUGGING`**|
|---|---|---|
|0 (リリースの既定値)|0 (無効)|0 (無効)|
|1|1 (有効)|0 (無効)|
|2 (デバッグの既定値)|(関連性なし)|1 (デバッグ モードで有効)|

チェックを行う反復子に関する警告を無効にする方法については、「」を参照してください [`_SCL_SECURE_NO_WARNINGS`](../standard-library/scl-secure-no-warnings.md) 。

### <a name="example"></a>例

マクロの値を指定するに `_ITERATOR_DEBUG_LEVEL` は、コンパイラオプションを使用し [`/D`](../build/reference/d-preprocessor-definitions.md) てコマンドラインで定義するか、または `#define` C++ 標準ライブラリヘッダーがソースファイルに含まれる前にを使用します。 たとえば、コマンド ラインで、*sample.cpp* をデバッグ モードでコンパイルし、反復子のデバッグのサポートを使用するには、`_ITERATOR_DEBUG_LEVEL` マクロ定義を指定します。

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

ソース ファイルで、反復子を定義する標準ライブラリ ヘッダーの前にマクロを指定します。

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>関連項目

[チェックを行う反復子](../standard-library/checked-iterators.md)\
[反復子のデバッグのサポート](../standard-library/debug-iterator-support.md)\
[安全なライブラリ: C++ 標準ライブラリ](../standard-library/safe-libraries-cpp-standard-library.md)
