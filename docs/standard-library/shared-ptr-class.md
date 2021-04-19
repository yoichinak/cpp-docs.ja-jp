---
description: '詳細情報: shared_ptr クラス'
title: shared_ptr クラス
ms.date: 07/29/2019
f1_keywords:
- memory/std::shared_ptr
- memory/std::shared_ptr::element_type
- memory/std::shared_ptr::get
- memory/std::shared_ptr::owner_before
- memory/std::shared_ptr::reset
- memory/std::shared_ptr::swap
- memory/std::shared_ptr::unique
- memory/std::shared_ptr::use_count
- memory/std::shared_ptr::operator boolean-type
- memory/std::shared_ptr::operator*
- memory/std::shared_ptr::operator=
- memory/std::shared_ptr::operator->
helpviewer_keywords:
- std::shared_ptr [C++]
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
ms.assetid: 1469fc51-c658-43f1-886c-f4530dd84860
ms.openlocfilehash: 8f809c4cf10c57e86f207090bd86cdbfeb31f226
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721538"
---
# <a name="shared_ptr-class"></a>`shared_ptr` クラス

参照カウント スマート ポインターを、動的に割り当てられたオブジェクトにラップします。

## <a name="syntax"></a>構文

```cpp
template <class T>
class shared_ptr;
```

## <a name="remarks"></a>解説

クラスは、 `shared_ptr` 参照カウントを使用してリソースを管理するオブジェクトを表します。 `shared_ptr` オブジェクトは、所有しているリソースへのポインターまたは null ポインターを効率的に保持します。 複数の `shared_ptr` オブジェクトが 1 つのリソースを所有することもできます。その場合、特定のリソースを所有する最後の `shared_ptr` オブジェクトが破棄された時点で、リソースが解放されます。

は、 `shared_ptr` 再割り当てまたはリセットされたときに、リソースの所有を停止します。

テンプレートの引数 `T` は、特定のメンバー関数について注記がある場合を除き、不完全な型になる場合があります。

`shared_ptr<T>` オブジェクトを `G*` 型のリソース ポインターまたは `shared_ptr<G>` から構築する場合、ポインターの型 `G*` は `T*` に変換可能であることが必要です。 変換できない場合、コードはコンパイルされません。 次に例を示します。

```cpp
#include <memory>
using namespace std;

class F {};
class G : public F {};

shared_ptr<G> sp0(new G);   // okay, template parameter G and argument G*
shared_ptr<G> sp1(sp0);     // okay, template parameter G and argument shared_ptr<G>
shared_ptr<F> sp2(new G);   // okay, G* convertible to F*
shared_ptr<F> sp3(sp0);     // okay, template parameter F and argument shared_ptr<G>
shared_ptr<F> sp4(sp2);     // okay, template parameter F and argument shared_ptr<F>
shared_ptr<int> sp5(new G); // error, G* not convertible to int*
shared_ptr<int> sp6(sp2);   // error, template parameter int and argument shared_ptr<F>
```

`shared_ptr` オブジェクトがリソースを所有するためには、次のいずれかの条件を満たしている必要があります。

- そのリソースへのポインターを使って構築されている。

- そのリソースを所有する `shared_ptr` オブジェクトから構築されている。

- そのリソースを指すオブジェクトから構築された場合 [`weak_ptr`](weak-ptr-class.md) は。

