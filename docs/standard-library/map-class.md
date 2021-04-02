---
title: map クラス
description: C++ 標準テンプレートライブラリ (STL) クラスの API リファレンス `map` 。このクラスは、各要素がデータ値と並べ替えキーのペアであるコレクションのデータを格納および取得するために使用されます。
ms.date: 9/10/2020
f1_keywords:
- map/std::map
- map/std::map::allocator_type
- map/std::map::const_iterator
- map/std::map::const_pointer
- map/std::map::const_reference
- map/std::map::const_reverse_iterator
- map/std::map::difference_type
- map/std::map::iterator
- map/std::map::key_compare
- map/std::map::key_type
- map/std::map::mapped_type
- map/std::map::pointer
- map/std::map::reference
- map/std::map::reverse_iterator
- map/std::map::size_type
- map/std::map::value_type
- map/std::map::at
- map/std::map::begin
- map/std::map::cbegin
- map/std::map::cend
- map/std::map::clear
- map/std::map::count
- map/std::map::contains
- map/std::map::crbegin
- map/std::map::crend
- map/std::map::emplace
- map/std::map::emplace_hint
- map/std::map::empty
- map/std::map::end
- map/std::map::equal_range
- map/std::map::erase
- map/std::map::find
- map/std::map::get_allocator
- map/std::map::insert
- map/std::map::key_comp
- map/std::map::lower_bound
- map/std::map::max_size
- map/std::map::rbegin
- map/std::map::rend
- map/std::map::size
- map/std::map::swap
- map/std::map::upper_bound
- map/std::map::value_comp
helpviewer_keywords:
- std::map [C++]
- std::map [C++], allocator_type
- std::map [C++], const_iterator
- std::map [C++], const_pointer
- std::map [C++], const_reference
- std::map [C++], const_reverse_iterator
- std::map [C++], difference_type
- std::map [C++], iterator
- std::map [C++], key_compare
- std::map [C++], key_type
- std::map [C++], mapped_type
- std::map [C++], pointer
- std::map [C++], reference
- std::map [C++], reverse_iterator
- std::map [C++], size_type
- std::map [C++], value_type
- std::map [C++], at
- std::map [C++], begin
- std::map [C++], cbegin
- std::map [C++], cend
- std::map [C++], clear
- std::map [C++], count
- std::map [C++], contains
- std::map [C++], crbegin
- std::map [C++], crend
- std::map [C++], emplace
- std::map [C++], emplace_hint
- std::map [C++], empty
- std::map [C++], end
- std::map [C++], equal_range
- std::map [C++], erase
- std::map [C++], find
- std::map [C++], get_allocator
- std::map [C++], insert
- std::map [C++], key_comp
- std::map [C++], lower_bound
- std::map [C++], max_size
- std::map [C++], rbegin
- std::map [C++], rend
- std::map [C++], size
- std::map [C++], swap
- std::map [C++], upper_bound
- std::map [C++], value_comp
ms.openlocfilehash: 7d8e4c674e525f1b67f000403791c7ccdb2f9673
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099743"
---
# <a name="map-class"></a>`map` クラス

データ値と並べ替えキーのペアになっている要素が含まれているコレクションに対して、データの格納と取得を実行するために使用します。 キーの値は一意で、データを自動的に並べ替えるために使用されます。

map 内の要素の値は直接変更できます。 キー値は定数であり、変更することはできません。 ただし、要素の値を変更した場合、変更前の要素に関連付けられていたキー値を削除し、変更後の新しい要素に対して新しいキー値を挿入する必要があります。

## <a name="syntax"></a>構文

```cpp
template <class Key,
    class Type,
    class Traits = less<Key>,
    class Allocator=allocator<pair <const Key, Type>>>
class map;
```

### <a name="parameters"></a>パラメーター

*`Key`*\
に格納されるキーのデータ型 `map` 。

*`Type`*\
`map` に格納される要素のデータ型。

*`Traits`*\
2つの要素の値を並べ替えキーとして比較して、内の相対順序を決定できる関数オブジェクトを提供する型 `map` 。 この引数は省略可能であり、既定値は二項述語 `less<Key>` です。

