---
description: 詳細については、「 &lt; メモリ関数」を参照してください。 &gt;
title: '&lt;memory&gt; 関数'
ms.date: 08/05/2019
f1_keywords:
- memory/std::addressof
- memory/std::align
- memory/std::allocate_shared
- memory/std::const_pointer_cast
- memory/std::declare_no_pointers
- memory/std::declare_reachable
- memory/std::dynamic_pointer_cast
- memory/std::get_deleter
- memory/std::get_pointer_safety
- memory/std::get_temporary_buffer
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
- memory/std::reinterpret_pointer_cast
- memory/std::return_temporary_buffer
- xmemory/std::return_temporary_buffer
- memory/std::static_pointer_cast
- memory/std::swap
- memory/std::undeclare_no_pointers
- memory/std::undeclare_reachable
- memory/std::uninitialized_copy
- memory/std::uninitialized_copy_n
- memory/std::uninitialized_fill
- memory/std::uninitialized_fill_n
ms.assetid: 3e1898c2-44b7-4626-87ce-84962e4c6f1a
helpviewer_keywords:
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::swap [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
ms.openlocfilehash: fe5aedffe76bb613d0f042d1aa521d4c43943b8b
ms.sourcegitcommit: a89eac9acdbd54a181e3bd5d5bc71a3ef3c1abca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106506053"
---
# <a name="memory-functions"></a>`<memory>` 関数

## <a name="addressof"></a><a name="addressof"></a> `addressof`

オブジェクトの実際のアドレスを取得します。

```cpp
template <class T>
T* addressof(
    T& value) noexcept;    // before C++17

template <class T>
constexpr T* addressof(
    T& value) noexcept;    // C++17

template <class T>
const T* addressof(
    const T&& value) = delete;   // C++17
```

### <a name="parameters"></a>パラメーター

*`value`*\
実際のアドレスを取得する対象のオブジェクトまたは関数。

### <a name="return-value"></a>戻り値

オーバーロードされたが *`value`* 存在する場合でも、によって参照されるオブジェクトまたは関数の実際のアドレス `operator&()` 。

### <a name="remarks"></a>Remarks

## <a name="align"></a><a name="align"></a> `align`

指定したサイズのストレージを、指定されたアラインメント仕様によって、指定されたストレージの最初の使用可能なアドレスに収めます。

```cpp
void* align(
    size_t alignment, // input
    size_t size,      // input
    void*& ptr,       // input/output
    size_t& space     // input/output
);
```

### <a name="parameters"></a>パラメーター

*`alignment`*\
試行するアラインメントの境界。

*`size`*\
アラインされたストレージのサイズ (バイト単位)。

*`ptr`*\
使用する利用可能な一連の記憶域プールの開始アドレス。 このパラメーターは出力パラメーターでもあり、アラインメントが成功した場合は新しい開始アドレスを格納するように設定されます。 が失敗した場合 `align()` 、このパラメーターは変更されません。

*`space`*\
アラインされた記憶域の作成に使用する `align()` で利用可能な合計領域。 このパラメーターは出力パラメーターでもあり、アラインされたストレージと関連するオーバーヘッドが差し引かれた後の記憶域バッファーに残されている調整された領域を格納します。

が失敗した場合 `align()` 、このパラメーターは変更されません。

### <a name="return-value"></a>戻り値

`NULL`要求されたアラインバッファーが使用可能な領域に収まりきらない場合はポインター。それ以外の場合はの新しい値 *`ptr`* 。

### <a name="remarks"></a>Remarks

変更された *`ptr`* パラメーターとパラメーターを使用すると、 *`space`* 同じバッファーでを繰り返し呼び出すことができ `align()` ます。また、との値が異なる場合も *`alignment`* *`size`* あります。 `align()` の使用方法の 1 つを次のコード スニペットに示します。

```cpp
#include <type_traits> // std::alignment_of()
#include <memory>
//...
char buffer[256]; // for simplicity
size_t alignment = std::alignment_of<int>::value;
void * ptr = buffer;
std::size_t space = sizeof(buffer); // Be sure this results in the true size of your buffer

while (std::align(alignment, sizeof(MyObj), ptr, space)) {
    // You now have storage the size of MyObj, starting at ptr, aligned on
    // int boundary. Use it here if you like, or save off the starting address
    // contained in ptr for later use.
    // ...
    // Last, move starting pointer and decrease available space before
    // the while loop restarts.
    ptr = reinterpret_cast<char*>(ptr) + sizeof(MyObj);
    space -= sizeof(MyObj);
}
// At this point, align() has returned a null pointer, signaling it is not
// possible to allow more aligned storage in this buffer.
```

## <a name="allocate_shared"></a><a name="allocate_shared"></a> `allocate_shared`

[`shared_ptr`](shared-ptr-class.md)指定されたアロケーターを使用して、指定された型に割り当てられ、構築されるオブジェクトに対してを作成します。 `shared_ptr` を返します。

```cpp
template <class T, class Allocator, class... Args>
shared_ptr<T> allocate_shared(
    Allocator alloc,
    Args&&... args);
```

### <a name="parameters"></a>パラメーター

*`alloc`*\
オブジェクトを作成するために使用されるアロケーター。

*`args`*\
オブジェクトになるゼロ個以上の引数。

### <a name="remarks"></a>Remarks

関数は、 `shared_ptr<T>` によって割り当てられて構築されたを指すポインターであるオブジェクトを作成し `T(args...)` *`alloc`* ます。

## <a name="atomic_compare_exchange_strong"></a><a name="atomic_compare_exchange_strong"></a> `atomic_compare_exchange_strong`

```cpp
template<class T>
bool atomic_compare_exchange_strong(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_weak"></a><a name="atomic_compare_exchange_weak"></a> `atomic_compare_exchange_weak`

```cpp
template<class T>
bool atomic_compare_exchange_weak(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_strong_explicit"></a><a name="atomic_compare_exchange_strong_explicit"></a> `atomic_compare_exchange_strong_explicit`

```cpp
template<class T>
bool atomic_compare_exchange_strong_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_compare_exchange_weak_explicit"></a><a name="atomic_compare_exchange_weak_explicit"></a> `atomic_compare_exchange_weak_explicit`

```cpp
template<class T>
bool atomic_compare_exchange_weak_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_exchange"></a><a name="atomic_exchange"></a> `atomic_exchange`

```cpp
template<class T>
shared_ptr<T> atomic_exchange(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_exchange_explicit"></a><a name="atomic_exchange_explicit"></a> `atomic_exchange_explicit`

```cpp
template<class T>
shared_ptr<T> atomic_exchange_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="atomic_is_lock_free"></a><a name="atomic_is_lock_free"></a> `atomic_is_lock_free`

```cpp
template<class T>
bool atomic_is_lock_free(
    const shared_ptr<T>* u);
```

## <a name="atomic_load"></a><a name="atomic_load"></a> `atomic_load`

```cpp
template<class T>
shared_ptr<T> atomic_load(
    const shared_ptr<T>* u);
```

## <a name="atomic_load_explicit"></a><a name="atomic_load_explicit"></a> `atomic_load_explicit`

```cpp
template<class T>
shared_ptr<T> atomic_load_explicit(
    const shared_ptr<T>* u,
    memory_order mo);
```

## <a name="atomic_store"></a><a name="atomic_store"></a> `atomic_store`

```cpp
template<class T>
void atomic_store(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_store_explicit"></a><a name="atomic_store_explicit"></a> `atomic_store_explicit`

```cpp
template<class T>
void atomic_store_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="const_pointer_cast"></a><a name="const_pointer_cast"></a> `const_pointer_cast`

定数をにキャスト [`shared_ptr`](shared-ptr-class.md) します。

```cpp
template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>パラメーター

*`T`*\
返される共有ポインターによって制御される型。

*`Other`*\
引数の共有ポインターによって制御される型。

*`sp`*\
引数の共有ポインター。

### <a name="remarks"></a>Remarks

`shared_ptr`が null ポインターを返す場合、テンプレート関数は空のオブジェクトを返します。それ以外の場合は、 `const_cast<T*>(sp.get())` `shared_ptr<T>` によって所有されているリソースを所有するオブジェクトを返し *`sp`* ます。 式 `const_cast<T*>(sp.get())` は有効な式である必要があります。

### <a name="example"></a>例

```cpp
// std__memory__const_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int);
    std::shared_ptr<const int> sp1 =
        std::const_pointer_cast<const int>(sp0);

    *sp0 = 3;
    std::cout << "sp1 == " << *sp1 << std::endl;

    return (0);
}
```

```Output
sp1 == 3
```

## <a name="declare_no_pointers"></a><a name="declare_no_pointers"></a> `declare_no_pointers`

ベース アドレス ポインターとブロック サイズで定義されたメモリ ブロック内の文字に追跡可能なポインターが含まれていないことを、ガベージ コレクターに通知します。

```cpp
void declare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>パラメーター

*`ptr`*\
追跡可能なポインターがもう含まれない最初の文字のアドレス。

*`size`*\
*`ptr`* 追跡可能なポインターを含まない、で開始されるブロックのサイズ。

### <a name="remarks"></a>Remarks

関数は、範囲内のアドレスに追跡可能なポインターが含まれていないことをガベージコレクターに通知 `[ptr, ptr + size)` します。 (割り当てられたストレージへのポインターは、到達可能な場合を除き、逆参照しないでください)。

## <a name="declare_reachable"></a><a name="declare_reachable"></a> `declare_reachable`

指定されたアドレスが、割り当てられたストレージのアドレスであり、そのストレージに到達可能であることをガベージ コレクションに通知します。

```cpp
void declare_reachable(
    void* ptr);
```

### <a name="parameters"></a>パラメーター

*`ptr`*\
到達可能な割り当て済みの有効なストレージ領域へのポインター。

### <a name="remarks"></a>Remarks

*`ptr`* が null でない場合、関数は、現在到達可能なガベージコレクターに通知し *`ptr`* ます。つまり、割り当てられた有効なストレージを指します。

## <a name="default_delete"></a><a name="default_delete"></a> `default_delete`

で割り当てられたオブジェクトを削除 **`operator new`** します。 での使用に適して [`unique_ptr`](unique-ptr-class.md) います。

```cpp
struct default_delete
{
    constexpr default_delete() noexcept = default;

    template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
    default_delete(const default_delete<Other>&) noexcept;

    void operator()(T* ptr) const noexcept;
};
```

### <a name="parameters"></a>パラメーター

*`ptr`*\
削除するオブジェクトへのポインター。

*`Other`*\
削除対象の配列内の要素の型。

### <a name="remarks"></a>Remarks

クラステンプレートでは、 **`operator new`** クラステンプレートでの使用に適した、で割り当てられたスカラーオブジェクトを削除する削除子を記述し `unique_ptr` ます。 明示的な特殊化 `default_delete<T[]>` もあります。

## <a name="destroy_at"></a><a name="destroy_at"></a> `destroy_at`

```cpp
template <class T>
void destroy_at(
    T* location);
```

`location->~T()` と同じ。

## <a name="destroy"></a><a name="destroy"></a> `destroy`

```cpp
template <class ForwardIterator>
void destroy(
    ForwardIterator first,
    ForwardIterator last);
```

次と同じ:

```cpp
for (; first != last; ++first)
    destroy_at(addressof(*first));
```

## <a name="destroy_n"></a><a name="destroy_n"></a> `destroy_n`

```cpp
template <class ForwardIterator, class Size>
ForwardIterator destroy_n(
    ForwardIterator first,
    Size count);
```

次と同じ:

```cpp
for (; count > 0; (void)++first, --count)
    destroy_at(addressof(*first));
return first;
```

## <a name="dynamic_pointer_cast"></a><a name="dynamic_pointer_cast"></a> `dynamic_pointer_cast`

に動的にキャスト [`shared_ptr`](shared-ptr-class.md) します。

```cpp
template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>パラメーター

*`T`*\
返される共有ポインターによって制御される型。

*`Other`*\
引数の共有ポインターによって制御される型。

*`sp`*\
引数の共有ポインター。

### <a name="remarks"></a>Remarks

`shared_ptr`が null ポインターを返す場合、テンプレート関数は空のオブジェクトを返します。それ以外の場合は、 `dynamic_cast<T*>(sp.get())` `shared_ptr<T>` によって所有されているリソースを所有するオブジェクトを返し *`sp`* ます。 式 `dynamic_cast<T*>(sp.get())` は有効な式である必要があります。

### <a name="example"></a>例

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::dynamic_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="get_deleter"></a><a name="get_deleter"></a> `get_deleter`

から削除子を取得し [`shared_ptr`](shared-ptr-class.md) ます。

```cpp
template <class Deleter, class T>
Deleter* get_deleter(
    const shared_ptr<T>& sp) noexcept;
```

### <a name="parameters"></a>パラメーター

*`Deleter`*\
削除子の型。

*`T`*\
共有ポインターによって制御される型。

*`sp`*\
共有ポインター。

### <a name="remarks"></a>Remarks

このテンプレート関数は、オブジェクトに属する型の削除子へのポインターを返し *`Deleter`* `shared_ptr` *`sp`* ます。 *`sp`* に削除子がない場合、または削除子が型でない場合 *`Deleter`* 、この関数は0を返します。

### <a name="example"></a>例

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct deleter
{
    void operator()(base *pb)
    {
        delete pb;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->value = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->value = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}
```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a><a name="get_pointer_safety"></a> `get_pointer_safety`

ガベージ コレクターが想定するポインターの安全性の種類を返します。

```cpp
pointer_safety get_pointer_safety() noexcept;
```

### <a name="remarks"></a>Remarks

関数は、自動ガベージコレクターが想定するポインターの安全性の種類を返します。

## <a name="get_temporary_buffer"></a><a name="get_temporary_buffer"></a> `get_temporary_buffer`

指定された数の要素を超えない要素のシーケンスの一時ストレージを割り当てます。

```cpp
template <class T>
pair<T *, ptrdiff_t> get_temporary_buffer(
    ptrdiff_t count);
```

### <a name="parameters"></a>パラメーター

*数*\
メモリの割り当て対象となる、必要な要素の最大数。

### <a name="return-value"></a>戻り値

最初のコンポーネントが割り当て済みのメモリへのポインターで、2 番目のコンポーネントがバッファーのサイズ指定である `pair`。これで、格納可能な要素の最大数が示されます。

### <a name="remarks"></a>Remarks

この関数はメモリを要求しますが、成功しない場合もあります。 バッファーが割り当てられなかった場合、関数は、2 番目のコンポーネントが 0 で、最初のコンポーネントが Null ポインターである pair を返します。

この関数は、一時的なメモリに対してのみ使用してください。

### <a name="example"></a>例

```cpp
// memory_get_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
        << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
        << "could store is given by: resultPair.second = "
        << resultPair.second << "." << endl;
}
```

```Output
The number of integers in the array is: 9.
The number of elements that the allocated memory
could store is given by: resultPair.second = 9.
```

## <a name="make_shared"></a><a name="make_shared"></a> `make_shared`

[`shared_ptr`](shared-ptr-class.md)既定のアロケーターを使用して0個以上の引数から構築された割り当て済みオブジェクトを指すを作成して返します。 指定された型のオブジェクトおよび `shared_ptr` の両方を割り当て構築することでオブジェクトの共有所有権を管理し、`shared_ptr` を返します。.

```cpp
template <class T, class... Args>
shared_ptr<T> make_shared(
    Args&&... args);
```

### <a name="parameters"></a>パラメーター

*`args`*\
0 個以上のコンス トラクター引数。 関数は、提供された引数に基づいてどのコンストラクターのオーバーロードを呼び出すかを推測します。

### <a name="remarks"></a>Remarks

オブジェクトを作成するための簡単で効率的な方法として `make_shared` を使用し、同時にオブジェクトへの共有アクセスを管理するために `shared_ptr` を使用します。 意味的には、これら 2 つのステートメントは同等です。

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

しかし、最初のステートメントで 2 つの割り当てが実行され、`shared_ptr` オブジェクトが正常に完了した後、`Example` の割り当てが失敗すると、名前のない `Example` オブジェクトがリークされます。 `make_shared` を使用するステートメントの方が、関数呼び出しが 1 つしか関係しないので簡単です。 ライブラリがオブジェクトとスマート ポインターの両方に対して単一の割り当てを行うことができるため効率的です。 この関数の方が高速でメモリの断片化が少なくなるため、1回の割り当てでは例外が発生する可能性はありません。 スマート ポインターでオブジェクトを参照したり参照カウントを更新したりするコードでは、局所性の改善によってパフォーマンスが向上します。

[`make_unique`](memory-functions.md#make_unique)オブジェクトへの共有アクセスが不要な場合は、を使用することを検討してください。 [`allocate_shared`](memory-functions.md#allocate_shared)オブジェクトのカスタムアロケーターを指定する必要がある場合は、を使用します。 オブジェクトにカスタム削除子が必要な場合、を使用することはできません。これは、 `make_shared` 削除子を引数として渡す方法がないためです。

次の例は、特定のコンストラクターのオーバーロードを呼び出して、型への共有ポインターを作成する方法を示しています。

### <a name="example"></a>例

```cpp
// stl_make_shared.cpp
// Compile by using: cl /W4 /EHsc stl_make_shared.cpp
#include <iostream>
#include <string>
#include <memory>
#include <vector>

class Song {
public:
    std::wstring title_;
    std::wstring artist_;

    Song(std::wstring title, std::wstring artist) : title_(title), artist_(artist) {}
    Song(std::wstring title) : title_(title), artist_(L"Unknown") {}
};

void CreateSharedPointers()
{
    // Okay, but less efficient to have separate allocations for
    // Song object and shared_ptr control block.
    auto song = new Song(L"Ode to Joy", L"Beethoven");
    std::shared_ptr<Song> sp0(song);

    // Use make_shared function when possible. Memory for control block
    // and Song object are allocated in the same call:
    auto sp1 = std::make_shared<Song>(L"Yesterday", L"The Beatles");
    auto sp2 = std::make_shared<Song>(L"Blackbird", L"The Beatles");

    // make_shared infers which constructor to use based on the arguments.
    auto sp3 = std::make_shared<Song>(L"Greensleeves");

    // The playlist vector makes copies of the shared_ptr pointers.
    std::vector<std::shared_ptr<Song>> playlist;
    playlist.push_back(sp0);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    playlist.push_back(sp3);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    for (auto&& sp : playlist)
    {
        std::wcout << L"Playing " << sp->title_ <<
            L" by " << sp->artist_ << L", use count: " <<
            sp.use_count() << std::endl;
    }
}

int main()
{
    CreateSharedPointers();
}
```

この例では、次の出力が生成されます: 

```Output
Playing Ode to Joy by Beethoven, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
Playing Greensleeves by Unknown, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
```

## <a name="make_unique"></a><a name="make_unique"></a> `make_unique`

指定された [`unique_ptr`](unique-ptr-class.md) 引数を使用して構築された、指定された型のオブジェクトに、を作成して返します。

```cpp
// make_unique<T>
template <class T, class... Args>
unique_ptr<T> make_unique(Args&&... args);

// make_unique<T[]>
template <class T>
unique_ptr<T> make_unique(size_t size);

// make_unique<T[N]> disallowed
template <class T, class... Args>
/* unspecified */ make_unique(Args&&...) = delete;
```

### <a name="parameters"></a>パラメーター

*`T`*\
`unique_ptr` が指すオブジェクトの型。

*`Args`*\
によって指定されたコンストラクター引数の型 *`args`* 。

*`args`*\
型のオブジェクトのコンストラクターに渡される引数 *`T`* 。

*`elements`*\
型の要素の配列 *`T`* 。

*`size`*\
新しい配列に領域を割り当てる要素の数。

### <a name="remarks"></a>Remarks

1つ目のオーバーロードは、単一のオブジェクトに使用されます。 2番目のオーバーロードが配列に対して呼び出されます。 3番目のオーバーロードは、型引数 () で配列のサイズを指定できないようにし `make_unique<T[N]>` ます。この構築は、現在の標準ではサポートされていません。 `make_unique` を使用して、配列への `unique_ptr` を作成する場合、配列要素を個別に初期化する必要があります。 このオーバーロードを使用するのではなく、を使用することをお勧めし [`std::vector`](vector-class.md) ます。

`make_unique` は、例外セーフを目的として慎重に実装されるため、`make_unique` コンストラクターを直接呼び出す代わりに、`unique_ptr` を使用することをお勧めします。

### <a name="example"></a>例

次の例は、`make_unique` を使用する方法を示しています。 その他の例については、「[方法: unique_ptr インスタンスを作成して使用する](../cpp/how-to-create-and-use-unique-ptr-instances.md)」を参照してください。

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

`unique_ptr` に関連してエラー C2280 が発生した場合、削除された関数であるコピー コンストラクターを呼び出そうとしたことが原因となっている可能性が高いです。

## <a name="owner_less"></a><a name="owner_less"></a> `owner_less`

共有ポインターとウィーク ポインターの所有権ベースの混合型比較を実行します。 **`true`** 左のパラメーターがメンバー関数によって右のパラメーターの前に並べられている場合は、を返し `owner_before` ます。

```cpp
template <class T>
    struct owner_less; // not defined

template <class T>
struct owner_less<shared_ptr<T>>
{
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;
};

template <class T>
struct owner_less<weak_ptr<T>>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;
};

template<> struct owner_less<void>
{
    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;
};
```

### <a name="parameters"></a>パラメーター

*`left`*\
共有またはウィーク ポインター。

*`right`*\
共有またはウィーク ポインター。

### <a name="remarks"></a>Remarks

クラステンプレートでは、すべてのメンバー演算子がを返すように定義されて `left.owner_before(right)` います。

## <a name="reinterpret_pointer_cast"></a><a name="reinterpret_pointer_cast"></a> `reinterpret_pointer_cast`

`shared_ptr`キャストを使用して、既存の共有ポインターから新しいを作成します。

```cpp
template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    const shared_ptr<U>& ptr) noexcept;

template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    shared_ptr<U>&& ptr) noexcept;
```

### <a name="parameters"></a>パラメーター

*`ptr`*\
への参照 `shared_ptr<U>` 。

### <a name="remarks"></a>Remarks

が空の場合は、 *`ptr`* 新しい `shared_ptr` も空になります。それ以外の場合は、との所有権が共有され *`ptr`* ます。 新しい共有ポインターは、を評価した結果です `reinterpret_cast<Y*>(ptr.get())` 。ここで、 `Y` は `typename std::shared_ptr<T>::element_type` です。 が整形式でない場合、動作は未定義です `reinterpret_cast<T*>((U*)nullptr)` 。

左辺値参照を受け取るテンプレート関数は、C++ 17 で新しく追加されたものです。 右辺値参照を受け取るテンプレート関数は、C++ 20 の新機能です。

## <a name="return_temporary_buffer"></a><a name="return_temporary_buffer"></a> `return_temporary_buffer`

`get_temporary_buffer` テンプレート関数を使用して割り当てられた一時メモリを解放します。

```cpp
template <class T>
void return_temporary_buffer(
    T* buffer);
```

### <a name="parameters"></a>パラメーター

*`buffer`*\
割り当てを解放するメモリへのポインター。

### <a name="remarks"></a>Remarks

この関数は、一時的なメモリに対してのみ使用してください。

### <a name="example"></a>例

```cpp
// memory_ret_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
         << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
         << " could store is given by: resultPair.second = "
         << resultPair.second << "." << endl;

    int* tempBuffer = resultPair.first;

    // Deallocates memory allocated with get_temporary_buffer
    return_temporary_buffer( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a><a name="static_pointer_cast"></a> `static_pointer_cast`

への静的キャスト [`shared_ptr`](shared-ptr-class.md) 。

```cpp
template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>パラメーター

*`T`*\
返される共有ポインターによって制御される型。

*`Other`*\
引数の共有ポインターによって制御される型。

*`sp`*\
引数の共有ポインター。

### <a name="remarks"></a>Remarks

が空のオブジェクトの場合、テンプレート関数は空のオブジェクトを返します `shared_ptr` 。それ以外の場合は、 *`sp`* `shared_ptr` `shared_ptr<T>` によって所有されているリソースを所有するオブジェクトを返し *`sp`* ます。 式 `static_cast<T*>(sp.get())` は有効な式である必要があります。

### <a name="example"></a>例

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::static_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="swap"></a><a name="swap"></a> `swap`

2つ [`shared_ptr`](shared-ptr-class.md) の [`unique_ptr`](unique-ptr-class.md) オブジェクト、オブジェクト、またはオブジェクトを交換 [`weak_ptr`](weak-ptr-class.md) します。

```cpp
template <class T>
void swap(
    shared_ptr<T>& left,
    shared_ptr<T>& right) noexcept;

template <class T, class Deleter>
void swap(
    unique_ptr<T, Deleter>& left,
    unique_ptr<T, Deleter>& right) noexcept;

template <class T>
void swap(
    weak_ptr<T>& left,
    weak_ptr<T>& right) noexcept;

```

### <a name="parameters"></a>パラメーター

*`T`*\
引数ポインターによって制御される型。

*`Deleter`*\
一意のポインター型の削除子。

*`left`*\
左のポインター。

*`right`*\
右ポインター。

### <a name="remarks"></a>Remarks

このテンプレート関数は、`left.swap(right)` を呼び出します。

### <a name="example"></a>例

```cpp
// std__memory__swap.cpp
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

## <a name="undeclare_no_pointers"></a><a name="undeclare_no_pointers"></a> `undeclare_no_pointers`

ベース アドレス ポインターとブロック サイズで定義されたメモリ ブロック内の文字が、追跡可能なポインターを含む可能性があることをガベージ コレクターに通知します。

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>パラメーター

*`ptr`*\
以前にを使用してマークされたメモリアドレスへのポインター [`declare_no_pointers`](#declare_no_pointers) 。

*`size`*\
メモリ範囲内のバイト数。 この値は、呼び出しで使用されている数値と同じである必要があり `declare_no_pointers` ます。

### <a name="remarks"></a>Remarks

関数は、アドレスの範囲に `[ptr, ptr + size)` 追跡可能なポインターが含まれている可能性があることをガベージコレクターに通知します。

## <a name="undeclare_reachable"></a><a name="undeclare_reachable"></a> `undeclare_reachable`

指定したメモリ位置の到達可能性の宣言を取り消します。

```cpp
template <class T>
T *undeclare_reachable(
    T* ptr);
```

### <a name="parameters"></a>パラメーター

*`ptr`*\
以前にを使用してマークされたメモリアドレスへのポインター [`declare_reachable`](#declare_reachable) 。

### <a name="remarks"></a>Remarks

*`ptr`* がでない場合 **`nullptr`** 、関数は、到達できなくなったガベージコレクターに通知し *`ptr`* ます。 と等しいを比較する、安全に派生したポインターを返し *`ptr`* ます。

## <a name="uninitialized_copy"></a><a name="uninitialized_copy"></a> `uninitialized_copy`

指定されたソース範囲にあるオブジェクトを、初期化されていないターゲット範囲にコピーします。

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>パラメーター

*`policy`*\
使用する実行ポリシー。

*`first`*\
ソース範囲内の先頭の要素を示す入力反復子。

*`last`*\
ソース範囲内の最後の要素を示す入力反復子。

*`dest`*\
ターゲット範囲内の先頭の要素を示す前方反復子。

### <a name="return-value"></a>戻り値

ソース範囲が空の場合を除き、ターゲット範囲を超える最初の位置を示す前方反復子。

### <a name="remarks"></a>Remarks

このアルゴリズムによって、オブジェクトの構築からメモリの割り当てを分離できます。

このテンプレート関数は、実質的に次の内容を実行します。

```cpp
while (first != last)
{
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

ただし、このコードが例外をスローする場合を除きます。 この場合は、構築されたオブジェクトはすべて破棄され、再度例外がスローされます。

実行ポリシーを使用したオーバーロードは、C++ 17 で新しく追加されたものです。

### <a name="example"></a>例

```cpp
// memory_uninit_copy.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    Integer(int x) : value(x) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    cout << "The initialized Array contains " << N << " elements: ";
    for (int i = 0; i < N; i++)
    {
        cout << " " << Array[i];
    }
    cout << endl;

    Integer* ArrayPtr = (Integer*)malloc(N * sizeof(int));
    Integer* LArrayPtr = uninitialized_copy(
        Array, Array + N, ArrayPtr);  // C4996

    cout << "Address of position after the last element in the array is: "
        << &Array[0] + N << endl;
    cout << "The iterator returned by uninitialized_copy addresses: "
        << (void*)LArrayPtr << endl;
    cout << "The address just beyond the last copied element is: "
        << (void*)(ArrayPtr + N) << endl;

    if ((&Array[0] + N) == (void*)LArrayPtr)
        cout << "The return value is an iterator "
        << "pointing just beyond the original array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the original array." << endl;

    if ((void*)LArrayPtr == (void*)(ArrayPtr + N))
        cout << "The return value is an iterator "
        << "pointing just beyond the copied array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the copied array." << endl;

    free(ArrayPtr);

    cout << "Note that the exact addresses returned will vary\n"
        << "with the memory allocation in individual computers."
        << endl;
}
```

## <a name="uninitialized_copy_n"></a><a name="uninitialized_copy_n"></a> `uninitialized_copy_n`

入力反復子から、指定した数の要素のコピーを作成します。 コピーは前方反復子に格納されます。

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>パラメーター

*`policy`*\
使用する実行ポリシー。

*`first`*\
コピーするオブジェクトを参照する入力反復子。

*`count`*\
オブジェクトをコピーする回数を指定する符号付きまたは符号なし整数型。

*`dest`*\
新しいコピー先を参照する前方反復子。

### <a name="return-value"></a>戻り値

ターゲットを超えた最初の位置を示す前方反復子。 ソース範囲が空の場合、反復子はをアドレス指定し *`first`* ます。

### <a name="remarks"></a>Remarks

このテンプレート関数は、次のコードを効果的に実行します。

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

ただし、このコードが例外をスローする場合を除きます。 この場合は、構築されたオブジェクトはすべて破棄され、再度例外がスローされます。

実行ポリシーを使用したオーバーロードは、C++ 17 で新しく追加されたものです。

## <a name="uninitialized_default_construct"></a><a name="uninitialized_default_construct"></a> `uninitialized_default_construct`

既定では、 `value_type` 指定された範囲内の反復子のオブジェクトを構築します。

```cpp
template <class ForwardIterator>
void uninitialized_default_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_default_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>パラメーター

*`policy`*\
使用する実行ポリシー。

*`first`*\
構築する範囲内の最初の要素を示す反復子。

*`last`*\
構築する範囲内の最後の要素の1つ後ろを指す反復子。

### <a name="remarks"></a>Remarks

実行ポリシーのないバージョンは、実質的に次のようになります。

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
```

例外がスローされた場合、以前に構築されたオブジェクトは、指定されていない順序で破棄されます。

実行ポリシーが指定されているバージョンは、同じ結果になりますが、指定したに従って実行され *`policy`* ます。

これらの関数は、C++ 17 で新しく追加されたものです。

## <a name="uninitialized_default_construct_n"></a><a name="uninitialized_default_construct_n"></a> `uninitialized_default_construct_n`

既定では、指定された位置から開始して、反復子の指定した数のオブジェクトを構築し `value_type` ます。

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>パラメーター

*`policy`*\
使用する実行ポリシー。

*`first`*\
構築するターゲット範囲内の最初の要素を示す反復子。

*`count`*\
構築するターゲット範囲内の要素の数。

### <a name="return-value"></a>戻り値

ソース範囲が空の場合を除き、ターゲット範囲を超える最初の位置を示す前方反復子。

### <a name="remarks"></a>Remarks

実行ポリシーのないバージョンは、実質的に次のようになります。

```cpp
for (; count>0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
return first;
```

例外がスローされた場合、以前に構築されたオブジェクトは、指定されていない順序で破棄されます。

実行ポリシーが指定されているバージョンは、同じ結果になりますが、指定したに従って実行され *`policy`* ます。

これらの関数は、C++ 17 で新しく追加されたものです。

## <a name="uninitialized_fill"></a><a name="uninitialized_fill"></a> `uninitialized_fill`

指定された値のオブジェクトを、初期化されていないコピー先の範囲にコピーします。

```cpp
template <class ForwardIterator, class T>
void uninitialized_fill(
    ForwardIterator first,
    ForwardIterator last,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class T>
void uninitialized_fill(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last,
    const T& value);
```

### <a name="parameters"></a>パラメーター

*`policy`*\
使用する実行ポリシー。

*`first`*\
初期化するターゲット範囲内の最初の要素を示す前方反復子。

*`last`*\
初期化するターゲット範囲内の最後の要素を示す前方反復子。

*`value`*\
ターゲット範囲を初期化するために使用される値。

### <a name="remarks"></a>Remarks

このアルゴリズムによって、オブジェクトの構築からメモリの割り当てを分離できます。

このテンプレート関数は、実質的に次の内容を実行します。

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (value);
```

ただし、このコードが例外をスローする場合を除きます。 この場合は、構築されたオブジェクトはすべて破棄され、再度例外がスローされます。

実行ポリシーを使用したオーバーロードは、C++ 17 で新しく追加されたものです。

### <a name="example"></a>例

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value ( 25 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill( Array, Array + N, value );
    cout << "The initialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        {
            cout << Array[ i ].get() << " ";
        }
    cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a><a name="uninitialized_fill_n"></a> `uninitialized_fill_n`

指定した値のオブジェクトを、初期化されていないターゲット範囲の指定した数の要素にコピーします。

```cpp
template <class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ForwardIterator first,
    Size count,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count,
    const T& value);
```

### <a name="parameters"></a>パラメーター

*`policy`*\
使用する実行ポリシー。

*`first`*\
初期化するターゲット範囲内の最初の要素を示す前方反復子。

*`count`*\
初期化する要素の数。

*`value`*\
ターゲット範囲を初期化するために使用する値。

### <a name="remarks"></a>Remarks

このアルゴリズムによって、オブジェクトの構築からメモリの割り当てを分離できます。

このテンプレート関数は、実質的に次の内容を実行します。

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(value);
return first;
```

ただし、このコードが例外をスローする場合を除きます。 この場合は、構築されたオブジェクトはすべて破棄され、再度例外がスローされます。

実行ポリシーを使用したオーバーロードは、C++ 17 で新しく追加されたものです。

### <a name="example"></a>例

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value( 60 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill_n( Array, N, value );  // C4996
    cout << "The uninitialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        cout << Array[ i ].get() <<  " ";
}
```

## <a name="uninitialized_move"></a><a name="uninitialized_move"></a> `uninitialized_move`

ソース範囲から初期化されていないターゲットメモリ領域に要素を移動します。

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>パラメーター

*`policy`*\
使用する実行ポリシー。

*`first`*\
移動するソース範囲内の最初の要素を示す入力反復子。

*`last`*\
移動するソース範囲内の最後の要素の1つ後ろのアドレスを示す入力反復子。

*`dest`*\
ターゲット範囲の先頭。

### <a name="remarks"></a>Remarks

実行ポリシーのないバージョンは、実質的に次のようになります。

```cpp
for (; first != last; (void)++dest, ++first)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return dest;
```

例外がスローされた場合、ソース範囲内の一部のオブジェクトが有効であるが指定されていない状態のままになることがあります。 以前に構築されたオブジェクトは、指定されていない順序で破棄されます。

実行ポリシーが指定されているバージョンは、同じ結果になりますが、指定したに従って実行され *`policy`* ます。

これらの関数は、C++ 17 で新しく追加されたものです。

## <a name="uninitialized_move_n"></a><a name="uninitialized_move_n"></a> `uninitialized_move_n`

指定した数の要素をソース範囲から初期化されていないターゲットメモリ領域に移動します。

```cpp
template <class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>パラメーター

*`policy`*\
使用する実行ポリシー。

*`first`*\
移動するソース範囲内の最初の要素を示す入力反復子。

*`count`*\
移動するソース範囲内の要素の数。

*`dest`*\
ターゲット範囲の先頭。

### <a name="remarks"></a>Remarks

実行ポリシーのないバージョンは、実質的に次のようになります。

```cpp
for (; count > 0; ++dest, (void) ++first, --count)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return {first, dest};
```

例外がスローされた場合、ソース範囲内の一部のオブジェクトが有効であるが指定されていない状態のままになることがあります。 以前に構築されたオブジェクトは、指定されていない順序で破棄されます。

実行ポリシーが指定されているバージョンは、同じ結果になりますが、指定したに従って実行され *`policy`* ます。

これらの関数は、C++ 17 で新しく追加されたものです。

## <a name="uninitialized_value_construct"></a><a name="uninitialized_value_construct"></a> `uninitialized_value_construct`

`value_type`指定された範囲内で、反復子の値の初期化によってオブジェクトを構築します。

```cpp
template <class ForwardIterator>
void uninitialized_value_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_value_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>パラメーター

*`policy`*\
使用する実行ポリシー。

*`first`*\
範囲から値への構造体の最初の要素を指す反復子。

*`last`*\
Range から value への構造体の最後の要素の1つ後ろを指す反復子。

### <a name="remarks"></a>Remarks

実行ポリシーのないバージョンは、実質的に次のようになります。

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
```

例外がスローされた場合、以前に構築されたオブジェクトは、指定されていない順序で破棄されます。

実行ポリシーが指定されているバージョンは、同じ結果になりますが、指定したに従って実行され *`policy`* ます。

メモリ割り当てエラーが発生した場合は、 `std::bad_alloc` 例外がスローされます。

これらの関数は、C++ 17 で新しく追加されたものです。

## <a name="uninitialized_value_construct_n"></a><a name="uninitialized_value_construct_n"></a> `uninitialized_value_construct_n`

指定した位置を開始位置として、反復子の `value_type` 値の初期化によって、指定した数のオブジェクトを構築します。

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>パラメーター

*`policy`*\
使用する実行ポリシー。

*`first`*\
構築するターゲット範囲内の最初の要素を示す反復子。

*`count`*\
構築するターゲット範囲内の要素の数。

### <a name="remarks"></a>Remarks

実行ポリシーのないバージョンは、実質的に次のようになります。

```cpp
for (; count > 0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
return first;
```

例外がスローされた場合、以前に構築されたオブジェクトは、指定されていない順序で破棄されます。

実行ポリシーが指定されているバージョンは、同じ結果になりますが、指定したに従って実行され *`policy`* ます。

メモリ割り当てエラーが発生した場合は、 `std::bad_alloc` 例外がスローされます。

これらの関数は、C++ 17 で新しく追加されたものです。

## <a name="uses_allocator_v"></a><a name="uses_allocator_v"></a> `uses_allocator_v`

テンプレートの値にアクセスするためのヘルパー変数テンプレート `uses_allocator` 。

```cpp
template <class T, class Alloc>
inline constexpr bool uses_allocator_v = uses_allocator<T, Alloc>::value;
```

## <a name="see-also"></a>関連項目

[`<memory>`](memory.md)
