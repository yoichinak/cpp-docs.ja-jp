---
description: '詳細情報: &lt; アルゴリズム&gt;'
title: '&lt;algorithm&gt;'
ms.date: 11/04/2016
f1_keywords:
- <algorithm>
helpviewer_keywords:
- algorithm header [C++]
- C++ Standard Library, algorithms
- <algorithm> header
ms.assetid: 19f97711-7a67-4a65-8fd1-9a2bd3ca327d
ms.openlocfilehash: 09d998b0afddd8cedda208d2703a615b50cac236
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721135"
---
# `<algorithm>`

アルゴリズムを実行する C++ 標準ライブラリ コンテナーのテンプレート関数を定義します。

## <a name="syntax"></a>構文

```cpp
(see relevant links below for specific algorithm syntax)
```

> [!NOTE]
> ライブラリは、 `<algorithm>` ステートメントも使用し `#include <initializer_list>` ます。

## <a name="remarks"></a>解説

C++ 標準ライブラリ アルゴリズムは、さまざまなデータ構造体を操作できるため汎用的です。 操作できるデータ構造には、`vector` や `list` などの C++ 標準ライブラリ コンテナー クラスだけではなく、特定のアルゴリズムの要件を満たす、プログラムで定義されたデータ構造や要素の配列も含まれます。 C++ 標準ライブラリ アルゴリズムは、反復子によって間接的にコンテナー要素にアクセスし、走査することによって、このレベルの一般性を実現します。

C++ 標準ライブラリ アルゴリズムは、通常、開始位置または終了位置によって指定される反復子範囲を処理します。 参照される範囲は、範囲内のすべてのポインターが逆参照可能であるという意味において有効であり、かつ各範囲のシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

C++ 標準ライブラリ アルゴリズムでは、各 C++ 標準ライブラリ コンテナーの操作およびメンバー関数でサポートされている操作を拡張し、たとえば、異なる型のコンテナー オブジェクトを同時に操作できるようにします。 2 個のサフィックスがアルゴリズムの目的に関する情報を伝えるために使用されています。

- サフィックスは、 `_if` 要素自体ではなく、要素の値を操作する関数オブジェクトと共にアルゴリズムが使用されることを示します。 `find_if` アルゴリズムは、値が関数オブジェクトによって指定されている基準を満たす要素を検索し、`find` アルゴリズムは、特定の値を検索します。

- _copy サフィックスは、アルゴリズムが要素の値を操作するだけではなく、変更された値をターゲット範囲にコピーすることを示します。 `reverse` アルゴリズムは、範囲内の要素の順序を反転し、`reverse_copy` アルゴリズムは、さらに結果をターゲット範囲にコピーします。

C++ 標準ライブラリ アルゴリズムは、通常、その目的や要件に関する事項を示すグループに分類されます。 これには、要素の値を変更する変更アルゴリズムと、要素の値を変更しない非変更アルゴリズムが含まれます。 変換アルゴリズムは、要素の順序を変更しますが、要素の値は変更しません。 削除アルゴリズムは、範囲または範囲のコピーから要素を除去できます。 並べ替えアルゴリズムは、さまざまな方法で範囲内の要素の順序を変更し、並べ替えられた範囲アルゴリズムは、特定の方法で要素が並べ替えられた範囲に対してのみ機能します。

