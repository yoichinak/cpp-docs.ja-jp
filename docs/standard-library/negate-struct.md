---
description: 詳細については、「構造体の反転」をご覧ください。
title: negate 構造体
ms.date: 11/04/2016
f1_keywords:
- functional/std::negate
helpviewer_keywords:
- negate struct
- negate class
ms.assetid: 8a372686-786e-4262-b37c-ca13dc11e62f
ms.openlocfilehash: fccc583d38b797a856ed4e0915e5e0255bb9eaee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338245"
---
# <a name="negate-struct"></a>negate 構造体

引数に対して算術否定演算 (単項 `operator-`) を実行する定義済みの関数オブジェクト。

## <a name="syntax"></a>構文

```
template <class Type = void>
struct negate : public unary_function<Type, Type>
{
    Type operator()(const Type& Left) const;
};

// specialized transparent functor for unary operator-
template <>
struct negate<void>
{
  template <class Type>
  auto operator()(Type&& Left) const`
    -> decltype(-std::forward<Type>(Left));
};
```

### <a name="parameters"></a>パラメーター

*各種*\
指定または推論された型のオペランドを受け取る `operator-` をサポートする任意の型。

*左側*\
符号を反転されるオペランド。 特殊化されたテンプレートは、推論された型の *型* の左辺値および右辺値参照引数の完全転送を行います。

## <a name="return-value"></a>戻り値

`-Left` の結果。 特殊化されたテンプレートは、単項によって返される型を持つ結果を完全に転送します `operator-` 。

## <a name="example"></a>例

```cpp
// functional_negate.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main( )
{
   vector <int> v1, v2 ( 8 );
   vector <int>::iterator Iter1, Iter2;

   int i;
   for ( i = -2 ; i <= 5 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   cout << "The vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // Finding the element-wise negatives of the vector v1
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), negate<int>( ) );

   cout << "The negated elements of the vector = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;
}
```

```Output
The vector v1 = ( -10 -5 0 5 10 15 20 25 )
The negated elements of the vector = ( 10 5 0 -5 -10 -15 -20 -25 )
```
