---
title: '&lt;bit&gt;'
description: 個々のビットとビットシーケンスのアクセス、操作、および処理を行う関数。
ms.date: 08/28/2020
f1_keywords:
- <bit>
helpviewer_keywords:
- bit header
ms.openlocfilehash: f9742ce1e15a817923c144544eb3bb6325e76765
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509961"
---
# <a name="ltbitgt"></a>&lt;bit&gt;

個々のビットとビットシーケンスをアクセス、操作、および処理する関数を定義します。

たとえば、ビットを回転させる関数、連続するセットまたはクリアビットの数を検索する関数、数値が2の整数の累乗であるかどうか、数値を表す最小ビット数などがあるかどうかなどがあります。

## <a name="requirements"></a>必要条件

**ヘッダー:**\<bit>

**名前空間:** std

[/std: c + + latest](../build/reference/std-specify-language-standard-version.md) が必要です。

## <a name="members"></a>メンバー

### <a name="types"></a>型

| Type | 説明 |
|--------|----------|
| [ビッグ](bit-enum.md) | スカラー型のエンディアンを指定します。 |

### <a name="functions"></a>関数

| 機能 | 説明 |
|-----|-----|
|[bit_cast](bit-functions.md#bit_cast) | オブジェクト表現を1つの型から別の型に再解釈します。 |
|[bit_ceil](bit-functions.md#bit_ceil) | 値以上の2の最小指数を求めます。 |
|[bit_floor](bit-functions.md#bit_floor) | 値を超えない2の最大の整数乗を求めます。 |
|[bit_width](bit-functions.md#bit_width) | 値を表すために必要な最小ビット数を求めます。 |
|[countl_zero](bit-functions.md#countl_zero) | 最上位ビットから開始して、連続するビットの数を0に設定します。 |
|[countl_one](bit-functions.md#countl_one) | 最上位ビットから順に1に設定される連続ビットの数をカウントします。 |
|[countr_zero](bit-functions.md#countr_zero) | 最下位ビットから開始して、連続するビットの数を0に設定します。 |
|[countr_one](bit-functions.md#countl_one) | 最下位ビットから順に1に設定される連続ビットの数をカウントします。 |
|[has_single_bit](bit-functions.md#has_single_bit) | 値に1ビットだけが設定されているかどうかを確認します。 これは、値が2の累乗であるかどうかをテストすることと同じです。 |
|[popcount](bit-functions.md#popcount) | 1に設定されたビット数をカウントします。 |
|[rotl](bit-functions.md#rotl) | ビットごとの左回転の結果を計算します。 |
|[rotr](bit-functions.md#rotr) | ビットごとの右回転の結果を計算します。 |

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](cpp-standard-library-header-files.md)
