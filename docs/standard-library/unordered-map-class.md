---
title: unordered_map クラス
description: '`unordered_map`要素の可変長シーケンスを制御する、C++ 標準ライブラリコンテナークラスの API リファレンスです。'
ms.date: 9/9/2020
f1_keywords:
- unordered_map/std::unordered_map
- unordered_map/std::unordered_map::allocator_type
- unordered_map/std::unordered_map::const_iterator
- unordered_map/std::unordered_map::const_local_iterator
- unordered_map/std::unordered_map::const_pointer
- unordered_map/std::unordered_map::const_reference
- unordered_map/std::unordered_map::difference_type
- unordered_map/std::unordered_map::hasher
- unordered_map/std::unordered_map::iterator
- unordered_map/std::unordered_map::key_equal
- unordered_map/std::unordered_map::key_type
- unordered_map/std::unordered_map::local_iterator
- unordered_map/std::unordered_map::mapped_type
- unordered_map/std::unordered_map::pointer
- unordered_map/std::unordered_map::reference
- unordered_map/std::unordered_map::size_type
- unordered_map/std::unordered_map::value_type
- unordered_map/std::unordered_map::at
- unordered_map/std::unordered_map::begin
- unordered_map/std::unordered_map::bucket
- unordered_map/std::unordered_map::bucket_count
- unordered_map/std::unordered_map::bucket_size
- unordered_map/std::unordered_map::cbegin
- unordered_map/std::unordered_map::cend
- unordered_map/std::unordered_map::clear
- unordered_map/std::unordered_map::contains
- unordered_map/std::unordered_map::count
- unordered_map/std::unordered_map::emplace
- unordered_map/std::unordered_map::emplace_hint
- unordered_map/std::unordered_map::empty
- unordered_map/std::unordered_map::end
- unordered_map/std::unordered_map::equal_range
- unordered_map/std::unordered_map::erase
- unordered_map/std::unordered_map::find
- unordered_map/std::unordered_map::get_allocator
- unordered_map/std::unordered_map::hash
- unordered_map/std::unordered_map::insert
- unordered_map/std::unordered_map::key_eq
- unordered_map/std::unordered_map::load_factor
- unordered_map/std::unordered_map::max_bucket_count
- unordered_map/std::unordered_map::max_load_factor
- unordered_map/std::unordered_map::max_size
- unordered_map/std::unordered_map::rehash
- unordered_map/std::unordered_map::size
- unordered_map/std::unordered_map::swap
- unordered_map/std::unordered_map::unordered_map
- unordered_map/std::unordered_map::hash_function
helpviewer_keywords:
- std::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::contains
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
- std::unordered_map::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash_function
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
ms.assetid: 7cf7cfa1-16e7-461c-a9b2-3b8d8ec24e0d
ms.openlocfilehash: bb03215fd32159cd45fe5bc8780b77623def5f10
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721577"
---
# <a name="unordered_map-class"></a>`unordered_map` クラス

クラステンプレートは、型の要素の可変長シーケンスを制御するオブジェクトを表し `std::pair<const Key, Ty>` ます。 このシーケンスは、ハッシュ関数によって、"バケット" と呼ばれる一列に並んだサブシーケンスに分割され、弱い順序付けがなされます。 各バケット内では、比較関数によって要素間の大小関係が決定されます。 各要素は、並べ替えキーと値という、2 つのオブジェクトを持ちます。 このシーケンスは、すべてのバケットの長さがおおよそ等しければ、シーケンス内の要素数にかかわらず一定の演算回数 (定数時間) で、任意の要素を検索、挿入、削除できるような方法で表現されます。 最悪のケースは、すべての要素が 1 つのバケットに集められたときです。演算の回数は、シーケンス内の要素数に比例して増えることになります (線形時間)。 要素を挿入しても反復子の有効性は失われません。また、要素を削除した場合は、削除された要素を指す反復子だけが無効化されます。

## <a name="syntax"></a>構文

```cpp
template <class Key,
    class Ty,
    class Hash = std::hash<Key>,
    class Pred = std::equal_to<Key>,
    class Alloc = std::allocator<std::pair<const Key, Ty>>>
class unordered_map;
```

### <a name="parameters"></a>パラメーター

*`Key`*\
キーの型。

*`Ty`*\
マップされた型。

*`Hash`*\
ハッシュ関数のオブジェクト型。

*`Pred`*\
等価比較関数のオブジェクト型。

*`Alloc`*\
アロケーター クラス。

## <a name="members"></a>メンバー

