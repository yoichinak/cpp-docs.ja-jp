---
description: '詳細情報: Concurrency:: graphics 名前空間'
title: Concurrency::graphics 名前空間
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: f4ab25a6bc6e7bfd318ea58bb6a7efe403c51a89
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132835"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics 名前空間

graphics 名前空間は、グラフィックス プログラミング用に設計された型と関数を提供します。

## <a name="syntax"></a>構文

```cpp
namespace graphics;
```

## <a name="members"></a>メンバー

### <a name="namespaces"></a>名前空間

|名前|説明|
|----------|-----------------|
|[Concurrency:: graphics::d irect3d 名前空間](concurrency-graphics-direct3d-namespace.md)|Direct3D の相互運用のための関数を提供します。|

### <a name="typedefs"></a>Typedefs

|名前|説明|
|----------|-----------------|
|`uint`|[Uint_2 クラス](uint-2-class.md)、 [uint_3 クラス](uint-3-class.md)、および[uint_4 クラス](uint-4-class.md)の要素型。 `typedef unsigned int uint;` として定義されている。|

### <a name="enumerations"></a>列挙型

|名前|説明|
|----------|-----------------|
|[Address_mode 列挙体](concurrency-graphics-namespace-enums.md#address_mode)。|テクスチャ サンプリングでサポートされているアドレス モードを指定します。|
|[filter_mode 列挙型](concurrency-graphics-namespace-enums.md#filter_mode)|テクスチャ サンプリングでサポートされているフィルター モードを指定します。|

### <a name="classes"></a>クラス

|名前|説明|
|----------|-----------------|
|[テクスチャクラス](texture-class.md)|テクスチャは範囲ドメイン内の accelerator_view についてのデータ集合体です。 これは、範囲ドメインの各要素に対して 1 つずつの変数のコレクションです。 各変数は、対応する C++ のプリミティブ型 (unsigned int、int、float、double)、またはスカラー型の norm、または unorm (concurrency::graphics で定義)、または concurrency::graphics で定義されている有効な short ベクター型の値を保持します。|
|[writeonly_texture_view クラス](writeonly-texture-view-class.md)|writeonly_texture_view はテクスチャへの writeonly アクセスを提供します。|
|[double_2 クラス](double-2-class.md)|2つの値の short ベクターを表し **`double`** ます。|
|[double_3 クラス](double-3-class.md)|3つの値の short ベクターを表し **`double`** ます。|
|[double_4 クラス](double-4-class.md)|4つの値の short ベクターを表し **`double`** ます。|
|[float_2 クラス](float-2-class.md)|2つの値の short ベクターを表し **`float`** ます。|
|[float_3 クラス](float-3-class.md)|3つの値の short ベクターを表し **`float`** ます。|
|[float_4 クラス](float-4-class.md)|4つの値の short ベクターを表し **`float`** ます。|
|[int_2 クラス](int-2-class.md)|2つの値の short ベクターを表し **`int`** ます。|
|[int_3 クラス](int-3-class.md)|3つの値の short ベクターを表し **`int`** ます。|
|[int_4 クラス](int-4-class.md)|4つの値の short ベクターを表し **`int`** ます。|
|[norm_2 クラス](norm-2-class.md)|2 個の `norm` 値の short ベクターを表します。|
|[norm_3 クラス](norm-3-class.md)|3つの値の short ベクターを表し `norm` ます。|
|[norm_4 クラス](norm-4-class.md)|4つの値の short ベクターを表し `norm` ます。|
|[uint_2 クラス](uint-2-class.md)|2 個の `uint` 値の short ベクターを表します。|
|[uint_3 クラス](uint-3-class.md)|3つの値の short ベクターを表し `uint` ます。|
|[uint_4 クラス](uint-4-class.md)|4つの値の short ベクターを表し `uint` ます。|
|[unorm_2 クラス](unorm-2-class.md)|2 個の `unorm` 値の short ベクターを表します。|
|[unorm_3 クラス](unorm-3-class.md)|3つの値の short ベクターを表し `unorm` ます。|
|[unorm_4 クラス](unorm-4-class.md)|4つの値の short ベクターを表し `unorm` ます。|
|[サンプラークラス](sampler-class.md)|テクスチャ サンプリングに使用するサンプラー構成を表します。|
|[short_vector 構造体](short-vector-structure.md)|値の short ベクターの基本実装を提供します。|
|[short_vector_traits 構造体](short-vector-traits-structure.md)|short ベクターの長さと型の取得を提供します。|
|[texture_view クラス](texture-view-class.md)|テクスチャへの読み取りアクセスおよび書き込みアクセスを提供します。|

### <a name="functions"></a>関数

|名前|説明|
|----------|-----------------|
|[copy](concurrency-graphics-namespace-functions.md#copy)|オーバーロードされます。 ソース テクスチャの内容をターゲット ホスト バッファーにコピーします。|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|オーバーロードされます。 ソース テクスチャの内容をターゲット ホスト バッファーに非同期にコピーします。|

## <a name="requirements"></a>要件

**ヘッダー:** amp_graphics

**名前空間:** Concurrency

## <a name="see-also"></a>関連項目

[Concurrency 名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
