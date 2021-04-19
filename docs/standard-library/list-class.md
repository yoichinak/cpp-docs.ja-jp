---
description: '詳細情報: list クラス'
title: list クラス
ms.date: 11/04/2016
f1_keywords:
- list/std::list
- list/std::list::allocator_type
- list/std::list::const_iterator
- list/std::list::const_pointer
- list/std::list::const_reference
- list/std::list::const_reverse_iterator
- list/std::list::difference_type
- list/std::list::iterator
- list/std::list::pointer
- list/std::list::reference
- list/std::list::reverse_iterator
- list/std::list::size_type
- list/std::list::value_type
- list/std::list::assign
- list/std::list::back
- list/std::list::begin
- list/std::list::cbegin
- list/std::list::cend
- list/std::list::clear
- list/std::list::crbegin
- list/std::list::crend
- list/std::list::emplace
- list/std::list::emplace_back
- list/std::list::emplace_front
- list/std::list::empty
- list/std::list::end
- list/std::list::erase
- list/std::list::front
- list/std::list::get_allocator
- list/std::list::insert
- list/std::list::max_size
- list/std::list::merge
- list/std::list::pop_back
- list/std::list::pop_front
- list/std::list::push_back
- list/std::list::push_front
- list/std::list::rbegin
- list/std::list::remove
- list/std::list::remove_if
- list/std::list::rend
- list/std::list::resize
- list/std::list::reverse
- list/std::list::size
- list/std::list::sort
- list/std::list::splice
- list/std::list::swap
- list/std::list::unique
helpviewer_keywords:
- std::list [C++]
- std::list [C++], allocator_type
- std::list [C++], const_iterator
- std::list [C++], const_pointer
- std::list [C++], const_reference
- std::list [C++], const_reverse_iterator
- std::list [C++], difference_type
- std::list [C++], iterator
- std::list [C++], pointer
- std::list [C++], reference
- std::list [C++], reverse_iterator
- std::list [C++], size_type
- std::list [C++], value_type
- std::list [C++], assign
- std::list [C++], back
- std::list [C++], begin
- std::list [C++], cbegin
- std::list [C++], cend
- std::list [C++], clear
- std::list [C++], crbegin
- std::list [C++], crend
- std::list [C++], emplace
- std::list [C++], emplace_back
- std::list [C++], emplace_front
- std::list [C++], empty
- std::list [C++], end
- std::list [C++], erase
- std::list [C++], front
- std::list [C++], get_allocator
- std::list [C++], insert
- std::list [C++], max_size
- std::list [C++], merge
- std::list [C++], pop_back
- std::list [C++], pop_front
- std::list [C++], push_back
- std::list [C++], push_front
- std::list [C++], rbegin
- std::list [C++], remove
- std::list [C++], remove_if
- std::list [C++], rend
- std::list [C++], resize
- std::list [C++], reverse
- std::list [C++], size
- std::list [C++], sort
- std::list [C++], splice
- std::list [C++], swap
- std::list [C++], unique
ms.assetid: d3707f4a-10fd-444f-b856-f9ca2077c1cd
ms.openlocfilehash: 67334c6e1e2c596c973aa7290c4ea3007de37923
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721434"
---
# <a name="list-class"></a>`list` クラス

C++ 標準ライブラリリストクラスは、シーケンスコンテナーのクラステンプレートで、シーケンス内の任意の場所での要素の直線的な配置を維持し、挿入と削除を効率的に行うことができます。 シーケンスは、要素の双方向リンクリストとして格納されます。各要素には、何らかの型のメンバーが含まれ *`Type`* ます。

## <a name="syntax"></a>構文

```cpp
template <class Type, class Allocator= allocator<Type>>
class list
```

### <a name="parameters"></a>パラメーター

*`Type`*\
list に格納される要素のデータ型。

*`Allocator`*\
メモリの list の割り当てと解放に関する詳細をカプセル化する、格納されたアロケーター オブジェクトを表す型。 この引数は省略可能であり、既定値は `allocator<Type>` です。

## <a name="remarks"></a>解説

一般的に、コンテナー型の選択は、アプリケーションにおいて必要な検索および挿入の種類に基づいている必要があります。 ベクターは、任意の要素へのランダム アクセスが優先事項であり、要素の挿入または削除がシーケンスの最後にのみ必要な場合に、シーケンスを管理するための推奨されるコンテナーです。 クラスの deque コンテナーでは、ランダム アクセスが必要であり、シーケンスの先頭と末尾の両方における挿入と削除が優先事項である場合に、より優れたパフォーマンスになります。