C++ 14 では、型パラメーターを持たない述語を指定することで、異種ルックアップを有効にすることができ `std::less<>` ます。 詳細については、「 [連想コンテナーの異種ルックアップ](../standard-library/stl-containers.md#sequence_containers) 」を参照してください。

*`Allocator`*\
メモリの map の割り当てと解放に関する詳細をカプセル化する、格納されたアロケーター オブジェクトを表す型。 この引数は省略可能であり、既定値は `allocator<pair<const Key, Type> >` です。

## <a name="remarks"></a>解説

C++ 標準ライブラリ map クラスには下記の特徴があります。

- 関連付けられたキー値に基づいて要素の値を効率的に取得する可変サイズのコンテナーです。

- 反転することができます。これは、要素にアクセスするための双方向反復子が用意されているためです。

- 並べ替えが実行されます。これは、指定した比較関数に従いキー値によって要素に順序が設定されるためです。

- 一意のクラスです。 これは、各要素が一意のキーを持つ必要があるためです。

- ペアを保持する連想コンテナーです。これは、要素のデータ値とキー値が分かれているためです。

- クラステンプレート。提供される機能はジェネリックであり、要素またはキーの型とは独立しています。 要素やキーに使用されているデータ型は、クラス テンプレートで比較関数やアロケーターと共にパラメーターとして指定されます。

Map クラスによって提供される反復子は双方向反復子ですが、 [`insert`](#insert) [`map`](#map) クラスおよびクラスメンバー関数には、弱い入力反復子であるテンプレートパラメーターとして使用されるバージョンがあります。この反復子の機能要件は、双方向反復子のクラスによって保証される値よりも少なくなります。 これらの反復子の機能に差異があるのは、反復子の概念が異なっているためです。 反復子の各概念には、反復子独自の一連の要件が含まれています。また、それらの要件を使用するアルゴリズムは、反復子の要件による影響を受けます。 たとえば、一部のオブジェクトを参照するために入力反復子が逆参照される場合があり、また、シーケンス内にある次の反復子に対して逆参照が増加する場合もあります。

コンテナーの種類を選択するときは、アプリケーションで必要となる検索や挿入の種類に基づいてい選択することをお勧めします。 連想コンテナーは、検索、挿入、削除の各操作用に最適化されています。 これらの操作を明示的にサポートするメンバー関数は、コンテナー内の要素の数の対数に比例して、最悪の場合は、最悪の時間に実行されます。 要素を挿入しても反復子の有効性は失われません。また、要素を削除した場合は、削除された要素を具体的に指す反復子だけが無効化されます。

値とキーを関連付ける条件をアプリケーションが満たしている場合、map が最適な連想コンテナーとして機能するように指定してください。 この種類の構造体のモデルとなるのは、一意に発生するキーワードおよび関連する文字列値 (キーワードの定義を指定) が順番に格納されたリストです。 単語に複数の正しい定義がある場合、そのキーは一意ではないため、multimap は選択したコンテナーになります。 また、キーワードのリストだけが格納される場合は、set が適切なコンテナーとなります。 キーワードを複数設定できる場合は、multiset が適切なコンテナーとなります。

マップは、型の格納されている関数オブジェクトを呼び出すことによって、制御する要素を並べ替え [`key_compare`](#key_compare) ます。 この格納されたオブジェクトは比較関数であり、メソッドを呼び出すことによってアクセスされ [`key_comp`](#key_comp) ます。 一般に、指定した2つの要素が比較され、一方が他方より小さいか、等しいかどうかが判断されます。 すべての要素を比較すると、等価でない要素の順序付けられたシーケンスが作成されます。

> [!NOTE]
> 比較関数は、数学上の標準的な意味で厳密弱順序を発生させる二項述語です。 二項述語 f (x, y) は、2つの引数オブジェクト (x および y) と戻り値 (または) を持つ関数オブジェクトです **`true`** **`false`** 。 Set に適用される順序付けは、二項述語が反対称、アンチ対称、および推移的であり、等価性が推移的である (x、y) と f (y、x) の両方がの場合に、2つのオブジェクト x と y が等価になるように定義されている場合、厳密弱順序になり **`false`** ます。 2 つのキーの等値に関する条件が等価性の条件よりも厳しく、優先される場合、順序付けは完全な順序付け (すべての要素が相互の値に基づいて並べ替えられる) となり、一致するそれぞれのキーを識別するのが難しくなります。
>
> C++ 14 で `std::less<>` は、型パラメーターを持たない述語または述語を指定することで、異種ルックアップを有効にすることができ `std::greater<>` ます。 詳細については、「 [連想コンテナーの異種ルックアップ](../standard-library/stl-containers.md#sequence_containers) 」を参照してください。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|名前|説明|
|-|-|
|[`map`](#map)|特定のサイズのリスト、特定の値の要素を持つリスト、特定の `allocator` を持つリストを構築します。または他の map のコピーとしてリストを構築します。|

### <a name="typedefs"></a>Typedefs

|名前|説明|
|-|-|
|[`allocator_type`](#allocator_type)|map オブジェクトの `allocator` クラスの typedef。|
|[`const_iterator`](#const_iterator)|内の要素を読み取ることができる双方向反復子の typedef **`const`** `map` 。|
|[`const_pointer`](#const_pointer)|Map 内の要素へのポインターの typedef **`const`** 。|
|[`const_reference`](#const_reference)|**`const`** 操作の読み取りと実行のために map に格納されている要素への参照の typedef **`const`** 。|
|[`const_reverse_iterator`](#const_reverse_iterator)|内の任意の要素を読み取ることができる双方向反復子を提供する型 **`const`** `map` 。|
|[`difference_type`](#difference_type)|反復子が指す要素の範囲内にある map の要素の数に対する符号付き整数の typedef。|
|[`iterator`](#iterator)|map 内の任意の要素の読み取りまたは変更ができる双方向反復子の typedef。|
|[`key_compare`](#key_compare)|2 つの並べ替えキーを比較して、`map` 内の 2 つの要素の相対順序を決定できる関数オブジェクトの typedef。|
|[`key_type`](#key_type)|map の各要素に格納されている並べ替えキーの typedef。|
|[`mapped_type`](#mapped_type)|map の各要素に格納されているデータの typedef。|
|[`pointer`](#pointer)|Map 内の要素へのポインターの typedef **`const`** 。|
|[`reference`](#reference)|map に格納されている要素への参照の typedef。|
|[`reverse_iterator`](#reverse_iterator)|反転された map 内の 1 つの要素の読み取りまたは変更ができる双方向反復子の typedef。|
|[`size_type`](#size_type)|map 内の要素の数に対する符号なし整数の typedef。|
|[`value_type`](#value_type)|map 内に要素として格納されるオブジェクトの種類の typedef。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[`at`](#at)|指定したキー値を持つ要素を検索します。|
|[`begin`](#begin)|`map` 内の最初の要素を指す反復子を返します。|
|[`cbegin`](#cbegin)|内の最初の要素を指す定数反復子を返し `map` ます。|
|[`cend`](#cend)|定数末尾超え反復子を返します。|
|[`clear`](#clear)|`map` のすべての要素を消去します。|
|[`contains`](#contains)<sup>C++ 20</sup>|内に指定されたキーを持つ要素があるかどうかを確認し `map` ます。|
|[`count`](#count)|パラメーターに指定したキーに一致するキーを持つ、map 内の要素の数を返します。|
|[`crbegin`](#crbegin)|反転された内の最初の要素を指す定数反復子を返し `map` ます。|
|[`crend`](#crend)|反転された内の最後の要素の後の位置を指す定数反復子を返し `map` ます。|
|[`emplace`](#emplace)|インプレースで構築された要素をに挿入 `map` します。|
|[`emplace_hint`](#emplace_hint)|インプレースで構築された要素を、 `map` 配置ヒントと共にに挿入します。|
|[`empty`](#empty)|が空の場合はを返し **`true`** `map` ます。|
|[`end`](#end)|末尾超え反復子を返します。|
|[`equal_range`](#equal_range)|反復子のペアを返します。 ペアに含まれる最初の反復子は、指定したキーよりも大きいキーを持つ、`map` 内の最初の要素を指します。 ペアに含まれる 2 番目の反復子は、指定したキーと等しいかそれよりも大きいキーを持つ、`map` 内の最初の要素を指します。|
|[`erase`](#erase)|指定した位置から map 内の要素または要素範囲を削除します。|
|[`find`](#find)|指定したキーと同じキーを持つ、内の要素の位置を指す反復子を返し `map` ます。|
|[`get_allocator`](#get_allocator)|`allocator` の構築に使用される `map` オブジェクトのコピーを返します。|
|[`insert`](#insert)|指定した位置において、`map` に単一の要素または要素の範囲を挿入します。|
|[`key_comp`](#key_comp)|内のキーの並べ替えに使用される比較オブジェクトのコピーを返し `map` ます。|
|[`lower_bound`](#lower_bound)|`map`指定したキーと等しいかそれより大きいキー値を持つ、内の最初の要素を指す反復子を返します。|
|[`max_size`](#max_size)|`map` の最大長を返します。|
|[`rbegin`](#rbegin)|反転された `map` 内の最初の要素を指す反復子を返します。|
|[`rend`](#rend)|反転された内の最後の要素の後の位置を指す反復子を返し `map` ます。|
|[`size`](#size)|`map` 内の要素数を返します。|
|[`swap`](#swap)|2 つの map の要素を交換します。|
|[`upper_bound`](#upper_bound)|`map`指定したキーよりも大きいキー値を持つ、内の最初の要素を指す反復子を返します。|
|[`value_comp`](#value_comp)|`map` 内の要素の値を並べ替えるために使用される比較オブジェクトのコピーを取得します。|

### <a name="operators"></a>オペレーター

|名前|説明|
|-|-|
|[`operator[]`](#op_at)|map に、指定したキー値を持つ要素を挿入します。|
|[`operator=`](#op_eq)|別の map のコピーで map の要素を置き換えます。|

## <a name="allocator_type"></a><a name="allocator_type"></a> `allocator_type`

map オブジェクトのアロケーター クラスを表す型。

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>例

の使用例については、の例を参照してください [`get_allocator`](#get_allocator) `allocator_type` 。

## <a name="at"></a><a name="at"></a> `at`

指定されたキー値を持つ要素を検索します。

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*`key`*\
検索するキー値。

### <a name="return-value"></a>戻り値

見つかった要素のデータ値への参照。

### <a name="remarks"></a>解説

引数のキー値が見つからない場合、関数はクラスクラスのオブジェクトを[ `out_of_range` スローします。](../standard-library/out-of-range-class.md)

### <a name="example"></a>例

```cpp
// map_at.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

typedef std::map<char, int> Mymap;
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

## <a name="begin"></a><a name="begin"></a> `begin`

`map` 内の最初の要素を指す反復子を返します。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>戻り値

内の最初の要素、 `map` または空のマップの次の位置を指す双方向反復子。

### <a name="example"></a>例

```cpp
// map_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err because the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "The first element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
The first element of m1 is now 1
```

## <a name="cbegin"></a><a name="cbegin"></a> `cbegin`

**`const`** 範囲内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>戻り値

**`const`** 範囲内の最初の要素、または空の範囲の末尾の次の位置 (空の範囲の場合は) を指す双方向反復子 `cbegin() == cend()` 。

### <a name="remarks"></a>解説

の戻り値を使用して、 `cbegin` 範囲内の要素を変更することはできません。

`begin()` メンバー関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常、 [`auto`](../cpp/auto-cpp.md) 次の例に示すように、型推論キーワードと共に使用されます。 この例では、 `Container` **`const`** とをサポートする任意の種類の変更可能な (非) コンテナーである `begin()` と見なし `cbegin()` ます。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>` cend`

**`const`** 範囲内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>戻り値

**`const`** 範囲の末尾の次の位置を指し示す双方向アクセス反復子。

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

## <a name="clear"></a><a name="clear"></a> `clear`

map のすべての要素を消去します。

```cpp
void clear();
```

### <a name="example"></a>例

次の例では、メンバー関数の使用方法を示し `map::clear` ます。

```cpp
// map_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 4));

    i = m1.size();
    cout << "The size of the map is initially "
         << i << "." << endl;

    m1.clear();
    i = m1.size();
    cout << "The size of the map after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the map is initially 2.
The size of the map after clearing is 0.
```

## <a name="const_iterator"></a><a name="const_iterator"></a> `const_iterator`

内の要素を読み取ることができる双方向反復子を提供する型 **`const`** `map` 。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>解説

型を `const_iterator` 使用して要素の値を変更することはできません。

`const_iterator`マップによって定義されるは、のオブジェクトである要素を指し [`value_type`](#value_type) ます。これは、 `pair<constKey, Type>` 最初のメンバーが要素のキーであり、2番目のメンバーが要素に保持されているマップされた datum であることを指します。

`const_iterator` `cIter` Map 内の要素を指すを逆参照するには、演算子を使用し `->` ます。

要素のキーの値にアクセスするには、を使用し `cIter`  ->  **`first`** ます。これは () に相当し \* `cIter` ます。 **`first`**.

要素のマップされた datum の値にアクセスするには、を使用し `cIter`  ->  **`second`** ます。これは () に相当し \* `cIter` ます。 **`second`**.

### <a name="example"></a>例

の使用例については、の例を参照してください [`begin`](#begin) `const_iterator` 。

## <a name="const_pointer"></a><a name="const_pointer"></a> `const_pointer`

Map 内の要素へのポインターを提供する型 **`const`** 。

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>解説

型を `const_pointer` 使用して要素の値を変更することはできません。

ほとんどの場合、 [`iterator`](#iterator) マップオブジェクト内の要素にアクセスするには、を使用する必要があります。

## <a name="const_reference"></a><a name="const_reference"></a> `const_reference`

**`const`** 操作の読み取りと実行のために map に格納されている要素への参照を提供する型 **`const`** 。

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>例

```cpp
// map_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference can't be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> `const_reverse_iterator`

内の任意の要素を読み取ることができる双方向反復子を提供する型 **`const`** `map` 。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>解説

型は `const_reverse_iterator` 要素の値を変更できず、逆方向にマップを反復処理するために使用されます。

`const_reverse_iterator`マップによって定義されるは、のオブジェクトである要素を指し [`value_type`](#value_type) ます。これは、 `pair<const Key, Type>` 最初のメンバーが要素のキーであり、2番目のメンバーが要素に保持されているマップされた datum であることを指します。

hash_map 内の要素を指す `const_reverse_iterator crIter` を逆参照するには、`->` 演算子を使用します。

要素のキーの値にアクセスするには、を使用します。 `crIter`  ->  **`first`** これは ( \* `crIter` ). **`first`** と同じです。

要素のマップされた datum の値にアクセスするには、を使用します。 `crIter`  ->  **`second`** これは ( \* `crIter` ). と同じ **`first`** です。

### <a name="example"></a>例

の [`rend`](#rend) 宣言方法や使用方法の例については、の例を参照してください `const_reverse_iterator` 。

## <a name="count"></a><a name="count"></a> `count`

パラメーター指定したキーに一致するキーを持つ、map 内の要素の数を返します。

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*`key`*\
照合される map の要素のキー値。

### <a name="return-value"></a>戻り値

map に、並べ替えキーがパラメーター キーと一致する要素が含まれている場合は 1。map に、キーが一致する要素が含まれていない場合は 0。

### <a name="remarks"></a>解説

メンバー関数は、次の範囲内の要素 *x* の数を返します。

\[ lower_bound (*キー*)、upper_bound (*キー*))

一意の連想コンテナーである map の場合、これは 0 または 1 です。

### <a name="example"></a>例

次の例では、メンバー関数の使用方法を示し `map::count` ます。

```cpp
// map_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Keys must be unique in map, so duplicates are ignored
    i = m1.count(1);
    cout << "The number of elements in m1 with a sort key of 1 is: "
         << i << "." << endl;

    i = m1.count(2);
    cout << "The number of elements in m1 with a sort key of 2 is: "
         << i << "." << endl;

    i = m1.count(3);
    cout << "The number of elements in m1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in m1 with a sort key of 1 is: 1.
The number of elements in m1 with a sort key of 2 is: 1.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="contains"></a><a name="contains"></a> `contains`

指定したキーを持つ要素が内に存在するかどうかを確認し `map` ます。

```cpp
bool contains(const Key& key) const;
template<class K> bool contains(const K& key) const;
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

`template<class K> bool contains(const K& key) const` が透過的な場合にのみ、オーバーロードの解決に参加 `key_compare` します。 詳細については、「 [連想コンテナーの異種ルックアップ](./stl-containers.md#heterogeneous-lookup-in-associative-containers-c14) 」を参照してください。

### <a name="example"></a>例

```cpp
// Requires /std:c++latest
#include <map>
#include <string>
#include <iostream>
#include <functional>

int main()
{
    std::map<int, bool> m = {{0, true},{1, false}};

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << m.contains(1) << '\n';
    std::cout << m.contains(2) << '\n';

    // call template function
    std::map<std::string, int, std::less<>> m2 = {{"ten", 10}, {"twenty", 20}, {"thirty", 30}};
    std::cout << m2.contains("ten");

    return 0;
}
```

```Output
true
false
true
```

## <a name="crbegin"></a><a name="crbegin"></a> `crbegin`

反転された map 内の最初の要素を指す定数反復子を返します。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>戻り値

反転された内の最初の要素を示す定数逆順双方向反復子。反転されていない [`map`](../standard-library/map-class.md) 内の最後の要素だったものを指す定数 `map` 。

### <a name="remarks"></a>解説

`crbegin` は、と共に使用されるのと同じように、反転されたで使用され `map` [`begin`](#begin) `map` ます。

戻り値がの `crbegin` 場合、 `map` オブジェクトを変更することはできません。

`crbegin` を使用して、`map` 内を後方に向かって反復処理できます。

### <a name="example"></a>例

```cpp
// map_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
```

## <a name="crend"></a><a name="crend"></a> `crend`

反転された map 内の最後の要素の次の位置を指す定数反復子を返します。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>戻り値

反転された内の最後の要素の次の位置 [`map`](../standard-library/map-class.md) (反転されていない内の最初の要素の前の位置) を指す定数逆順双方向反復子 `map` 。

### <a name="remarks"></a>解説

`crend` は、と共に使用されるのと同様に、反転されたマップで使用され [`end`](#end) `map` ます。

戻り値がの `crend` 場合、 `map` オブジェクトを変更することはできません。

`crend` を使用して、逆順反復子が `map` の末尾に達したかどうかをテストできます。

`crend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// map_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
```

## <a name="difference_type"></a><a name="difference_type"></a> `difference_type`

反復子が指す要素の範囲内にある map の要素の数を表すのに使用できる符号付き整数型。

```cpp
typedef allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>解説

`difference_type` は、コンテナーの反復子を減算またはインクリメントするときに返される型です。 通常 `difference_type` は、*[ first,  last)* の範囲内で、反復子 `first` と `last` の間にある要素の数を表すために使用され、`first` が指す要素と、`last` が指す要素の 1 つ前までの範囲の要素を含みます。

`difference_type`は、入力反復子の要件を満たすすべての反復子 (set などの反転可能なコンテナーによってサポートされる双方向反復子のクラスを含む) に対して使用できますが、反復子間の減算は、vector などのランダムアクセスコンテナーによって提供されるランダムアクセス反復子によってのみサポートされます。

### <a name="example"></a>例

```cpp
// map_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 2, 30 ) );

   map <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a map
   map <int, int>::difference_type  df_count = 1;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter)
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the map m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the map m1 is: 4.
```

## <a name="emplace"></a><a name="emplace"></a> `emplace`

インプレースで構築された (コピーまたは移動操作が実行されない) 要素をマップに挿入します。

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>パラメーター

*`args`*\
値が同じ順序付けになる要素がマップにまだ含まれていない場合に、マップに挿入する要素を構築するために転送される引数。

### <a name="return-value"></a>戻り値

[`pair`](../standard-library/pair-structure.md) **`bool`** `true` 挿入が行われた場合、および `false` マップに既に順序に等しい値の要素が含まれている場合は、そのコンポーネントを持つ。 戻り値のペアの反復子コンポーネントは、コンポーネントが true の場合は新しく挿入された要素を指し、 **`bool`** コンポーネントが false の場合は既存の要素を指し **`bool`** ます。

`pair` `pr` の反復子コンポーネントにアクセスするには `pr.first` を使用し、これを逆参照するには `*pr.first` を使用します。 コンポーネントにアクセスするには **`bool`** 、を使用 `pr.second` します。 例については、この記事で後ほど説明するサンプル コードを参照してください。

### <a name="remarks"></a>解説

この関数では、反復子や参照は無効になりません。

Emplacement の実行中に例外がスローされた場合、コンテナーの状態は変更されません。

要素のは [`value_type`](#value_type) ペアであるため、要素の値は順序付けされたペアになり、最初のコンポーネントはキー値と等しく、2番目のコンポーネントは要素のデータ値と同じになります。

### <a name="example"></a>例

```cpp
// map_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    map<int, string> m1;

    auto ret = m1.emplace(10, "ten");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
        cout << "map not modified" << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;

    ret = m1.emplace(10, "one zero");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;
}
```

## <a name="emplace_hint"></a><a name="emplace_hint"></a> `emplace_hint`

インプレースで構築された (コピーまたは移動操作が実行されない) 要素を、配置ヒントと一緒に挿入します。

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>パラメーター

*`args`*\
マップに挿入する要素を構築するために転送される引数。キーが同じ順序付けになる要素がマップにまだ含まれていない場合は、より一般的になります。

*`where`*\
正しい挿入ポイントの検索を開始する場所  (その位置がの直前にある *場合、挿入* は、対数時間ではなく償却定数時間で実行できます)。

### <a name="return-value"></a>戻り値

新しく挿入される要素を指す反復子。

要素が既に存在するために挿入が失敗した場合は、既存の要素への反復子を要素のキーと共に返します。

### <a name="remarks"></a>解説

この関数では、反復子や参照は無効になりません。

Emplacement の実行中に例外がスローされた場合、コンテナーの状態は変更されません。

要素のは [`value_type`](#value_type) ペアであるため、要素の値は順序付けされたペアになり、最初のコンポーネントはキー値と等しく、2番目のコンポーネントは要素のデータ値と同じになります。

### <a name="example"></a>例

```cpp
// map_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: " << endl;

    for (const auto& p : m) {
        cout << "(" << p.first <<  "," << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    map<string, string> m1;

    // Emplace some test data
    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "map starting data: ";
    print(m1);
    cout << endl;

    // Emplace with hint
    // m1.end() should be the "next" element after this emplacement
    m1.emplace_hint(m1.end(), "Doug", "Engineering");

    cout << "map modified, now contains ";
    print(m1);
    cout << endl;
}
```

## <a name="empty"></a><a name="empty"></a> `empty`

map が空かどうかをテストします。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

**`true`** マップが空の場合は。 **`false`** マップが空でない場合はです。

### <a name="example"></a>例

```cpp
// map_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The map m1 is empty." << endl;
   else
      cout << "The map m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The map m2 is empty." << endl;
   else
      cout << "The map m2 is not empty." << endl;
}
```

```Output
The map m1 is not empty.
The map m2 is empty.
```

## <a name="end"></a><a name="end"></a> `end`

末尾超え反復子を返します。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>戻り値

末尾超え反復子。 map が空の場合は、`map::end() == map::begin()`。

### <a name="remarks"></a>解説

`end` は、反復子が map の末尾を越えたかどうかをテストするために使用されます。

`end` によって返された値は逆参照しないでください。

コード例については、「」を参照してください [`map::find`](#find) 。

## <a name="equal_range"></a><a name="equal_range"></a> `equal_range`

キーのとキーのを表す反復子のペアを返し [`lower_bound`](#lower_bound) [`upper_bound`](#upper_bound) ます。

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>パラメーター

*`key`*\
検索対象の map 内の要素の並べ替えキーと比較される引数キー値。

### <a name="return-value"></a>戻り値

`pr`メンバー関数によって返されたペアの最初の反復子にアクセスするには、を使用し `pr` ます。 **最初** に、下限の反復子を逆参照するには、(を使用し \* `pr` ます。 **最初**)。 `pr`メンバー関数によって返されたペアの2番目の反復子にアクセスするには、を使用し `pr` ます。 **次** に、上限の反復子を逆参照するには、(を使用し \* `pr` ます。 **2 番目**)。

### <a name="example"></a>例

```cpp
// map_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef map <int, int, less<int> > IntMap;
   IntMap m1;
   map <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the map m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the map m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The map m1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of map m1 with a key >= 40 is: "
           << p2.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the map m1 is: 20.
The upper bound of the element with a key of 2 in the map m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The map m1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a><a name="erase"></a> `erase`

マップ内の要素または要素の範囲を指定した位置から削除するか、または指定したキーと一致する要素を削除します。

```cpp
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,
    const_iterator Last);

size_type erase(
    const key_type& Key);
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

3 番目のメンバー関数の場合は、マップから削除された要素の数を返します。

### <a name="example"></a>例

```cpp
// map_erase.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions
#include <utility>  // make_pair()

using namespace std;

using mymap = map<int, string>;

void printmap(const mymap& m) {
    for (const auto& elem : m) {
        cout << " [" << elem.first << ", " << elem.second << "]";
    }
    cout << endl << "size() == " << m.size() << endl << endl;
}

int main()
{
    mymap m1;

    // Fill in some data to test with, one at a time
    m1.insert(make_pair(1, "A"));
    m1.insert(make_pair(2, "B"));
    m1.insert(make_pair(3, "C"));
    m1.insert(make_pair(4, "D"));
    m1.insert(make_pair(5, "E"));

    cout << "Starting data of map m1 is:" << endl;
    printmap(m1);
    // The 1st member function removes an element at a given position
    m1.erase(next(m1.begin()));
    cout << "After the 2nd element is deleted, the map m1 is:" << endl;
    printmap(m1);

    // Fill in some data to test with, one at a time, using an initializer list
    mymap m2
    {
        { 10, "Bob" },
        { 11, "Rob" },
        { 12, "Robert" },
        { 13, "Bert" },
        { 14, "Bobby" }
    };

    cout << "Starting data of map m2 is:" << endl;
    printmap(m2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    m2.erase(next(m2.begin()), prev(m2.end()));
    cout << "After the middle elements are deleted, the map m2 is:" << endl;
    printmap(m2);

    mymap m3;

    // Fill in some data to test with, one at a time, using emplace
    m3.emplace(1, "red");
    m3.emplace(2, "yellow");
    m3.emplace(3, "blue");
    m3.emplace(4, "green");
    m3.emplace(5, "orange");
    m3.emplace(6, "purple");
    m3.emplace(7, "pink");

    cout << "Starting data of map m3 is:" << endl;
    printmap(m3);
    // The 3rd member function removes elements with a given Key
    mymap::size_type count = m3.erase(2);
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from m3 is: " << count << "." << endl;
    cout << "After the element with a key of 2 is deleted, the map m3 is:" << endl;
    printmap(m3);
}
```

## <a name="find"></a><a name="find"></a> `find`

指定したキーと等価のキーを持つ、map 内の要素の位置を参照する反復子を返します。

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*`key`*\
検索対象の map 内の要素の並べ替えキーによって照合されるキー値。

### <a name="return-value"></a>戻り値

指定したキーを持つ要素の位置を参照する反復子 `map` `map::end()` 。キーの一致が検出されない場合は、内の最後の要素の次の位置 ()。

### <a name="remarks"></a>解説

このメンバー関数は、 `map` 小なり比較関係に基づいて順序を誘発する二項述語の下で、並べ替えキーが引数キーと等価である内の要素を参照する反復子を返します。

の戻り値がに割り当てられている場合、 `find` `const_iterator` map オブジェクトを変更することはできません。 の戻り値 `find` がに割り当てられている場合 `iterator` 、map オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// compile with: /EHsc /W4 /MTd
#include <map>
#include <iostream>
#include <vector>
#include <string>
#include <utility>  // make_pair()

using namespace std;

template <typename A, typename B> void print_elem(const pair<A, B>& p) {
    cout << "(" << p.first << ", " << p.second << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

template <typename C, class T> void findit(const C& c, T val) {
    cout << "Trying find() on value " << val << endl;
    auto result = c.find(val);
    if (result != c.end()) {
        cout << "Element found: "; print_elem(*result); cout << endl;
    } else {
        cout << "Element not found." << endl;
    }
}

int main()
{
    map<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting map m1 is (key, value):" << endl;
    print_collection(m1);

    vector<pair<int, string>> v;
    v.push_back(make_pair(43, "Tc"));
    v.push_back(make_pair(41, "Nb"));
    v.push_back(make_pair(46, "Pd"));
    v.push_back(make_pair(42, "Mo"));
    v.push_back(make_pair(44, "Ru"));
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate

    cout << "Inserting the following vector data into m1:" << endl;
    print_collection(v);

    m1.insert(v.begin(), v.end());

    cout << "The modified map m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}
```

## <a name="get_allocator"></a><a name="get_allocator"></a> `get_allocator`

map の構築に使用されるアロケーター オブジェクトのコピーを返します。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>戻り値

map で使用されるアロケーター。

### <a name="remarks"></a>解説

map クラスのアロケーターは、クラスがどのようにストレージを管理するかを指定します。 C++ 標準ライブラリ コンテナー クラスで提供される既定のアロケーターは、ほとんどのプログラミング要件に対応しています。 独自のアロケーター クラスを作成して使用することは、C++ における高度な作業の 1 つです。

### <a name="example"></a>例

```cpp
// map_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int>::allocator_type m1_Alloc;
   map <int, int>::allocator_type m2_Alloc;
   map <int, double>::allocator_type m3_Alloc;
   map <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   map <int, int> m1;
   map <int, int, allocator<int> > m2;
   map <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated\n"
        << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated\n"
        << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a map m4
   // with the allocator of map m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( m1_Alloc == m4_Alloc )
   {
      cout << "The allocators are interchangeable." << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable." << endl;
   }
}
```

## <a name="insert"></a><a name="insert"></a> `insert`

map に要素または要素範囲を挿入します。

```cpp
// (1) single element
pair<iterator, bool> insert(
    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(
    ValTy&& Val);

// (3) single element with hint
iterator insert(
    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(
    initializer_list<value_type>
IList);
```

### <a name="parameters"></a>パラメーター

*`Val`*\
キーが同じ順序付けになる要素がマップにまだ含まれていない場合に、map に挿入する要素の値。

*`Where`*\
正しい挿入ポイントの検索を開始する場所  (そのポイントがの直前にある場合 *`Where`* 、挿入は対数時間ではなく償却定数時間で実行できます)。

*`ValTy`*\
Map がの要素を構築するために使用できる引数の型を指定し、 [`value_type`](#value_type) を *`Val`* 引数として完全転送するテンプレートパラメーター。

*`First`*\
コピーされる最初の要素の位置。

*`Last`*\
コピーされる最後の要素の次の位置。

*`InputIterator`*\
オブジェクトの構築に使用できる型の要素を指す [入力反復子](../standard-library/input-iterator-tag-struct.md) の要件を満たすテンプレート関数引数 [`value_type`](#value_type) 。

*`IList`*\
[`initializer_list`](../standard-library/initializer-list.md)要素のコピー元の。

### <a name="return-value"></a>戻り値

単一要素のメンバー関数 (1) と (2) は、挿入が行われた場合はそのコンポーネントが true であるを返し、 [`pair`](../standard-library/pair-structure.md) **`bool`** map に順序の値が同じキーを持つ要素が既に含まれている場合は false を返します。 戻り値のペアの反復子コンポーネントは、コンポーネントが true の場合は新しく挿入された要素を指し、 **`bool`** コンポーネントが false の場合は既存の要素を指し **`bool`** ます。

単一要素とヒントのメンバー関数 (3) と (4) は、map に挿入された新しい要素の位置を指す反復子を返します。ただし、同じキーを持つ要素が既に存在する場合、この反復子は既存の要素を指します。

### <a name="remarks"></a>解説

この関数では、反復子、ポインター、参照は無効になりません。

要素を1つだけ挿入するときに、例外がスローされた場合、コンテナーの状態は変更されません。 複数の要素を挿入するときに例外がスローされた場合、コンテナーの状態は未指定ですが、有効な状態になっています。

単一要素のメンバー関数によって返される `pair` `pr` の反復子コンポーネントにアクセスするには `pr.first` を使用し、返されるペアに含まれる反復子を逆参照するには、`*pr.first` を使用すると要素が与えられます。 コンポーネントにアクセスするには **`bool`** 、を使用 `pr.second` します。 例については、この記事で後ほど説明するサンプル コードを参照してください。

[`value_type`](#value_type)コンテナーのは、コンテナーに属する typedef であり、map の場合、 `map<K, V>::value_type` は `pair<const K, V>` です。 要素の値は順序付けされたペアになり、このペアの最初のコンポーネントはキー値と同じで、2 番目のコンポーネントは要素のデータ値と同じになります。

範囲のメンバー関数 (5) は、map に要素値のシーケンスを挿入します。このシーケンスは、範囲 `[First, Last)` の反復子によってアドレス指定された各要素に対応します。したがって、`Last` は挿入されません。 コンテナーのメンバー関数 `end()` は、コンテナー内にある最後の要素の直後の位置を参照します。たとえば、ステートメント `m.insert(v.begin(), v.end());` は、`v` のすべての要素を `m` に挿入しようとします。 範囲内で一意の値を持つ要素だけが挿入されますが、値が重複する要素は無視されます。 拒否される要素を確認するには、1 つの要素が指定された `insert` を使用します。

初期化子リストのメンバー関数 (6) は、を使用し [`initializer_list`](../standard-library/initializer-list.md) て map に要素をコピーします。

インプレースで構築された要素の挿入 (つまり、コピーまたは移動操作は実行されません) については、「」および「」を参照してください [`map::emplace`](#emplace) [`map::emplace_hint`](#emplace_hint) 。

### <a name="example"></a>例

```cpp
// map_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>
#include <vector>
#include <utility>  // make_pair()

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    map<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    auto ret = m1.insert(make_pair(1, 111));
    if (!ret.second){
        auto pr = *ret.first;
        cout << "Insert failed, element with key value 1 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "The modified key and mapped values of m1 are:" << endl;
        print(m1);
    }
    cout << endl;

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    map<int, int> m2;
    vector<pair<int, int>> v;
    v.push_back(make_pair(43, 294));
    v.push_back(make_pair(41, 262));
    v.push_back(make_pair(45, 330));
    v.push_back(make_pair(42, 277));
    v.push_back(make_pair(44, 311));

    cout << "Inserting the following vector data into m2:" << endl;
    print(v);

    m2.insert(v.begin(), v.end());

    cout << "The modified key and mapped values of m2 are:" << endl;
    print(m2);
    cout << endl;

    // The templatized versions move-constructing elements
    map<int, string>  m3;
    pair<int, string> ip1(475, "blue"), ip2(510, "green");

    // single element
    m3.insert(move(ip1));
    cout << "After the first move insertion, m3 contains:" << endl;
    print(m3);

    // single element with hint
    m3.insert(m3.end(), move(ip2));
    cout << "After the second move insertion, m3 contains:" << endl;
    print(m3);
    cout << endl;

    map<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}
```

## <a name="iterator"></a><a name="iterator"></a> `iterator`

map 内の任意の要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>解説

マップによって定義される反復子は、のオブジェクトである要素を指します。これは、 [`value_type`](#value_type) `pair<const Key, Type>` 最初のメンバーが要素のキーであり、2番目のメンバーが要素に保持されているマップされた datum であることを指します。

Map 内の要素を指す反復子 *Iter* を逆参照するには、演算子を使用し `->` ます。

要素のキーの値にアクセスするに `Iter->first` は、を使用します。これは、と同じ `(*Iter).first` です。 要素のマップされた datum の値にアクセスするに `Iter->second` は、を使用します。これは、と同じ `(*Iter).second` です。

### <a name="example"></a>例

の [`begin`](#begin) 宣言方法や使用方法の例については、「」の例を参照してください `iterator` 。

## <a name="key_comp"></a><a name="key_comp"></a> `key_comp`

map 内のキーの並べ替えに使用する比較オブジェクトのコピーを取得します。

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>戻り値

map が要素の並べ替えに使用する関数オブジェクトを返します。

### <a name="remarks"></a>解説

格納されているオブジェクトは以下のメンバー関数を定義します。

`bool operator(const Key& left, const Key& right);`

**`true`** が `left` 並べ替え順序でに先行する場合と等しくない場合は、を返し `right` ます。

### <a name="example"></a>例

```cpp
// map_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of m1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of m1."
           << endl;
   }

   map <int, int, greater<int> > m2;
   map <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of m2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of m2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.
```

## <a name="key_compare"></a><a name="key_compare"></a> `key_compare`

2 つの並べ替えキーを比較して、`map` 内の 2 つの要素の相対順序を決定できる関数オブジェクトを提供する型。

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>解説

`key_compare` は、テンプレートパラメーターのシノニムです *`Traits`* 。

の詳細については *`Traits`* 、 [ `map` クラス](../standard-library/map-class.md)のトピックを参照してください。

### <a name="example"></a>例

の [`key_comp`](#key_comp) 宣言方法や使用方法の例については、「」の例を参照してください `key_compare` 。

## <a name="key_type"></a><a name="key_type"></a> `key_type`

map の各要素に格納されている並べ替えキーを表す型。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>解説

`key_type` は、テンプレートパラメーターのシノニムです *`Key`* 。

の詳細については *`Key`* 、 [ `map` クラス](../standard-library/map-class.md)のトピックの「**解説**」を参照してください。

### <a name="example"></a>例

の [`value_type`](#value_type) 宣言方法や使用方法の例については、「」の例を参照してください `key_type` 。

## <a name="lower_bound"></a><a name="lower_bound"></a> `lower_bound`

指定したキー以上のキー値を持つ、map 内の最初の要素を指す反復子を返します。

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*`key`*\
検索対象の map 内の要素の並べ替えキーと比較される引数キー値。

### <a name="return-value"></a>戻り値

`iterator` `const_iterator` 引数キー以上のキーを持つ map 内の要素の位置を指すまたは `map` 。キーの一致が検出されない場合は、内の最後の要素の次の位置を指すまたは。

の戻り値がに割り当てられている場合、 `lower_bound` `const_iterator` map オブジェクトを変更することはできません。 の戻り値がに割り当てられている場合は、 `lower_bound` `iterator` map オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// map_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The first element of map m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for this key, end( ) is returned
   m1_RcIter = m1. lower_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of map m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1. lower_bound ( m1_AcIter -> first );
   cout << "The element of m1 with a key matching "
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key of 2 is: 20.
The map m1 doesn't have an element with a key of 4.
The element of m1 with a key matching that of the last element is: 30.
```

## <a name="map"></a><a name="map"></a> `map`

空のマップを構築するか、他のマップの全体または一部のコピーであるマップを構築します。

```cpp
map();

explicit map(
    const Traits& Comp);

map(
    const Traits& Comp,
    const Allocator& Al);

map(
    const map& Right);

map(
    map&& Right);

map(
    initializer_list<value_type> IList);

map(
    initializer_list<value_type> IList,
    const Traits& Comp);

map(
    initializer_list<value_type> IList,
    const Traits& Comp,
    const Allocator& Allocator);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>パラメーター

*`Al`*\
このマップ オブジェクトに使用するストレージ アロケーター クラス。既定では、`Allocator` です。

*`Comp`*\
`const Traits` 内の要素の並べ替えに使用される、`map` 型の比較関数。既定では `hash_compare` です。

*`Right`*\
構築される map のコピー元となる map。

*`First`*\
コピーする要素範囲内の最初の要素の位置。

*`Last`*\
コピーする要素範囲を超える最初の要素の位置。

*`IList`*\
要素のコピー元の initializer_list。

### <a name="remarks"></a>解説

すべてのコンストラクターは、アロケーターオブジェクトの型を格納します。このオブジェクトは、マップのメモリストレージを管理し、後でを呼び出して取得することができ [`get_allocator`](#get_allocator) ます。 代替アロケーターの代わりに使用されるクラス宣言やプリプロセス マクロでは、アロケーターのパラメーターが省略される場合があります。

すべてのコンストラクターは、それぞれのマップを初期化します。

すべてのコンストラクターは、特徴の型の関数オブジェクトを格納します。これは、マップのキーの順序を確立するために使用され、後でを呼び出して返すことができ [`key_comp`](#key_comp) ます。

最初の3つのコンストラクターは、空の初期マップを指定します。2番目のコンストラクターは、要素の順序を確立するために使用する比較関数の型 () を指定し、3番目のコンストラクターは *`Comp`* 使用するアロケーターの型 () を明示的に指定し *`Al`* ます。 キーワードを入力すると、 **`explicit`** 特定の種類の自動型変換が抑制されます。

4番目のコンストラクターは、マップのコピーを指定し *`Right`* ます。

5番目のコンストラクターは、を移動してマップのコピーを指定し *`Right`* ます。

6番目、7番目、および8番目のコンストラクターは、を使用して `initializer_list` メンバーをコピーします。

次の 3 つのコンストラクターは、map の範囲 `[First, Last)` をコピーします。下のコンストラクターになるほど、より明確に `Traits` クラスの比較関数と Allocator の型が指定されています。

### <a name="example"></a>例

```cpp
// map_map.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;
    map <int, int>::iterator m1_Iter, m3_Iter, m4_Iter, m5_Iter, m6_Iter, m7_Iter;
    map <int, int, less<int> >::iterator m2_Iter;

    // Create an empty map m0 of key type integer
    map <int, int> m0;

    // Create an empty map m1 with the key comparison
    // function of less than, then insert 4 elements
    map <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty map m2 with the key comparison
    // function of greater than, then insert 2 elements
    map <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a map m3 with the
    // allocator of map m1
    map <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    map <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, map m4, of map m1
    map <int, int> m4(m1);

    // Create a map m5 by copying the range m1[ first,  last)
    map <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    map <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a map m6 by copying the range m4[ first,  last)
    // and with the allocator of map m2
    map <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    map <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for(auto i : m2)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m3 =";
    for (auto i : m3)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m4 =";
    for (auto i : m4)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m5 =";
    for (auto i : m5)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m6 =";
    for (auto i : m6)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m7 by moving m5
    cout << "m7 =";
    map<int, int> m7(move(m5));
    for (auto i : m7)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m8 by copying in an initializer_list
    map<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m9 with an initializer_list and a comparator
    map<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m10 with an initializer_list, a comparator, and an allocator
    map<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;
}
```

## <a name="mapped_type"></a><a name="mapped_type"></a> `mapped_type`

map に格納されているデータを表す型。

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>解説

この型 `mapped_type` は、クラスの *型* テンプレートパラメーターのシノニムです。

の詳細については *`Type`* 、 [ `map` クラス](../standard-library/map-class.md)のトピックを参照してください。

### <a name="example"></a>例

の [`value_type`](#value_type) 宣言方法や使用方法の例については、「」の例を参照してください `mapped_type` 。

## <a name="max_size"></a><a name="max_size"></a> `max_size`

map の最大長を返します。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

map の可能な最大長。

### <a name="example"></a>例

```cpp
// map_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the map is " << i << "."
        << endl << "(Magnitude is machine specific.)";
}
```

## <a name="operator"></a><a name="op_at"></a> `operator[]`

map に、指定したキー値を持つ要素を挿入します。

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>パラメーター

*`key`*\
挿入する要素のキー値。

### <a name="return-value"></a>戻り値

挿入される要素のデータ値への参照。

### <a name="remarks"></a>解説

引数のキー値が見つからない場合は、データ型の既定値と共に挿入されます。

`operator[]` はを使用して map に要素を挿入するために使用でき `m` `m[key] = DataValue;` `DataValue` `mapped_type` ます。は、キー値がである要素のの値です *`key`* 。

`operator[]` を使用して要素を挿入した場合、返される参照では、挿入によって既存の要素が変更される、または新しい要素が作成されるかどうかは指示されません。 メンバー関数とは、 [`find`](#find) [`insert`](#insert) 挿入前に指定されたキーを持つ要素が既に存在するかどうかを判断するために使用できます。

### <a name="example"></a>例

```cpp
// map_op_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: iterator pIter;

   // Insert a data value of 10 with a key of 1
   // into a map using the operator[] member function
   m1[ 1 ] = 10;

   // Compare other ways to insert objects into a map
   m1.insert ( map <int, int> :: value_type ( 2, 20 ) );
   m1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // If the key already exists, operator[]
   // changes the value of the datum in the element
   m1[ 2 ] = 40;

   // operator[] will also insert the value of the data
   // type's default constructor if the value is unspecified
   m1[5];

   cout  << "The keys of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

// insert by moving key
    map<string, int> c2;
    string str("abc");
    cout << "c2[move(str)] == " << c2[move(str)] << endl;
    cout << "c2["abc"] == " << c2["abc"] << endl;

    return (0);
}
```

```Output
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 30.
The keys of the mapped elements are now: 1 2 3 5.
The values of the mapped elements are now: 10 40 30 0.
c2[move(str)] == 0
c2["abc"] == 1
```

## <a name="operator"></a><a name="op_eq"></a> `operator=`

別の map のコピーで map の要素を置き換えます。

```cpp
map& operator=(const map& right);
map& operator=(map&& right);
```

### <a name="parameters"></a>パラメーター

*`right`*\
[`map`](../standard-library/map-class.md)にコピーされる `map` 。

### <a name="remarks"></a>解説

内の既存の要素を消去した後 `map` 、は `operator=` の内容をマップにコピーまたは移動し *`right`* ます。

### <a name="example"></a>例

```cpp
// map_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   map<int, int> v1, v2, v3;
   map<int, int>::iterator iter;

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

## <a name="pointer"></a><a name="pointer"></a> `pointer`

map 内の要素へのポインターを提供する型。

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>解説

型は、 `pointer` 要素の値を変更するために使用できます。

ほとんどの場合、 [`iterator`](#iterator) マップオブジェクト内の要素にアクセスするには、を使用する必要があります。

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

反転された map 内の最初の要素を指す反復子を返します。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>戻り値

反転された map 内の最初の要素を指す、または反転されていない map 内の最後の要素だったものを指す、逆順双方向反復子。

### <a name="remarks"></a>解説

`rbegin` は、マップで使用されるのと同様に、反転されたマップで使用され [`begin`](#begin) ます。

の戻り値がに割り当てられている場合、 `rbegin` `const_reverse_iterator` map オブジェクトを変更することはできません。 `rbegin` の戻り値が `reverse_iterator` に割り当てられている場合、map オブジェクトを変更できます。

`rbegin` を使用して、map 内を後方に向かって反復処理できます。

### <a name="example"></a>例

```cpp
// map_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the first element in the reversed map is 2.
```

## <a name="reference"></a><a name="reference"></a> `reference`

map に格納されている要素への参照を提供する型。

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>例

```cpp
// map_reference.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference can't be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a><a name="rend"></a> `rend`

反転された map 内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>戻り値

反転された map 内の最後の要素の次の場所 (反転されていない map 内の最初の要素の前の場所) を指す、逆順双方向反復子。

### <a name="remarks"></a>解説

`rend` は、マップで使用されるのと同様に、反転されたマップで使用され [`end`](#end) ます。

の戻り値がに割り当てられている場合、 `rend` `const_reverse_iterator` map オブジェクトを変更することはできません。 `rend` の戻り値が `reverse_iterator` に割り当てられている場合、map オブジェクトを変更できます。

`rend` を使用して、逆順反復子が map の末尾に達したかどうかをテストできます。

`rend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// map_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the last element in the reversed map is 2.
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> `reverse_iterator`

反転された map 内の 1 つの要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>解説

型は `reverse_iterator` 要素の値を変更できず、逆方向にマップを反復処理するために使用されます。

`reverse_iterator`マップによって定義されるは、のオブジェクトである要素を指し [`value_type`](#value_type) ます。これは、 `pair<const Key, Type>` 最初のメンバーが要素のキーであり、2番目のメンバーが要素に保持されているマップされた datum であることを指します。

`reverse_iterator`Map 内の要素を指す *rIter* を逆参照するには、演算子を使用し `->` ます。

要素のキーの値にアクセスするには、first を使用し `rIter`  ->  ます。これは、() に相当し \* `rIter` ます。 **最初** に。 要素のマップされた datum の値にアクセスするには、second を使用し `rIter`  ->  ます。これは () と同じです \* `rIter` 。 **最初** に。

### <a name="example"></a>例

の [`rbegin`](#rbegin) 宣言方法や使用方法の例については、「」の例を参照してください `reverse_iterator` 。

## <a name="size"></a><a name="size"></a> `size`

`map` 内の要素数を返します。

```cpp
size_type size() const;
```

### <a name="return-value"></a>戻り値

map の現在の長さ。

### <a name="example"></a>例

次の例では、メンバー関数の使用方法を示し `map::size` ます。

```cpp
// map_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1, m2;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The map length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The map length is now " << i << "." << endl;
}
```

```Output
The map length is 1.
The map length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> `size_type`

map 内の要素の数を表すことができる符号なし整数型。

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>例

の [`size`](#size) 宣言方法や使用方法の例については、の例を参照してください `size_type` 。

## <a name="swap"></a><a name="swap"></a> フォト

2 つの map の要素を交換します。

```cpp
void swap(
    map<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*`right`*\
ターゲットの map と交換する要素を提供する引数の map。

### <a name="remarks"></a>解説

メンバー関数は、要素を交換する 2 つの map において要素を指定している参照、ポインター、反復子を無効化することはありません。

### <a name="example"></a>例

```cpp
// map_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   map <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   //m2 is said to be the argument map; m1 the target map
   m1.swap( m2 );

   cout << "After swapping with m2, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original map m1 is: 10 20 30.
After swapping with m2, map m1 is: 100 200.
After swapping with m3, map m1 is: 300.
```

## <a name="upper_bound"></a><a name="upper_bound"></a> `upper_bound`

指定したキーよりも大きいキー値を持つ map 内の最初の要素を指す反復子を返します。

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*`key`*\
検索対象の map 内の要素の並べ替えキー値と比較される引数キー値。

### <a name="return-value"></a>戻り値

`iterator` `const_iterator` 引数キーより大きいキーを持つ map 内の要素の位置を指すまたは `map` 。キーの一致が検出されない場合は、内の最後の要素の次の位置を指すまたは。

戻り値がに割り当てられている場合 `const_iterator` 、map オブジェクトを変更することはできません。 戻り値がに割り当てられている場合は、 `iterator` map オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// map_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of map m1 with a key "
        << "greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end is returned
   m1_RcIter = m1. upper_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key greater than 4." << endl;
   else
      cout << "The element of map m1 with a key > 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1. upper_bound ( m1_AcIter -> first );
   cout << "The 1st element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key greater than 2 is: 30.
The map m1 doesn't have an element with a key greater than 4.
The 1st element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="value_comp"></a><a name="value_comp"></a> `value_comp`

このメンバー関数は、キー値の比較によって map の要素の順序を決定する関数オブジェクトを返します。

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>戻り値

map が要素の並べ替えに使用する比較関数オブジェクトを返します。

### <a name="remarks"></a>解説

Map *m* の場合、2つの要素 *e1*(*k1*、 *d1*) と *e2*(*k2*、 *d2*) が型のオブジェクト `value_type` であり、 *k1* と *k1* が型のキーであり、d1 と d2 が型のデータである場合、 `key_type` はと  `mapped_type` `m.value_comp(e1, e2)` 同じに `m.key_comp(k1, k2)` なります。 格納されているオブジェクトは以下のメンバー関数を定義します。

`bool operator( value_type& left, value_type& right);`

は、 **`true`** のキー値が `left` 並べ替え順序においてのキー値と一致しない場合にを返し `right` ます。

### <a name="example"></a>例

```cpp
// map_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   pair< map<int,int>::iterator, bool > pr1, pr2;

   pr1= m1.insert ( map <int, int> :: value_type ( 1, 10 ) );
   pr2= m1.insert ( map <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *pr1.first, *pr2.first ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."
           << endl;
   }

   if(vc1( *pr2.first, *pr1.first ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."
           << endl;
   }
}
```

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="value_type"></a><a name="value_type"></a> `value_type`

map 内に要素として格納されるオブジェクトの種類。

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>例

```cpp
// map_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: key_type key1;
   map <int, int> :: mapped_type mapped1;
   map <int, int> :: value_type value1;
   map <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   m1.insert ( map <int, int> :: value_type ( 1, 10 ) );

   // Compare other ways to insert objects into a map
   m1.insert ( cInt2Int ( 2, 20 ) );
   m1[ 3 ] = 30;

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the map is "
        << key1 << "." << endl;

   cout << "The data value of first element in the map is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type isn't assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

## <a name="see-also"></a>関連項目

[ある](./stl-containers.md)\
[C++ 標準ライブラリのスレッドセーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリリファレンス](../standard-library/cpp-standard-library-reference.md)