- そのリソースの所有権が割り当てられている場合は、またはのいずれかの [`shared_ptr::operator=`](#op_eq) メンバー関数を呼び出し [`shared_ptr::reset`](#reset) ます。

リソースを所有する `shared_ptr` オブジェクトは、コントロール ブロックを共有します。 コントロール ブロックは以下の情報を保持します。

- リソースを所有する `shared_ptr` オブジェクトの数。

- リソースを指す `weak_ptr` オブジェクトの数。

- リソースの削除子 (存在する場合)

- コントロール ブロックのカスタム アロケーター (存在する場合)

null ポインターを使用して初期化される `shared_ptr` オブジェクトにはコントロール ブロックが存在し、空ではありません。 `shared_ptr` オブジェクトがリソースを所有するのは、そのリソースが解放されるまでの間です。 `weak_ptr` オブジェクトがリソースを指しているのは、そのリソースが解放されるまでの間です。

リソースを所有する `shared_ptr` オブジェクトの数がゼロになると、リソースを削除するか、リソースのアドレスを削除子に渡すことによって、リソースが解放されます。どちらの方法で解放されるかは、最初にリソースの所有権が作成された方法によって決定されます。 リソースを所有する `shared_ptr` オブジェクトの数がゼロになり、そのリソースを指す `weak_ptr` オブジェクトの数がゼロになると、コントロール ブロックのカスタム アロケーターを使用して (存在する場合)、コントロール ブロックが解放されます。

空の `shared_ptr` オブジェクトは、リソースを一切所有せず、コントロール ブロックも持ちません。

削除子は、メンバー関数 `operator()` を持つ関数オブジェクトです。 この型はコピーによって構築可能であること、また、コピー コンストラクターおよびデストラクターによって例外がスローされないことが必要です。 削除子は、削除するオブジェクトを指定する 1 つのパラメーターを受け入れます。

一部の関数では、結果として生成される `shared_ptr<T>` または `weak_ptr<T>` オブジェクトのプロパティを定義する引数リストが使用されます。 その場合、引数リストは次のような方法で指定できます。

引数なし: 結果として生成されるオブジェクトは、空の `shared_ptr` オブジェクトまたは空の `weak_ptr` オブジェクトです。

`ptr` -- 管理対象リソースへの `Other*` 型のポインター。 `T` は完全な型である必要があります。 関数が失敗した場合 (制御ブロックを割り当てることができないため)、式が評価さ `delete ptr` れます。

`ptr, deleter`: 管理対象リソースに対する `Other*` 型のポインターおよびそのリソースの削除子です。 関数が失敗した場合 (制御ブロックを割り当てることができないため)、を呼び出します。これは `deleter(ptr)` 、適切に定義されている必要があります。

`ptr, deleter, alloc` -- 管理対象リソース、そのリソースの削除子、および割り当てと解放を行う必要があるすべてのストレージを管理するためのアロケーターへの `Other*` 型のポインター。 関数が失敗した場合 (制御ブロックを割り当てることができないため)、を呼び出します。これは `deleter(ptr)` 、適切に定義されている必要があります。

`sp`: 管理対象のリソースを所有する `shared_ptr<Other>` オブジェクトです。

`wp`: 管理対象のリソースを指し示す `weak_ptr<Other>` オブジェクトです。

`ap`: 管理対象のリソースへのポインターを保持する `auto_ptr<Other>` オブジェクトです。 関数が成功した場合は、を呼び出します。それ以外の場合はを呼び出し `ap.release()` `ap` ます。

いずれの場合も、ポインターの型 `Other*` は `T*` に変換可能である必要があります。

## <a name="thread-safety"></a>スレッド セーフ

複数のスレッドが異なる `shared_ptr` オブジェクト (所有権を共有するコピーである場合も含めて) に対する読み取りと書き込みを同時に行うことができます。

## <a name="members"></a>メンバー

|名前|Description|
|-|-|
| **コンストラクター** | |
|[`shared_ptr`](#shared_ptr)|`shared_ptr` を構築します。|
|[`~shared_ptr`](#dtorshared_ptr)|`shared_ptr` を破棄します。|
| **Typedefs** | |
|[`element_type`](#element_type)|要素の型。|
|[`weak_type`](#weak_type)|要素への弱いポインターの型。|
| **メンバー関数** | |
|[`get`](#get)|所有されているリソースのアドレスを取得します。|
|[`owner_before`](#owner_before)|この `shared_ptr` が、指定されたポインターの前に順序付けされている (またはそれよりも少ない) 場合は true を返します。|
|[`reset`](#reset)|所有されたリソースを置き換えます。|
|[`swap`](#swap)|2 つの `shared_ptr` オブジェクトを交換します。|
|[`unique`](#unique)|所有されたリソースが一意であるかどうかをテストします。|
|[`use_count`](#use_count)|リソース所有者の数をカウントします。|
| **演算子** | |
|[`operator bool`](#op_bool)|所有されたリソースが存在するかどうかをテストします。|
|[`operator*`](#op_star)|指定された値を取得します。|
|[`operator=`](#op_eq)|所有されたリソースを置き換えます。|
|[`operator->`](#op_arrow)|指定された値へのポインターを取得します。|

## <a name="element_type"></a><a name="element_type"></a> `element_type`

要素の型。

```cpp
typedef T element_type;                  // before C++17
using element_type = remove_extent_t<T>; // C++17
```

### <a name="remarks"></a>解説

この `element_type` 型は、テンプレートパラメーターのシノニムです `T` 。

### <a name="example"></a>例

```cpp
// std__memory__shared_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::shared_ptr<int>::element_type val = *sp0;

    std::cout << "*sp0 == " << val << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
```

## <a name="get"></a><a name="get"></a> `get`

所有されているリソースのアドレスを取得します。

```cpp
element_type* get() const noexcept;
```

### <a name="remarks"></a>解説

メンバー関数は、所有されたリソースのアドレスを返します。 オブジェクトがリソースを所有していない場合は、0を返します。

### <a name="example"></a>例

```cpp
// std__memory__shared_ptr_get.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "sp0.get() == 0 == " << std::boolalpha
        << (sp0.get() == 0) << std::endl;
    std::cout << "*sp1.get() == " << *sp1.get() << std::endl;

    return (0);
}
```

```Output
sp0.get() == 0 == true
*sp1.get() == 5
```

## <a name="operator-bool"></a><a name="op_bool"></a> `operator bool`

所有されたリソースが存在するかどうかをテストします。

```cpp
explicit operator bool() const noexcept;
```

### <a name="remarks"></a>解説

演算子は、の場合はの値を返し **`true`** ます。それ以外の場合はを返し `get() != nullptr` **`false`** ます。

### <a name="example"></a>例

```cpp
// std__memory__shared_ptr_operator_bool.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;
    std::cout << "(bool)sp1 == " << std::boolalpha
        << (bool)sp1 << std::endl;

    return (0);
}
```

```Output
(bool)sp0 == false
(bool)sp1 == true
```

## <a name="operator"></a><a name="op_star"></a> `operator*`

指定された値を取得します。

```cpp
T& operator*() const noexcept;
```

### <a name="remarks"></a>解説

間接演算子は `*get()` を返します。 つまり、格納されたポインターは、null にすることはできません。

### <a name="example"></a>例

```cpp
// std__memory__shared_ptr_operator_st.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
```

## <a name="operator"></a><a name="op_eq"></a> `operator=`

所有されたリソースを置き換えます。

```cpp
shared_ptr& operator=(const shared_ptr& sp) noexcept;

shared_ptr& operator=(shared_ptr&& sp) noexcept;

template <class Other>
shared_ptr& operator=(const shared_ptr<Other>& sp) noexcept;

template <class Other>
shared_ptr& operator=(shared_ptr<Other>&& sp) noexcept;

template <class Other>
shared_ptr& operator=(auto_ptr<Other>&& ap);    // deprecated in C++11, removed in C++17

template <class Other, class Deleter>
shared_ptr& operator=(unique_ptr<Other, Deleter>&& up);
```

### <a name="parameters"></a>パラメーター

*`sp`*\
コピーまたは移動する共有ポインター。

*`ap`*\
移動する自動ポインター。 `auto_ptr`オーバーロードは c++ 11 で非推奨とされ、c++ 17 では削除されています。

*`up`*\
所有権を採用するオブジェクトへの一意のポインター。 *`up`* 呼び出しの後にオブジェクトを所有しません。

*`Other`*\
*`sp`*、 *`ap`* 、またはが指すオブジェクトの型 *`up`* 。

*`Deleter`*\
所有オブジェクトの削除子の種類。後でオブジェクトを削除するために格納されます。

### <a name="remarks"></a>解説

すべての演算子は、によって現在所有されているリソースの参照カウントをデクリメント **`*this`** し、オペランドシーケンスによって指定されたリソースの所有権をに割り当て **`*this`** ます。 参照数がゼロになる場合は、リソースが解放されます。 操作が失敗した場合は、 **`*this`** 変更されません。

### <a name="example"></a>例

```cpp
// std__memory__shared_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));
    std::unique_ptr<int> up(new int(10));

    sp0 = sp1;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    sp0 = up;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
*sp0 == 10
```

## <a name="operator-"></a><a name="op_arrow"></a> `operator->`

指定された値へのポインターを取得します。

```cpp
T* operator->() const noexcept;
```

### <a name="remarks"></a>解説

`sp` がクラス `shared_ptr<T>` のオブジェクトである場合に式 `sp->member` が `(sp.get())->member` と同様に動作するよう、選択演算子は `get()` を返します。 そのため、格納されているポインターを null にすることはできず、`T` はメンバー `member` を持つクラス、構造体、または共用体型にする必要があります。

### <a name="example"></a>例

```cpp
// std__memory__shared_ptr_operator_ar.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

typedef std::pair<int, int> Mypair;
int main()
{
    std::shared_ptr<Mypair> sp0(new Mypair(1, 2));

    std::cout << "sp0->first == " << sp0->first << std::endl;
    std::cout << "sp0->second == " << sp0->second << std::endl;

    return (0);
}
```

```Output
sp0->first == 1
sp0->second == 2
```

## <a name="owner_before"></a><a name="owner_before"></a> `owner_before`

この `shared_ptr` が、指定されたポインターの前に順序付けされている (またはそれよりも少ない) 場合は true を返します。

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr) const noexcept;

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr) const noexcept;
```

### <a name="parameters"></a>パラメーター

*`ptr`*\
またはのいずれかへの左辺値参照 `shared_ptr` `weak_ptr` 。

### <a name="remarks"></a>解説

テンプレートメンバー関数は、 **`*this`** がの前にある場合に true を返し `ptr` ます。

## <a name="reset"></a><a name="reset"></a> `reset`

所有されたリソースを置き換えます。

```cpp
void reset() noexcept;

template <class Other>
void reset(Other *ptr);

template <class Other, class Deleter>
void reset(
    Other *ptr,
    Deleter deleter);

template <class Other, class Deleter, class Allocator>
void reset(
    Other *ptr,
    Deleter deleter,
    Allocator alloc);
```

### <a name="parameters"></a>パラメーター

*`Other`*\
引数ポインターによって制御される型。

*`Deleter`*\
削除子の型。

*`ptr`*\
コピーするポインター。

*`deleter`*\
コピーする削除子。

*`Allocator`*\
アロケーターの型。

*`alloc`*\
コピーするアロケーター。

### <a name="remarks"></a>解説

すべての演算子は、によって現在所有されているリソースの参照カウントをデクリメント **`*this`** し、オペランドシーケンスによって指定されたリソースの所有権をに割り当て **`*this`** ます。 参照数がゼロになる場合は、リソースが解放されます。 操作が失敗した場合は、 **`*this`** 変更されません。

### <a name="example"></a>例

```cpp
// std__memory__shared_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp(new int(5));

    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset();
    std::cout << "(bool)sp == " << std::boolalpha
        << (bool)sp << std::endl;

    sp.reset(new int(10));
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset(new int(15), deleter());
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    return (0);
}
```

```Output
*sp == 5
(bool)sp == false
*sp == 10
*sp == 15
```

## <a name="shared_ptr"></a><a name="shared_ptr"></a> `shared_ptr`

`shared_ptr` を構築します。

```cpp
constexpr shared_ptr() noexcept;

constexpr shared_ptr(nullptr_t) noexcept : shared_ptr() {}

shared_ptr(const shared_ptr& sp) noexcept;

shared_ptr(shared_ptr&& sp) noexcept;

template <class Other>
explicit shared_ptr(Other* ptr);

template <class Other, class Deleter>
shared_ptr(
    Other* ptr,
    Deleter deleter);

template <class Deleter>
shared_ptr(
    nullptr_t ptr,
    Deleter deleter);

template <class Other, class Deleter, class Allocator>
shared_ptr(
    Other* ptr,
    Deleter deleter,
    Allocator alloc);

template <class Deleter, class Allocator>
shared_ptr(
    nullptr_t ptr,
    Deleter deleter,
    Allocator alloc);

template <class Other>
shared_ptr(
    const shared_ptr<Other>& sp) noexcept;

template <class Other>
explicit shared_ptr(
    const weak_ptr<Other>& wp);

template <class &>
shared_ptr(
    std::auto_ptr<Other>& ap);

template <class &>
shared_ptr(
    std::auto_ptr<Other>&& ap);

template <class Other, class Deleter>
shared_ptr(
    unique_ptr<Other, Deleter>&& up);

template <class Other>
shared_ptr(
    const shared_ptr<Other>& sp,
    element_type* ptr) noexcept;

template <class Other>
shared_ptr(
    shared_ptr<Other>&& sp,
    element_type* ptr) noexcept;

template <class Other, class Deleter>
shared_ptr(
    const unique_ptr<Other, Deleter>& up) = delete;
```

### <a name="parameters"></a>パラメーター

*`Other`*\
引数ポインターによって制御される型。

*`ptr`*\
コピーするポインター。

*`Deleter`*\
削除子の型。

*`Allocator`*\
アロケーターの型。

*`deleter`*\
削除子。

*`alloc`*\
アロケーター。

*`sp`*\
コピーするスマート ポインター。

*`wp`*\
ウィーク ポインター。

*`ap`*\
コピーする自動ポインター。

### <a name="remarks"></a>解説

それぞれのコンストラクターは、オペランド シーケンスで指定されたリソースを所有するオブジェクトを構築します。 コンストラクターは、 `shared_ptr(const weak_ptr<Other>& wp)` の場合、型の例外オブジェクトをスローし [`bad_weak_ptr`](bad-weak-ptr-class.md) `wp.expired()` ます。

### <a name="example"></a>例

```cpp
// std__memory__shared_ptr_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp0;
    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    std::shared_ptr<int> sp2(new int(10), deleter());
    std::cout << "*sp2 == " << *sp2 << std::endl;

    std::shared_ptr<int> sp3(sp2);
    std::cout << "*sp3 == " << *sp3 << std::endl;

    std::weak_ptr<int> wp(sp3);
    std::shared_ptr<int> sp4(wp);
    std::cout << "*sp4 == " << *sp4 << std::endl;

    std::auto_ptr<int> ap(new int(15));
    std::shared_ptr<int> sp5(ap);
    std::cout << "*sp5 == " << *sp5 << std::endl;

    return (0);
}
```

```Output
(bool)sp0 == false
*sp1 == 5
*sp2 == 10
*sp3 == 10
*sp4 == 10
*sp5 == 15
```

## <a name="shared_ptr"></a><a name="dtorshared_ptr"></a> `~shared_ptr`

`shared_ptr` を破棄します。

```cpp
~shared_ptr();
```

### <a name="remarks"></a>解説

デストラクターは、によって現在所有されているリソースの参照カウントをデクリメントし **`*this`** ます。 参照数がゼロになる場合は、リソースが解放されます。

### <a name="example"></a>例

```cpp
// std__memory__shared_ptr_destroy.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << "use count == " << sp1.use_count() << std::endl;

    {
        std::shared_ptr<int> sp2(sp1);
        std::cout << "*sp2 == " << *sp2 << std::endl;
        std::cout << "use count == " << sp1.use_count() << std::endl;
    }

    // check use count after sp2 is destroyed
    std::cout << "use count == " << sp1.use_count() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
use count == 1
*sp2 == 5
use count == 2
use count == 1
```

## <a name="swap"></a><a name="swap"></a> `swap`

2 つの `shared_ptr` オブジェクトを交換します。

```cpp
void swap(shared_ptr& sp) noexcept;
```

### <a name="parameters"></a>パラメーター

*`sp`*\
交換先の共有ポインター。

### <a name="remarks"></a>解説

このメンバー関数は、 **`*this`** その後、によって所有されているリソース *`sp`* と、 *`sp`* その後、によって所有された元のリソースを残し **`*this`** ます。 この関数はこれら 2 つのリソースの参照数を変更せず、例外をスローしません。

### <a name="example"></a>例

```cpp
// std__memory__shared_ptr_swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5
*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="unique"></a><a name="unique"></a> `unique`

所有されたリソースが一意であるかどうかをテストします。 この関数は C++ 17 で非推奨とされ、C++ 20 で削除されました。

```cpp
bool unique() const noexcept;
```

### <a name="remarks"></a>解説

このメンバー関数は、 **`true`** が所有するリソースを所有している他のオブジェクトがない場合はを返し `shared_ptr` **`*this`** ます。それ以外の場合はを返し **`false`** ます。

### <a name="example"></a>例

```cpp
// std__memory__shared_ptr_unique.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    return (0);
}
```

```Output
sp1.unique() == true
sp1.unique() == false
```

## <a name="use_count"></a><a name="use_count"></a> `use_count`

リソース所有者の数をカウントします。

```cpp
long use_count() const noexcept;
```

### <a name="remarks"></a>解説

このメンバー関数は、 `shared_ptr` によって所有されているリソースを所有するオブジェクトの数を返し **`*this`** ます。

### <a name="example"></a>例

```cpp
// std__memory__shared_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    return (0);
}
```

```Output
sp1.use_count() == 1
sp1.use_count() == 2
```

## <a name="weak_type"></a><a name="weak_type"></a> `weak_type`

要素への弱いポインターの型。

```cpp
using weak_type = weak_ptr<T>; // C++17
```

### <a name="remarks"></a>解説

`weak_type`定義は c++ 17 で追加されました。

## <a name="see-also"></a>関連項目

[ヘッダーファイルのリファレンス](cpp-standard-library-header-files.md)\
[`<memory>`](memory.md)\
[`unique_ptr`](unique-ptr-class.md)\
[`weak_ptr` クラス](weak-ptr-class.md)
