---
description: '詳細情報: less 構造体'
title: less 構造体
ms.date: 11/04/2016
f1_keywords:
- functional/std::less
helpviewer_keywords:
- less struct
- less function
ms.assetid: 39349da3-11cd-4774-b2cc-b46af5aae5d7
ms.openlocfilehash: b80789f2d2f2c8d1267450a39c39317af1da9244
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312879"
---
# <a name="less-struct"></a>less 構造体

引数に対して "より小さい" 演算 (`operator<`) を実行する二項述語。

## <a name="syntax"></a>構文

```cpp
template <class Type = void>
struct less : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator<
template <>
struct less<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) <std::forward<U>(Right));
};
```

### <a name="parameters"></a>パラメーター

*型*、 *T*、 *U*\
指定または推論された型のオペランドを受け取る `operator<` をサポートする任意の型。

*左側*\
より小さい演算の左オペランド。 非特殊テンプレートは、type *型* の左辺値参照引数を受け取ります。 特殊化されたテンプレートは、推論された型 *T* の左辺値および右辺値参照引数の完全転送を行います。

*そうです*\
より小さい演算の右オペランド。 非特殊テンプレートは、type *型* の左辺値参照引数を受け取ります。 特殊化されたテンプレートは、推論された型 *U* の左辺値および右辺値参照引数の完全転送を行います。

## <a name="return-value"></a>戻り値

`Left < Right` の結果。 特殊化されたテンプレートは、結果の完全転送を行います。結果には `operator<` によって返された型が含まれます。

## <a name="remarks"></a>解説

二項述語> は、型 `less` < `Type` の要素値のセットの厳密弱順序を等価クラスに提供します。これは、この型が、順序付けされた標準の数学的要件を満たす場合に限ります。 任意のポインター型に対する特殊化によって、要素の完全な順序付けが生成されます。この場合、一意の値を持つすべての要素が、相互の値に基づいて並べ替えられます。

## <a name="example"></a>例

```cpp
// functional_less.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

struct MyStruct {
   MyStruct(int i) : m_i(i){}

   bool operator < (const MyStruct & rhs) const {
      return m_i < rhs.m_i;
   }

   int m_i;
};

int main() {
   using namespace std;
   vector <MyStruct> v1;
   vector <MyStruct>::iterator Iter1;
   vector <MyStruct>::reverse_iterator rIter1;

   int i;
   for ( i = 0 ; i < 7 ; i++ )
       v1.push_back( MyStruct(rand()));

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )
cout << Iter1->m_i << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   sort( v1.begin( ), v1.end( ), less<MyStruct>());

   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )
cout << Iter1->m_i << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (41 18467 6334 26500 19169 15724 11478)
Sorted vector v1 = (41 6334 11478 15724 18467 19169 26500)
```