数値処理のために用意されている C++ 標準ライブラリの数値アルゴリズムには独自のヘッダーファイルがあり [`<numeric>`](numeric.md) 、関数オブジェクトとアダプターは、 [`<functional>`](functional.md) ブール値を返すヘッダー関数オブジェクトで述語として知られています。 既定の二項述語は比較 `operator<` です。 通常、順序を並べ替える要素は、小なり比較だけを実行できる必要があります。これにより、2 つの要素が指定されたときに、それらの要素が等しいか (どちらか一方が小さくはない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます。

### <a name="function-templates"></a>関数テンプレート

|名前|Description|
|-|-|
|[`adjacent_find`](algorithm-functions.md#adjacent_find)|等しいか、または指定された条件を満たす 2 個の隣接する要素を検索します。|
|[`all_of`](algorithm-functions.md#all_of)|**`true`** 指定された範囲内の各要素に条件が存在する場合、を返します。|
|[`any_of`](algorithm-functions.md#any_of)|**`true`** 指定された要素の範囲内に条件が1回以上存在する場合に、を返します。|
|[`binary_search`](algorithm-functions.md#binary_search)|並べ替えられた範囲に、指定された値と等しい要素が存在するか、または二項述語で指定された意味で、指定された値と等価の要素が存在するかどうかをテストします。|
|[`clamp`](algorithm-functions.md#clamp)||
|[`copy`](algorithm-functions.md#copy)|要素のソース シーケンス全体を繰り返し、順方向の新しい位置を割り当てて、ソース範囲内からターゲットの範囲に要素の値を割り当てます。|
|[`copy_backward`](algorithm-functions.md#copy_backward)|要素のソース シーケンス全体を繰り返し、逆方向の新しい位置を割り当てて、ソース範囲内からターゲットの範囲に要素の値を割り当てます。|
|[`copy_if`](algorithm-functions.md#copy_if)|指定された条件をテストする特定の範囲のすべての要素をコピーする **`true`**|
|[`copy_n`](algorithm-functions.md#copy_n)|指定された数の要素をコピーします。|
|[`count`](algorithm-functions.md#count)|範囲内で値が指定された値と一致する要素の数を返します。|
|[`count_if`](algorithm-functions.md#count_if)|範囲内で値が指定された条件と一致する要素の数を返します。|
|[`equal`](algorithm-functions.md#equal)|二項述語によって指定された等値または等価について、2 つの範囲を要素ごとに比較します。|
|[`equal_range`](algorithm-functions.md#equal_range)|順序付けられた範囲内で、最初の位置が指定された要素の位置以下で、2 番目の位置が要素の位置を超える位置のペアを検索します。ここで、シーケンス内の位置を確立するために使用される等価または順序付けの意味は、二項述語によって指定できます。|
|[`fill`](algorithm-functions.md#fill)|指定された範囲のすべての要素に同じ新しい値を割り当てます。|
|[`fill_n`](algorithm-functions.md#fill_n)|特定の要素で始まる要素範囲で、指定された数の要素に新しい値を割り当てます。|
|[`find`](algorithm-functions.md#find)|範囲内で指定された値を持つ要素が最初に出現する位置を検索します。|
|[`find_end`](algorithm-functions.md#find_end)|範囲内で指定されたシーケンスと等しい、つまり二項述語で指定された意味で等価である最後のサブシーケンスを検索します。|
|[`find_first_of`](algorithm-functions.md#find_first_of)|対象範囲内で複数の値のうち最初に出現するもの、つまり二項述語で指定された意味で、指定された要素のセットと等価である複数の要素のうち最初に出現するものを検索します。|
|[`find_if`](algorithm-functions.md#find_if)|範囲内で指定された条件を満たす要素が最初に出現する位置を検索します。|
|[`find_if_not`](algorithm-functions.md#find_if_not)|指定された範囲内で条件を満たさない最初の要素を返します。|
|[`for_each`](algorithm-functions.md#for_each)|範囲内で順方向順序で各要素に対して指定された関数を適用し、関数オブジェクトを返します。|
|[`for_each_n`](algorithm-functions.md#for_each_n)||
|[`generate`](algorithm-functions.md#generate)|範囲内の各要素に関数オブジェクトによって生成される値を割り当てます。|
|[`generate_n`](algorithm-functions.md#generate_n)|範囲内の指定された数の要素に関数オブジェクトによって生成される値を割り当て、最後に割り当てられた値を 1 つ超えた位置を返します。|
|[`includes`](algorithm-functions.md#includes)|1 つの並べ替えられた範囲に、別の並べ替えられた範囲内のすべての要素が含まれるかどうかをテストします。要素間の順序または等価の基準は二項述語によって指定できます。|
|[`inplace_merge`](algorithm-functions.md#inplace_merge)|2 つの連続する並べ替えられた範囲の要素を単一の並べ替えられた範囲として連結します。順序の基準は二項述語によって指定できます。|
|[`is_heap`](algorithm-functions.md#is_heap)|**`true`** 指定された範囲の要素がヒープを形成する場合はを返します。|
|[`is_heap_until`](algorithm-functions.md#is_heap_until)|**`true`** 指定された範囲が最後の要素までヒープを形成する場合はを返します。|
|[`is_partitioned`](algorithm-functions.md#is_partitioned)|**`true`** 条件をテストする特定の範囲のすべての要素が、テスト対象の要素の前にある場合は、を返し **`true`** **`false`** ます。|
|[`is_permutation`](algorithm-functions.md#is_permutation)|特定の範囲の要素が有効な順列を形成するかどうかを決定します。|
|[`is_sorted`](algorithm-functions.md#is_sorted)|指定した **`true`** 範囲の要素が並べ替えられた順序である場合はを返します。|
|[`is_sorted_until`](algorithm-functions.md#is_sorted_until)|指定した **`true`** 範囲の要素が並べ替えられた順序である場合はを返します。|
|[`iter_swap`](algorithm-functions.md#iter_swap)|指定された反復子のペアで参照される 2 個の値を交換します。|
|[`lexicographical_compare`](algorithm-functions.md#lexicographical_compare)|2 つのシーケンスを要素ごとに比較して、2 つのうちどちらが小さいかを判断します。|
|[`lower_bound`](algorithm-functions.md#lower_bound)|順序の基準が二項述語で指定できる場合に、順序付けられた範囲内で、指定した値と等価以上の値を持つ最初の要素の位置を検索します。|
|[`make_heap`](algorithm-functions.md#make_heap)|指定された範囲の要素を、最初の要素が最大であるヒープに変換します。並べ替えの基準は二項述語によって指定できます。|
|[`max`](algorithm-functions.md#max)|2 つのオブジェクトを比較し、大きい方のオブジェクトを返します。順序の基準は、二項述語によって指定できます。|
|[`max_element`](algorithm-functions.md#max_element)|並べ替え基準をバイナリ述語で指定できる、指定された範囲内の最大の要素の最初の出現箇所を検索します。|
|[`merge`](algorithm-functions.md#merge)|2 つの並べ替えられたソース範囲のすべての要素を単一の並べ替えられたターゲット範囲として連結します。順序の基準は二項述語によって指定できます。|
|[`min`](algorithm-functions.md#min)|2 つのオブジェクトを比較し、小さい方のオブジェクトを返します。順序の基準は、二項述語によって指定できます。|
|[`min_element`](algorithm-functions.md#min_element)|指定された範囲内の最小の要素の最初の出現箇所を検索します。順序の基準は二項述語によって指定できます。|
|[`minmax`](algorithm-functions.md#minmax)|2 つの入力パラメーターを比較し、それらを昇順のペアとして返します。|
|[`minmax_element`](algorithm-functions.md#minmax_element)|とによって実行される作業を [`min_element`](algorithm-functions.md#min_element) [`max_element`](algorithm-functions.md#max_element) 1 回の呼び出しで実行します。|
|[`mismatch`](algorithm-functions.md#mismatch)|二項述語によって指定された等値または等価について、2 つの範囲を要素ごとに比較し、相違点が発生する最初の位置を検索します。|
|[`<alg> move`](algorithm-functions.md#alg_move)|指定された範囲に関連付けられている要素を移動します。|
|[`move_backward`](algorithm-functions.md#move_backward)|ある反復子の要素を別の反復子に移動します。 移動は、指定した範囲の最後の要素から開始され、その範囲内の先頭の要素で終了します。|
|[`next_permutation`](algorithm-functions.md#next_permutation)|範囲内の要素の順序を変更し、元の順序を辞書式に次に大きい順列 (存在する場合) に置き換えます。next の意味は二項述語によって指定できます。|
|[`none_of`](algorithm-functions.md#none_of)|**`true`** 指定された範囲内の要素間に条件が存在しない場合はを返します。|
|[`nth_element`](algorithm-functions.md#nth_element)|要素の範囲を分割し、その範囲内のシーケンスの *n* 番目の要素を正しく検索します。これにより、その前にあるすべての要素がそれ以下で、シーケンス内の後続のすべての要素がその値以上になります。|
|[`partial_sort`](algorithm-functions.md#partial_sort)|範囲内で指定された数の、より小さい要素を、降順以外の順序、または二項述語で指定された順序の基準に従って配置します。|
|[`partial_sort_copy`](algorithm-functions.md#partial_sort_copy)|ソース範囲からターゲット範囲に要素をコピーします。ソース要素は小なりまたは指定された別の二項述語によって並べ替えられます。|
|[`partition`](algorithm-functions.md#partition)|範囲内の要素を 2 つの分離されたセットに分類し、単項述語を満たす要素が単項述語を満たさない要素よりも前に来るように配置します。|
|[`partition_copy`](algorithm-functions.md#partition_copy)|条件が **`true`** 1 つの宛先にあり、条件が別の変換先になる要素をコピーし **`false`** ます。 要素は指定された範囲に含まれている必要があります。|
|[`partition_point`](algorithm-functions.md#partition_point)|特定の範囲内で条件を満たさない最初の要素を返します。 要素は、条件を満たす要素が条件を満たさない要素の前に来るように並べ替えられます。|
|[`pop_heap`](algorithm-functions.md#pop_heap)|ヒープの先頭と範囲内の最後から 2 番目の位置との間で最大の要素を削除し、残りの要素から新しいヒープを形成します。|
|[`prev_permutation`](algorithm-functions.md#prev_permutation)|範囲内の要素の順序を変更し、元の順序を辞書式に次に大きい順列 (存在する場合) に置き換えます。next の意味は二項述語によって指定できます。|
|[`push_heap`](algorithm-functions.md#push_heap)|範囲の末尾にある要素を、範囲内の以前の要素で構成される既存のヒープに追加します。|
|[`random_shuffle`](algorithm-functions.md#random_shuffle)|範囲内の *N* 個の要素のシーケンスを、ランダムに選択された *N*! 個の可能な配置の 1 つに再配置します。|
|[`remove`](algorithm-functions.md#remove)|特定の範囲から指定された値を除去します。残りの要素の順序に影響を及ぼすことはなく、指定された値を含まない新しい範囲の末尾を返します。|
|[`remove_copy`](algorithm-functions.md#remove_copy)|ソース範囲からターゲット範囲に要素をコピーしますが、指定された値の要素はコピーされません。残りの要素の順序に影響を及ぼすことはなく、新しいターゲット範囲の末尾を返します。|
|[`remove_copy_if`](algorithm-functions.md#remove_copy_if)|ソース範囲からターゲット範囲に要素をコピーしますが、述語を満たす要素はコピーされません。残りの要素の順序に影響を及ぼすことはなく、新しいターゲット範囲の末尾を返します。|
|[`remove_if`](algorithm-functions.md#remove_if)|特定の範囲から述語を満たす要素を除去します。残りの要素の順序に影響を及ぼすことはなく、指定された値を含まない新しい範囲の末尾を返します。|
|[`replace`](algorithm-functions.md#replace)|範囲内の各要素が指定された値に一致するかどうかを調べ、一致する場合は置き換えます。|
|[`replace_copy`](algorithm-functions.md#replace_copy)|ソース範囲内の各要素が指定された値に一致するかどうかを調べ、一致する場合は置き換えて結果を新しいターゲット範囲にコピーします。|
|[`replace_copy_if`](algorithm-functions.md#replace_copy_if)|ソース範囲内の各要素が指定された述語を満たすかどうかを調べ、満たす場合は置き換えて結果を新しいターゲット範囲にコピーします。|
|[`replace_if`](algorithm-functions.md#replace_if)|範囲内の各要素が指定された述語を満たすかどうかを調べ、満たす場合は置き換えます。|
|[`reverse`](algorithm-functions.md#reverse)|範囲内の要素の順序を反転させます。|
|[`reverse_copy`](algorithm-functions.md#reverse_copy)|ソース範囲内の要素の順序を反転し、結果をターゲット範囲にコピーします。|
|[`rotate`](algorithm-functions.md#rotate)|2 つの隣接する範囲の要素を交換します。|
|[`rotate_copy`](algorithm-functions.md#rotate_copy)|ソース範囲内の 2 つの隣接する範囲の要素を交換し、結果をターゲット範囲にコピーします。|
|[`sample`](algorithm-functions.md#sample)||
|[`search`](algorithm-functions.md#search)|要素が特定の要素シーケンス内の要素と等しいか、または要素が二項述語で指定される意味において特定のシーケンス内の要素と等価であるシーケンスが、対象範囲内で最初に出現する位置を検索します。|
|[`search_n`](algorithm-functions.md#search_n)|特定の値を持つか、二項述語によって指定される値と関連する、指定された数の要素で構成される範囲内の最初のサブシーケンスを検索します。|
|[`set_difference`](algorithm-functions.md#set_difference)|1 つの並べ替えられたソース範囲内に属するが、2 番目の並べ替えられたソース範囲には属さないすべての要素を単一の並べ替えられたターゲット範囲として結合します。順序の基準は二項述語によって指定できます。|
|[`set_intersection`](algorithm-functions.md#set_intersection)|両方の並べ替えられたソース範囲に属するすべての要素を単一の並べ替えられたターゲット範囲として結合します。順序の基準は二項述語によって指定できます。|
|[`set_symmetric_difference`](algorithm-functions.md#set_symmetric_difference)|並べ替えられたソース範囲の一方には属するが、両方には属さないすべての要素を単一の並べ替えられたターゲット範囲として結合します。順序の基準は二項述語によって指定できます。|
|[`set_union`](algorithm-functions.md#set_union)|2 つの並べ替えられたソース範囲の少なくとも一方に属するすべての要素を単一の並べ替えられたターゲット範囲として結合します。順序の基準は二項述語によって指定できます。|
|[`sort`](algorithm-functions.md#sort)|指定された範囲の要素を、降順以外の順序、または二項述語で指定された順序の基準に従って配置します。|
|[`shuffle`](algorithm-functions.md#shuffle)|乱数ジェネレーターを使用して、指定の範囲の要素をシャッフル (並べ替え) します。|
|[`sort_heap`](algorithm-functions.md#sort_heap)|ヒープを並べ替えられた範囲に変換します。|
|[`stable_partition`](algorithm-functions.md#stable_partition)|範囲内の要素を 2 つの分離されたセットに分類し、等価要素の相対順序は維持して、単項述語を満たす要素が単項述語を満たさない要素よりも前に来るように配置します。|
|[`stable_sort`](algorithm-functions.md#stable_sort)|指定された範囲の要素を、降順以外の順序、または二項述語で指定された順序の基準に従って、等価要素の相対順序を維持して配置します。|
|[`swap`](algorithm-functions.md#swap)|2 種類のオブジェクトの間で、最初のオブジェクトの内容を 2 番目のオブジェクトに割り当て、2 番目のオブジェクトの内容を最初のオブジェクトに割り当てて、要素の値を交換します。|
|[`swap_ranges`](algorithm-functions.md#swap_ranges)|1 つの範囲の要素を、同じサイズの別の範囲の要素と交換します。|
|[`transform`](algorithm-functions.md#transform)|指定された関数オブジェクトをソース範囲内の各要素、または 2 つのソース範囲内の要素のペアに適用し、関数オブジェクトの戻り値をターゲット範囲にコピーします。|
|[`unique`](algorithm-functions.md#unique)|指定された範囲内の互いに隣接する重複要素を削除します。|
|[`unique_copy`](algorithm-functions.md#unique_copy)|互いに隣接する重複要素を除き、ソース範囲の要素をターゲット範囲にコピーします。|
|[`upper_bound`](algorithm-functions.md#upper_bound)|順序の基準が二項述語で指定できる場合に、順序付けられた範囲内で、指定した値を超える値を持つ最初の要素の位置を検索します。|

## <a name="see-also"></a>関連項目

[ヘッダーファイルのリファレンス](cpp-standard-library-header-files.md)\
[C++ 標準ライブラリのスレッドセーフ](thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリリファレンス](cpp-standard-library-reference.md)