リストメンバー関数 [`merge`](#merge) 、、 [`reverse`](#reverse) [`unique`](#unique) 、、およびは、 [`remove`](#remove) [`remove_if`](#remove_if) リストオブジェクトの操作に対して最適化されており、対応する汎用的な関数に代わる高パフォーマンスを提供します。

リストの再割り当ては、メンバー関数がリストの要素を挿入または消去する必要がある場合に発生します。 このような場合、制御対象シーケンスの消去部分を指す反復子または参照は常に無効になります。

C++ 標準ライブラリの標準ヘッダーをインクルードして、 `<list>` [`container`](../standard-library/stl-containers.md) クラステンプレートリストといくつかのサポートテンプレートを定義します。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|名前|Description|
|-|-|
|[`list`](#list)|特定のサイズのリスト、特定の値の要素を持つリスト、特定の `allocator` を持つリストを構築します。または他のリストのコピーとしてリストを構築します。|

### <a name="typedefs"></a>Typedefs

|名前|Description|
|-|-|
|[`allocator_type`](#allocator_type)|リスト オブジェクトの `allocator` クラスを表す型。|
|[`const_iterator`](#const_iterator)|リスト内の要素を読み取ることができる双方向反復子を提供する型 **`const`** 。|
|[`const_pointer`](#const_pointer)|リスト内の要素へのポインターを提供する型 **`const`** 。|
|[`const_reference`](#const_reference)|**`const`** 読み取りと操作の実行のためにリストに格納されている要素への参照を提供する型 **`const`** 。|
|[`const_reverse_iterator`](#const_reverse_iterator)|リスト内の任意の要素を読み取ることができる双方向反復子を提供する型 **`const`** 。|
|[`difference_type`](#difference_type)|同じリスト内の要素を参照する 2 反復子の違いを提供する型。|
|[`iterator`](#iterator)|リスト内の任意の要素の読み取りまたは変更ができる双方向反復子を提供する型。|
|[`pointer`](#pointer)|リスト内の要素へのポインターを提供する型。|
|[`reference`](#reference)|**`const`** 読み取りと操作の実行のためにリストに格納されている要素への参照を提供する型 **`const`** 。|
|[`reverse_iterator`](#reverse_iterator)|逆順のリスト内の 1 つの要素の読み取りまたは変更ができる双方向反復子を提供する型。|
|[`size_type`](#size_type)|リスト内の要素の数をカウントする型。|
|[`value_type`](#value_type)|リスト内に格納されているデータ型を表す型。|

### <a name="functions"></a>関数

|名前|Description|
|-|-|
|[`assign`](#assign)|リストから要素を消去し、対象のリストに新しい要素のセットをコピーします。|
|[`back`](#back)|リストの最後の要素への参照を返します。|
|[`begin`](#begin)|リスト内の最初の要素を指す反復子を返します。|
|[`cbegin`](#cbegin)|リスト内の最初の要素を指す定数反復子を返します。|
|[`cend`](#cend)|リスト内の最後の要素の次の場所を指す定数反復子を返します。|
|[`clear`](#clear)|リストのすべての要素を消去します。|
|[`crbegin`](#crbegin)|逆順のリスト内の最初の要素を指す定数反復子を返します。|
|[`crend`](#crend)|逆順のリスト内の最後の要素の次の位置を指す定数反復子を返します。|
|[`emplace`](#emplace)|指定した位置において、構築された要素をリスト内の適切な場所に挿入します。|
|[`emplace_back`](#emplace_back)|イン プレースで構築された要素をリストの末尾に追加します。|
|[`emplace_front`](#emplace_front)|イン プレースで構築された要素をリストの先頭に追加します。|
|[`empty`](#empty)|リストが空かどうかをテストします。|
|[`end`](#end)|リスト内の最後の要素の次の位置を指す反復子を返します。|
|[`erase`](#erase)|指定した位置からリスト内の要素または要素範囲を削除します。|
|[`front`](#front)|リスト内の最初の要素への参照を返します。|
|[`get_allocator`](#get_allocator)|リストの構築に使用される `allocator` オブジェクトのコピーを返します。|
|[`insert`](#insert)|リストの指定した位置に要素、複数の要素、または要素の範囲を挿入します。|
|[`max_size`](#max_size)|リストの最大長を返します。|
|[`merge`](#merge)|引数リストから要素を削除し、それを対象のリストに挿入して、新たに組み合わされたセットの要素を昇順またはその他の指定された順序で並べ替えます。|
|[`pop_back`](#pop_back)|リストの末尾の要素を削除します。|
|[`pop_front`](#pop_front)|リストの先頭から要素を削除します。|
|[`push_back`](#push_back)|リストの末尾に要素を追加します。|
|[`push_front`](#push_front)|リストの先頭に要素を追加します。|
|[`rbegin`](#rbegin)|逆順のリスト内の最初の要素を指す反復子を返します。|
|[`remove`](#remove)|指定された値と一致するリストの要素を消去します。|
|[`remove_if`](#remove_if)|指定した述語の条件を満たすリストから要素を消去します。|
|[`rend`](#rend)|逆順のリスト内の最後の要素の次の位置を指す反復子を返します。|
|[`resize`](#resize)|リストの新しいサイズを指定します。|
|[`reverse`](#reverse)|要素がリストに出現する順序を反転させます。|
|[`size`](#size)|リスト内の要素数を返します。|
|[`sort`](#sort)|リストの要素を、昇順または他の順序関係に従って整列します。|
|[`splice`](#splice)|引数リストから要素を削除し、それらを対象のリストに挿入します。|
|[`swap`](#swap)|2 つのリストの要素を交換します。|
|[`unique`](#unique)|隣接する重複要素、または他のいずれかの二項述語の条件を満たす、隣接する要素をリストから削除します。|

### <a name="operators"></a>演算子

|名前|Description|
|-|-|
|[`operator=`](#op_eq)|別のリストのコピーでリストの要素を置き換えます。|

## <a name="requirements"></a>要件

**ヘッダー**: `<list>`

## <a name="allocator_type"></a><a name="allocator_type"></a> `allocator_type`

リスト オブジェクトの allocator クラスを表す型。

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>解説

`allocator_type` は、テンプレートパラメーターのシノニムです *`Allocator`* 。

### <a name="example"></a>例

の例を参照してください [`get_allocator`](#get_allocator) 。

## <a name="assign"></a><a name="assign"></a> `assign`

リストから要素を消去し、対象のリストに新しい要素のセットをコピーします。

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign
    initializer_list<Type> IList);

template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>パラメーター

*`First`*\
引数リストからコピーされる要素範囲内の最初の要素の位置。

*`Last`*\
引数リストからコピーされる要素範囲を超える最初の要素の位置。

*`Count`*\
リストに挿入される要素のコピーの数。

*`Val`*\
リストに挿入される要素の値。

*`IList`*\
挿入される要素を含む initializer_list。

### <a name="remarks"></a>解説

対象のリスト内にある既存の要素が消去されると、assign によって、元のリストまたは他のリストからコピーされる指定の要素範囲が対象のリストに挿入されるか、指定した値の新しい要素のコピーが対象のリストに挿入されます。

### <a name="example"></a>例

```cpp
// list_assign.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    list<int> c1, c2;
    list<int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign({ 10, 20, 30, 40 });
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 10 20 30c1 = 50 60c1 = 4 4 4 4 4 4 4c1 = 10 20 30 40
```

## <a name="back"></a><a name="back"></a> `back`

リストの最後の要素への参照を返します。

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>戻り値

リストの最後の要素。 リストが空の場合、戻り値は定義されません。

### <a name="remarks"></a>解説

`back` の戻り値が `const_reference` に割り当てられている場合、リスト オブジェクトを変更することはできません。 `back` の戻り値が `reference` に割り当てられている場合、リスト オブジェクトを変更できます。

[`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md)1 または2として定義されたを使用してコンパイルされた場合、空のリスト内の要素にアクセスしようとすると、ランタイムエラーが発生します。  詳細については、「[チェックを行う反復子](../standard-library/checked-iterators.md)」をご覧ください。

### <a name="example"></a>例

```cpp
// list_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.back( );
   const int& ii = c1.front( );

   cout << "The last integer of c1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of c1 is " << ii << endl;
}
```

```Output
The last integer of c1 is 11
The next-to-last integer of c1 is 10
```

## <a name="begin"></a><a name="begin"></a> `begin`

リスト内の最初の要素を指す反復子を返します。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>戻り値

リスト内の最初の要素、または空のリストの次の位置を指す双方向反復子。

### <a name="remarks"></a>解説

の戻り値 `begin` がに割り当てられている場合 `const_iterator` 、リストオブジェクト内の要素は変更できません。 の戻り値 `begin` がに割り当てられている場合 `iterator` 、リストオブジェクト内の要素を変更できます。

### <a name="example"></a>例

```cpp
// list_begin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::const_iterator c1_cIter;

   c1.push_back( 1 );
   c1.push_back( 2 );

   c1_Iter = c1.begin( );
   cout << "The first element of c1 is " << *c1_Iter << endl;

*c1_Iter = 20;
   c1_Iter = c1.begin( );
   cout << "The first element of c1 is now " << *c1_Iter << endl;

   // The following line would be an error because iterator is const
   // *c1_cIter = 200;
}
```

```Output
The first element of c1 is 1
The first element of c1 is now 20
```

## <a name="cbegin"></a><a name="cbegin"></a> `cbegin`

**`const`** 範囲内の最初の要素を指す反復子を返します。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>戻り値

**`const`** 範囲の最初の要素、または空の範囲の末尾の次の位置 (空の範囲の場合は) を指す双方向アクセス反復子 `cbegin() == cend()` 。

### <a name="remarks"></a>解説

`cbegin` の戻り値で範囲内の要素を変更することはできません。

`begin()` メンバー関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常、 [`auto`](../cpp/auto-cpp.md) 次の例に示すように、型推論キーワードと共に使用されます。 この例では、 `Container` **`const`** とをサポートする任意の種類の変更可能な (非) コンテナーである `begin()` と見なし `cbegin()` ます。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> `cend`

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

## <a name="clear"></a><a name="clear"></a> クリア

リストのすべての要素を消去します。

```cpp
void clear();
```

### <a name="example"></a>例

```cpp
// list_clear.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the list is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of list after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the list is initially 3
The size of list after clearing is 0
```

## <a name="const_iterator"></a><a name="const_iterator"></a> `const_iterator`

リスト内の要素を読み取ることができる双方向反復子を提供する型 **`const`** 。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>解説

`const_iterator` 型で要素の値を変更することはできません。

### <a name="example"></a>例

の例を参照してください [`back`](#back) 。

## <a name="const_pointer"></a><a name="const_pointer"></a> `const_pointer`

リスト内の要素へのポインターを提供 **`const`** します。

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>解説

`const_pointer` 型で要素の値を変更することはできません。

ほとんどの場合、 [`iterator`](#iterator) リストオブジェクト内の要素にアクセスするには、を使用する必要があります。

## <a name="const_reference"></a><a name="const_reference"></a> `const_reference`

**`const`** 読み取りと操作の実行のためにリストに格納されている要素への参照を提供する型 **`const`** 。

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>解説

`const_reference` 型で要素の値を変更することはできません。

### <a name="example"></a>例

```cpp
// list_const_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const list <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error because c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> `const_reverse_iterator`

リスト内の任意の要素を読み取ることができる双方向反復子を提供する型 **`const`** 。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>解説

`const_reverse_iterator` 型は要素の値を変更できず、逆の順序でリストを反復処理するために使用します。

### <a name="example"></a>例

の例を参照してください [`rbegin`](#rbegin) 。

## <a name="crbegin"></a><a name="crbegin"></a> `crbegin`

逆順のリスト内の最初の要素を指す定数反復子を返します。

```cpp
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>戻り値

逆順のリスト内の最初の要素を指す定数逆順双方向反復子 (または通常の順序の `list` 内の最後の要素だったものを指す定数逆順双方向反復子)。

### <a name="remarks"></a>解説

`crbegin` は、と共に使用されるのと同様に、逆順のリストで使用され [`list::begin`](#begin) `list` ます。

戻り値が `crbegin` の場合、リスト オブジェクトは変更できません。 [`list::rbegin`](#rbegin) を使用すると、リストを後方に反復処理できます。

### <a name="example"></a>例

```cpp
// list_crbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_crIter = c1.crbegin( );
   cout << "The last element in the list is " << *c1_crIter << "." << endl;
}
```

```Output
The last element in the list is 30.
```

## <a name="crend"></a><a name="crend"></a> `crend`

逆順のリスト内の最後の要素の次の位置を指す定数反復子を返します。

```cpp
const_reverse_iterator rend() const;
```

### <a name="return-value"></a>戻り値

反転された内の最後の要素の次の位置 [`list`](../standard-library/list-class.md) (反転されていない内の最初の要素の前の位置) を指す定数逆順双方向反復子 `list` 。

### <a name="remarks"></a>解説

`crend` は、と共に使用されるのと同様に、逆順のリストで使用され [`list::end`](#end) `list` ます。

戻り値が `crend` の場合、`list` オブジェクトは変更できません。

`crend` を使用して、逆順反復子が `list` の末尾に達したかどうかをテストできます。

`crend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// list_crend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_crIter = c1.crend( );
   c1_crIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_crIter << endl;
}
```

```Output
The first element in the list is: 10
```

## <a name="difference_type"></a><a name="difference_type"></a> `difference_type`

list の要素の数を、反復子が指す要素の範囲に基づいて表すために使用できる符号付き整数型。

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>解説

`difference_type` は、コンテナーの反復子を減算またはインクリメントするときに返される型です。 通常、`difference_type` は、[ `first`, `last`) の範囲内で、反復子 `first` と `last` の間にある要素の数を表すために使用され、`first` が指す要素と、`last` が指す要素の 1 つ前までの範囲の要素を含みます。

`difference_type`は、入力反復子の要件を満たすすべての反復子 (set などの反転可能なコンテナーによってサポートされる双方向反復子のクラスを含む) でも使用できますが、反復子間の減算は、 [ `vector` クラス](../standard-library/vector-class.md)などのランダムアクセスコンテナーによって提供されるランダムアクセス反復子によってのみサポートされます。

### <a name="example"></a>例

```cpp
// list_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <list>
#include <algorithm>

int main( )
{
   using namespace std;

   list <int> c1;
   list <int>::iterator   c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

    list <int>::difference_type df_typ1, df_typ2, df_typ3;

   df_typ1 = count( c1_Iter, c2_Iter, 10 );
   df_typ2 = count( c1_Iter, c2_Iter, 20 );
   df_typ3 = count( c1_Iter, c2_Iter, 30 );
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";
}
```

```Output
The number '10' is in c1 collection 1 times.
The number '20' is in c1 collection 2 times.
The number '30' is in c1 collection 3 times.
```

## <a name="emplace"></a><a name="emplace"></a> `emplace`

指定した位置において、構築された要素をリスト内の適切な場所に挿入します。

```cpp
void emplace(iterator Where, Type&& val);
```

### <a name="parameters"></a>パラメーター

*`Where`*\
[`list`](../standard-library/list-class.md)最初の要素が挿入される、ターゲット内の位置。

*`val`*\
`list` の末尾に追加する要素。

### <a name="remarks"></a>解説

例外がスローされた場合、`list` は変更されず、例外が再度スローされます。

### <a name="example"></a>例

```cpp
// list_emplace.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace(c2.begin(), move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_back"></a><a name="emplace_back"></a> `emplace_back`

イン プレースで構築された要素をリストの末尾に追加します。

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>パラメーター

*`val`*\
の末尾に追加する要素 [`list`](../standard-library/list-class.md) 。

### <a name="remarks"></a>解説

例外がスローされた場合、`list` は変更されず、例外が再度スローされます。

### <a name="example"></a>例

```cpp
// list_emplace_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_front"></a><a name="emplace_front"></a> `emplace_front`

イン プレースで構築された要素をリストの先頭に追加します。

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>パラメーター

*`val`*\
の先頭に追加される要素 [`list`](../standard-library/list-class.md) 。

### <a name="remarks"></a>解説

例外がスローされた場合、`list` は変更されず、例外が再度スローされます。

### <a name="example"></a>例

```cpp
// list_emplace_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="empty"></a><a name="empty"></a> `empty`

リストが空かどうかをテストします。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

**`true`** リストが空の場合は。 **`false`** リストが空でない場合は。

### <a name="example"></a>例

```cpp
// list_empty.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The list is empty." << endl;
   else
      cout << "The list is not empty." << endl;
}
```

```Output
The list is not empty.
```

## <a name="end"></a><a name="end"></a> `end`

リスト内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>戻り値

リスト内の最後の要素の次の位置を指す双方向反復子。 リストが空の場合は、`list::end == list::begin`。

### <a name="remarks"></a>解説

`end` は、反復子がリストの末尾に到達したかどうかをテストするために使用されます。

### <a name="example"></a>例

```cpp
// list_end.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
*c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is "
        << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // list <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The list is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The list is now: 10 400 30
```

## <a name="erase"></a><a name="erase"></a> `erase`

指定した位置からリスト内の要素または要素範囲を削除します。

```cpp
iterator erase(iterator Where);
iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>パラメーター

*`Where`*\
リストから削除される要素の位置。

*`first`*\
リストから削除される最初の要素の位置。

*`last`*\
リストから削除される最後の要素の次の位置。

### <a name="return-value"></a>戻り値

削除された要素の後に残る最初の要素を指定する双方向反復子。このような要素が存在しない場合は、リストの末尾へのポインター。

### <a name="remarks"></a>解説

再割り当ては発生しないため、反復子と参照は、消去された要素に対してのみ無効になります。

`erase` は例外をスローしません。

### <a name="example"></a>例

```cpp
// list_erase.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial list is:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the list becomes:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, the list becomes: ";
   for (Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
The initial list is: 10 20 30 40 50
After erasing the first element, the list becomes: 20 30 40 50
After erasing all elements but the first, the list becomes:  20
```

## <a name="front"></a><a name="front"></a> `front`

リスト内の最初の要素への参照を返します。

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>戻り値

リストが空の場合、戻り値は定義されません。

### <a name="remarks"></a>解説

`front` の戻り値が `const_reference` に割り当てられている場合、リスト オブジェクトを変更することはできません。 `front` の戻り値が `reference` に割り当てられている場合、リスト オブジェクトを変更できます。

[`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md)1 または2として定義されたを使用してコンパイルされた場合、空のリスト内の要素にアクセスしようとすると、ランタイムエラーが発生します。  詳細については、「[チェックを行う反復子](../standard-library/checked-iterators.md)」をご覧ください。

### <a name="example"></a>例

```cpp
// list_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );

   int& i = c1.front();
   const int& ii = c1.front();

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The first integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The first integer of c1 is 11
```

## <a name="get_allocator"></a><a name="get_allocator"></a> `get_allocator`

リストの構築に使用されるアロケーター オブジェクトのコピーを返します。

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>戻り値

リストで使用されるアロケーター。

### <a name="remarks"></a>解説

list クラスのアロケーターは、クラスがどのようにストレージを管理するかを指定します。 C++ 標準ライブラリ コンテナー クラスで提供される既定のアロケーターは、ほとんどのプログラミング要件に対応しています。 独自のアロケーター クラスを作成して使用することは、C++ における高度な作業の 1 つです。

### <a name="example"></a>例

```cpp
// list_get_allocator.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   list <int> c1;
   list <int, allocator<int> > c2 = list <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   list <int> c3( c1.get_allocator( ) );

   list<int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a><a name="insert"></a> `insert`

リストの指定した位置に要素、複数の要素、または要素の範囲を挿入します。

```cpp
iterator insert(iterator Where, const Type& Val);
iterator insert(iterator Where, Type&& Val);

void insert(iterator Where, size_type Count, const Type& Val);
iterator insert(iterator Where, initializer_list<Type> IList);

template <class InputIterator>
void insert(iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>パラメーター

*`Where`*\
最初の要素が挿入される、ターゲット リスト内の位置。

*`Val`*\
リストに挿入される要素の値。

*`Count`*\
リストに挿入される要素の数。

*`First`*\
コピーされる引数リストの要素範囲内にある最初の要素の位置。

*`Last`*\
コピーされる引数リストの要素範囲外にある最初の要素の位置。

### <a name="return-value"></a>戻り値

最初の 2 つの insert 関数は、新しい要素がリストに挿入される位置を指す反復子を返します。

### <a name="example"></a>例

```cpp
// list_class_insert.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    list <int> c1, c2;
    list <int>::iterator Iter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    c1.insert(Iter, 100);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    Iter++;
    c1.insert(Iter, 2, 200);

    cout << "c1 =";
    for(auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.insert(++c1.begin(), c2.begin(), --c2.end());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    // initialize a list of strings by moving
    list < string > c3;
    string str("a");

    c3.insert(c3.begin(), move(str));
    cout << "Moved first element: " << c3.front() << endl;

    // Assign with an initializer_list
    list <int> c4{ {1, 2, 3, 4} };
    c4.insert(c4.begin(), { 5, 6, 7, 8 });

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;
}
```

## <a name="iterator"></a><a name="iterator"></a> `iterator`

リスト内の任意の要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>解説

型は、 `iterator` 要素の値を変更するために使用できます。

### <a name="example"></a>例

の例を参照してください [`begin`](#begin) 。

## <a name="list"></a><a name="list"></a> `list`

特定のサイズ、特定の値の要素、または特定のアロケーターを持つリストを構築します。あるいは他のリストの全体または一部のコピーとして構築します。

```cpp
list();
explicit list(const Allocator& Al);
explicit list(size_type Count);
list(size_type Count, const Type& Val);
list(size_type Count, const Type& Val, const Allocator& Al);

list(const list& Right);
list(list&& Right);
list(initializer_list<Type> IList, const Allocator& Al);

template <class InputIterator>
list(InputIterator First, InputIterator Last);

template <class InputIterator>
list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>パラメーター

*`Al`*\
このオブジェクトに対して使用するアロケーター クラス。

*`Count`*\
構築されたリスト内の要素の数。

*`Val`*\
リスト内の要素の値。

*`Right`*\
構築されたリストがコピーになる元のリスト。

*`First`*\
コピーする要素範囲内の最初の要素の位置。

*`Last`*\
コピーする要素範囲を超える最初の要素の位置。

*`IList`*\
コピーされる要素を含む initializer_list。

### <a name="remarks"></a>解説

すべてのコンストラクターは、アロケーターオブジェクト () を格納 *`Al`* し、リストを初期化します。

[`get_allocator`](#get_allocator) リストを構築するために使用されるアロケーターオブジェクトのコピーを返します。

最初の2つのコンストラクターは、空の初期リストを指定します。2番目のコンストラクターは、使用するアロケーターの型 () を指定し *`Al`* ます。

3番目のコンストラクターは、 *`Count`* クラスの既定値の要素の指定された数 () の繰り返しを指定し `Type` ます。

4番目と5番目のコンストラクターは、値の () 要素の繰り返しを指定し *`Count`* *`Val`* ます。

6番目のコンストラクターは、リストのコピーを指定し *`Right`* ます。

7番目のコンストラクターは、リストを移動し *`Right`* ます。

8 番目のコンストラクターは、initializer_list を使用して要素を指定します。

次の 2 つのコンストラクターは、リストの範囲 `[First, Last)` をコピーします。

コンストラクターでは、暫定的な再割り当てを実行しません。

### <a name="example"></a>例

```cpp
// list_class_list.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty list c0
    list <int> c0;

    // Create a list c1 with 3 elements of default value 0
    list <int> c1(3);

    // Create a list c2 with 5 elements of value 2
    list <int> c2(5, 2);

    // Create a list c3 with 3 elements of value 1 and with the
    // allocator of list c2
    list <int> c3(3, 1, c2.get_allocator());

    // Create a copy, list c4, of list c2
    list <int> c4(c2);

    // Create a list c5 by copying the range c4[ first,  last)
    list <int>::iterator c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    list <int> c5(c4.begin(), c4_Iter);

    // Create a list c6 by copying the range c4[ first,  last) and with
    // the allocator of list c2
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    list <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    cout << "c2 =";
    for (auto c : c2)
        cout << " " << c;
    cout << endl;

    cout << "c3 =";
    for (auto c : c3)
        cout << " " << c;
    cout << endl;

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;

    cout << "c6 =";
    for (auto c : c6)
        cout << " " << c;
    cout << endl;

    // Move list c6 to list c7
    list <int> c7(move(c6));
    cout << "c7 =";
    for (auto c : c7)
        cout << " " << c;
    cout << endl;

    // Construct with initializer_list
    list<int> c8({ 1, 2, 3, 4 });
    cout << "c8 =";
    for (auto c : c8)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 0 0 0c2 = 2 2 2 2 2c3 = 1 1 1c4 = 2 2 2 2 2c5 = 2 2c6 = 2 2 2c7 = 2 2 2c8 = 1 2 3 4
```

## <a name="max_size"></a><a name="max_size"></a> `max_size`

リストの最大長を返します。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

リストの可能な最大長。

### <a name="example"></a>例

```cpp
// list_max_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   i = c1.max_size( );
   cout << "Maximum possible length of the list is " << i << "." << endl;
}
```

## <a name="merge"></a><a name="merge"></a> `merge`

引数リストから要素を削除し、それを対象のリストに挿入して、新たに組み合わされたセットの要素を昇順またはその他の指定された順序で並べ替えます。

```cpp
void merge(list<Type, Allocator>& right);

template <class Traits>
void merge(list<Type, Allocator>& right, Traits comp);
```

### <a name="parameters"></a>パラメーター

*`right`*\
対象のリストにマージする引数リスト。

*`comp`*\
対象のリストの要素の並べ替えに使用する比較演算子。

### <a name="remarks"></a>解説

引数リスト *`right`* がターゲットリストにマージされます。

引数リストと対象のリストはどちらも、結果のシーケンスを並べ替える場合と同じ比較関係を使用して並べ替える必要があります。 1 つ目のメンバー関数の既定の順序は昇順です。 2番目のメンバー関数は、クラスのユーザー指定の比較演算を実行し *`comp`* `Traits` ます。

### <a name="example"></a>例

```cpp
// list_merge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter, c2_Iter, c3_Iter;

   c1.push_back( 3 );
   c1.push_back( 6 );
   c2.push_back( 2 );
   c2.push_back( 4 );
   c3.push_back( 5 );
   c3.push_back( 1 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   cout << "c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   c2.merge( c1 );  // Merge c1 into c2 in (default) ascending order
   c2.sort( greater<int>( ) );
   cout << "After merging c1 with c2 and sorting with >: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   cout << "c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;

   c2.merge( c3, greater<int>( ) );
   cout << "After merging c3 with c2 according to the '>' comparison relation: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
c1 = 3 6
c2 = 2 4
After merging c1 with c2 and sorting with >: c2 = 6 4 3 2
c3 = 5 1
After merging c3 with c2 according to the '>' comparison relation: c2 = 6 5 4 3 2 1
```

## <a name="operator"></a><a name="op_eq"></a> `operator=`

別のリストのコピーでリストの要素を置き換えます。

```cpp
list& operator=(const list& right);
list& operator=(list&& right);
```

### <a name="parameters"></a>パラメーター

*`right`*\
[`list`](../standard-library/list-class.md)にコピーされる `list` 。

### <a name="remarks"></a>解説

内の既存の要素を消去した後、 `list` 演算子はの内容をにコピーまたは移動し *`right`* `list` ます。

### <a name="example"></a>例

```cpp
// list_operator_as.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int> v1, v2, v3;
   list<int>::iterator iter;

   v1.push_back(10);
   v1.push_back(20);
   v1.push_back(30);
   v1.push_back(40);
   v1.push_back(50);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = forward< list<int> >(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a><a name="pointer"></a> `pointer`

リストの要素へのポインターを提供します。

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>解説

型は、 `pointer` 要素の値を変更するために使用できます。

ほとんどの場合、 [`iterator`](#iterator) リストオブジェクト内の要素にアクセスするには、を使用する必要があります。

## <a name="pop_back"></a><a name="pop_back"></a> `pop_back`

リストの末尾の要素を削除します。

```cpp
void pop_back();
```

### <a name="remarks"></a>解説

最後の要素は空でない必要があります。 `pop_back` は例外をスローしません。

### <a name="example"></a>例

```cpp
// list_pop_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the list, "
           "the last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the list, the last element is: 1
```

## <a name="pop_front"></a><a name="pop_front"></a> `pop_front`

リストの先頭から要素を削除します。

```cpp
void pop_front();
```

### <a name="remarks"></a>解説

最初の要素は空でない必要があります。 `pop_front` は例外をスローしません。

### <a name="example"></a>例

```cpp
// list_pop_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the list, "
         "the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the list, the first element is: 2
```

## <a name="push_back"></a><a name="push_back"></a> `push_back`

リストの末尾に要素を追加します。

```cpp
void push_back(const Type& val);
void push_back(Type&& val);
```

### <a name="parameters"></a>パラメーター

*`val`*\
リストの末尾に追加する要素。

### <a name="remarks"></a>解説

例外がスローされた場合、リストは変更されず、例外が再度スローされます。

### <a name="example"></a>例

```cpp
// list_push_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   if ( c1.size( ) != 0 )
      cout << "Last element: " << c1.back( ) << endl;

   c1.push_back( 2 );
   if ( c1.size( ) != 0 )
      cout << "New last element: " << c1.back( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved first element: a
```

## <a name="push_front"></a><a name="push_front"></a> `push_front`

リストの先頭に要素を追加します。

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>パラメーター

*`val`*\
リストの先頭に追加する要素。

### <a name="remarks"></a>解説

例外がスローされた場合、リストは変更されず、例外が再度スローされます。

### <a name="example"></a>例

```cpp
// list_push_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
First element: 1
New first element: 2
Moved first element: a
```

## <a name="rbegin"></a><a name="rbegin"></a> `rbegin`

逆順のリスト内の最初の要素を示す反復子を返します。

```cpp
const_reverse_iterator rbegin() const;
reverse_iterator rbegin();
```

### <a name="return-value"></a>戻り値

逆順のリスト内の最初の要素を指す反転双方向反復子 (または通常の順序のリスト内の最後の要素だったものを指す反転双方向反復子)。

### <a name="remarks"></a>解説

`rbegin` は、リストで使用されるのと同様に、逆順のリストで使用され [`begin`](#begin) ます。

`rbegin` の戻り値が `const_reverse_iterator` に割り当てられている場合、リスト オブジェクトを変更することはできません。 `rbegin` の戻り値が `reverse_iterator` に割り当てられている場合、リスト オブジェクトを変更できます。

`rbegin` を使用して、リスト内を後方に向かって反復処理できます。

### <a name="example"></a>例

```cpp
// list_rbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line replaced the line above, *c1_rIter = 40;
   // (below) would be an error
   //list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_rIter = c1.rbegin( );
   cout << "The last element in the list is " << *c1_rIter << "." << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration through a list in
   // reverse order
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rbegin( );
*c1_rIter = 40;
   cout << "The last element in the list is now " << *c1_rIter << "." << endl;
}
```

```Output
The last element in the list is 30.
The list is: 10 20 30
The reversed list is: 30 20 10
The last element in the list is now 40.
```

## <a name="reference"></a><a name="reference"></a> `reference`

list に格納されている要素への参照を提供する型。

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>例

```cpp
// list_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="remove"></a><a name="remove"></a> `remove`

指定された値と一致するリストの要素を消去します。

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>パラメーター

*`val`*\
要素によって保持されている場合、リストからその要素が削除される原因となる値。

### <a name="remarks"></a>解説

要素の残りの順序は影響を受けません。

### <a name="example"></a>例

```cpp
// list_remove.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 5 );
   c1.push_back( 100 );
   c1.push_back( 5 );
   c1.push_back( 200 );
   c1.push_back( 5 );
   c1.push_back( 300 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove( 5 );
   cout << "After removing elements with value 5, the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 5 100 5 200 5 300
After removing elements with value 5, the list becomes c2 = 100 200 300
```

## <a name="remove_if"></a><a name="remove_if"></a> `remove_if`

指定した述語を満たすリストから要素を消去します。

```cpp
template <class Predicate>
void remove_if(Predicate pred)
```

### <a name="parameters"></a>パラメーター

*`pred`*\
要素によって満たされる場合、単項述語は結果的にリストからその要素を削除します。

### <a name="example"></a>例

```cpp
// list_remove_if.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

template <class T> class is_odd : public std::unary_function<T, bool>
{
public:
   bool operator( ) ( T& val )
   {
   return ( val % 2 ) == 1;
   }
};

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 3 );
   c1.push_back( 4 );
   c1.push_back( 5 );
   c1.push_back( 6 );
   c1.push_back( 7 );
   c1.push_back( 8 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove_if( is_odd<int>( ) );

   cout << "After removing the odd elements, "
        << "the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 3 4 5 6 7 8
After removing the odd elements, the list becomes c2 = 4 6 8
```

## <a name="rend"></a><a name="rend"></a> `rend`

逆順のリスト内の最後の要素の次の場所を指す反復子を返します。

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>戻り値

逆順のリスト内の最後の要素の次の場所 (通常の順序のリスト内の最初の要素の前の場所) を指す逆順双方向反復子。

### <a name="remarks"></a>解説

`rend` は、リストで使用されるのと同様に、逆順のリストで使用され [`end`](#end) ます。

`rend` の戻り値が `const_reverse_iterator` に割り当てられている場合、リスト オブジェクトを変更することはできません。 `rend` の戻り値が `reverse_iterator` に割り当てられている場合、リスト オブジェクトを変更できます。

`rend` を使用して、逆順反復子がリストの末尾に達したかどうかをテストできます。

`rend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// list_rend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error would
   // have resulted in the line modifying an element (commented below)
   // because the iterator would have been const
   // list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_rIter << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rend can be used to test if an iteration is through all of the
   // elements of a reversed list
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--;  // Decrementing the reverse iterator moves it backward
                // in the reversed list (to the last element here)

*c1_rIter = 40;  // This modification of the last element would have
                    // caused an error if a const_reverse iterator had
                    // been declared (as noted above)

   cout << "The modified reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;
}
```

```Output
The first element in the list is: 10
The list is: 10 20 30
The reversed list is: 30 20 10
The modified reversed list is: 30 20 40
```

## <a name="resize"></a><a name="resize"></a> `resize`

リストの新しいサイズを指定します。

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>パラメーター

*`_Newsize`*\
リストの新しいサイズ。

*`val`*\
新しいサイズが元のサイズよりも大きい場合に、リストに追加される新しい要素の値。 この値を省略した場合、新しい要素にはそのクラスの既定値が割り当てられます。

### <a name="remarks"></a>解説

リストのサイズが要求されたサイズより小さい場合は、要求された *`_Newsize`* サイズに達するまで要素がリストに追加されます。

リストのサイズが要求されたサイズよりも大きい場合、リストがサイズに達するまで、リストの末尾に近い要素が削除され *`_Newsize`* ます。

リストの現在のサイズが要求されたサイズと同じ場合は、何も実行されません。

[`size`](#size) リストの現在のサイズを反映します。

### <a name="example"></a>例

```cpp
// list_resize.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is 4
The value of the last element is 40
The size of c1 is now 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse"></a><a name="reverse"></a> `reverse`

要素がリストに出現する順序を反転させます。

```cpp
void reverse();
```

### <a name="example"></a>例

```cpp
// list_reverse.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.reverse( );
   cout << "Reversed c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
c1 = 10 20 30
Reversed c1 = 30 20 10
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> `reverse_iterator`

逆順のリスト内の 1 つの要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>解説

型 `reverse_iterator` は、逆の順序でリストを反復処理するために使用します。

### <a name="example"></a>例

の例を参照してください [`rbegin`](#rbegin) 。

## <a name="size"></a><a name="size"></a> `size`

リスト内の要素数を返します。

```cpp
size_type size() const;
```

### <a name="return-value"></a>戻り値

リストの現在の長さ。

### <a name="example"></a>例

```cpp
// list_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   c1.push_back( 5 );
   i = c1.size( );
   cout << "List length is " << i << "." << endl;

   c1.push_back( 7 );
   i = c1.size( );
   cout << "List length is now " << i << "." << endl;
}
```

```Output
List length is 1.
List length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> `size_type`

リスト内の要素の数をカウントする型。

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>例

の例を参照してください [`size`](#size) 。

## <a name="sort"></a><a name="sort"></a> `sort`

リストの要素を、昇順またはいくつかの他のユーザー指定の順序で整列します。

```cpp
void sort();

template <class Traits>
    void sort(Traits comp);
```

### <a name="parameters"></a>パラメーター

*`comp`*\
連続する要素の並べ替えに使用される比較演算子。

### <a name="remarks"></a>解説

既定では、最初のメンバー関数は要素を昇順に並べ替えます。

メンバーテンプレート関数は、クラスのユーザー指定の比較演算に従って要素を並べ替え *`comp`* `Traits` ます。

### <a name="example"></a>例

```cpp
// list_sort.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 20 );
   c1.push_back( 10 );
   c1.push_back( 30 );

   cout << "Before sorting: c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( );
   cout << "After sorting c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( greater<int>( ) );
   cout << "After sorting with 'greater than' operation, c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
Before sorting: c1 = 20 10 30
After sorting c1 = 10 20 30
After sorting with 'greater than' operation, c1 = 30 20 10
```

## <a name="splice"></a><a name="splice"></a> `splice`

ソース リストから要素を削除して、ターゲット リストに挿入します。

```cpp
// insert the entire source list
void splice(const_iterator Where, list<Type, Allocator>& Source);
void splice(const_iterator Where, list<Type, Allocator>&& Source);

// insert one element of the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator Iter);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator Iter);

// insert a range of elements from the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator First, const_iterator Last);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator First, const_iterator Last);
```

### <a name="parameters"></a>パラメーター

*`Where`*\
挿入されるターゲット リスト内の位置。

*`Source`*\
ターゲット リストに挿入されるソース リスト。

*`Iter`*\
ソース リストから挿入される要素。

*`First`*\
ソース リストから挿入される範囲内の最初の要素。

*`Last`*\
ソース リストから挿入される範囲内の最後の要素を超える最初の位置。

### <a name="remarks"></a>解説

メンバー関数の最初のペアは、ソースリスト内のすべての要素を、によって参照される位置の前にコピー先リストに挿入 *`Where`* し、ソースリストからすべての要素を削除します。 ( `&Source` はと等しくない必要があり **`this`** ます)。

メンバー関数の2番目のペアは、で参照される要素を、によって参照される *`Iter`* ターゲットリスト内の位置の前に挿入 *`Where`* し、ソースリストから *Iter* を削除します。 (`Where == Iter || Where == ++Iter` の場合は、何も変わりません)。

メンバー関数の3番目のペアは、[,) で指定された範囲を、によって参照される `First` `Last` ターゲットリスト内の要素の前に挿入 *`Where`* し、ソースリストからその要素の範囲を削除します。 (の場合、が指す要素を範囲に含めることはでき `&Source == this` `[First, Last)` ません *`Where`* )。

範囲を持つスプライスによっ `N` て要素が挿入されると、 `&Source != this` クラスのオブジェクト [`iterator`](../standard-library/forward-list-class.md#iterator) が1回インクリメントされ `N` ます。

すべての場合において、スプライスされた要素を参照する反復子、ポインター、参照は有効なままでターゲット コンテナーに転送されます。

### <a name="example"></a>例

```cpp
// list_splice.cpp
// compile with: /EHsc /W4
#include <list>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    list<int> c1{10,11};
    list<int> c2{20,21,22};
    list<int> c3{30,31};
    list<int> c4{40,41,42,43};

    list<int>::iterator where_iter;
    list<int>::iterator first_iter;
    list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    --last_iter;
    c2.splice(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = 2 elements: (10) (11)c2 = 3 elements: (20) (21) (22)c3 = 2 elements: (30) (31)c4 = 4 elements: (40) (41) (42) (43)After splicing c1 into c2:c1 = 0 elements:c2 = 5 elements: (20) (10) (11) (21) (22)After splicing the first element of c3 into c2:c3 = 1 elements: (31)c2 = 6 elements: (20) (10) (11) (30) (21) (22)After splicing a range of c4 into c2:c4 = 2 elements: (40) (43)c2 = 8 elements: (20) (10) (11) (30) (41) (42) (21) (22)
```

## <a name="swap"></a><a name="swap"></a> `swap`

2 つのリストの要素を交換します。

```cpp
void swap(list<Type, Allocator>& right);
friend void swap(list<Type, Allocator>& left, list<Type, Allocator>& right)
```

### <a name="parameters"></a>パラメーター

*`right`*\
交換する要素を提供するリスト、または要素がリストの要素と交換されるリスト *`left`* 。

*`left`*\
リストの要素と交換される要素を含むリスト *`right`* 。

### <a name="example"></a>例

```cpp
// list_swap.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original list c1 is: 1 2 3
After swapping with c2, list c1 is: 10 20
After swapping with c3, list c1 is: 100
```

## <a name="unique"></a><a name="unique"></a> `unique`

隣接する重複要素、または他のいずれかの二項述語の条件を満たす隣接する要素を list から削除します。

```cpp
void unique();

template <class BinaryPredicate>
void unique(BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*`pred`*\
一連の要素の比較に使用する二項述語。

### <a name="remarks"></a>解説

この関数は、すべての重複要素が隣接するように list が並べ替えられていることを前提とします。 隣接していない重複要素は削除されません。

1 つ目のメンバー関数は、その直前の要素に一致するすべての要素を削除します。

2番目のメンバー関数は、 *`pred`* その前の要素と比較したときに、述語関数を満たすすべての要素を削除します。 引数のヘッダーで宣言されている任意のバイナリ関数オブジェクトを使用することも、独自の関数オブジェクトを作成することもでき `<functional>` *`pred`* ます。

### <a name="example"></a>例

```cpp
// list_unique.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter,c3_Iter;
   not_equal_to<int> mypred;

   c1.push_back( -10 );
   c1.push_back( 10 );
   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 20 );
   c1.push_back( -10 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.unique( );
   cout << "After removing successive duplicate elements, c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   list <int> c3 = c2;
   c3.unique( mypred );
   cout << "After removing successive unequal elements, c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = -10 10 10 20 20 -10
After removing successive duplicate elements, c2 = -10 10 20 -10
After removing successive unequal elements, c3 = -10 -10
```

## <a name="value_type"></a><a name="value_type"></a> `value_type`

リスト内に格納されているデータ型を表す型。

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>解説

`value_type` は、テンプレートパラメーターのシノニムです *`Type`* 。

### <a name="example"></a>例

```cpp
// list_value_type.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```