|型の定義|説明|
|-|-|
|[`allocator_type`](#allocator_type)|ストレージを管理するためのアロケーターの型です。|
|[`const_iterator`](#const_iterator)|被制御シーケンスの定数反復子の型です。|
|[`const_local_iterator`](#const_local_iterator)|被制御シーケンスの定数バケット反復子の型です。|
|[`const_pointer`](#const_pointer)|要素への定数ポインターの型です。|
|[`const_reference`](#const_reference)|要素への定数参照の型です。|
|[`difference_type`](#difference_type)|2 つの要素間の距離を表す、符号付きの型です。|
|[`hasher`](#hasher)|ハッシュ関数の型です。|
|[`iterator`](#iterator)|被制御シーケンスの反復子の型です。|
|[`key_equal`](#key_equal)|比較関数の型です。|
|[`key_type`](#key_type)|順序付けキーの型です。|
|[`local_iterator`](#local_iterator)|被制御シーケンスのバケット反復子の型です。|
|[`mapped_type`](#mapped_type)|各キーに関連付けられた、マップされた値の型です。|
|[`pointer`](#pointer)|要素へのポインターの型です。|
|[`reference`](#reference)|要素への参照の型です。|
|[`size_type`](#size_type)|2 つの要素間の距離を表す、符号なしの型です。|
|[`value_type`](#value_type)|要素の型。|

|メンバー関数|Description|
|-|-|
|[`at`](#at)|指定したキーを持つ要素を検索します。|
|[`begin`](#begin)|被制御シーケンスの先頭を指定します。|
|[`bucket`](#bucket)|キー値のバケット番号を取得します。|
|[`bucket_count`](#bucket_count)|バケット数を取得します。|
|[`bucket_size`](#bucket_size)|バケットのサイズを取得します。|
|[`cbegin`](#cbegin)|被制御シーケンスの先頭を指定します。|
|[`cend`](#cend)|被制御シーケンスの末尾を指定します。|
|[`clear`](#clear)|すべての要素を削除します。|
|[`count`](#count)|指定したキーに一致する要素の数を検索します。|
|[`contains`](#contains)<sup>C++ 20</sup>|に指定されたキーを持つ要素があるかどうかを確認し `unordered_map` ます。|
|[`emplace`](#emplace)|構築された要素を適切な場所に追加します。|
|[`emplace_hint`](#emplace_hint)|構築された要素を適切な場所にヒントと一緒に追加します。|
|[`empty`](#empty)|要素が存在しないかどうかをテストします。|
|[`end`](#end)|被制御シーケンスの末尾を指定します。|
|[`equal_range`](#equal_range)|指定したキーに一致する範囲を検索します。|
|[`erase`](#erase)|指定した位置にある要素を削除します。|
|[`find`](#find)|指定したキーに一致する要素を検索します。|
|[`get_allocator`](#get_allocator)|格納されているアロケーター オブジェクトを取得します。|
|[`hash_function`](#hash)|格納されているハッシュ関数オブジェクトを取得します。|
|[`insert`](#insert)|要素を追加します。|
|[`key_eq`](#key_eq)|格納されている比較関数オブジェクトを取得します。|
|[`load_factor`](#load_factor)|バケットごとの平均要素数をカウントします。|
|[`max_bucket_count`](#max_bucket_count)|最大バケット数を取得します。|
|[`max_load_factor`](#max_load_factor)|バケットあたりの最大要素数を取得または設定します。|
|[`max_size`](#max_size)|被制御シーケンスの最大サイズを取得します。|
|[`rehash`](#rehash)|ハッシュ テーブルをリビルドします。|
|[`size`](#size)|要素の数をカウントします。|
|[`swap`](#swap)|2 つのコンテナーのコンテンツを交換します。|
|[`unordered_map`](#unordered_map)|コンテナー オブジェクトを構築します。|

|演算子|Description|
|-|-|
|[`unordered_map::operator[]`](#op_at)|指定したキーを持つ要素を検索または挿入します。|
|[`unordered_map::operator=`](#op_eq)|ハッシュ テーブルをコピーします。|

## <a name="remarks"></a>解説

オブジェクトは、格納されている2つのオブジェクト、型の比較関数オブジェクト、 [`unordered_map::key_equal`](#key_equal) および型のハッシュ関数オブジェクトを呼び出すことによって、制御するシーケンスを並べ替え [`unordered_map::hasher`](#hasher) ます。 メンバー関数を呼び出すことによって最初に格納されたオブジェクトにアクセス [`unordered_map::key_eq`](#key_eq) `()` し、メンバー関数を呼び出すことによって、2番目の格納されるオブジェクトにアクセスし [`unordered_map::hash_function`](#hash) `()` ます。 具体的には、`X` 型のすべての値 `Y` と `Key` について、`key_eq()(X, Y)` が呼び出され、2 つの引数値の大小関係が等しい場合は true が返されます。`hash_function()(keyval)` の呼び出しからは、`size_t` 型の値の分布が生成されます。 クラステンプレート[ `unordered_multimap` クラス](../standard-library/unordered-multimap-class.md)とは異なり、型のオブジェクトは、 `unordered_map` `key_eq()(X, Y)` 被制御シーケンスの任意の2つの要素に対して常に false になります。 キーの重複は許されません。

このオブジェクトには、さらに、適切とされるバケットあたりの最大平均要素数を指定する最大テーブル占有率が格納されます。 要素を挿入すること [`unordered_map::load_factor`](#load_factor) `()` によってが最大の占有率を超える場合、コンテナーはバケット数を増やし、必要に応じてハッシュテーブルを再構築します。

被制御シーケンスにおける要素の実際の順序は、ハッシュ関数、比較関数、挿入の順序、最大テーブル占有率、現在のバケット数などによって異なります。 通常、被制御シーケンス内の要素の順序を予測することはできません。 ただし、被制御シーケンス内で同じ大小関係を持った一連の要素は必ず隣接して存在します。

オブジェクトは、型の格納されているアロケーターオブジェクトを介して制御するシーケンスのストレージを割り当て、解放し [`unordered_map::allocator_type`](#allocator_type) ます。 このようなアロケーターオブジェクトは、型のオブジェクトと同じ外部インターフェイスを持っている必要があり `allocator` ます。 コンテナー オブジェクトを代入しても、格納されているアロケーター オブジェクトはコピーされない点に注意してください。

## <a name="requirements"></a>要件

**ヘッダー:**`<unordered_map>`

**名前空間:** std

## <a name="unordered_mapallocator_type"></a><a name="allocator_type"></a> `unordered_map::allocator_type`

ストレージを管理するためのアロケーターの型です。

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>解説

この型は、テンプレート パラメーター `Alloc` のシノニムです。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_allocator_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="unordered_mapat"></a><a name="at"></a> `unordered_map::at`

指定したキー値を持つ、unordered_map 内の要素を検索します。

```cpp
Ty& at(const Key& key);
const Ty& at(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*`key`*\
検索するキー値。

### <a name="return-value"></a>戻り値

見つかった要素のデータ値への参照。

### <a name="remarks"></a>解説

引数のキー値が見つからない場合、この関数は、 `out_of_range`クラスのオブジェクトをスローします。

### <a name="example"></a>例

```cpp
// unordered_map_at.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // find and show elements
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;

    return (0);
}
```

## <a name="unordered_mapbegin"></a><a name="begin"></a> `unordered_map::begin`

被制御シーケンスまたはバケットの先頭を指定します。

```cpp
iterator begin();
const_iterator begin() const;
local_iterator begin(size_type nbucket);
const_local_iterator begin(size_type nbucket) const;
```

### <a name="parameters"></a>パラメーター

*`nbucket`*\
バケット番号。

### <a name="remarks"></a>解説

最初の 2 つのメンバー関数は、シーケンスの最初の要素 (または空のシーケンスの末尾の次の位置) を示す前方反復子を返します。 最後の2つのメンバー関数は、バケットの最初の要素 *`nbucket`* (または空のバケットの末尾の次の位置) を示す前方反復子を返します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_begin.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect first two items " [c 3] [b 2]"
    Mymap::iterator it2 = c1.begin();
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    ++it2;
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[c, 3] [b, 2]
[a, 1]
```

## <a name="unordered_mapbucket"></a><a name="bucket"></a> `unordered_map::bucket`

キー値のバケット番号を取得します。

```cpp
size_type bucket(const Key& keyval) const;
```

### <a name="parameters"></a>パラメーター

*`keyval`*\
マップするキー値。

### <a name="remarks"></a>解説

このメンバー関数は、キー値に現在対応しているバケット番号を返し *`keyval`* ます。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_bucket.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="unordered_mapbucket_count"></a><a name="bucket_count"></a> `unordered_map::bucket_count`

バケット数を取得します。

```cpp
size_type bucket_count() const;
```

### <a name="remarks"></a>解説

このメンバー関数は、現在のバケット数を返します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_bucket_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3][b, 2][a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_mapbucket_size"></a><a name="bucket_size"></a> `unordered_map::bucket_size`

バケットのサイズを取得します。

```cpp
size_type bucket_size(size_type nbucket) const;
```

### <a name="parameters"></a>パラメーター

*`nbucket`*\
バケット番号。

### <a name="remarks"></a>解説

メンバー関数は、バケット番号のサイズを返し *`nbucket`* ます。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_bucket_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="unordered_mapcbegin"></a><a name="cbegin"></a> `unordered_map::cbegin`

**`const`** 範囲内の最初の要素を指す反復子を返します。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>戻り値

**`const`** 範囲の最初の要素、または空の範囲の末尾の次の位置 (空の範囲の場合は) を指す前方アクセス反復子 `cbegin() == cend()` 。

### <a name="remarks"></a>解説

`cbegin` の戻り値で範囲内の要素を変更することはできません。

`begin()` メンバー関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常、 [`auto`](../cpp/auto-cpp.md) 次の例に示すように、型推論キーワードと共に使用されます。 この例では、 `Container` **`const`** とをサポートする任意の種類の変更可能な (非) コンテナーである `begin()` と見なし `cbegin()` ます。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="unordered_mapcend"></a><a name="cend"></a> `unordered_map::cend`

**`const`** 範囲内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>戻り値

**`const`** 範囲の末尾の次の位置を指し示す前方アクセス反復子。

### <a name="remarks"></a>解説

`cend` は、反復子が範囲の末尾を超えたかどうかをテストするために使用されます。

`end()` メンバー関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常、 [`auto`](../cpp/auto-cpp.md) 次の例に示すように、型推論キーワードと共に使用されます。 この例では、 `Container` **`const`** とをサポートする任意の種類の変更可能な (非) コンテナーである `end()` と見なし `cend()` ます。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();
// i2 is Container<T>::const_iterator
```

`cend` によって返された値は逆参照しないでください。

## <a name="unordered_mapclear"></a><a name="clear"></a> `unordered_map::clear`

すべての要素を削除します。

```cpp
void clear();
```

### <a name="remarks"></a>解説

このメンバー関数はを呼び出し `unordered_map::erase(unordered_map::begin(), unordered_map::end())` [`unordered_map::erase`](#erase) [`unordered_map::begin`](#begin) [`unordered_map::end`](#end) ます。「」、「」、および「」を参照してください。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_clear.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapconst_iterator"></a><a name="const_iterator"></a> `unordered_map::const_iterator`

被制御シーケンスの定数反復子の型です。

```cpp
typedef T1 const_iterator;
```

### <a name="remarks"></a>解説

この型は、被制御シーケンスの定数前方反復子として使用できるオブジェクトを表します。 ここでは、実装定義型 `T1`のシノニムとして記述されています。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_const_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapconst_local_iterator"></a><a name="const_local_iterator"></a> `unordered_map::const_local_iterator`

被制御シーケンスの定数バケット反復子の型です。

```cpp
typedef T5 const_local_iterator;
```

### <a name="remarks"></a>解説

この型は、バケットの定数前方反復子として使用できるオブジェクトを表します。 ここでは、実装定義型 `T5`のシノニムとして記述されています。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_const_local_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[a, 1]
```

## <a name="unordered_mapconst_pointer"></a><a name="const_pointer"></a> `unordered_map::const_pointer`

要素への定数ポインターの型です。

```cpp
typedef Alloc::const_pointer const_pointer;
```

### <a name="remarks"></a>解説

この型は、被制御シーケンスの要素への定数ポインターとして使用できるオブジェクトを表します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_const_pointer.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapconst_reference"></a><a name="const_reference"></a> `unordered_map::const_reference`

要素への定数参照の型です。

```cpp
typedef Alloc::const_reference const_reference;
```

### <a name="remarks"></a>解説

この型は、被制御シーケンスの要素への定数参照として使用できるオブジェクトを表します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_const_reference.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapcontains"></a><a name="contains"></a> `unordered_map::contains`

指定したキーを持つ要素が内に存在するかどうかを確認し `unordered_map` ます。
C++ 20 で導入されました。

```cpp
bool contains(const Key& key) const;
<class K> bool contains(const K& key) const;
```

### <a name="parameters"></a>パラメーター

*`K`*\
キーの型。

*`key`*\
検索する要素のキー値。

### <a name="return-value"></a>戻り値

`true` 要素がコンテナーで見つかった場合は。 `false` それ以外の場合は。

### <a name="remarks"></a>解説

`contains()` は C++ 20 で新しく追加されたものです。 これを使用するには、コンパイラオプションを指定し [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) ます。

`template<class K> bool contains(const K& key) const` が透過的な場合にのみ、オーバーロードの解決に参加 `key_compare` します。

### <a name="example"></a>例

```cpp
// Requires /std:c++latest
#include <unordered_map>
#include <iostream>

int main()
{
    std::unordered_map<int, bool> theUnorderedMap = {{0, false}, {1,true}};

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << theUnorderedMap.contains(1) << '\n';
    std::cout << theUnorderedMap.contains(2) << '\n';

    return 0;
}
```

```Output
true
false
```

## <a name="unordered_mapcount"></a><a name="count"></a> `unordered_map::count`

指定したキーに一致する要素の数を検索します。

```cpp
size_type count(const Key& keyval) const;
```

### <a name="parameters"></a>パラメーター

*`keyval`*\
検索対象のキー値。

### <a name="remarks"></a>解説

このメンバー関数は、で区切られた範囲内の要素の数を返し [`unordered_map::equal_range(keyval)`](#equal_range) ます。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
count('A') == 0
count('b') == 1
count('C') == 0
```

## <a name="unordered_mapdifference_type"></a><a name="difference_type"></a> `unordered_map::difference_type`

2 つの要素間の距離を表す、符号付きの型です。

```cpp
typedef T3 difference_type;
```

### <a name="remarks"></a>解説

符号付き整数型は、被制御シーケンス内にある 2 つの要素のアドレスの違いを表すことのできるオブジェクトを記述します。 ここでは、実装定義型 `T3`のシノニムとして記述されています。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_difference_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // compute positive difference
    Mymap::difference_type diff = 0;
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference
    diff = 0;
    for (Mymap::const_iterator it = c1.end();
        it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
end()-begin() == 3
begin()-end() == -3
```

## <a name="unordered_mapemplace"></a><a name="emplace"></a> `unordered_map::emplace`

インプレースで構築された (コピーまたは移動操作が実行されない) 要素を unordered_map に挿入します。

```cpp
template <class... Args>
pair<iterator, bool>  emplace( Args&&... args);
```

### <a name="parameters"></a>パラメーター

*`args`*\
`unordered_map`値が同じ順序付けになる要素がにまだ含まれていない場合に、に挿入される要素を構築するために転送される引数。

### <a name="return-value"></a>戻り値

`pair` **`bool`** 挿入が行われた場合は true を返し、には `unordered_map` 順序で同じ値のキーを持つ要素が既に含まれており、その反復子コンポーネントによって、新しい要素が挿入されたアドレスまたは要素が既に配置されているアドレスが返されます。

このメンバー関数によって返されたペア `pr` の反復子コンポーネントにアクセスするには `pr.first` を使用し、この反復子を逆参照するには `*(pr.first)` を使用します。 **`bool`** `pr` このメンバー関数によって返されたペアのコンポーネントにアクセスするには、を使用し `pr.second` ます。

### <a name="remarks"></a>解説

この関数では、反復子や参照は無効になりません。

挿入時、例外がスローされたが、コンテナーのハッシュ関数ではエラーが発生しなかった場合、コンテナーは変更されません。 ハッシュ関数で例外がスローされた場合、結果は未定義になります。

コード例については、「」を参照してください [`map::emplace`](../standard-library/map-class.md#emplace) 。

## <a name="unordered_mapemplace_hint"></a><a name="emplace_hint"></a> `unordered_map::emplace_hint`

インプレースで構築された (コピーまたは移動操作が実行されない) 要素を、配置ヒントと一緒に挿入します。

```cpp
template <class... Args>
iterator emplace_hint(const_iterator where, Args&&... args);
```

### <a name="parameters"></a>パラメーター

*`args`*\
挿入される要素が unordered_map にまだ含まれていない場合、一般的には、キーが同じ順序付けになる要素が unordered_map にまだ含まれていない場合に、unordered_map に挿入される要素を構築するために転送される引数。

*`where`*\
正しい挿入ポイントの検索を開始する場所に関するヒント。

### <a name="return-value"></a>戻り値

新しく挿入される要素を指す反復子。

要素が既に存在するために挿入が失敗した場合は、既存の要素を指す反復子を返します。

### <a name="remarks"></a>解説

この関数では、参照は無効になりません。

挿入時、例外がスローされたが、コンテナーのハッシュ関数ではエラーが発生しなかった場合、コンテナーは変更されません。 ハッシュ関数で例外がスローされた場合、結果は未定義になります。

要素のは [`value_type`](../standard-library/map-class.md#value_type) ペアであるため、要素の値は順序付けされたペアになり、最初のコンポーネントはキー値と等しく、2番目のコンポーネントは要素のデータ値と同じになります。

コード例については、「」を参照してください [`map::emplace_hint`](../standard-library/map-class.md#emplace_hint) 。

## <a name="unordered_mapempty"></a><a name="empty"></a> `unordered_map::empty`

要素が存在しないかどうかをテストします。

```cpp
bool empty() const;
```

### <a name="remarks"></a>解説

このメンバー関数は、被制御シーケンスが空の場合に true を返します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_empty.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapend"></a><a name="end"></a> `unordered_map::end`

被制御シーケンスの末尾を指定します。

```cpp
iterator end();
const_iterator end() const;
local_iterator end(size_type nbucket);
const_local_iterator end(size_type nbucket) const;
```

### <a name="parameters"></a>パラメーター

*`nbucket`*\
バケット番号。

### <a name="remarks"></a>解説

最初の 2 つのメンバー関数は、シーケンスの末尾の次を示す前方反復子を返します。 最後の2つのメンバー関数は、バケットの末尾の次の位置を示す前方反復子を返し *`nbucket`* ます。

## <a name="unordered_mapequal_range"></a><a name="equal_range"></a> `unordered_map::equal_range`

指定したキーに一致する範囲を検索します。

```cpp
std::pair<iterator, iterator>  equal_range(const Key& keyval);
std::pair<const_iterator, const_iterator>  equal_range(const Key& keyval) const;
```

### <a name="parameters"></a>パラメーター

*`keyval`*\
検索対象のキー値。

### <a name="remarks"></a>解説

このメンバー関数は、 `X` `[X.first, X.second)` と等価の順序付けを持つ被制御シーケンスの要素だけを区切る反復子のペアを返し *`keyval`* ます。 そのような要素が存在しない場合は、どちらの反復子も `end()`です。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_equal_range.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display results of failed search
    std::pair<Mymap::iterator, Mymap::iterator> pair1 =
        c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    // display results of successful search
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
equal_range('x'):
equal_range('b'): [b, 2]
```

## <a name="unordered_maperase"></a><a name="erase"></a> `unordered_map::erase`

指定した位置から unordered_map 内の要素または要素範囲を削除するか、指定したキーと一致する要素を削除します。

```cpp
iterator erase(const_iterator Where);
iterator erase(const_iterator First, const_iterator Last);
size_type erase(const key_type& Key);
```

### <a name="parameters"></a>パラメーター

*`Where`*\
削除される要素の位置。

*`First`*\
削除される最初の要素の位置。

*`Last`*\
削除される最後の要素の次の位置。

*`Key`*\
削除される要素のキー値。

### <a name="return-value"></a>戻り値

最初の 2 つのメンバー関数の場合は、削除された要素の後の最初の残存要素、またはマップの最後の要素 (このような要素が存在しない場合) を指定する双方向反復子。

3 番目のメンバー関数では、unordered_map から削除された要素の数が返されます。

### <a name="remarks"></a>解説

コード例については、「」を参照してください [`map::erase`](../standard-library/map-class.md#erase) 。

## <a name="unordered_mapfind"></a><a name="find"></a> unordered_map:: find

指定したキーに一致する要素を検索します。

```cpp
const_iterator find(const Key& keyval) const;
```

### <a name="parameters"></a>パラメーター

*`keyval`*\
検索対象のキー値。

### <a name="remarks"></a>解説

このメンバー関数は、を返し [`unordered_map::equal_range(keyval).first`](#equal_range) ます。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_find.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // try to find and fail
    std::cout << "find('A') == "
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed
    Mymap::iterator it = c1.find('b');
    std::cout << "find('b') == "
        << std::boolalpha << (it != c1.end())
        << ": [" << it->first << ", " << it->second << "]" << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
find('A') == false
find('b') == true: [b, 2]
```

## <a name="unordered_mapget_allocator"></a><a name="get_allocator"></a> `unordered_map::get_allocator`

格納されているアロケーター オブジェクトを取得します。

```cpp
Alloc get_allocator() const;
```

### <a name="remarks"></a>解説

このメンバー関数は、格納されているアロケーター オブジェクトを返します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_get_allocator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="unordered_maphash_function"></a><a name="hash"></a> `unordered_map::hash_function`

格納されているハッシュ関数オブジェクトを取得します。

```cpp
Hash hash_function() const;
```

### <a name="remarks"></a>解説

このメンバー関数は、格納されているハッシュ関数オブジェクトを返します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_hash_function.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="unordered_maphasher"></a><a name="hasher"></a> `unordered_map::hasher`

ハッシュ関数の型です。

```cpp
typedef Hash hasher;
```

### <a name="remarks"></a>解説

この型は、テンプレート パラメーター `Hash` のシノニムです。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_hasher.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="unordered_mapinsert"></a><a name="insert"></a> `unordered_map::insert`

unordered_map に要素または要素範囲を挿入します。

```cpp
// (1) single element
pair<iterator, bool> insert(    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(    ValTy&& Val);

// (3) single element with hint
iterator insert(    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(initializer_list<value_type>
IList);
```

### <a name="parameters"></a>パラメーター

*`Val`*\
キーが同じ順序付けになる要素が unordered_map にまだ含まれていない場合に、unordered_map に挿入される要素の値。

*`Where`*\
正しい挿入ポイントの検索を開始する場所 

*`ValTy`*\
Unordered_map がの要素を構築するために使用できる引数の型を指定し、 [`value_type`](../standard-library/map-class.md#value_type) を *`Val`* 引数として完全転送するテンプレートパラメーター。

*`First`*\
コピーされる最初の要素の位置。

*`Last`*\
コピーされる最後の要素の次の位置。

*`InputIterator`*\
オブジェクトの構築に使用できる型の要素を指す [入力反復子](../standard-library/input-iterator-tag-struct.md) の要件を満たすテンプレート関数引数 [`value_type`](../standard-library/map-class.md#value_type) 。

*`IList`*\
[`initializer_list`](../standard-library/initializer-list.md)要素のコピー元の。

### <a name="return-value"></a>戻り値

単一要素のメンバー関数 (1) と (2) は、 [`pair`](../standard-library/pair-structure.md) **`bool`** `true` 値が挿入された場合、および `false` その `unordered_map` キーの順序が同じである要素がに既に含まれている場合に、そのコンポーネントを含むを返します。 戻り値のペアの反復子コンポーネントは、コンポーネントがの場合は新しく挿入された要素を指し、 **`bool`** `true` コンポーネントがの場合は既存の要素を指し **`bool`** `false` ます。

単一要素とヒントのメンバー関数 (3) と (4) は、unordered_map に挿入された新しい要素の位置を指す反復子を返します。ただし、同じキーを持つ要素が既に存在する場合、この反復子は既存の要素を指します。

### <a name="remarks"></a>解説

この関数では、反復子、ポインター、参照は無効になりません。

要素を 1 つだけ挿入するとき、例外がスローされたが、コンテナーのハッシュ関数ではエラーが発生しなかった場合、コンテナーの状態は変更されません。 ハッシュ関数で例外がスローされた場合、結果は未定義になります。 複数の要素を挿入するときに例外がスローされた場合、コンテナーの状態は未指定ですが、有効な状態になっています。

単一要素のメンバー関数によって返される `pair` `pr` の反復子コンポーネントにアクセスするには `pr.first` を使用し、返されるペアに含まれる反復子を逆参照するには、`*pr.first` を使用すると要素が与えられます。 コンポーネントにアクセスするには **`bool`** 、を使用 `pr.second` します。 例については、この記事で後ほど説明するサンプル コードを参照してください。

[`value_type`](../standard-library/map-class.md#value_type)コンテナーのは、コンテナーに属する typedef であり、map の場合、 `map<K, V>::value_type` は `pair<const K, V>` です。 要素の値は順序付けされたペアになり、このペアの最初のコンポーネントはキー値と同じで、2 番目のコンポーネントは要素のデータ値と同じになります。

範囲のメンバー関数 (5) は、unordered_map に要素値のシーケンスを挿入します。このシーケンスは、範囲 `[First, Last)` の反復子によってアドレス指定された各要素に対応します。したがって、`Last` は挿入されません。 コンテナーのメンバー関数 `end()` は、コンテナー内にある最後の要素の直後の位置を参照します。たとえば、ステートメント `m.insert(v.begin(), v.end());` は、`v` のすべての要素を `m` に挿入しようとします。 範囲内で一意の値を持つ要素だけが挿入されますが、値が重複する要素は無視されます。 拒否される要素を確認するには、1 つの要素が指定された `insert` を使用します。

初期化子リストのメンバー関数 (6) は、を使用し [`initializer_list`](../standard-library/initializer-list.md) て unordered_map に要素をコピーします。

インプレースで構築された要素の挿入 (つまり、コピーまたは移動操作は実行されません) については、「」および「」を参照してください [`unordered_map::emplace`](#emplace) [`unordered_map::emplace_hint`](#emplace_hint) 。

コード例については、「」を参照してください [`map::insert`](../standard-library/map-class.md#insert) 。

## <a name="unordered_mapiterator"></a><a name="iterator"></a> `unordered_map::iterator`

被制御シーケンスの反復子の型です。

```cpp
typedef T0 iterator;
```

### <a name="remarks"></a>解説

この型は、被制御シーケンスの前方反復子として使用できるオブジェクトを表します。 ここでは、実装定義型 `T0`のシノニムとして記述されています。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapkey_eq"></a><a name="key_eq"></a> `unordered_map::key_eq`

格納されている比較関数オブジェクトを取得します。

```cpp
Pred key_eq() const;
```

### <a name="remarks"></a>解説

このメンバー関数は、格納されている比較関数オブジェクトを返します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_key_eq.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    Mymap::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
        << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
        << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
    }
```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="unordered_mapkey_equal"></a><a name="key_equal"></a> `unordered_map::key_equal`

比較関数の型です。

```cpp
typedef Pred key_equal;
```

### <a name="remarks"></a>解説

この型は、テンプレート パラメーター `Pred` のシノニムです。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_key_equal.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    Mymap::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
        << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
        << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
    }
```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="unordered_mapkey_type"></a><a name="key_type"></a> `unordered_map::key_type`

順序付けキーの型です。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>解説

この型は、テンプレート パラメーター `Key` のシノニムです。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_key_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapload_factor"></a><a name="load_factor"></a> `unordered_map::load_factor`

バケットごとの平均要素数をカウントします。

```cpp
float load_factor() const;
```

### <a name="remarks"></a>解説

このメンバー関数は `(float)unordered_map::size() / (float)unordered_map::bucket_count()` 、バケットごとの平均要素数を返します。「」および「」を参照してください [`unordered_map::size`](#size) [`unordered_map::bucket_count`](#bucket_count) 。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_load_factor.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_maplocal_iterator"></a><a name="local_iterator"></a> `unordered_map::local_iterator`

バケット反復子の型。

```cpp
typedef T4 local_iterator;
```

### <a name="remarks"></a>解説

この型は、バケットの前方反復子として使用できるオブジェクトを表します。 ここでは、実装定義型 `T4`のシノニムとして記述されています。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_local_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect bucket containing 'a'
    Mymap::local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[a, 1]
```

## <a name="unordered_mapmapped_type"></a><a name="mapped_type"></a> `unordered_map::mapped_type`

各キーに関連付けられた、マップされた値の型です。

```cpp
typedef Ty mapped_type;
```

### <a name="remarks"></a>解説

この型は、テンプレート パラメーター `Ty` のシノニムです。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_mapped_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapmax_bucket_count"></a><a name="max_bucket_count"></a> `unordered_map::max_bucket_count`

最大バケット数を取得します。

```cpp
size_type max_bucket_count() const;
```

### <a name="remarks"></a>解説

このメンバー関数は、現在許可されているバケットの最大数を返します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_max_bucket_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_mapmax_load_factor"></a><a name="max_load_factor"></a> `unordered_map::max_load_factor`

バケットあたりの最大要素数を取得または設定します。

```cpp
float max_load_factor() const;

void max_load_factor(float factor);
```

### <a name="parameters"></a>パラメーター

*`factor`*\
新しい最大テーブル占有率。

### <a name="remarks"></a>解説

1 つ目のメンバー関数は、格納されている最大テーブル占有率を返します。 2番目のメンバー関数は、格納されている最大占有率をに置き換え *`factor`* ます。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_max_load_factor.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_mapmax_size"></a><a name="max_size"></a> `unordered_map::max_size`

被制御シーケンスの最大サイズを取得します。

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>解説

このメンバー関数は、オブジェクトが制御できる最も長いシーケンスの長さを返します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_max_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    std::cout << "max_size() == " << c1.max_size() << std::endl;

    return (0);
    }
```

```Output
max_size() == 536870911
```

## <a name="unordered_mapoperator"></a><a name="op_at"></a> `unordered_map::operator[]`

指定したキーを持つ要素を検索または挿入します。

```cpp
Ty& operator[](const Key& keyval);

Ty& operator[](Key&& keyval);
```

### <a name="parameters"></a>パラメーター

*`Keyval`*\
検索または挿入するキー値。

### <a name="return-value"></a>戻り値

挿入される要素のデータ値への参照。

### <a name="remarks"></a>解説

引数のキー値が見つからない場合は、データ型の既定値と一緒に挿入されます。

`operator[]` はを使用して map に要素を挿入するために使用でき *`m`* *`m[Key] = DataValue;`* *`DataValue`* `mapped_type` ます。は、キー値がである要素のの値です *`Key`* 。

`operator[]` を使用して要素を挿入した場合、返される参照では、挿入によって既存の要素が変更される、または新しい要素が作成されるかどうかは指示されません。 メンバー関数とは、 [`find`](../standard-library/map-class.md#find) [`insert`](../standard-library/map-class.md#insert) 挿入前に指定されたキーを持つ要素が既に存在するかどうかを判断するために使用できます。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_operator_sub.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>
#include <string>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// try to find and fail
    std::cout << "c1['A'] == " << c1['A'] << std::endl;

// try to find and succeed
    std::cout << "c1['a'] == " << c1['a'] << std::endl;

// redisplay contents
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// insert by moving key
    std::unordered_map<string, int> c2;
    std::string str("abc");
    std::cout << "c2[std::move(str)] == " << c2[std::move(str)] << std::endl;
    std::cout << "c2["abc"] == " << c2["abc"] << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
c1['A'] == 0
c1['a'] == 1
[c, 3] [b, 2] [A, 0] [a, 1]
c2[move(str)] == 0
c2["abc"] == 1
```

### <a name="remarks"></a>解説

このメンバー関数は、の戻り値として反復子を決定し `where` `unordered_map::insert(unordered_map::value_type(keyval, Ty())` ます。「」および「」を参照してください [`unordered_map::insert`](#insert) [`unordered_map::value_type`](#value_type) 。 (そのような要素が存在しない場合は、指定されたキーを持つ要素を挿入します。)次に、への参照を返し `(*where).second` ます。

## <a name="unordered_mapoperator"></a><a name="op_eq"></a> `unordered_map::operator=`

別の unordered_map の要素を使用してこの unordered_map の要素を置き換えます。

```cpp
unordered_map& operator=(const unordered_map& right);

unordered_map& operator=(unordered_map&& right);
```

### <a name="parameters"></a>パラメーター

*`right`*\
演算子関数がそこからコンテンツを割り当てる unordered_map。

### <a name="remarks"></a>解説

最初のバージョンは、からすべての要素 *`right`* をこの unordered_map にコピーします。

2番目のバージョンは、からすべての要素 *`right`* をこの unordered_map に移動します。

この unordered_map 実行前に実行されていた要素 `operator=` はすべて破棄されます。

### <a name="example"></a>例

```cpp
// unordered_map_operator_as.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

int main( )
   {
   using namespace std;
   unordered_map<int, int> v1, v2, v3;
   unordered_map<int, int>::iterator iter;

   v1.insert(pair<int, int>(1, 10));

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;
   }
```

## <a name="unordered_mappointer"></a><a name="pointer"></a> `unordered_map::pointer`

要素へのポインターの型です。

```cpp
typedef Alloc::pointer pointer;
```

### <a name="remarks"></a>解説

この型は、被制御シーケンスの要素へのポインターとして機能するオブジェクトを表します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_pointer.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Mymap::pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
        }
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapreference"></a><a name="reference"></a> `unordered_map::reference`

要素への参照の型です。

```cpp
typedef Alloc::reference reference;
```

### <a name="remarks"></a>解説

この型は、被制御シーケンスの要素への参照として使用できるオブジェクトを表します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_reference.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Mymap::reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
        }
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_maprehash"></a><a name="rehash"></a> `unordered_map::rehash`

ハッシュ テーブルをリビルドします。

```cpp
void rehash(size_type nbuckets);
```

### <a name="parameters"></a>パラメーター

*`nbuckets`*\
要求されたバケット数。

### <a name="remarks"></a>解説

このメンバー関数は、バケット数を以上に変更し、必要に応じ *`nbuckets`* てハッシュテーブルを再構築します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_rehash.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_load_factor() == 0.1
```

## <a name="unordered_mapsize"></a><a name="size"></a> `unordered_map::size`

要素の数をカウントします。

```cpp
size_type size() const;
```

### <a name="remarks"></a>解説

このメンバー関数は、被制御シーケンスの長さを返します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

// display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapsize_type"></a><a name="size_type"></a> `unordered_map::size_type`

2 つの要素間の距離を表す、符号なしの型です。

```cpp
typedef T2 size_type;
```

### <a name="remarks"></a>解説

符号なし整数型は、被制御シーケンスの長さを表すことができるオブジェクトを表します。 ここでは、実装定義型 `T2`のシノニムとして記述されています。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_size_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::size_type sz = c1.size();

    std::cout << "size == " << sz << std::endl;

    return (0);
    }
```

```Output
size == 0
```

## <a name="unordered_mapswap"></a><a name="swap"></a> `unordered_map::swap`

2 つのコンテナーのコンテンツを交換します。

```cpp
void swap(unordered_map& right);
```

### <a name="parameters"></a>パラメーター

*`right`*\
交換先のコンテナー。

### <a name="remarks"></a>解説

このメンバー関数は、との間で被制御シーケンスを交換し **`*this`** *`right`* ます。 が `unordered_map::get_allocator() == right.get_allocator()` 一定の [`unordered_map::get_allocator`](#get_allocator) 時間内に実行される場合は、型の格納された特性オブジェクトをコピーした結果としてのみ例外をスロー `Tr` し、2つの被制御シーケンス内の要素を指定する参照、ポインター、または反復子を無効にします。 それ以外の場合、2 つの被制御シーケンス内の要素数に比例した回数、要素の割り当てとコンストラクター呼び出しが実行されます。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_swap.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    Mymap c2;

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    c1.swap(c2);

// display contents " [f 6] [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    swap(c1, c2);

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[f, 6] [e, 5] [d, 4]
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapunordered_map"></a><a name="unordered_map"></a> `unordered_map::unordered_map`

コンテナー オブジェクトを構築します。

```cpp
unordered_map(const unordered_map& Right);

explicit unordered_map(
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Allocator());

unordered_map(unordered_map&& Right);
unordered_map(initializer_list<Type> IList);
unordered_map(initializer_list<Type> IList, size_type Bucket_count);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    KeyEqual& equal);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    KeyEqual& Equal
    const Allocator& Al);

template <class InIt>
unordered_map(
    InputIterator First,
    InputIterator Last,
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());
```

### <a name="parameters"></a>パラメーター

*`Al`*\
格納するアロケーター オブジェクト。

*`Comp`*\
格納する比較関数オブジェクト。

*`Hash`*\
格納するハッシュ関数オブジェクト。

*`Bucket_count`*\
最小バケット数。

*`Right`*\
コピーするコンテナー。

*`First`*\
コピーされる最初の要素の位置。

*`Last`*\
コピーされる最後の要素の次の位置。

*`IList`*\
コピーされる要素を含む initializer_list。

### <a name="remarks"></a>解説

1 つ目のコンストラクターは、`right` によって制御されるシーケンスのコピーを指定します。 2 つ目のコンストラクターは、空の被制御シーケンスのコピーを指定します。 3 つ目のコンストラクターは、要素値 `[first, last)` のシーケンスを挿入します。 4 つ目のコンストラクターは、`right` を移動することによって、シーケンスのコピーを指定します。

さらに、格納された複数の値を初期化する処理が実行されます。この処理は、すべてのコンストラクターに共通です。 コピーコンストラクターでは、値はから取得され *`Right`* ます。 それ以外の場合:

バケットの最小数は引数 (存在する場合) です。 *`Bucket_count`* それ以外の場合は、実装定義の値としてここで説明されている既定値になり `N0` ます。

ハッシュ関数オブジェクトは引数 *`Hash`* (存在する場合)、それ以外の場合はです `Hash()` 。

比較関数オブジェクトは引数 (存在する場合) です。 *`Comp`* それ以外の場合は、になり `Pred()` ます。

アロケーターオブジェクトは引数 (存在する場合) です。 *`Al`* それ以外の場合は、になり `Alloc()` ます。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_construct.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>
#include <initializer_list>

using namespace std;

using Mymap = unordered_map<char, int>;

int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c2(8,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >());

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    // display contents " [f 6] [e 5] [d 4]"
    for (const auto& c : c2) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c3(c1.begin(),
        c1.end(),
        8,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >());

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c3) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c4(move(c3));

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c4) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
    cout << endl;

    // Construct with an initializer_list
    unordered_map<int, char> c5({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } });
    for (const auto& c : c5) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size
    unordered_map<int, char> c6({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } }, 4);
    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
    cout << endl;

    // Initializer_list plus size and hash
    unordered_map<int, char, hash<char>> c7(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size, hash, and key_equal
    unordered_map<int, char, hash<char>, equal_to<char>> c8(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>(),
        equal_to<char>()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size, hash, key_equal, and allocator
    unordered_map<int, char, hash<char>, equal_to<char>> c9(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
}
```

```Output
[a, 1] [b, 2] [c, 3]
[d, 4] [e, 5] [f, 6]
[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]

[5, g] [6, h] [7, i] [8, j]
[a, 1] [b, 2] [c, 3]

[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]
```

## <a name="unordered_mapvalue_type"></a><a name="value_type"></a> `unordered_map::value_type`

要素の型。

```cpp
typedef std::pair<const Key, Ty> value_type;
```

### <a name="remarks"></a>解説

この型は、被制御シーケンス内の要素を示します。

### <a name="example"></a>例

```cpp
// std__unordered_map__unordered_map_value_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="see-also"></a>関連項目

[`<unordered_map>`](../standard-library/unordered-map.md)\
[C++ 標準ライブラリのスレッドセーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
