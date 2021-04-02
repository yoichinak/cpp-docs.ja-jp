---
title: basic_string クラス
description: 標準 C++ 文字列クラスの API リファレンス `basic_string` です。
ms.date: 01/15/2021
f1_keywords:
- xstring/std::basic_string
- xstring/std::basic_string::allocator_type
- xstring/std::basic_string::const_iterator
- xstring/std::basic_string::const_pointer
- xstring/std::basic_string::const_reference
- xstring/std::basic_string::const_reverse_iterator
- xstring/std::basic_string::difference_type
- xstring/std::basic_string::iterator
- xstring/std::basic_string::npos
- xstring/std::basic_string::pointer
- xstring/std::basic_string::reference
- xstring/std::basic_string::reverse_iterator
- xstring/std::basic_string::size_type
- xstring/std::basic_string::traits_type
- xstring/std::basic_string::value_type
- xstring/std::basic_string::append
- xstring/std::basic_string::assign
- xstring/std::basic_string::at
- xstring/std::basic_string::back
- xstring/std::basic_string::begin
- xstring/std::basic_string::c_str
- xstring/std::basic_string::capacity
- xstring/std::basic_string::cbegin
- xstring/std::basic_string::cend
- xstring/std::basic_string::clear
- xstring/std::basic_string::compare
- xstring/std::basic_string::copy
- xstring/std::basic_string::crbegin
- xstring/std::basic_string::crend
- xstring/std::basic_string::_Copy_s
- xstring/std::basic_string::data
- xstring/std::basic_string::empty
- xstring/std::basic_string::end
- xstring/std::basic_string::erase
- xstring/std::basic_string::find
- xstring/std::basic_string::find_first_not_of
- xstring/std::basic_string::find_first_of
- xstring/std::basic_string::find_last_not_of
- xstring/std::basic_string::find_last_of
- xstring/std::basic_string::front
- xstring/std::basic_string::get_allocator
- xstring/std::basic_string::insert
- xstring/std::basic_string::length
- xstring/std::basic_string::max_size
- xstring/std::basic_string::pop_back
- xstring/std::basic_string::push_back
- xstring/std::basic_string::rbegin
- xstring/std::basic_string::rend
- xstring/std::basic_string::replace
- xstring/std::basic_string::reserve
- xstring/std::basic_string::resize
- xstring/std::basic_string::rfind
- xstring/std::basic_string::shrink_to_fit
- xstring/std::basic_string::size
- xstring/std::basic_string::substr
- xstring/std::basic_string::ends_with
- xstring/std::basic_string::starts_with
- xstring/std::basic_string::swap
- xstring/std::literals::string_literals
- std::literals::string_literals
- string_literals
- xstring/std::literals::string_literals::operator "s
- std::literals::string_literals::operator s
helpviewer_keywords:
- std::basic_string [C++]
- std::basic_string [C++], allocator_type
- std::basic_string [C++], const_iterator
- std::basic_string [C++], const_pointer
- std::basic_string [C++], const_reference
- std::basic_string [C++], const_reverse_iterator
- std::basic_string [C++], difference_type
- std::basic_string [C++], iterator
- std::basic_string [C++], npos
- std::basic_string [C++], pointer
- std::basic_string [C++], reference
- std::basic_string [C++], reverse_iterator
- std::basic_string [C++], size_type
- std::basic_string [C++], traits_type
- std::basic_string [C++], value_type
- std::basic_string [C++], append
- std::basic_string [C++], assign
- std::basic_string [C++], at
- std::basic_string [C++], back
- std::basic_string [C++], begin
- std::basic_string [C++], c_str
- std::basic_string [C++], capacity
- std::basic_string [C++], cbegin
- std::basic_string [C++], cend
- std::basic_string [C++], clear
- std::basic_string [C++], compare
- std::basic_string [C++], copy
- std::basic_string [C++], crbegin
- std::basic_string [C++], crend
- std::basic_string [C++], _Copy_s
- std::basic_string [C++], data
- std::basic_string [C++], empty
- std::basic_string [C++], end
- std::basic_string [C++], erase
- std::basic_string [C++], find
- std::basic_string [C++], find_first_not_of
- std::basic_string [C++], find_first_of
- std::basic_string [C++], find_last_not_of
- std::basic_string [C++], find_last_of
- std::basic_string [C++], front
- std::basic_string [C++], get_allocator
- std::basic_string [C++], insert
- std::basic_string [C++], length
- std::basic_string [C++], max_size
- std::basic_string [C++], pop_back
- std::basic_string [C++], push_back
- std::basic_string [C++], rbegin
- std::basic_string [C++], rend
- std::basic_string [C++], replace
- std::basic_string [C++], reserve
- std::basic_string [C++], resize
- std::basic_string [C++], rfind
- std::basic_string [C++], shrink_to_fit
- std::basic_string [C++], size
- std::basic_string [C++], starts_with
- std::basic_string [C++], ends_with
- std::basic_string [C++], substr
- std::basic_string [C++], swap
ms.openlocfilehash: d4990b58e0f71d095f97435ad8449ade3fa240d7
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099558"
---
# <a name="basic_string-class"></a>`basic_string` クラス

型のオブジェクトによって制御されるシーケンスは `basic_string` 標準 C++ 文字列クラスであり、通常は文字列と呼ばれますが、C++ 標準ライブラリ全体で使用される、null で終わる C スタイルの文字列と混同しないようにしてください。 標準 C++ 文字列は、比較演算子、連結演算、反復子、C++ 標準ライブラリアルゴリズム、クラスアロケーターによって管理されるメモリを使用したコピーと割り当てなど、通常の型として文字列を使用できるようにするコンテナーです。 標準 C++ 文字列を null で終わる C スタイルの文字列に変換する必要がある場合は、メンバーを使用し [`basic_string::c_str`](#c_str) ます。

## <a name="syntax"></a>構文

```cpp
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_string;
```

### <a name="parameters"></a>パラメーター

*`CharType`*\
文字列に格納される単一文字のデータ型。 C++ 標準ライブラリでは、このクラステンプレートの特殊化が提供されて [`string`](../standard-library/string-typedefs.md#string) `char` [`wstring`](../standard-library/string-typedefs.md#wstring) `wchar_t` [`u16string`](../standard-library/string-typedefs.md#u16string) `char16_t` [`u32string`](../standard-library/string-typedefs.md#u32string) `char32_t` います。また、の場合は型、の場合は、の場合は、の場合は型定義が使用されます。

*`Traits`*\
Basic_string 特殊化の要素のさまざまな重要なプロパティ `CharType` は、クラスによって記述され `Traits` ます。 既定値は `char_traits`<`CharType`> です。

*`Allocator`*\
メモリの文字列の割り当てと解放に関する詳細をカプセル化する、格納されたアロケーター オブジェクトを表す型。 既定値は `allocator<CharType>` です。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[`basic_string`](#basic_string)|空または特定の文字によって初期化される文字列、または他の文字列オブジェクトまたは C 文字列の全体または一部のコピーである文字列を作成します。|

### <a name="typedefs"></a>Typedefs

|型名|説明|
|-|-|
|[`allocator_type`](#allocator_type)|文字列オブジェクトの `allocator` クラス型を表す型。|
|[`const_iterator`](#const_iterator)|文字列内の `const` 要素にアクセスし、読み取ることができるランダム アクセス反復子を提供する型。|
|[`const_pointer`](#const_pointer)|文字列内の `const` 要素へのポインターを提供する型。|
|[`const_reference`](#const_reference)|読み取りと `const` 操作の実行のために、文字列に格納された `const` 要素への参照を提供する型。|
|[`const_reverse_iterator`](#const_reverse_iterator)|文字列内の任意の `const` 要素を読み取ることができるランダム アクセス反復子を提供する型。|
|[`difference_type`](#difference_type)|同じ文字列内の要素を参照する 2 反復子の違いを提供する型。|
|[`iterator`](#iterator)|文字列内の任意の要素を読み取り、または変更できるランダム アクセス反復子を提供する型。|
|[`npos`](#npos)|検索関数でエラーが発生した場合に "見つかりません" または "すべての残りの文字" を示す-1 に初期化された符号なし整数値。|
|[`pointer`](#pointer)|文字列または文字アレイ内の文字要素へのポインターを提供する型。|
|[`reference`](#reference)|文字列に格納されている要素への参照を提供する型。|
|[`reverse_iterator`](#reverse_iterator)|反転文字列内の要素を読み取り、または変更できるランダム アクセス反復子を提供する型。|
|[`size_type`](#size_type)|文字列の要素の数の符号なし整数型。|
|[`traits_type`](#traits_type)|文字列に格納されている要素の文字の特徴の型。|
|[`value_type`](#value_type)|文字列に格納された文字の型を表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[`append`](#append)|文字列の末尾に文字を追加します。|
|[`assign`](#assign)|文字列の内容に新しい文字の値を割り当てます。|
|[`at`](#at)|文字列内の指定した位置にある要素への参照を返します。|
|[`back`](#back)||
|[`begin`](#begin)|文字列の 1 つ目の要素を示す反復子を返します。|
|[`c_str`](#c_str)|C スタイルの null で終わる文字列として、文字列の内容を変換します。|
|[`capacity`](#capacity)|文字列のメモリ割り当てを増やさずに文字列に格納できる要素の最大数を返します。|
|[`cbegin`](#cbegin)|文字列の 1 つ目の要素を示す定数反復子を返します。|
|[`cend`](#cend)|文字列内の最後の要素の次の場所を指す定数反復子を返します。|
|[`clear`](#clear)|文字列のすべての要素を消去します。|
|[`compare`](#compare)|2 つの文字列が等しいかどうか、または一方が辞書式に他方よりも小さいかどうかを判断するために、特定の文字列を含む文字列を比較します。|
|[`copy`](#copy)|コピー元の文字列のインデックス位置からターゲットの文字配列に最大で指定された文字数をコピーします。 非推奨になりました。 代わりにを使用 [`basic_string::_Copy_s`](#copy_s) してください。|
|[`crbegin`](#crbegin)|反転文字列内の最初の要素を示す定数反復子を返します。|
|[`crend`](#crend)|反転文字列内の最後の要素の次の場所を指す定数反復子を返します。|
|[`_Copy_s`](#copy_s)|コピー元の文字列のインデックス位置からターゲットの文字配列に最大で指定された文字数をコピーします。|
|[`data`](#data)|文字列の内容を文字配列に変換します。|
|[`empty`](#empty)|文字列に文字が含まれているかどうかをテストします。|
|[`end`](#end)|文字列内の最後の要素の次の場所を指す反復子を返します。|
|[`ends_with`](#ends_with)<sup>C++ 20</sup>|文字列が指定したサフィックスで終わるかどうかを確認します。|
|[`erase`](#erase)|指定した位置から文字列の要素または要素範囲を削除します。|
|[`find`](#find)|指定された文字シーケンスに一致する部分文字列の最初の出現を文字列で前方に検索します。|
|[`find_first_not_of`](#find_first_not_of)|指定した文字列の要素ではない最初の文字を文字列で検索します。|
|[`find_first_of`](#find_first_of)|指定された文字列の要素と一致する最初の文字を文字列で検索します。|
|[`find_last_not_of`](#find_last_not_of)|指定した文字列の要素ではない最後の文字を文字列で検索します。|
|[`find_last_of`](#find_last_of)|指定された文字列の要素である最後の文字を文字列で検索します。|
|[`front`](#front)|文字列内の最初の要素への参照を返します。|
|[`get_allocator`](#get_allocator)|文字列の構築に使用される `allocator` オブジェクトのコピーを返します。|
|[`insert`](#insert)|要素、複数の要素、または要素の範囲を、指定した位置にある文字列に挿入します。|
|[`length`](#length)|文字列内の現在の要素数を返します。|
|[`max_size`](#max_size)|文字列が含むことができる最大文字数を返します。|
|[`pop_back`](#pop_back)|文字列の最後の要素を消去します。|
|[`push_back`](#push_back)|文字列の末尾に要素を追加します。|
|[`rbegin`](#rbegin)|反転文字列の 1 つ目の要素への反復子を返します。|
|[`rend`](#rend)|反転文字列内の最後の要素の先を示す反復子を返します。|
|[`replace`](#replace)|指定された場所の文字列の要素を指定された文字、または他の範囲、文字列、または C 文字列からコピーされた文字で置き換えます。|
|[`reserve`](#reserve)|文字列のキャパシティを少なくとも指定した数に設定します。|
|[`resize`](#resize)|要素を必要に応じて追加または削除して、文字列の新しいサイズを指定します。|
|[`rfind`](#rfind)|指定された文字シーケンスに一致する部分文字列の最初の出現を文字列で後方に検索します。|
|[`shrink_to_fit`](#shrink_to_fit)|文字列の余分なキャパシティを破棄します。|
|[`size`](#size)|文字列内の現在の要素数を返します。|
|[`starts_with`](#starts_with)<sup>C++ 20</sup>|文字列が指定したプレフィックスで始まるかどうかを確認します。|
|[`substr`](#substr)|指定された位置から始まる文字列から最大でいくつかの文字の部分文字列をコピーします。|
|[`swap`](#swap)|2 つの文字列の内容を交換します。|

### <a name="operators"></a>オペレーター

|演算子|説明|
|-|-|
|[`operator+=`](#op_add_eq)|文字列に文字を追加します。|
|[`operator=`](#op_eq)|文字列の内容に新しい文字の値を割り当てます。|
|[`operator`&#91;&#93;](#op_at)|文字列に指定したインデックスのある文字への参照を提供します。|

### <a name="literals"></a>リテラル

を定義するヘッダーは、 `basic_string` 次の [ユーザー定義リテラル](../cpp/user-defined-literals-cpp.md)も定義します。このリテラルは、入力パラメーターから指定された型の文字列を作成します。

| 宣言 | 説明 |
|--|--|
| `inline string operator"" s(const char* str, size_t len)` | 戻り値: `string(str, len)` |
| `inline string operator"" s(const wchar_t* str, size_t len)` | 戻り値: `wstring(str, len)` |
| `inline basic_string<char8_t> operator"" s(const char8_t* str, size_t len)` | 戻り値: `basic_string<char8_t>(str, len)` |
| `inline u16string operator"" s(const char16_t* str, size_t len)` | 戻り値: `u16string(str, len)` |
| `inline u32string operator"" s(const char32_t* str, size_t len)` | 戻り値: `u32string(str, len)` |

## <a name="remarks"></a>解説

関数は、要素よりも長いシーケンスを生成するように要求された場合 [`max_size`](#max_size) 、型のオブジェクトをスローして長さエラーを報告し [`length_error`](../standard-library/length-error-class.md) ます。

被制御シーケンスの要素を指定する参照、ポインター、および反復子は、被制御シーケンスを変更する関数の呼び出しの後、または非メンバー関数への最初の呼び出しの後に無効になることがあり `const` ます。

## <a name="requirements"></a>必要条件

**ヘッダー:**\<string>

**名前空間:** std

## <a name="basic_stringallocator_type"></a><a name="allocator_type"></a> `basic_string::allocator_type`

文字列オブジェクトの allocator クラスを表す型。

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>解説

この型は、テンプレート パラメーター `Allocator` のシノニムです。

### <a name="example"></a>例

```cpp
// basic_string_allocator_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   string s1;
   basic_string <char>::allocator_type xchar = s1.get_allocator( );
   // You can now call functions on the allocator class xchar used by s1
}
```

## <a name="basic_stringappend"></a><a name="append"></a> `basic_string::append`

文字列の末尾に文字を追加します。

```cpp
basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& append(
    size_type count,
    value_type char_value);

template <class InputIterator>
basic_string<CharType, Traits, Allocator>& append(
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& append(
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& append(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>パラメーター

*`ptr`*\
追加される C 文字列。

*`str`*\
文字が追加される文字列。

*`offset`*\
追加する文字の元の文字列の一部のインデックス。

*`count`*\
ソース文字列から追加される最大文字数。

*`char_value`*\
追加される文字値。

*`first`*\
追加される範囲内の先頭の要素の位置を示す入力反復子。

*`last`*\
`const_pointer` `const_iterator` 追加される範囲内の最後の要素の次の位置を示す入力反復子、、または。

### <a name="return-value"></a>戻り値

このメンバー関数によって渡された文字が付加される文字列オブジェクトへの参照。

### <a name="remarks"></a>解説

文字は、 [`operator+=`](#op_add_eq) またはメンバー関数またはを使用して文字列に追加でき `append` [`push_back`](#push_back) ます。 `operator+=` 1つの引数の値を追加します。複数引数のメンバー関数では、 `append` 文字列の特定の部分を追加することを許可します。

### <a name="example"></a>例

```cpp
// basic_string_append.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // appending a C-string to a string
   string str1a ( "Hello " );
   cout << "The original string str1 is: " << str1a << endl;
   const char *cstr1a = "Out There ";
   cout << "The C-string cstr1a is: " << cstr1a << endl;
   str1a.append ( cstr1a );
   cout << "Appending the C-string cstr1a to string str1 gives: "
        << str1a << "." << endl << endl;

   // The second member function
   // appending part of a C-string to a string
   string str1b ( "Hello " );
   cout << "The string str1b is: " << str1b << endl;
   const char *cstr1b = "Out There ";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b.append ( cstr1b , 3 );
   cout << "Appending the 1st part of the C-string cstr1b "
        << "to string str1 gives: " << str1b << "."
        << endl << endl;

   // The third member function
   // appending part of one string to another
   string str1c ( "Hello " ), str2c ( "Wide World " );
   cout << "The string str2c is: " << str2c << endl;
   str1c.append ( str2c , 5 , 5 );
   cout << "The appended string str1 is: "
        << str1c << "." << endl << endl;

   // The fourth member function
   // appending one string to another in two ways,
   // comparing append and operator [ ]
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World " );
   cout << "The  string str2d is: " << str2d << endl;
   str1d.append ( str2d );
   cout << "The appended string str1d is: "
        << str1d << "." << endl;
   str1d += str3d;
   cout << "The doubly appended strig str1 is: "
        << str1d << "." << endl << endl;

   // The fifth member function
   // appending characters to a string
   string str1e ( "Hello " );
   str1e.append ( 4 , '!' );
   cout << "The string str1 appended with exclamations is: "
        << str1e << endl << endl;

   // The sixth member function
   // appending a range of one string to another
   string str1f ( "Hello " ), str2f ( "Wide World " );
   cout << "The string str2f is: " << str2f << endl;
   str1f.append ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );
   cout << "The appended string str1 is: "
        << str1f << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello
The C-string cstr1a is: Out There
Appending the C-string cstr1a to string str1 gives: Hello Out There .

The string str1b is: Hello
The C-string cstr1b is: Out There
Appending the 1st part of the C-string cstr1b to string str1 gives: Hello Out.

The string str2c is: Wide World
The appended string str1 is: Hello World.

The  string str2d is: Wide
The appended string str1d is: Hello Wide .
The doubly appended strig str1 is: Hello Wide World .

The string str1 appended with exclamations is: Hello !!!!

The string str2f is: Wide World
The appended string str1 is: Hello World.
```

## <a name="basic_stringassign"></a><a name="assign"></a> `basic_string::assign`

文字列の内容に新しい文字の値を割り当てます。

```cpp
basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type off,
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& assign(
    size_type count,
    value_type char_value);

template <class InIt>
basic_string<CharType, Traits, Allocator>& assign(
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& assign(
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& assign(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>パラメーター

*`ptr`*\
対象の文字列に割り当てられる C 文字列の文字を指すポインター。

*`count`*\
ソース文字列から割り当てられる文字数。

*`str`*\
対象の文字列に割り当てられる文字のソース文字列。

*`char_value`*\
割り当てられる文字値。

*`first`*\
ターゲット範囲に割り当てられるソース文字列の範囲の最初の文字の位置を示す、入力反復子、const_pointer、または const_iterator。

*`last`*\
ターゲット範囲に割り当てられるソース文字列の範囲の最後の文字の次の文字の位置を示す、入力反復子、const_pointer、または const_iterator。

*`off`*\
割り当てられる新しい文字の開始位置。

### <a name="return-value"></a>戻り値

このメンバー関数によって新しい文字が割り当てられる文字列オブジェクトへの参照。

### <a name="remarks"></a>解説

文字列には、新しい文字値を割り当てることができます。 新しい値には、文字列および C 文字列または単一の文字を指定できます。 [`operator=`](#op_eq)新しい値を1つのパラメーターで記述できる場合はを使用できます。それ以外の場合は、複数のパラメーターを持つメンバー関数を使用して、 `assign` 対象の文字列に割り当てる文字列の部分を指定できます。

### <a name="example"></a>例

```cpp
// basic_string_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning the
   // characters of a C-string to a string
   string str1a;
   const char *cstr1a = "Out There";
   cout << "The C-string cstr1a is: " << cstr1a <<  "." << endl;
   str1a.assign ( cstr1a );
   cout << "Assigning the C-string cstr1a to string str1 gives: "
        << str1a << "." << endl << endl;

   // The second member function assigning a specific
   // number of the of characters a C-string to a string
   string  str1b;
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b.assign ( cstr1b , 3 );
   cout << "Assigning the 1st part of the C-string cstr1b "
        << "to string str1 gives: " << str1b << "."
        << endl << endl;

   // The third member function assigning a specific number
   // of the characters from one string to another string
   string str1c ( "Hello " ), str2c ( "Wide World " );
   cout << "The string str2c is: " << str2c << endl;
   str1c.assign ( str2c , 5 , 5 );
   cout << "The newly assigned string str1 is: "
        << str1c << "." << endl << endl;

   // The fourth member function assigning the characters
   // from one string to another string in two equivalent
   // ways, comparing the assign and operator =
   string str1d ( "Hello" ), str2d ( "Wide" ), str3d ( "World" );
   cout << "The original string str1 is: " << str1d << "." << endl;
   cout << "The string str2d is: " << str2d << endl;
   str1d.assign ( str2d );
   cout << "The string str1 newly assigned with string str2d is: "
        << str1d << "." << endl;
   cout << "The string str3d is: " << str3d << "." << endl;
   str1d = str3d;
   cout << "The string str1 reassigned with string str3d is: "
        << str1d << "." << endl << endl;

   // The fifth member function assigning a specific
   // number of characters of a certain value to a string
   string str1e ( "Hello " );
   str1e.assign ( 4 , '!' );
   cout << "The string str1 assigned with eclamations is: "
        << str1e << endl << endl;

   // The sixth member function assigning the value from
   // the range of one string to another string
   string str1f ( "Hello " ), str2f ( "Wide World " );
   cout << "The string str2f is: " << str2f << endl;
   str1f.assign ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );
   cout << "The string str1 assigned a range of string str2f is: "
        << str1f << "." << endl << endl;
}
```

```Output
The C-string cstr1a is: Out There.
Assigning the C-string cstr1a to string str1 gives: Out There.

The C-string cstr1b is: Out There
Assigning the 1st part of the C-string cstr1b to string str1 gives: Out.

The string str2c is: Wide World
The newly assigned string str1 is: World.

The original string str1 is: Hello.
The string str2d is: Wide
The string str1 newly assigned with string str2d is: Wide.
The string str3d is: World.
The string str1 reassigned with string str3d is: World.

The string str1 assigned with eclamations is: !!!!

The string str2f is: Wide World
The string str1 assigned a range of string str2f is: World.
```

## <a name="basic_stringat"></a><a name="at"></a> `basic_string::at`

文字列に指定したインデックスのある文字への参照を提供します。

```cpp
const_reference at(size_type offset) const;

reference at(size_type offset);
```

### <a name="parameters"></a>パラメーター

*`offset`*\
参照される要素の位置のインデックス。

### <a name="return-value"></a>戻り値

パラメーターのインデックスで指定した位置の文字列の文字への参照。

### <a name="remarks"></a>解説

文字列の最初の要素は0のインデックスを持ち、次の要素は正の整数で連続してインデックスが付けられます。これにより、長さ *n* の文字列には、n *-* 1 という数値でインデックス付けされた *n* 番目の要素が含まれるようになります。

メンバー [ `operator`&#91;&#93;](#op_at)は、 `at` 文字列の要素に対する読み取りおよび書き込みアクセスを提供するメンバー関数よりも高速です。

メンバーは、 `operator[]` パラメーターとして渡されたインデックスが有効であるかどうかを確認しませんが、メンバー関数は、有効でない `at` 場合に使用する必要があります。 無効なインデックスです。これは、0または文字列のサイズ以上のインデックスではなく、 `at` [ `out_of_range` クラス](../standard-library/out-of-range-class.md)の例外をスローします。 無効なインデックスが `operator[]` に渡されると、未定義の動作が発生しますが、文字列の長さと等しいインデックスは、const 文字列の有効なインデックスで、このインデックスが渡されると演算子は null 文字を返します。

返される参照は、文字列の再割り当てまたは非文字列の変更によって無効にされる場合があり `const` ます。

### <a name="example"></a>例

```cpp
// basic_string_at.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );
   const string  cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );
   cout << "The original string str1 is: " << str1 << endl;
   cout << "The original string str2 is: " << str2 << endl;

   // Element access to the non const strings
   basic_string <char>::reference refStr1 = str1 [6];
   basic_string <char>::reference refStr2 = str2.at ( 3 );

   cout << "The character with an index of 6 in string str1 is: "
        << refStr1 << "." << endl;
   cout << "The character with an index of 3 in string str2 is: "
        << refStr2 << "." << endl;

   // Element access to the const strings
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );

   if ( crefStr1 == '\0' )
      cout << "The null character is returned as a valid reference."
           << endl;
   else
      cout << "The null character is not returned." << endl;
   cout << "The character with index 8 in the const string cstr2 is: "
        << crefStr2 << "." << endl;
}
```

## <a name="basic_stringback"></a><a name="back"></a> `basic_string::back`

文字列の最後の要素への参照を返します。

```cpp
const_reference back() const;

reference back();
```

### <a name="return-value"></a>戻り値

文字列の最後の要素 (空以外でなければなりません) への参照。

### <a name="remarks"></a>解説

## <a name="basic_stringbasic_string"></a><a name="basic_string"></a> `basic_string::basic_string`

特定の文字によって初期化された空の文字列を作成します。または、他の文字列オブジェクトか C スタイル (null で終わる) 文字列の全体または一部のコピーである文字列を作成します。

```cpp
basic_string();

explicit basic_string(
    const allocator_type& alloc_type);

basic_string(
    const basic_string& right);

basic_string(
    basic_string&& right);

basic_string(
    const basic_string& right,
    size_type right_offset,
    size_type count = npos);

basic_string(
    const basic_string& right,
    size_type right_offset,
    size_type count,
    const allocator_type& alloc_type);

basic_string(
    const value_type* ptr,
    size_type count);

basic_string(
    const value_type* ptr,
    size_type count,
    const allocator_type& alloc_type);

basic_string(
    const value_type* ptr);

basic_string(
    const value_type* ptr,
    const allocator_type& alloc_type);

basic_string(
    size_type count,
    value_type char_value);

basic_string(
    size_type count,
    value_type char_value,
    const allocator_type& alloc_type);

template <class InputIterator>
basic_string(
    InputIterator first,
    InputIterator last);

template <class InputIterator>
basic_string(
    InputIterator first,
    InputIterator last,
    const allocator_type& alloc_type);

basic_string(
    const_pointer first,
    const_pointer last);

basic_string(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>パラメーター

*`ptr`*\
作成される `string` の初期化に使用される文字が含まれた C 文字列。 この値を null ポインターにすることはできません。

*`alloc_type`*\
作成される文字列オブジェクトのストレージ アロケーター クラス。

*`count`*\
初期化される文字数。

*`right`*\
作成される文字列を初期化するための文字列。

*`right_offset`*\
作成される文字列の文字値を初期化するために最初に使用される、文字列内の文字のインデックス。

*`char_value`*\
作成される文字列にコピーされる文字値。

*`first`*\
挿入されるソース範囲内の先頭の要素の位置を示す、入力反復子、const_pointer、または const_iterator。

*`last`*\
挿入されるソース範囲の最後の要素の次の要素の位置を示す、入力反復子、const_pointer、または const_iterator。

### <a name="return-value"></a>戻り値

コンストラクターによって作成される文字列オブジェクトへの参照。

### <a name="remarks"></a>解説

すべてのコンストラクターは、を格納 [`basic_string::allocator_type`](#allocator_type) し、被制御シーケンスを初期化します。 アロケーター オブジェクトは、引数 `al` が指定されていれば、この引数です。 コピーコンストラクターの場合は、 `right.get_allocator()` への呼び出し [`basic_string::get_allocator`](#get_allocator) です。 それ以外の場合、アロケーターは `Alloc()` です。

被制御シーケンスは、残りのオペランドで指定された、オペランド シーケンスのコピーに初期化されます。 オペランド シーケンスを含まないコンストラクターは、空の初期被制御シーケンスを指定します。 `InputIterator`がテンプレートコンストラクターの整数型である場合、オペランドシーケンスは `first,  last` と同じように動作し `(size_type) first, (value_type) last` ます。

### <a name="example"></a>例

```cpp
// basic_string_ctor.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function initializing with a C-string
   const char *cstr1a = "Hello Out There.";
   basic_string <char> str1a ( cstr1a , 5);
   cout << "The string initialized by C-string cstr1a is: "
        << str1a << "." << endl;

   // The second member function initializing with a string
   string  str2a ( "How Do You Do" );
   basic_string <char> str2b ( str2a , 7 , 7 );
   cout << "The string initialized by part of the string cstr2a is: "
        << str2b << "." << endl;

   // The third member function initializing a string
   // with a number of characters of a specific value
   basic_string <char> str3a ( 5, '9' );
   cout << "The string initialized by five number 9s is: "
        << str3a << endl;

   // The fourth member function creates an empty string
   // and string with a specified allocator
   basic_string <char> str4a;
   string str4b;
   basic_string <char> str4c ( str4b.get_allocator( ) );
   if (str4c.empty ( ) )
      cout << "The string str4c is empty." << endl;
   else
      cout << "The string str4c is not empty." << endl;

   // The fifth member function initializes a string from
   // another range of characters
   string str5a ( "Hello World" );
   basic_string <char> str5b ( str5a.begin ( ) + 5 , str5a.end ( ) );
   cout << "The string initialized by another range is: "
        << str5b << "." << endl;
}
```

## <a name="basic_stringbegin"></a><a name="begin"></a> `basic_string::begin`

文字列の 1 つ目の要素を示す反復子を返します。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>戻り値

シーケンスの最初の要素または空のシーケンスの末尾の次の位置を示すランダム アクセス反復子。

### <a name="example"></a>例

```cpp
// basic_string_begin.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( ) {
   using namespace std;
   string str1 ( "No way out." ), str2;
   basic_string <char>::iterator strp_Iter, str1_Iter, str2_Iter;
   basic_string <char>::const_iterator str1_cIter;

   str1_Iter = str1.begin ( );
   cout << "The first character of the string str1 is: "
        << *str1_Iter << endl;
   cout << "The full original string str1 is: " << str1 << endl;

   // The dereferenced iterator can be used to modify a character
*str1_Iter = 'G';
   cout << "The first character of the modified str1 is now: "
        << *str1_Iter << endl;
   cout << "The full modified string str1 is now: " << str1 << endl;

   // The following line would be an error because iterator is const
   // *str1_cIter = 'g';

   // For an empty string, begin is equivalent to end
   if (  str2.begin ( ) == str2.end ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The string str2 is not empty." << endl;
}
```

## <a name="basic_stringc_str"></a><a name="c_str"></a> `basic_string::c_str`

C スタイルの null で終わる文字列として、文字列の内容を変換します。

```cpp
const value_type *c_str() const;
```

### <a name="return-value"></a>戻り値

呼び出し文字列の C スタイル バージョンへのポインター。  ポインター値は、 `const` オブジェクトのクラスでデストラクターを含む非関数を呼び出した後に有効ではありません `basic_string` 。

### <a name="remarks"></a>解説

クラステンプレートに属する文字列型のオブジェクトは、 `basic_string<char>` 必ずしも null で終わるとは限りません。 Null 文字 `'\0'` は、文字列の末尾を示すために C 文字列内の特殊文字として使用されますが、文字列型のオブジェクトでは特別な意味を持たず、他の文字と同様に文字列の一部である可能性があります。 から文字列への変換は自動的に行われ `const char *` ますが、string クラスは、C スタイルの文字列から型のオブジェクトへの自動変換を提供しません `basic_string<char>` 。

返された C スタイルの文字列を変更することはできません。これは、文字列へのポインターを無効にしたり、文字列の有効期間が限定され、クラス文字列によって所有されているために削除されたりする可能性があります。

### <a name="example"></a>例

```cpp
// basic_string_c_str.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string  str1 ( "Hello world" );
   cout << "The original string object str1 is: "
        << str1 << endl;
   cout << "The length of the string object str1 = "
        << str1.length ( ) << endl << endl;

   // Converting a string to an array of characters
   const char *ptr1 = 0;
   ptr1= str1.data ( );
   cout << "The modified string object ptr1 is: " << ptr1
        << endl;
   cout << "The length of character array str1 = "
        << strlen ( ptr1) << endl << endl;

   // Converting a string to a C-style string
   const char *c_str1 = str1.c_str ( );
   cout << "The C-style string c_str1 is: " << c_str1
        << endl;
   cout << "The length of C-style string str1 = "
        << strlen ( c_str1) << endl << endl;
}
```

```Output
The original string object str1 is: Hello world
The length of the string object str1 = 11

The modified string object ptr1 is: Hello world
The length of character array str1 = 11

The C-style string c_str1 is: Hello world
The length of C-style string str1 = 11
```

## <a name="basic_stringcapacity"></a><a name="capacity"></a> `basic_string::capacity`

文字列のメモリ割り当てを増やさずに文字列に格納できる要素の最大数を返します。

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>戻り値

文字列を保持するためにメモリに現在割り当てられている記憶域のサイズ。

### <a name="remarks"></a>解説

このメンバー関数は、被制御シーケンスを保持するために現在割り当てられているストレージを返します。これは、少なくとも同じサイズの値 [`size`](#size) です。

### <a name="example"></a>例

```cpp
// basic_string_capacity.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size (  );
   lenStr1 = str1.length (  );
   capStr1 = str1.capacity (  );
   max_sizeStr1 = str1.max_size (  );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringcbegin"></a><a name="cbegin"></a> `basic_string::cbegin`

範囲内の最初の要素を示す `const` 反復子を返します。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>戻り値

範囲の最初の要素、または空の範囲の末尾の次の位置 (空の範囲の場合、`const`) を指し示す `cbegin() == cend()` ランダム アクセス反復子。

### <a name="remarks"></a>解説

の戻り値を使用して、 `cbegin` 範囲内の要素を変更することはできません。

`begin()` メンバー関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常は、 [`auto`](../cpp/auto-cpp.md) 次の例に示すように、型推論キーワードと共に使用されます。 この例では、 `Container` `const` とをサポートする任意の種類の変更可能な (非) コンテナーである `begin()` と見なし `cbegin()` ます。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="basic_stringcend"></a><a name="cend"></a> `basic_string::cend`

範囲内の最後の要素の次の位置を指す `const` 反復子を返します。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>戻り値

範囲の末尾の次の位置を指し示す `const` ランダム アクセス反復子。

### <a name="remarks"></a>解説

`cend` は、反復子が範囲の末尾を超えたかどうかをテストするために使用されます。

`end()` メンバー関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常は、 [`auto`](../cpp/auto-cpp.md) 次の例に示すように、型推論キーワードと共に使用されます。 この例では、 `Container` `const` とをサポートする任意の種類の変更可能な (非) コンテナーである `end()` と見なし `cend()` ます。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

によって返された値を `cend` 逆参照することはできません。

## <a name="basic_stringclear"></a><a name="clear"></a> `basic_string::clear`

文字列のすべての要素を消去します。

```cpp
void clear();
```

### <a name="remarks"></a>解説

このメンバー関数が呼び出された文字列は空になります。

### <a name="example"></a>例

```cpp
// basic_string_clear.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ("Hello world"), str2;
   basic_string <char>::iterator str_Iter;
   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   str1.clear ( );
   cout << "The modified string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   //For an empty string, begin is equivalent to end
   if ( str1.begin ( ) == str1.end ( ) )
      cout << "Nothing printed above because "
           << "the string str1 is empty." << endl;
   else
      cout << "The string str1 is not empty." << endl;
}
```

```Output
The original string str1 is: Hello world
The modified string str1 is:
Nothing printed above because the string str1 is empty.
```

## <a name="basic_stringcompare"></a><a name="compare"></a> `basic_string::compare`

2つの文字列が等しいかどうかを判断するために、指定された文字列を使用して大文字と小文字を区別する比較を行います。

```cpp
int compare(
    const basic_string<CharType, Traits, Allocator>& str) const;

int compare(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str) const;

int compare(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count) const;

int compare(
    const value_type* ptr) const;

int compare(
    size_type position_1,
    size_type number_1,
    const value_type* ptr) const;

int compare(
    size_type position_1,
    size_type number_1,
    const value_type* ptr
    size_type number_2) const;
```

### <a name="parameters"></a>パラメーター

*`str`*\
オペランド文字列と比較する文字列。

*`position_1`*\
比較の開始位置を示すオペランド文字列のインデックス。

*`number_1`*\
比較するオペランド文字列の最大文字数。

*`number_2`*\
比較するパラメーター文字列の最大文字数。

*`offset`*\
比較の開始位置を示すパラメーター文字列のインデックス。

*`count`*\
比較するパラメーター文字列の最大文字数。

*`ptr`*\
オペランド文字列と比較する C 文字列。

### <a name="return-value"></a>戻り値

オペランド文字列がパラメーター文字列より小さい場合は負の値、2 つの文字列が等しい場合は 0、オペランド文字列がパラメーター文字列より大きい場合は正の値になります。

### <a name="remarks"></a>解説

`compare`メンバー関数は、使用されているに応じて、パラメーターとオペランド文字列のすべて (または一部) を比較します。

比較では大文字と小文字が区別されます。

### <a name="example"></a>例

```cpp
// basic_string_compare.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function compares
   // an operand string to a parameter string
   int comp1;
   string s1o ( "CAB" );
   string s1p ( "CAB" );
   cout << "The operand string is: " << s1o << endl;
   cout << "The parameter string is: " << s1p << endl;
   comp1 = s1o.compare ( s1p );
   if ( comp1 < 0 )
      cout << "The operand string is less than "
           << "the parameter string." << endl;
   else if ( comp1 == 0 )
      cout << "The operand string is equal to "
           << "the parameter string." << endl;
   else
      cout << "The operand string is greater than "
           << "the parameter string." << endl;
   cout << endl;

   // The second member function compares part of
   // an operand string to a parameter string
   int comp2a, comp2b;
   string s2o ( "AACAB" );
   string s2p ( "CAB" );
   cout << "The operand string is: " << s2o << endl;
   cout << "The parameter string is: " << s2p << endl;
   comp2a = s2o.compare (  2 , 3 , s2p );
   if ( comp2a < 0 )
      cout << "The last three characters of "
           << "the operand string\n are less than "
           << "the parameter string." << endl;
   else if ( comp2a == 0 )
      cout << "The last three characters of "
           << "the operand string\n are equal to "
           << "the parameter string." << endl;
   else
      cout << "The last three characters of "
           << "the operand string\n is greater than "
           << "the parameter string." << endl;

   comp2b = s2o.compare (  0 , 3 , s2p );
   if ( comp2b < 0 )
      cout << "The first three characters of "
           << "the operand string\n are less than "
           << "the parameter string." << endl;
   else if ( comp2b == 0 )
      cout << "The first three characters of "
           << "the operand string\n are equal to "
           << "the parameter string." << endl;
   else
      cout << "The first three characters of "
           << "the operand string\n is greater than "
           << "the parameter string." << endl;
   cout << endl;

   // The third member function compares part of
   // an operand string to part of a parameter string
   int comp3a;
   string s3o ( "AACAB" );
   string s3p ( "DCABD" );
   cout << "The operand string is: " << s3o << endl;
   cout << "The parameter string is: " << s3p << endl;
   comp3a = s3o.compare (  2 , 3 , s3p , 1 , 3 );
   if ( comp3a < 0 )
      cout << "The three characters from position 2 of "
           << "the operand string are less than\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   else if ( comp3a == 0 )
      cout << "The three characters from position 2 of "
           << "the operand string are equal to\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   else
      cout << "The three characters from position 2 of "
           << "the operand string is greater than\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   cout << endl;

   // The fourth member function compares
   // an operand string to a parameter C-string
   int comp4a;
   string s4o ( "ABC" );
   const char* cs4p = "DEF";
   cout << "The operand string is: " << s4o << endl;
   cout << "The parameter C-string is: " << cs4p << endl;
   comp4a = s4o.compare ( cs4p );
   if ( comp4a < 0 )
      cout << "The operand string is less than "
           << "the parameter C-string." << endl;
   else if ( comp4a == 0 )
      cout << "The operand string is equal to "
           << "the parameter C-string." << endl;
   else
      cout << "The operand string is greater than "
           << "the parameter C-string." << endl;
   cout << endl;

   // The fifth member function compares part of
   // an operand string to a parameter C-string
   int comp5a;
   string s5o ( "AACAB" );
   const char* cs5p = "CAB";
   cout << "The operand string is: " << s5o << endl;
   cout << "The parameter string is: " << cs5p << endl;
   comp5a = s5o.compare (  2 , 3 , s2p );
   if ( comp5a < 0 )
      cout << "The last three characters of "
           << "the operand string\n are less than "
           << "the parameter C-string." << endl;
   else if ( comp5a == 0 )
      cout << "The last three characters of "
           << "the operand string\n are equal to "
           << "the parameter C-string." << endl;
   else
      cout << "The last three characters of "
           << "the operand string\n is greater than "
           << "the parameter C-string." << endl;
   cout << endl;

   // The sixth member function compares part of
   // an operand string to part of an equal length of
   // a parameter C-string
   int comp6a;
   string s6o ( "AACAB" );
   const char* cs6p = "ACAB";
   cout << "The operand string is: " << s6o << endl;
   cout << "The parameter C-string is: " << cs6p << endl;
   comp6a = s6o.compare (  1 , 3 , cs6p , 3 );
   if ( comp6a < 0 )
      cout << "The 3 characters from position 1 of "
           << "the operand string are less than\n "
           << "the first 3 characters of the parameter C-string."
           << endl;
   else if ( comp6a == 0 )
      cout << "The 3 characters from position 2 of "
           << "the operand string are equal to\n "
           << "the first 3 characters of the parameter C-string."
           <<  endl;
   else
      cout << "The 3 characters from position 2 of "
           << "the operand string is greater than\n "
           << "the first 3 characters of the parameter C-string."
           << endl;
   cout << endl;
}
```

```Output
The operand string is: CAB
The parameter string is: CAB
The operand string is equal to the parameter string.

The operand string is: AACAB
The parameter string is: CAB
The last three characters of the operand string
are equal to the parameter string.
The first three characters of the operand string
are less than the parameter string.

The operand string is: AACAB
The parameter string is: DCABD
The three characters from position 2 of the operand string are equal to
the 3 characters parameter string from position 1.

The operand string is: ABC
The parameter C-string is: DEF
The operand string is less than the parameter C-string.

The operand string is: AACAB
The parameter string is: CAB
The last three characters of the operand string
are equal to the parameter C-string.

The operand string is: AACAB
The parameter C-string is: ACAB
The 3 characters from position 2 of the operand string are equal to
the first 3 characters of the parameter C-string.
```

## <a name="basic_stringconst_iterator"></a><a name="const_iterator"></a> `basic_string::const_iterator`

文字列内の `const` 要素にアクセスし、読み取ることができるランダム アクセス反復子を提供する型。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>解説

型を `const_iterator` 使用して文字の値を変更することはできません。また、文字列を前方方向に反復処理するために使用されます。

### <a name="example"></a>例

の [`begin`](#begin) 宣言方法や使用方法の例については、の例を参照してください `const_iterator` 。

## <a name="basic_stringconst_pointer"></a><a name="const_pointer"></a> `basic_string::const_pointer`

文字列内の `const` 要素へのポインターを提供する型。

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>解説

この型は `allocator_type::const_pointer` の同意語です。

型の場合 `string` は、と同じ `char*` です。

Const として宣言されているポインターは、宣言されているときに初期化する必要があります。 Const ポインターは常に同じメモリ位置を指し、定数または非定数データを指す場合があります。

### <a name="example"></a>例

```cpp
// basic_string_const_ptr.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   basic_string<char>::const_pointer pstr1a = "In Here";
   const char *cstr1c = "Out There";

   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;
   cout << "The C-string cstr1c is: " << cstr1c << "." << endl;
}
```

```Output
The string pstr1a is: In Here.
The C-string cstr1c is: Out There.
```

## <a name="basic_stringconst_reference"></a><a name="const_reference"></a> `basic_string::const_reference`

読み取りと `const` 操作の実行のために、文字列に格納された `const` 要素への参照を提供する型。

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="remarks"></a>解説

型を `const_reference` 使用して要素の値を変更することはできません。

この型は `allocator_type::const_reference` の同意語です。 型の場合 `string` は、const に相当 `char&` します。

### <a name="example"></a>例

の [`at`](#at) 宣言方法や使用方法の例については、の例を参照してください `const_reference` 。

## <a name="basic_stringconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> `basic_string::const_reverse_iterator`

文字列内の任意の `const` 要素を読み取ることができるランダム アクセス反復子を提供する型。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>解説

型は、 `const_reverse_iterator` 文字の値を変更することはできず、逆に文字列を反復処理するために使用されます。

### <a name="example"></a>例

の [`rbegin`](#rbegin) 宣言方法や使用方法の例については、の例を参照してください `const_reverse_iterator` 。

## <a name="basic_stringcopy"></a><a name="copy"></a> `basic_string::copy`

コピー元の文字列のインデックス位置からターゲットの文字配列に最大で指定された文字数をコピーします。

渡された値が正しいことの確認を呼び出し元に依存するため、このメソッドは安全ではない可能性があります。 代わりにを使用することを検討してください [`basic_string::_Copy_s`](#copy_s) 。

```cpp
size_type copy(
    value_type* ptr,
    size_type count,
    size_type offset = 0) const;
```

### <a name="parameters"></a>パラメーター

*`ptr`*\
要素のコピー先のターゲット文字配列。

*`count`* コピー元の文字列からコピーされる最大文字数。

*`offset`*\
ソース文字列内のコピーの作成開始位置。

### <a name="return-value"></a>戻り値

コピーされた文字数。

### <a name="remarks"></a>解説

コピーの末尾に null 文字は追加されません。

### <a name="example"></a>例

```cpp
// basic_string_copy.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello World" );
   basic_string <char>::iterator str_Iter;
   char array1 [ 20 ] = { 0 };
   char array2 [ 10 ] = { 0 };
   basic_string <char>:: pointer array1Ptr = array1;
   basic_string <char>:: value_type *array2Ptr = array2;

   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   basic_string <char>:: size_type nArray1;
   // Note: string::copy is potentially unsafe, consider
   // using string::_Copy_s instead.
   nArray1 = str1.copy ( array1Ptr , 12 );  // C4996
   cout << "The number of copied characters in array1 is: "
        << nArray1 << endl;
   cout << "The copied characters array1 is: " << array1 << endl;

   basic_string <char>:: size_type nArray2;
   // Note: string::copy is potentially unsafe, consider
   // using string::_Copy_s instead.
   nArray2 = str1.copy ( array2Ptr , 5 , 6  );  // C4996
   cout << "The number of copied characters in array2 is: "
           << nArray2 << endl;
   cout << "The copied characters array2 is: " << array2Ptr << endl;
}
```

```Output
The original string str1 is: Hello World
The number of copied characters in array1 is: 11
The copied characters array1 is: Hello World
The number of copied characters in array2 is: 5
The copied characters array2 is: World
```

## <a name="basic_stringcrbegin"></a><a name="crbegin"></a> `basic_string::crbegin`

反転文字列内の最初の要素を示す定数反復子を返します。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>戻り値

文字列の末尾の次の位置を指し示す反転反復子。 この位置が反転文字列の先頭に指定されます。

## <a name="basic_stringcrend"></a><a name="crend"></a> `basic_string::crend`

反転さ `const` れた文字列内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>戻り値

反転された `const` 文字列内の最後の要素の次の位置 (反転されていない文字列内の最初の要素の前の位置) を指す反転反復子。

### <a name="remarks"></a>解説

## <a name="basic_string_copy_s"></a><a name="copy_s"></a> `basic_string::_Copy_s`

コピー元の文字列のインデックス位置からターゲットの文字配列に最大で指定された文字数をコピーします。

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type offset = 0) const;
```

### <a name="parameters"></a>パラメーター

*`dest`*\
要素のコピー先のターゲット文字配列。

*`dest_size`*\
*Dest* のサイズ。

*`count`* コピー元の文字列からコピーされる最大文字数。

*`offset`*\
ソース文字列内のコピーの作成開始位置。

### <a name="return-value"></a>戻り値

実際にコピーされた文字数。

### <a name="remarks"></a>解説

コピーの末尾に null 文字は追加されません。

### <a name="example"></a>例

```cpp
// basic_string__Copy_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;
    string str1("Hello World");
    basic_string<char>::iterator str_Iter;
    const int array1_size = 20;
    char array1[array1_size] = { 0 };
    const int array2_size = 10;
    char array2[array2_size] = { 0 };
    basic_string<char>:: pointer array1Ptr = array1;
    basic_string<char>:: value_type *array2Ptr = array2;

    cout << "The original string str1 is: ";
    for (str_Iter = str1.begin(); str_Iter != str1.end(); str_Iter++)
        cout << *str_Iter;
    cout << endl;

    basic_string<char>::size_type nArray1;
    nArray1 = str1._Copy_s(array1Ptr, array1_size, 12);
    cout << "The number of copied characters in array1 is: "
         << nArray1 << endl;
    cout << "The copied characters array1 is: " << array1 << endl;

    basic_string<char>:: size_type nArray2;
    nArray2 = str1._Copy_s(array2Ptr, array2_size, 5, 6);
    cout << "The number of copied characters in array2 is: "
         << nArray2 << endl;
    cout << "The copied characters array2 is: " << array2Ptr << endl;
}
```

```Output
The original string str1 is: Hello World
The number of copied characters in array1 is: 11
The copied characters array1 is: Hello World
The number of copied characters in array2 is: 5
The copied characters array2 is: World
```

## <a name="basic_stringdata"></a><a name="data"></a> `basic_string::data`

文字列の内容を、null で終わる文字配列に変換します。

```cpp
const value_type *data() const noexcept;
value_type *data() noexcept;
```

### <a name="return-value"></a>戻り値

文字列の内容を格納している null で終わる配列の最初の要素へのポインター。 空の文字列の場合、ポインターはに等しい1つの null 文字を指し `value_type()` ます。

### <a name="remarks"></a>解説

有効な範囲でポイントによって返されるポインター `data` `[data(), data() + size()]` 。 範囲内の各要素は、文字列内の現在のデータに対応しています。 つまり、の範囲内の有効なオフセットごとに *`n`* `data() + n == addressof(operator[](n))` 。

のオーバーロードによって返される文字列の内容を変更すると、 `const` `data` 動作は定義されません。 また、ターミナルの null 文字が他の値に変更された場合は、未定義の動作が発生します。 `const`文字列への非参照が標準ライブラリ関数に渡された場合、返されたポインターは無効になる可能性があります。 また、非メンバー関数の呼び出しによって無効にすることもでき `const` ます。 メンバー、、、、、、、およびへの呼び出しで `at` `back` は、 `begin` `end` `front` `rbegin` `rend` `operator[]` ポインターは無効になりません。

C++ 11 より前では、は、返された `data` 文字列が null で終わることを保証しませんでした。 C++ 11 以降では、 `data` と `c_str` はどちらも null で終わる文字列を返し、実質的には同じです。

非 `const` オーバーロードは、c++ 17 で新しく追加されたものです。 これを使用するに **`/std:c++17`** は、またはコンパイラオプションを指定し **`/std:c++latest`** ます。

### <a name="example"></a>例

```cpp
// basic_string_data.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string str1 ( "Hello world" );
   cout << "The original string object str1 is: "
        << str1 << endl;
   cout << "The length of the string object str1 = "
        << str1.length ( ) << endl << endl;

   // Converting a string to an array of characters
   const char *ptr1 = 0;
   ptr1= str1.data ( );
   cout << "The modified string object ptr1 is: " << ptr1
        << endl;
   cout << "The length of character array str1 = "
        << strlen ( ptr1) << endl << endl;

   // Converting a string to a C-style string
   const char *c_str1 = str1.c_str ( );
   cout << "The C-style string c_str1 is: " << c_str1
        << endl;
   cout << "The length of C-style string str1 = "
        << strlen ( c_str1) << endl << endl;
}
```

```Output
The original string object str1 is: Hello world
The length of the string object str1 = 11

The modified string object ptr1 is: Hello world
The length of character array str1 = 11

The C-style string c_str1 is: Hello world
The length of C-style string str1 = 11
```

## <a name="basic_stringdifference_type"></a><a name="difference_type"></a> `basic_string::difference_type`

同じ文字列内の要素を参照する 2 反復子の違いを提供する型。

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>解説

符号付き整数型は、被制御シーケンス内にある 2 つの要素のアドレスの違いを表すことのできるオブジェクトを記述します。

型の場合 `string` は、と同じ `ptrdiff_t` です。

### <a name="example"></a>例

```cpp
// basic_string_diff_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "quintillion" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexChFi, indexChLi;

   indexChFi = str1.find_first_of ( "i" );
   indexChLi = str1.find_last_of ( "i" );
   basic_string<char>::difference_type diffi = indexChLi - indexChFi;

   cout << "The first character i is at position: "
        << indexChFi << "." << endl;
   cout << "The last character i is at position: "
        << indexChLi << "." << endl;
   cout << "The difference is: " << diffi << "." << endl;
}
```

```Output
The original string str1 is: quintillion
The first character i is at position: 2.
The last character i is at position: 8.
The difference is: 6.
```

## <a name="basic_stringempty"></a><a name="empty"></a> `basic_string::empty`

文字列に文字が含まれているかどうかをテストします。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

`true` 文字列オブジェクトに文字が含まれていない場合は。 `false` 少なくとも1つの文字がある場合。

### <a name="remarks"></a>解説

このメンバー関数は、 [`size`](#size) = = 0 に相当します。

### <a name="example"></a>例

```cpp
// basic_string_empty.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main() {
   using namespace std;

   bool b1, b2;

   string str1 ("Hello world");
   cout << "The original string object str1 is: " << str1 << endl;
   b1 = str1.empty();
   if (b1)
      cout << "The string object str1 is empty." << endl;
   else
      cout << "The string object str1 is not empty." << endl;
   cout << endl;

   // An example of an empty string object
   string str2;
   b2 = str2.empty();
   if (b2)
      cout << "The string object str2 is empty." << endl;
   else
      cout << "The string object str2 is not empty." << endl;
}
```

## <a name="basic_stringend"></a><a name="end"></a> `basic_string::end`

文字列内の最後の要素の次の場所を指す反復子を返します。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>戻り値

文字列内の最後の要素の次の位置を指すランダム アクセス反復子を返します。

### <a name="remarks"></a>解説

`end` は、反復子が文字列の末尾に到達したかどうかをテストするためによく使用されます。 によって返された値を `end` 逆参照することはできません。

の戻り値がに割り当てられている場合、 `end` `const_iterator` 文字列オブジェクトは変更できません。 の戻り値がに割り当てられている場合は、 `end` `iterator` 文字列オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// basic_string_end.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "No way out." ), str2;
   basic_string <char>::iterator str_Iter, str1_Iter, str2_Iter;
   basic_string <char>::const_iterator str1_cIter;

   str1_Iter = str1.end ( );
   str1_Iter--;
   str1_Iter--;
   cout << "The last character-letter of the string str1 is: " << *str1_Iter << endl;
   cout << "The full original string str1 is: " << str1 << endl;

   // end used to test when an iterator has reached the end of its string
   cout << "The string is now: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
   *str1_Iter = 'T';
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_Iter << endl;
   cout << "The modified string str1 is now: " << str1 << endl;

   // The following line would be an error because iterator is const
   // *str1_cIter = 'T';

   // For an empty string, end is equivalent to begin
   if ( str2.begin( ) == str2.end ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The last character-letter of the string str1 is: t
The full original string str1 is: No way out.
The string is now: No way out.
The last character-letter of the modified str1 is now: T
The modified string str1 is now: No way ouT.
The string str2 is empty.
```

## <a name="basic_stringends_with"></a><a name="ends_with"></a> `basic_string::ends_with`

文字列が指定したサフィックスで終わるかどうかを確認します。

```cpp
bool ends_with(const CharType c) const noexcept;
bool ends_with(const CharType* const x) const noexcept;
bool ends_with(const basic_string_view sv) const noexcept;
```

### <a name="parameters"></a>パラメーター

*`c`*\
検索する単一の文字のサフィックス。

*`sv`*\
検索するサフィックスを含む文字列ビュー。 \
文字列ビューに変換するを渡すことができ `std::basic_string` ます。

*`x`*\
検索するサフィックスを格納している Null で終わる文字列。

### <a name="return-value"></a>戻り値

`true` 文字列が指定したサフィックスで終わる場合は。 `false` それ以外の場合は。

### <a name="remarks"></a>解説

`ends_with()` は C++ 20 で新しく追加されたものです。 これを使用するには、コンパイラオプションを指定し [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) ます。

[`starts_with`](#starts_with)文字列が指定したプレフィックスで始まるかどうかを確認するには、「」を参照してください。

### <a name="example"></a>例

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::basic_string<char> str = "abcdefg";

    std::cout << std::boolalpha; // so booleans show as 'true'/'false'
    std::cout << str.ends_with('g') << '\n';
    std::cout << str.ends_with("eFg") << '\n';

    std::basic_string<char> str2 = "efg";
    std::cout << str.ends_with(str2);

    return 0;
}
```

```Output
true
false
true
```

## <a name="basic_stringerase"></a><a name="erase"></a> `basic_string::erase`

指定した位置から文字列の要素または要素範囲を削除します。

```cpp
iterator erase(
    iterator first,
    iterator last);

iterator erase(
    iterator iter);

basic_string<CharType, Traits, Allocator>& erase(
    size_type offset = 0,
    size_type count = npos);
```

### <a name="parameters"></a>パラメーター

*`first`*\
消去範囲内の最初の要素の位置を示す反復子。

*`last`*\
消去範囲内の最後の要素の次の位置を示す反復子。

*`iter`*\
消去される文字列内の要素の位置を示す反復子。

*`offset`*\
削除される文字列内の最初の文字のインデックス。

*`count`*\
で始まる文字列の範囲内にある場合に削除される要素の数 *`offset`* 。

### <a name="return-value"></a>戻り値

最初の 2 つのメンバー関数には、メンバー関数によって削除される最後の文字の後の最初の文字を指定する反復子。 3 番目のメンバー関数には、要素を消去する文字列オブジェクトへの参照。

### <a name="remarks"></a>解説

3番目のメンバー関数はを返し `*this` ます。

### <a name="example"></a>例

```cpp
// basic_string_erase.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The 1st member function using a range demarcated
   // by iterators
   string str1 ( "Hello world" );
   basic_string <char>::iterator str1_Iter;
   cout << "The original string object str1 is: "
        << str1 << "." << endl;
   str1_Iter = str1.erase ( str1.begin ( ) + 3 , str1.end ( ) - 1 );
   cout << "The first element after those removed is: "
        << *str1_Iter << "." << endl;
   cout << "The modified string object str1 is: " << str1
           << "." << endl << endl;

   // The 2nd member function erasing a char pointed to
   // by an iterator
   string str2 ( "Hello World" );
   basic_string <char>::iterator str2_Iter;
   cout << "The original string object str2 is: " << str2
        << "." << endl;
   str2_Iter = str2.erase ( str2.begin ( ) + 5 );
   cout << "The first element after those removed is: "
        << *str2_Iter << "." << endl;
   cout << "The modified string object str2 is: " << str2
        << "." << endl << endl;

   // The 3rd member function erasing a number of chars
   // after a char
   string str3 ( "Hello computer" ), str3m;
   basic_string <char>::iterator str3_Iter;
   cout << "The original string object str3 is: "
        << str3 << "." << endl;
   str3m = str3.erase ( 6 , 8 );
   cout << "The modified string object str3m is: "
        << str3m << "." << endl;
}
```

```Output
The original string object str1 is: Hello world.
The first element after those removed is: d.
The modified string object str1 is: Held.

The original string object str2 is: Hello World.
The first element after those removed is: W.
The modified string object str2 is: HelloWorld.

The original string object str3 is: Hello computer.
The modified string object str3m is: Hello .
```

## <a name="basic_stringfind"></a><a name="find"></a> `basic_string::find`

指定された文字シーケンスに一致する部分文字列の最初の出現を文字列で前方に検索します。

```cpp
size_type find(
    value_type char_value,
    size_type offset = 0) const;

size_type find(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>パラメーター

*`char_value`*\
メンバー関数が検索される文字値。

*`offset`*\
検索を開始する位置のインデックス。

*`ptr`*\
メンバー関数が検索される C 文字列。

*`count`*\
メンバー関数が検索される C 文字列で、最初の文字から順方向に数えた文字数。

*`str`*\
メンバー関数が検索される文字列。

### <a name="return-value"></a>戻り値

成功した場合、検索する部分文字列の最初の文字のインデックス、それ以外の場合 `npos`。

### <a name="example"></a>例

```cpp
// basic_string_find.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "Hello Everyone" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;

   indexCh1a = str1.find ( "e" , 3 );
   if (indexCh1a != string::npos )
      cout << "The index of the 1st 'e' found after the 3rd"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'e' was not found in str1 ." << endl;

   indexCh1b = str1.find ( "x" );
   if (indexCh1b != string::npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The Character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "Let me make this perfectly clear." );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "perfect";
   indexCh2a = str2.find ( cstr2 , 5 );
   if ( indexCh2a != string::npos )
      cout << "The index of the 1st element of 'perfect' "
           << "after\n the 5th position in str2 is: "
           << indexCh2a << endl;
   else
      cout << "The substring 'perfect' was not found in str2 ."
           << endl;

   const char *cstr2b = "imperfectly";
   indexCh2b = str2.find ( cstr2b , 0 );
   if (indexCh2b != string::npos )
      cout << "The index of the 1st element of 'imperfect' "
           << "after\n the 5th position in str3 is: "
           << indexCh2b << endl;
   else
      cout << "The substring 'imperfect' was not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "This is a sample string for this program" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "sample";
   indexCh3a = str3.find ( cstr3a );
   if ( indexCh3a != string::npos )
      cout << "The index of the 1st element of sample "
           << "in str3 is: " << indexCh3a << endl;
   else
      cout << "The substring 'sample' was not found in str3 ."
           << endl;

   const char *cstr3b = "for";
   indexCh3b = str3.find ( cstr3b , indexCh3a + 1 , 2 );
   if (indexCh3b != string::npos )
      cout << "The index of the next occurrence of 'for' is in "
           << "str3 begins at: " << indexCh3b << endl << endl;
   else
      cout << "There is no next occurrence of 'for' in str3 ."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "clearly this perfectly unclear." );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "clear" );
   indexCh4a = str4.find ( str4a , 5 );
   if ( indexCh4a != string::npos )
      cout << "The index of the 1st element of 'clear' "
           << "after\n the 5th position in str4 is: "
           << indexCh4a << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl;

   string str4b ( "clear" );
   indexCh4b = str4.find ( str4b );
   if (indexCh4b != string::npos )
      cout << "The index of the 1st element of 'clear' "
           << "in str4 is: "
           << indexCh4b << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl << endl;
}
```

```Output
The original string str1 is: Hello Everyone
The index of the 1st 'e' found after the 3rd position in str1 is: 8
The Character 'x' was not found in str1.

The original string str2 is: Let me make this perfectly clear.
The index of the 1st element of 'perfect' after
the 5th position in str2 is: 17
The substring 'imperfect' was not found in str2 .

The original string str3 is: This is a sample string for this program
The index of the 1st element of sample in str3 is: 10
The index of the next occurrence of 'for' is in str3 begins at: 24

The original string str4 is: clearly this perfectly unclear.
The index of the 1st element of 'clear' after
the 5th position in str4 is: 25
The index of the 1st element of 'clear' in str4 is: 0
```

## <a name="basic_stringfind_first_not_of"></a><a name="find_first_not_of"></a> `basic_string::find_first_not_of`

指定した文字列の要素ではない最初の文字を文字列で検索します。

```cpp
size_type find_first_not_of(
    value_type char_value,
    size_type offset = 0) const;

size_type find_first_not_of(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find_first_not_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_first_not_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>パラメーター

*`char_value`*\
メンバー関数が検索される文字値。

*`offset`*\
検索を開始する位置のインデックス。

*`ptr`*\
メンバー関数が検索される C 文字列。

*`count`*\
メンバー関数が検索される C 文字列で、最初の文字から順方向に数えた文字数。

*`str`*\
メンバー関数が検索される文字列。

### <a name="return-value"></a>戻り値

成功した場合、検索する部分文字列の最初の文字のインデックス、それ以外の場合 `npos`。

### <a name="example"></a>例

```cpp
// basic_string_find_first_not_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "xddd-1234-abcd" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_first_not_of ( "d" , 2 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'd' found after the 3rd"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_not_of  ( "x" );
   if (indexCh1b != npos )
      cout << "The index of the 'non x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'non x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "BBB-1111" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_first_not_of ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'B1' in str2 after\n the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not"
           << "\n found in str2 after the 6th position."
           << endl;

   const char *cstr2b = "B2";
   indexCh2b = str2.find_first_not_of ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'B2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'B2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "444-555-GGG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "45G";
   indexCh3a = str3.find_first_not_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element in str3\n other than one of the "
           << "characters in '45G' is: " << indexCh3a
           << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string '45G'. "
           << endl;

   const char *cstr3b = "45G";
   indexCh3b = str3.find_first_not_of ( cstr3b , indexCh3a + 1 , 2 );
   if ( indexCh3b != npos )
      cout << "The index of the second occurrence of an "
           << "element of '45G' in str3\n after the 0th "
           << "position is: " << indexCh3b << endl << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string  '45G'. "
           << endl  << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_first_not_of ( str4a , 5 );
   if (indexCh4a != npos )
      cout << "The index of the 1st non occurrence of an "
           << "element of 'ba3' in str4 after\n the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements other than those in the substring"
           << " 'ba3' were not found in the string str4."
           << endl;

   string str4b ( "12" );
   indexCh4b = str4.find_first_not_of ( str4b  );
   if (indexCh4b != npos )
      cout << "The index of the 1st non occurrence of an "
           << "element of '12' in str4 after\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements other than those in the substring"
           << " '12' were not found in the string str4."
           << endl;
}
```

```Output
The original string str1 is: xddd-1234-abcd
The index of the 1st 'd' found after the 3rd position in str1 is: 4
The index of the 'non x' found in str1 is: 1

The original string str2 is: BBB-1111
Elements of the substring 'B1' were not
found in str2 after the 6th position.
The index of the 1st element of 'B2' after
the 0th position in str2 is: 3

The original string str3 is: 444-555-GGG
The index of the 1st occurrence of an element in str3
other than one of the characters in '45G' is: 3
The index of the second occurrence of an element of '45G' in str3
after the 0th position is: 7

The original string str4 is: 12-ab-12-ab
The index of the 1st non occurrence of an element of 'ba3' in str4 after
the 5th position is: 5
The index of the 1st non occurrence of an element of '12' in str4 after
the 0th position is: 2
```

## <a name="basic_stringfind_first_of"></a><a name="find_first_of"></a> `basic_string::find_first_of`

指定された文字列の要素と一致する最初の文字を文字列で検索します。

```cpp
size_type find_first_of(
    value_type char_value,
    size_type offset = 0) const;

size_type find_first_of(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find_first_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_first_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>パラメーター

*`char_value`*\
メンバー関数が検索される文字値。

*`offset`*\
検索を開始する位置のインデックス。

*`ptr`*\
メンバー関数が検索される C 文字列。

*`count`*\
メンバー関数が検索される C 文字列で、最初の文字から順方向に数えた文字数。

*`str`*\
メンバー関数が検索される文字列。

### <a name="return-value"></a>戻り値

成功した場合、検索する部分文字列の最初の文字のインデックス、それ以外の場合 `npos`。

### <a name="example"></a>例

```cpp
// basic_string_find_first_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "abcd-1234-abcd-1234" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_first_of ( "d" , 5 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'd' found after the 5th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_of ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for any element of a substring as specified by a C-string
   string str2 ( "ABCD-1234-ABCD-1234" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_first_of ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'B1' in str2 after\n the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not "
           << "found in str2 after the 10th position."
           << endl;

   const char *cstr2b = "D2";
   indexCh2b = str2.find_first_of ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'D2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'D2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for any element of a substring as specified by a C-string
   string str3 ( "123-abc-123-abc-456-EFG-456-EFG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "5G";
   indexCh3a = str3.find_first_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of '5G' in str3 after\n the 0th "
           << "position is: " << indexCh3a << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n after the 0th position."
           << endl;

   const char *cstr3b = "5GF";
   indexCh3b = str3.find_first_of  ( cstr3b , indexCh3a + 1 , 2 );
   if (indexCh3b != npos )
      cout << "The index of the second occurrence of an "
           << "element of '5G' in str3\n after the 0th "
           << "position is: " << indexCh3b << endl << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n after the first occurrrence."
           << endl << endl;

   // The fourth member function searches a string
   // for any element of a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_first_of ( str4a , 5 );
   if ( indexCh4a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'ba3' in str4 after\n the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements of the substring 'ba3' were not "
           << "found in str4\n after the 0th position."
           << endl;

   string str4b ( "a2" );
   indexCh4b = str4.find_first_of ( str4b );
   if ( indexCh4b != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'a2' in str4 after\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements of the substring 'a2' were not "
           << "found in str4\n after the 0th position."
           << endl;
}
```

```Output
The original string str1 is: abcd-1234-abcd-1234
The index of the 1st 'd' found after the 5th position in str1 is: 13
The character 'x' was not found in str1.

The original string str2 is: ABCD-1234-ABCD-1234
The index of the 1st occurrence of an element of 'B1' in str2 after
the 6th position is: 11
The index of the 1st element of 'D2' after
the 0th position in str2 is: 3

The original string str3 is: 123-abc-123-abc-456-EFG-456-EFG
The index of the 1st occurrence of an element of '5G' in str3 after
the 0th position is: 17
The index of the second occurrence of an element of '5G' in str3
after the 0th position is: 22

The original string str4 is: 12-ab-12-ab
The index of the 1st occurrence of an element of 'ba3' in str4 after
the 5th position is: 9
The index of the 1st occurrence of an element of 'a2' in str4 after
the 0th position is: 1
```

## <a name="basic_stringfind_last_not_of"></a><a name="find_last_not_of"></a> `basic_string::find_last_not_of`

指定した文字列の要素ではない最後の文字を文字列で検索します。

```cpp
size_type find_last_not_of(
    value_type char_value,
    size_type offset = npos) const;

size_type find_last_not_of(
    const value_type* ptr,
    size_type offset = npos) const;

size_type find_last_not_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_last_not_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>パラメーター

*`char_value`*\
メンバー関数が検索される文字値。

*`offset`*\
検索を終了する位置のインデックス。

*`ptr`*\
メンバー関数が検索される C 文字列。

*`count`*\
メンバー関数が検索される C 文字列で、最初の文字から順方向に数えた文字数。

*`str`*\
メンバー関数が検索される文字列。

### <a name="return-value"></a>戻り値

成功した場合、検索する部分文字列の最初の文字のインデックス、それ以外の場合 `npos`。

### <a name="example"></a>例

```cpp
// basic_string_find_last_not_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "dddd-1dd4-abdd" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_last_not_of ( "d" , 7 );
   if ( indexCh1a != npos )
      cout << "The index of the last non 'd'\n found before the "
           << "7th position in str1 is: " << indexCh1a << endl;
   else
      cout << "The non 'd' character was not found ." << endl;

   indexCh1b = str1.find_last_not_of  ( "d" );
   if ( indexCh1b != npos )
      cout << "The index of the non 'd' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The Character 'non x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "BBB-1111" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_last_not_of  ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the last occurrence of a "
           << "element\n not of 'B1' in str2 before the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements not of the substring 'B1' were not "
           << "\n found in str2 before the 6th position."
           << endl;

   const char *cstr2b = "B-1";
   indexCh2b = str2.find_last_not_of  ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the last element not "
           << "in 'B-1'\n is: "
           << indexCh2b << endl << endl;
   else
      cout << "The elements of the substring 'B-1' were "
           << "not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "444-555-GGG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "45G";
   indexCh3a = str3.find_last_not_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the last occurrence of an "
           << "element in str3\n other than one of the "
           << "characters in '45G' is: " << indexCh3a
           << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string  '45G'. "
           << endl;

   const char *cstr3b = "45G";
   indexCh3b = str3.find_last_not_of ( cstr3b , 6 , indexCh3a - 1 );
   if (indexCh3b != npos )
      cout << "The index of the penultimate occurrence of an "
           << "element\n not in '45G' in str3 is: "
           << indexCh3b << endl << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string '45G'. "
           << endl  << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "b-a" );
   indexCh4a = str4.find_last_not_of  ( str4a , 5 );
   if ( indexCh4a != npos )
      cout << "The index of the last occurrence of an "
           << "element not\n in 'b-a' in str4 before the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements other than those in the substring"
           << " 'b-a' were not found in the string str4."
           << endl;

   string str4b ( "12" );
   indexCh4b = str4.find_last_not_of ( str4b  );
   if ( indexCh4b != npos )
      cout << "The index of the last occurrence of an "
           << "element not in '12'\n in str4 before the end "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements other than those in the substring"
           << " '12'\n were not found in the string str4."
           << endl;
}
```

```Output
The original string str1 is: dddd-1dd4-abdd
The index of the last non 'd'
found before the 7th position in str1 is: 5
The index of the non 'd' found in str1 is: 11

The original string str2 is: BBB-1111
The index of the last occurrence of a element
not of 'B1' in str2 before the 6th position is: 3
The elements of the substring 'B-1' were not found in str2 .

The original string str3 is: 444-555-GGG
The index of the last occurrence of an element in str3
other than one of the characters in '45G' is: 7
The index of the penultimate occurrence of an element
not in '45G' in str3 is: 3

The original string str4 is: 12-ab-12-ab
The index of the last occurrence of an element not
in 'b-a' in str4 before the 5th position is: 1
The index of the last occurrence of an element not in '12'
in str4 before the end position is: 10
```

## <a name="basic_stringfind_last_of"></a><a name="find_last_of"></a> `basic_string::find_last_of`

指定された文字列の要素と一致する最後の文字を文字列で検索します。

```cpp
size_type find_last_of(
    value_type char_value,
    size_type offset = npos) const;

size_type find_last_of(
    const value_type* ptr,
    size_type offset = npos) const;

size_type find_last_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_last_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>パラメーター

*`char_value`*\
メンバー関数が検索される文字値。

*`offset`*\
検索を終了する位置のインデックス。

*`ptr`*\
メンバー関数が検索される C 文字列。

*`count`*\
メンバー関数が検索される C 文字列で、最初の文字から順方向に数えた文字数。

*`str`*\
メンバー関数が検索される文字列。

### <a name="return-value"></a>戻り値

成功した場合は検索する部分文字列の最後の文字のインデックス、それ以外の場合は `npos`。

### <a name="example"></a>例

```cpp
// basic_string_find_last_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "abcd-1234-abcd-1234" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_last_of ( "d" , 14 );
   if ( indexCh1a != npos )
      cout << "The index of the last 'd' found before the 14th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_of ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "ABCD-1234-ABCD-1234" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_last_of  ( cstr2 , 12 );
   if (indexCh2a != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'B1' in str2 before\n the 12th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not "
           << "found in str2 before the 12th position."
           << endl;

   const char *cstr2b = "D2";
   indexCh2b = str2.find_last_of  ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the last element of 'D2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'D2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "456-EFG-456-EFG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a;

   const char *cstr3a = "5E";
   indexCh3a = str3.find_last_of ( cstr3a , 8 , 8 );
   if ( indexCh3a != npos )
      cout << "The index of the last occurrence of an "
           << "element of '5E' in str3 before\n the 8th "
           << "position is: " << indexCh3a << endl << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n before the 8th position."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_last_of  ( str4a , 8 );
   if ( indexCh4a != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'ba3' in str4 before\n the 8th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements of the substring 'ba3' were not "
           << "found in str4\n after the 0th position."
           << endl;

   string str4b ( "a2" );
   indexCh4b = str4.find_last_of ( str4b  );
   if ( indexCh4b != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'a2' in str4 before\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements of the substring 'a2' were not "
           << "found in str4\n after the 0th position."
           << endl;
}
```

```Output
The original string str1 is: abcd-1234-abcd-1234
The index of the last 'd' found before the 14th position in str1 is: 13
The character 'x' was not found in str1.

The original string str2 is: ABCD-1234-ABCD-1234
The index of the last occurrence of an element of 'B1' in str2 before
the 12th position is: 11
The index of the last element of 'D2' after
the 0th position in str2 is: 16

The original string str3 is: 456-EFG-456-EFG
The index of the last occurrence of an element of '5E' in str3 before
the 8th position is: 4

The original string str4 is: 12-ab-12-ab
The index of the last occurrence of an element of 'ba3' in str4 before
the 8th position is: 4
The index of the last occurrence of an element of 'a2' in str4 before
the 0th position is: 9
```

## <a name="basic_stringfront"></a><a name="front"></a> `basic_string::front`

文字列内の最初の要素への参照を返します。

```cpp
const_reference front() const;

reference front();
```

### <a name="return-value"></a>戻り値

文字列の最初の要素への参照。空以外でなければなりません。

### <a name="remarks"></a>解説

## <a name="basic_stringget_allocator"></a><a name="get_allocator"></a> `basic_string::get_allocator`

文字列の構築に使用されるアロケーター オブジェクトのコピーを返します。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>戻り値

文字列で使用されるアロケーター。

### <a name="remarks"></a>解説

このメンバー関数は、格納されているアロケーター オブジェクトを返します。

この文字列クラスのアロケーターは、クラスがどのようにストレージを管理するかを指定します。 コンテナー クラスで提供される既定のアロケーターは、ほとんどのプログラミング要件に対応しています。 独自のアロケータークラスの記述と使用は、高度な C++ 機能です。

### <a name="example"></a>例

```cpp
// basic_string_get_allocator.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   string s1;
   basic_string <char> s2;
   basic_string <char, char_traits< char >, allocator< char > > s3;

   // s4 will use the same allocator class as s1
   basic_string <char> s4( s1.get_allocator ( ) );

   basic_string <char>::allocator_type xchar = s1.get_allocator( );
   // You can now call functions on the allocator class xchar used by s1
}
```

## <a name="basic_stringinsert"></a><a name="insert"></a> `basic_string::insert`

要素、複数の要素、または要素の範囲を、指定した位置にある文字列に挿入します。

```cpp
basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    size_type count,
    value_type char_value);

iterator insert(
    iterator iter);

iterator insert(
    iterator iter,
    value_type char_value)l
template <class InputIterator>
void insert(
    iterator iter,
    InputIterator first,
    InputIterator last);

void insert(
    iterator iter,
    size_type count,
    value_type char_value);

void insert(
    iterator iter,
    const_pointer first,
    const_pointer last);

void insert(
    iterator iter,
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>パラメーター

*`position`*\
新しい文字の挿入ポイントの背後の位置にあるインデックス。

*`ptr`*\
C 文字列全体または一部がこの文字列に挿入されます。

*`count`*\
挿入する文字の数。

*`str`*\
文字列全体または一部が対象の文字列に挿入されます。

*`offset`*\
追加する文字の元の文字列の一部のインデックス。

*`char_value`*\
挿入する要素の文字の値。

*`iter`*\
文字を挿入する背後の位置を示す反復子。

*`first`*\
`const_pointer` `const_iterator` 挿入されるソース範囲内の最初の要素を示す入力反復子、、または。

*`last`*\
`const_pointer` `const_iterator` 挿入されるソース範囲内の最後の要素の次の位置を示す入力反復子、、または。

### <a name="return-value"></a>戻り値

メンバー関数によって新しい文字が割り当てられる文字列オブジェクトへの参照。個々の文字の挿入の場合は、挿入された文字の位置を示す反復子、または none (特定のメンバー関数に応じて)。

### <a name="example"></a>例

```cpp
// basic_string_insert.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function inserting a C-string
   // at a given position
   basic_string <char> str1a ( "way" );
   const char *cstr1a = "a";
   str1a.insert ( 0, cstr1a );
   cout << "The string with a C-string inserted at position 0 is: "
        << str1a << "." << endl;

   // The second member function inserting a C-string
   // at a given position for a specified number of elements
   basic_string <char> str2a ( "Good" );
   const char *cstr2a = "Bye Bye Baby";
   str2a.insert ( 4, cstr2a ,3 );
   cout << "The string with a C-string inserted at the end is: "
        << str2a << "." << endl;

   // The third member function inserting a string
   // at a given position
   basic_string <char> str3a ( "Bye" );
   string str3b ( "Good" );
   str3a.insert ( 0, str3b );
   cout << "The string with a string inserted at position 0 is: "
        << str3a << "." << endl;

   // The fourth member function inserting part of
   // a string at a given position
   basic_string <char> str4a ( "Good " );
   string str4b ( "Bye Bye Baby" );
   str4a.insert ( 5, str4b , 8 , 4 );
   cout << "The string with part of a string inserted at position 4 is: "
        << str4a << "." << endl;

   // The fifth member function inserts a number of characters
   // at a specified position in the string
   string str5 ( "The number is: ." );
   str5.insert ( 15 , 3 , '3' );
   cout << "The string with characters inserted is: "
        << str5 << endl;

   // The sixth member function inserts a character
   // at a specified position in the string
   string str6 ( "ABCDFG" );
   basic_string <char>::iterator str6_Iter = ( str6.begin ( ) + 4 );
   str6.insert ( str6_Iter , 'e' );
   cout << "The string with a character inserted is: "
        << str6 << endl;

   // The seventh member function inserts a range
   // at a specified position in the string
   string str7a ( "ABCDHIJ" );
   string str7b ( "abcdefgh" );
   basic_string <char>::iterator str7a_Iter = (str7a.begin ( ) + 4 );
   str7a.insert ( str7a_Iter , str7b.begin ( ) + 4 , str7b.end ( ) -1 );
   cout << "The string with a character inserted from a range is: "
        << str7a << endl;

   // The eighth member function inserts a number of
   // characters at a specified position in the string
   string str8 ( "ABCDHIJ" );
   basic_string <char>::iterator str8_Iter = ( str8.begin ( ) + 4 );
   str8.insert ( str8_Iter , 3 , 'e' );
   cout << "The string with a character inserted from a range is: "
        << str8 << endl;
}
```

```Output
The string with a C-string inserted at position 0 is: away.
The string with a C-string inserted at the end is: GoodBye.
The string with a string inserted at position 0 is: GoodBye.
The string with part of a string inserted at position 4 is: Good Baby.
The string with characters inserted is: The number is: 333.
The string with a character inserted is: ABCDeFG
The string with a character inserted from a range is: ABCDefgHIJ
The string with a character inserted from a range is: ABCDeeeHIJ
```

## <a name="basic_stringiterator"></a><a name="iterator"></a> `basic_string::iterator`

文字列内の `const` 要素にアクセスし、読み取ることができるランダム アクセス反復子を提供する型。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>解説

型は、 `iterator` 文字の値を変更するために使用でき、前方方向に文字列を反復処理するために使用されます。

### <a name="example"></a>例

の [`begin`](#begin) 宣言方法や使用方法の例については、の例を参照してください `iterator` 。

## <a name="basic_stringlength"></a><a name="length"></a> `basic_string::length`

文字列内の現在の要素数を返します。

```cpp
size_type length() const;
```

### <a name="remarks"></a>解説

メンバー関数はと同じ [`size`](#size) です。

### <a name="example"></a>例

```cpp
// basic_string_length.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringmax_size"></a><a name="max_size"></a> `basic_string::max_size`

文字列が含むことができる最大文字数を返します。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

文字列が含むことができる最大文字数。

### <a name="remarks"></a>解説

型[ `length_error` クラス](../standard-library/length-error-class.md)の例外は、操作が最大サイズを超える長さの文字列を生成した場合にスローされます。

### <a name="example"></a>例

```cpp
// basic_string_max_size.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringnpos"></a><a name="npos"></a> `basic_string::npos`

検索関数でエラーが発生した場合に "見つかりません" または "すべての残りの文字" を示す-1 に初期化された符号なし整数値。

```cpp
static const size_type npos = -1;
```

### <a name="remarks"></a>解説

戻り値が値に対してチェックされるとき、戻り値が型であり、またはではない場合は `npos` 機能しない可能性があり [`size_type`](#size_type) `int` `unsigned` ます。

### <a name="example"></a>例

の [`find`](#find) 宣言方法や使用方法の例については、の例を参照してください `npos` 。

## <a name="basic_stringoperator"></a><a name="op_add_eq"></a> `basic_string::operator+=`

文字列に文字を追加します。

```cpp
basic_string<CharType, Traits, Allocator>& operator+=(
    value_type char_value);

basic_string<CharType, Traits, Allocator>& operator+=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator+=(
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*`char_value`*\
追加される文字。

*`ptr`*\
追加される C 文字列の文字。

*`right`*\
追加される文字列の文字。

### <a name="return-value"></a>戻り値

このメンバー関数によって渡された文字が付加される文字列オブジェクトへの参照。

### <a name="remarks"></a>解説

文字は、 `operator+=` またはメンバー関数またはを使用して文字列に追加でき [`append`](#append) [`push_back`](#push_back) ます。 `operator+=` が単一引数値を追加するのに対し、複数引数の append メンバー関数では、文字列の特定の部分を指定して追加できます。

### <a name="example"></a>例

```cpp
// basic_string_op_app.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // appending a single character to a string
   string str1a ( "Hello" );
   cout << "The original string str1 is: " << str1a << endl;
   str1a +=  '!' ;
   cout << "The string str1 appended with an exclamation is: "
        << str1a << endl << endl;

   // The second member function
   // appending a C-string to a string
   string  str1b ( "Hello " );
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b +=  cstr1b;
   cout << "Appending the C-string cstr1b to string str1 gives: "
        << str1b << "." << endl << endl;

   // The third member function
   // appending one string to another in two ways,
   // comparing append and operator [ ]
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World" );
   cout << "The string str2d is: " << str2d << endl;
   str1d.append ( str2d );
   cout << "The appended string str1d is: "
        << str1d << "." << endl;
   str1d += str3d;
   cout << "The doubly appended strig str1 is: "
        << str1d << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello
The string str1 appended with an exclamation is: Hello!

The C-string cstr1b is: Out There
Appending the C-string cstr1b to string str1 gives: Hello Out There.

The string str2d is: Wide
The appended string str1d is: Hello Wide .
The doubly appended strig str1 is: Hello Wide World.
```

## <a name="basic_stringoperator"></a><a name="op_eq"></a> `basic_string::operator=`

文字列の内容に新しい文字の値を割り当てます。

```cpp
basic_string<CharType, Traits, Allocator>& operator=(
    value_type char_value);

basic_string<CharType, Traits, Allocator>& operator=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>& right);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>&& right);
```

### <a name="parameters"></a>パラメーター

*`char_value`*\
割り当てられる文字値。

*`ptr`*\
対象の文字列に割り当てられる C 文字列の文字を指すポインター。

*`right`*\
対象の文字列に割り当てられる文字のソース文字列。

### <a name="return-value"></a>戻り値

このメンバー関数によって新しい文字が割り当てられる文字列オブジェクトへの参照。

### <a name="remarks"></a>解説

文字列には、新しい文字値を割り当てることができます。 新しい値には、文字列および C 文字列または単一の文字を指定できます。 `operator=`新しい値を1つのパラメーターで記述できる場合はを使用できます。それ以外の場合は、複数のパラメーターを持つメンバー関数を使用して、 [`assign`](#assign) 対象の文字列に割り当てる文字列の部分を指定できます。

### <a name="example"></a>例

```cpp
// basic_string_op_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning a
   // character of a certain value to a string
   string str1a ( "Hello " );
   str1a = '0';
   cout << "The string str1 assigned with the zero character is: "
        << str1a << endl << endl;

   // The second member function assigning the
   // characters of a C-string to a string
   string  str1b;
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b <<  "." << endl;
   str1b = cstr1b;
   cout << "Assigning the C-string cstr1a to string str1 gives: "
        << str1b << "." << endl << endl;

   // The third member function assigning the characters
   // from one string to another string in two equivalent
   // ways, comparing the assign and operator =
   string str1c ( "Hello" ), str2c ( "Wide" ), str3c ( "World" );
   cout << "The original string str1 is: " << str1c << "." << endl;
   cout << "The string str2c is: " << str2c << "." << endl;
   str1c.assign ( str2c );
   cout << "The string str1 newly assigned with string str2c is: "
        << str1c << "." << endl;
   cout << "The string str3c is: " << str3c << "." << endl;
   str1c = str3c;
   cout << "The string str1 reassigned with string str3c is: "
        << str1c << "." << endl << endl;
}
```

```Output
The string str1 assigned with the zero character is: 0

The C-string cstr1b is: Out There.
Assigning the C-string cstr1a to string str1 gives: Out There.

The original string str1 is: Hello.
The string str2c is: Wide.
The string str1 newly assigned with string str2c is: Wide.
The string str3c is: World.
The string str1 reassigned with string str3c is: World.
```

## <a name="basic_stringoperator"></a><a name="op_at"></a> `basic_string::operator[]`

文字列に指定したインデックスのある文字への参照を提供します。

```cpp
const_reference operator[](size_type offset) const;
reference operator[](size_type offset);
```

### <a name="parameters"></a>パラメーター

*`offset`*\
参照される要素の位置のインデックス。

### <a name="return-value"></a>戻り値

パラメーターのインデックスで指定した位置の文字列の文字への参照。

### <a name="remarks"></a>解説

文字列の最初の要素のインデックスは0で、次の要素は正の整数で連続してインデックスが付けられます。 長さ *n* の文字列には、 *n-1* という数値でインデックス付けされた *n* 番目の要素が含まれていることを意味します。

`operator[]` は、 [`at`](#at) 文字列の要素に対する読み取りおよび書き込みアクセスを提供するメンバー関数よりも高速です。

`operator[]` は、パラメーターとして渡されたインデックスが有効であるかどうかを確認しませんが、メンバー関数は有効なの `at` で使用する必要があります。 メンバー関数に渡されたインデックス (0 または文字列のサイズ以上のインデックス) が `at` [ `out_of_range` クラス](../standard-library/out-of-range-class.md)例外をスローしました。 無効なインデックスが `operator[]` に渡されると、未定義の動作が発生しますが、文字列の長さと等しいインデックスは、const 文字列の有効なインデックスで、このインデックスが渡されると演算子は null 文字を返します。

返される参照は、文字列の再割り当てまたは非文字列の変更によって無効にされる場合があり `const` ます。

を [`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md) 1 または2に設定してコンパイルすると、文字列の境界の外にある要素にアクセスしようとすると、ランタイムエラーが発生します。 詳細については、「[チェックを行う反復子](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// basic_string_op_ref.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );
   const string cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );
   cout << "The original string str1 is: " << str1 << endl;
   cout << "The original string str2 is: " << str2 << endl;

   // Element access to the non-const strings
   basic_string <char>::reference refStr1 = str1 [6];
   basic_string <char>::reference refStr2 = str2.at ( 3 );

   cout << "The character with an index of 6 in string str1 is: "
        << refStr1 << "." << endl;
   cout << "The character with an index of 3 in string str2 is: "
        << refStr2 << "." << endl;

   // Element access to the const strings
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );

   if ( crefStr1 == '\0' )
      cout << "The null character is returned as a valid reference."
           << endl;
   else
      cout << "The null character is not returned." << endl;
   cout << "The character with index of 8 in the const string cstr2 is: "
        << crefStr2 << "." << endl;
}
```

## <a name="basic_stringpointer"></a><a name="pointer"></a> `basic_string::pointer`

文字列または文字アレイ内の文字要素へのポインターを提供する型。

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>解説

この型は `allocator_type::pointer` の同意語です。

型の場合 `string` は、と同じ `char *` です。

### <a name="example"></a>例

```cpp
// basic_string_pointer.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   basic_string<char>::pointer pstr1a = "In Here";
   char *cstr1b = "Out There";
   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;
   cout << "The C-string cstr1b is: " << cstr1b << "." << endl;
}
```

```Output
The string pstr1a is: In Here.
The C-string cstr1b is: Out There.
```

## <a name="basic_stringpop_back"></a><a name="pop_back"></a> `basic_string::pop_back`

文字列の最後の要素を消去します。

```cpp
void pop_back();
```

### <a name="remarks"></a>解説

このメンバー関数は、事実上 `erase(size() - 1)` を呼び出して、シーケンスの最後の要素 (空であってはなりません) を消去します。

## <a name="basic_stringpush_back"></a><a name="push_back"></a> `basic_string::push_back`

文字列の末尾に要素を追加します。

```cpp
void push_back(value_type char_value);
```

### <a name="parameters"></a>パラメーター

*`char_value`*\
文字列の末尾に追加する文字。

### <a name="remarks"></a>解説

このメンバー関数は、を実際に呼び出し `insert( end, char_value )` ます。 詳細については、[`insert`](#insert) および [`end`](#end) を参照してください。

### <a name="example"></a>例

```cpp
// basic_string_push_back.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "abc" );
   basic_string <char>::iterator str_Iter, str1_Iter;

   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   // str1.push_back ( 'd' );
   str1_Iter = str1.end ( );
   str1_Iter--;
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_Iter << endl;

   cout << "The modified string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;
}
```

```Output
The original string str1 is: abc
The last character-letter of the modified str1 is now: c
The modified string str1 is: abc
```

## <a name="basic_stringrbegin"></a><a name="rbegin"></a> `basic_string::rbegin`

反転文字列の 1 つ目の要素への反復子を返します。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>戻り値

対応する通常の順序の文字列の最後の要素を指す、反転文字列内の最初の要素へのランダム アクセス反復子を返します。

### <a name="remarks"></a>解説

`rbegin` は、文字列と共に使用されるのと同じように、逆順の文字列で使用され [`begin`](#begin) ます。

の戻り値がに割り当てられている場合、 `rbegin` `const_reverse_iterator` 文字列オブジェクトは変更できません。 `rbegin` の戻り値が `reverse_iterator` に割り当てられている場合、文字列オブジェクトを変更することができます。

`rbegin` は、逆方向の文字列の反復処理を初期化するために使用できます。

### <a name="example"></a>例

```cpp
// basic_string_rbegin.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Able was I ere I saw Elba" ), str2;
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;
   basic_string <char>::const_reverse_iterator str1_rcIter;

   str1_rIter = str1.rbegin ( );
   // str1_rIter--;
   cout << "The first character-letter of the reversed string str1 is: "
        << *str1_rIter << endl;
   cout << "The full reversed string str1 is:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
   *str1_rIter = 'A';
   cout << "The first character-letter of the modified str1 is now: "
        << *str1_rIter << endl;
   cout << "The full modified reversed string str1 is now:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The following line would be an error because iterator is const
   // *str1_rcIter = 'A';

   // For an empty string, begin is equivalent to end
   if ( str2.rbegin( ) == str2.rend ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The first character-letter of the reversed string str1 is: a
The full reversed string str1 is:
ablE was I ere I saw elbA
The first character-letter of the modified str1 is now: A
The full modified reversed string str1 is now:
AblE was I ere I saw elbA
The string str2 is empty.
```

## <a name="basic_stringreference"></a><a name="reference"></a> `basic_string::reference`

文字列に格納されている要素への参照を提供する型。

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="remarks"></a>解説

型は、 `reference` 要素の値を変更するために使用できます。

この型は `allocator_type::reference` の同意語です。

型の場合 `string` は、と同じ `chr&` です。

### <a name="example"></a>例

の [`at`](#at) 宣言方法や使用方法の例については、の例を参照してください `reference` 。

## <a name="basic_stringrend"></a><a name="rend"></a> `basic_string::rend`

反転文字列内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>戻り値

反転文字列内の最後の要素の次の位置を指す逆順ランダム アクセス反復子を返します。

### <a name="remarks"></a>解説

`rend` は、文字列と共に使用されるのと同じように、逆順の文字列で使用され [`end`](#end) ます。

の戻り値がに割り当てられている場合、 `rend` `const_reverse_iterator` 文字列オブジェクトは変更できません。 `rend` の戻り値が `reverse_iterator` に割り当てられている場合、文字列オブジェクトを変更することができます。

`rend` を使って、逆順反復子が文字列の末尾に達したかどうかをテストできます。

によって返された値を `rend` 逆参照することはできません。

### <a name="example"></a>例

```cpp
// basic_string_rend.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Able was I ere I saw Elba"), str2;
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;
   basic_string <char>::const_reverse_iterator str1_rcIter;

   str1_rIter = str1.rend ( );
   str1_rIter--;
   cout << "The last character-letter of the reversed string str1 is: "
        << *str1_rIter << endl;
   cout << "The full reversed string str1 is:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
   *str1_rIter = 'o';
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_rIter << endl;
   cout << "The full modified reversed string str1 is now:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The following line would be an error because iterator is const
   // *str1_rcIter = 'T';

   // For an empty string, end is equivalent to begin
   if ( str2.rbegin( ) == str2.rend ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The last character-letter of the reversed string str1 is: A
The full reversed string str1 is:
ablE was I ere I saw elbA
The last character-letter of the modified str1 is now: o
The full modified reversed string str1 is now:
ablE was I ere I saw elbo
The string str2 is empty.
```

## <a name="basic_stringreplace"></a><a name="replace"></a> `basic_string::replace`

指定した位置にある文字列内の要素を、指定した文字、または他の範囲、文字列、または C 文字列からコピーした文字で置換します。

```cpp
basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const value_type* ptr,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type position_2,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    size_type count,
    value_type char_value);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const value_type* ptr,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    size_type number_2,
    value_type char_value);

template <class InputIterator>
basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>パラメーター

*`str`*\
オペランド文字列の文字のソースとなる文字列。

*`position_1`*\
置換の開始位置を示すオペランド文字列のインデックス。

*`number_1`*\
オペランド文字列内で置換する最大文字数。

*`position_2`*\
コピーの開始位置を示すパラメーター文字列のインデックス。

*`number_2`*\
パラメーター C 文字列から使用する最大文字数。

*`ptr`*\
オペランド文字列の文字のソースとなる C 文字列。

*`char_value`*\
オペランド文字列にコピーする文字。

*`first0`*\
オペランド文字列内で削除される最初の文字を指定する反復子。

*`last0`*\
オペランド文字列内で削除される最後の文字を指定する反復子。

*`first`*\
パラメーター文字列にコピーされる最初の文字を指定する、反復子、const_pointer、または const_iterator。

*`last`*\
パラメーター文字列にコピーされる最後の文字を指定する、反復子、const_pointer、または const_iterator。

*`count`*\
*`char_value`* がオペランド文字列にコピーされた回数。

### <a name="return-value"></a>戻り値

置換が行われたオペランド文字列。

### <a name="example"></a>例

```cpp
// basic_string_replace.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first two member functions replace
   // part of the operand string with
   // characters from a parameter string or C-string
   string result1a, result1b;
   string s1o ( "AAAAAAAA" );
   string s1p ( "BBB" );
   const char* cs1p = "CCC";
   cout << "The operand string s1o is: " << s1o << endl;
   cout << "The parameter string s1p is: " << s1p << endl;
   cout << "The parameter C-string cs1p is: " << cs1p << endl;
   result1a = s1o.replace ( 1 , 3 , s1p );
   cout << "The result of s1o.replace ( 1 , 3 , s1p )\n is "
        << "the string: " << result1a << "." << endl;
   result1b = s1o.replace ( 5 , 3 , cs1p );
   cout << "The result of s1o.replace ( 5 , 3 , cs1p )\n is "
        << "the string: " << result1b << "." << endl;
   cout << endl;

   // The third & fourth member function replace
   // part of the operand string with characters
   // form part of a parameter string or C-string
   string result2a, result2b;
   string s2o ( "AAAAAAAA" );
   string s2p ( "BBB" );
   const char* cs2p = "CCC";
   cout << "The operand string s2o is: " << s2o << endl;
   cout << "The parameter string s1p is: " << s2p << endl;
   cout << "The parameter C-string cs2p is: " << cs2p << endl;
   result2a = s2o.replace ( 1 , 3 , s2p , 1 , 2 );
   cout << "The result of s2o.replace (1, 3, s2p, 1, 2)\n is "
        << "the string: " << result2a << "." << endl;
   result2b = s2o.replace ( 4 , 3 , cs2p , 1 );
   cout << "The result of s2o.replace (4 ,3 ,cs2p)\n is "
        << "the string: " << result2b << "." << endl;
   cout << endl;

   // The fifth member function replaces
   // part of the operand string with characters
   string result3a;
   string s3o ( "AAAAAAAA" );
   char ch3p = 'C';
   cout << "The operand string s3o is: " << s3o << endl;
   cout << "The parameter character c1p is: " << ch3p << endl;
   result3a = s3o.replace ( 1 , 3 , 4 , ch3p );
   cout << "The result of s3o.replace(1, 3, 4, ch3p)\n is "
        << "the string: " << result3a << "." << endl;
   cout << endl;

   // The sixth & seventh member functions replace
   // part of the operand string, delineated with iterators,
   // with a parameter string or C-string
   string s4o ( "AAAAAAAA" );
   string s4p ( "BBB" );
   const char* cs4p = "CCC";
   cout << "The operand string s4o is: " << s4o << endl;
   cout << "The parameter string s4p is: " << s4p << endl;
   cout << "The parameter C-string cs4p is: " << cs4p << endl;
   basic_string<char>::iterator IterF0, IterL0;
   IterF0 = s4o.begin ( );
   IterL0 = s4o.begin ( ) + 3;
   string result4a, result4b;
   result4a = s4o.replace ( IterF0 , IterL0 , s4p );
   cout << "The result of s1o.replace (IterF0, IterL0, s4p)\n is "
        << "the string: " << result4a << "." << endl;
   result4b = s4o.replace ( IterF0 , IterL0 , cs4p );
   cout << "The result of s4o.replace (IterF0, IterL0, cs4p)\n is "
        << "the string: " << result4b << "." << endl;
   cout << endl;

   // The 8th member function replaces
   // part of the operand string delineated with iterators
   // with a number of characters from a parameter C-string
   string s5o ( "AAAAAAAF" );
   const char* cs5p = "CCCBB";
   cout << "The operand string s5o is: " << s5o << endl;
   cout << "The parameter C-string cs5p is: " << cs5p << endl;
   basic_string<char>::iterator IterF1, IterL1;
   IterF1 = s5o.begin ( );
   IterL1 = s5o.begin ( ) + 4;
   string result5a;
   result5a = s5o.replace ( IterF1 , IterL1 , cs5p , 4 );
   cout << "The result of s5o.replace (IterF1, IterL1, cs4p ,4)\n is "
        << "the string: " << result5a << "." << endl;
   cout << endl;

   // The 9th member function replaces
   // part of the operand string delineated with iterators
   // with specified characters
   string s6o ( "AAAAAAAG" );
   char ch6p = 'q';
   cout << "The operand string s6o is: " << s6o << endl;
   cout << "The parameter character ch6p is: " << ch6p << endl;
   basic_string<char>::iterator IterF2, IterL2;
   IterF2 = s6o.begin ( );
   IterL2 = s6o.begin ( ) + 3;
   string result6a;
   result6a = s6o.replace ( IterF2 , IterL2 , 4 , ch6p );
   cout << "The result of s6o.replace (IterF1, IterL1, 4, ch6p)\n is "
        << "the string: " << result6a << "." << endl;
   cout << endl;

   // The 10th member function replaces
   // part of the operand string delineated with iterators
   // with part of a parameter string delineated with iterators
   string s7o ( "OOOOOOO" );
   string s7p ( "PPPP" );
   cout << "The operand string s7o is: " << s7o << endl;
   cout << "The parameter string s7p is: " << s7p << endl;
   basic_string<char>::iterator IterF3, IterL3, IterF4, IterL4;
   IterF3 = s7o.begin ( ) + 1;
   IterL3 = s7o.begin ( ) + 3;
   IterF4 = s7p.begin ( );
   IterL4 = s7p.begin ( ) + 2;
   string result7a;
   result7a = s7o.replace ( IterF3 , IterL3 , IterF4 , IterL4 );
   cout << "The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)\n is "
        << "the string: " << result7a << "." << endl;
   cout << endl;
}
```

```Output
The operand string s1o is: AAAAAAAA
The parameter string s1p is: BBB
The parameter C-string cs1p is: CCC
The result of s1o.replace ( 1 , 3 , s1p )
is the string: ABBBAAAA.
The result of s1o.replace ( 5 , 3 , cs1p )
is the string: ABBBACCC.

The operand string s2o is: AAAAAAAA
The parameter string s1p is: BBB
The parameter C-string cs2p is: CCC
The result of s2o.replace (1, 3, s2p, 1, 2)
is the string: ABBAAAA.
The result of s2o.replace (4 ,3 ,cs2p)
is the string: ABBAC.

The operand string s3o is: AAAAAAAA
The parameter character c1p is: C
The result of s3o.replace(1, 3, 4, ch3p)
is the string: ACCCCAAAA.

The operand string s4o is: AAAAAAAA
The parameter string s4p is: BBB
The parameter C-string cs4p is: CCC
The result of s1o.replace (IterF0, IterL0, s4p)
is the string: BBBAAAAA.
The result of s4o.replace (IterF0, IterL0, cs4p)
is the string: CCCAAAAA.

The operand string s5o is: AAAAAAAF
The parameter C-string cs5p is: CCCBB
The result of s5o.replace (IterF1, IterL1, cs4p ,4)
is the string: CCCBAAAF.

The operand string s6o is: AAAAAAAG
The parameter character ch6p is: q
The result of s6o.replace (IterF1, IterL1, 4, ch6p)
is the string: qqqqAAAAG.

The operand string s7o is: OOOOOOO
The parameter string s7p is: PPPP
The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)
is the string: OPPOOOO.
```

## <a name="basic_stringreserve"></a><a name="reserve"></a> `basic_string::reserve`

文字列のキャパシティを少なくとも指定した数に設定します。

```cpp
void reserve(size_type count = 0);
```

### <a name="parameters"></a>パラメーター

*`count`*\
メモリが予約されている文字数。

### <a name="remarks"></a>解説

再割り当ては時間のかかるプロセスであるため、十分な容量を確保することが重要です。 また、文字列内の文字を参照するすべての参照、ポインター、および反復子を無効にします。

String オブジェクト型の容量の概念は、型のオブジェクトの場合と同じです `vector` 。 とは異なり `vector` 、メンバー関数を `reserve` 呼び出してオブジェクトの容量を縮小することができます。 要求は非バインドで、発生する場合もあればしない場合もあります。 パラメーターの既定値が0の場合、の呼び出しは、 `reserve` 現在文字列内にある文字数に合うように文字列の容量を縮小する非バインド要求です。 容量は現在の文字数より小さくなることはありません。

`reserve` の呼び出しは、文字列の容量を縮小できる唯一の方法です。 ただし、前述のように、この要求は非バインドで発生しない場合があります。

### <a name="example"></a>例

```cpp
// basic_string_reserve.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   basic_string <char>::size_type sizeStr1, sizerStr1;
   sizeStr1 = str1.size ( );
   basic_string <char>::size_type capStr1, caprStr1;
   capStr1 = str1.capacity ( );

   // Compare size & capacity of the original string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl << endl;

   // Compare size & capacity of the string
   // with added capacity
   str1.reserve ( 40 );
   sizerStr1 = str1.size ( );
   caprStr1 = str1.capacity ( );

   cout << "The string str1with augmented capacity is: "
        << str1 << endl;
   cout << "The current size of string str1 is: "
        << sizerStr1 << "." << endl;
   cout << "The new capacity of string str1 is: "
        << caprStr1 << "." << endl << endl;

   // Compare size & capacity of the string
   // with downsized capacity
   str1.reserve ( );
   basic_string <char>::size_type sizedStr1;
   basic_string <char>::size_type capdStr1;
   sizedStr1 = str1.size ( );
   capdStr1 = str1.capacity ( );

   cout << "The string str1 with downsized capacity is: "
        << str1 << endl;
   cout << "The current size of string str1 is: "
        << sizedStr1 << "." << endl;
   cout << "The reduced capacity of string str1 is: "
        << capdStr1 << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello world
The current size of original string str1 is: 11.
The capacity of original string str1 is: 15.

The string str1with augmented capacity is: Hello world
The current size of string str1 is: 11.
The new capacity of string str1 is: 47.

The string str1 with downsized capacity is: Hello world
The current size of string str1 is: 11.
The reduced capacity of string str1 is: 47.
```

## <a name="basic_stringresize"></a><a name="resize"></a> `basic_string::resize`

要素を必要に応じて追加または削除して、文字列の新しいサイズを指定します。

```cpp
void resize(
    size_type count,);

void resize(
    size_type count,
    value_type char_value);
```

### <a name="parameters"></a>パラメーター

*`count`*\
文字列の新しいサイズ。

*`char_value`*\
より多くの要素が必要な場合は、追加された文字がで初期化される値。

### <a name="remarks"></a>解説

結果のサイズが最大文字数を超えている場合、フォームは `length_error` をスローします。

### <a name="example"></a>例

```cpp
// basic_string_resize.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ( "Hello world" );
   cout << "The original string str1 is: " << str1 << endl;

   basic_string <char>::size_type sizeStr1;
   sizeStr1 = str1.size ( );
   basic_string <char>::size_type capStr1;
   capStr1 = str1.capacity ( );

   // Compare size & capacity of the original string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to increase size by 2 elements: exclamations
   str1.resize ( str1.size ( ) + 2 , '!' );
   cout << "The resized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   capStr1 = str1.capacity ( );

   // Compare size & capacity of a string after resizing
   cout << "The current size of resized string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of resized string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to increase size by 20 elements:
   str1.resize ( str1.size ( ) + 20 );
   cout << "The resized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   capStr1 = str1.capacity ( );

   // Compare size & capacity of a string after resizing
   // note capacity increases automatically as required
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to downsize by 28 elements:
   str1.resize ( str1.size ( ) - 28 );
   cout << "The downsized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size (  );
   capStr1 = str1.capacity (  );

   // Compare size & capacity of a string after downsizing
   cout << "The current size of downsized string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of downsized string str1 is: "
        << capStr1 << "." << endl;
}
```

```Output
The original string str1 is: Hello world
The current size of original string str1 is: 11.
The capacity of original string str1 is: 15.

The resized string str1 is: Hello world!!
The current size of resized string str1 is: 13.
The capacity of resized string str1 is: 15.

The resized string str1 is: Hello world!!
The current size of modified string str1 is: 33.
The capacity of modified string str1 is: 47.

The downsized string str1 is: Hello
The current size of downsized string str1 is: 5.
The capacity of downsized string str1 is: 47.
```

## <a name="basic_stringreverse_iterator"></a><a name="reverse_iterator"></a> `basic_string::reverse_iterator`

文字列に格納されている要素への参照を提供する型。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>解説

`reverse_iterator` 型は文字の値を変更するために使用でき、逆の順序で文字列を反復処理するために使用されます。

### <a name="example"></a>例

の [`rbegin`](#rbegin) 宣言方法や使用方法の例については、の例を参照してください `reverse_iterator` 。

## <a name="basic_stringrfind"></a><a name="rfind"></a> `basic_string::rfind`

指定された文字シーケンスに一致する部分文字列の最初の出現を文字列で後方に検索します。

```cpp
size_type rfind(
    value_type char_value,
    size_type offset = npos) const;

size_type rfind(
    const value_type* ptr,
    size_type offset = npos) const;

size_type rfind(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type rfind(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>パラメーター

*`char_value`*\
メンバー関数が検索される文字値。

*`offset`*\
検索を開始する位置のインデックス。

*`ptr`*\
メンバー関数が検索される C 文字列。

*`count`*\
メンバー関数が検索される C 文字列で、最初の文字から順方向に数えた文字数。

*`str`*\
メンバー関数が検索される文字列。

### <a name="return-value"></a>戻り値

成功した場合は、逆順での検索で最後に出現した部分文字列の最初の文字のインデックス、それ以外の場合は `npos`。

### <a name="example"></a>例

```cpp
// basic_string_rfind.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "Hello Everyone" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.rfind ( "e" , 9 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'e' found before the 9th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'e' was not found in str1 ." << endl;

   indexCh1b = str1.rfind ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "Let me make this perfectly clear." );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "perfect";
   indexCh2a = str2.rfind ( cstr2 , 30 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st element of 'perfect' "
           << "before\n the 30th position in str2 is: "
           << indexCh2a << endl;
   else
      cout << "The substring 'perfect' was not found in str2 ."
           << endl;

   const char *cstr2b = "imperfectly";
   indexCh2b = str2.rfind ( cstr2b , 30 );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'imperfect' "
           << "before\n the 5th position in str3 is: "
           << indexCh2b << endl;
   else
      cout << "The substring 'imperfect' was not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "It is a nice day. I am happy." );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "nice";
   indexCh3a = str3.rfind ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st element of 'nice' "
           << "in str3 is: " << indexCh3a << endl;
   else
      cout << "The substring 'nice' was not found in str3 ."
           << endl;

   const char *cstr3b = "am";
   indexCh3b = str3.rfind ( cstr3b , indexCh3a + 25 , 2 );
   if ( indexCh3b != npos )
      cout << "The index of the next occurrence of 'am' in "
           << "str3 begins at: " << indexCh3b << endl << endl;
   else
      cout << "There is no next occurrence of 'am' in str3 ."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "This perfectly unclear." );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "clear" );
   indexCh4a = str4.rfind ( str4a , 15 );
   if (indexCh4a != npos )
      cout << "The index of the 1st element of 'clear' "
           << "before\n the 15th position in str4 is: "
           << indexCh4a << endl;
   else
      cout << "The substring 'clear' was not found in str4 "
           << "before the 15th position." << endl;

   string str4b ( "clear" );
   indexCh4b = str4.rfind ( str4b );
   if ( indexCh4b != npos )
      cout << "The index of the 1st element of 'clear' "
           << "in str4 is: "
           << indexCh4b << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl << endl;
}
```

```Output
The original string str1 is: Hello Everyone
The index of the 1st 'e' found before the 9th position in str1 is: 8
The character 'x' was not found in str1.

The original string str2 is: Let me make this perfectly clear.
The index of the 1st element of 'perfect' before
the 30th position in str2 is: 17
The substring 'imperfect' was not found in str2 .

The original string str3 is: It is a nice day. I am happy.
The index of the 1st element of 'nice' in str3 is: 8
The index of the next occurrence of 'am' in str3 begins at: 20

The original string str4 is: This perfectly unclear.
The substring 'clear' was not found in str4 before the 15th position.
The index of the 1st element of 'clear' in str4 is: 17
```

## <a name="basic_stringshrink_to_fit"></a><a name="shrink_to_fit"></a> `basic_string::shrink_to_fit`

文字列の余分なキャパシティを破棄します。

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>解説

このメンバー関数は、コンテナー内の不要な記憶域を削除します。

## <a name="basic_stringsize"></a><a name="size"></a> `basic_string::size`

文字列内の現在の要素数を返します。

```cpp
size_type size() const;
```

### <a name="return-value"></a>戻り値

文字列の長さ。

### <a name="example"></a>例

```cpp
// basic_string_size.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size (  );
   lenStr1 = str1.length (  );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity (  );
   max_sizeStr1 = str1.max_size (  );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringsize_type"></a><a name="size_type"></a> `basic_string::size_type`

文字列内の要素とインデックスの数を表すことができる符号なし整数型。

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="remarks"></a>解説

これはと同じ `allocator_type::size_type` です。

型の場合 `string` は、と同じ `size_t` です。

### <a name="example"></a>例

```cpp
// basic_string_size_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" );

   basic_string <char>::size_type sizeStr1, capStr1;
   sizeStr1 = str1.size (  );
   capStr1 = str1.capacity (  );

   cout << "The current size of string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of string str1 is: " << capStr1
         << "." << endl;
}
```

```Output
The current size of string str1 is: 11.
The capacity of string str1 is: 15.
```

## <a name="basic_stringstarts_with"></a><a name="starts_with"></a> `basic_string::starts_with`

文字列が指定したプレフィックスで始まるかどうかを確認します。

```cpp
bool starts_with(const CharType c) const noexcept;
bool starts_with(const CharType* const x) const noexcept;
bool starts_with(const basic_string_view sv) const noexcept;
```

### <a name="parameters"></a>パラメーター

*`c`*\
検索する単一の文字のプレフィックス。

*`sv`*\
検索するプレフィックスを含む文字列ビュー。 \
文字列ビューに変換するを渡すことができ `std::basic_string` ます。

*`x`*\
検索するプレフィックスを格納している Null で終わる文字列。

### <a name="return-value"></a>戻り値

`true` 文字列が指定したプレフィックスで始まる場合は。 `false` それ以外の場合は。

### <a name="remarks"></a>解説

`starts_with()` は C++ 20 で新しく追加されたものです。 これを使用するには、コンパイラオプションを指定し [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) ます。

[`ends_with`](#ends_with)文字列が指定したサフィックスで終わるかどうかを確認するには、「」を参照してください。

### <a name="example"></a>例

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::basic_string<char> str = "abcdefg";

    std::cout << std::boolalpha; // so booleans show as 'true'/'false'
    std::cout << str.starts_with('b') << '\n';
    std::cout << str.starts_with("aBc") << '\n';

    std::basic_string<char> str2 = "abc";
    std::cout << str.starts_with(str2);

    return 0;
}
```

```Output
false
false
true
```

## <a name="basic_stringsubstr"></a><a name="substr"></a> `basic_string::substr`

指定された位置から始まる文字列から最大でいくつかの文字の部分文字列をコピーします。

```cpp
basic_string<CharType, Traits, Allocator> substr(
    size_type offset = 0,
    size_type count = npos) const;
```

### <a name="parameters"></a>パラメーター

*`offset`*\
文字列のコピーが作成された位置の要素を特定するインデックス (既定値は 0)。

*`count`*\
コピーされる文字数 (存在する場合)。

### <a name="return-value"></a>戻り値

最初の引数で指定された位置から始まる文字列オペランドの要素のコピーである部分文字列オブジェクト。

### <a name="example"></a>例

```cpp
// basic_string_substr.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string  str1 ("Heterological paradoxes are persistent.");
   cout << "The original string str1 is: \n " << str1
        << endl << endl;

   basic_string <char> str2 = str1.substr ( 6 , 7 );
   cout << "The substring str1 copied is: " << str2
        << endl << endl;

   basic_string <char> str3 = str1.substr (  );
   cout << "The default substring str3 is: \n " << str3
        <<  "\n which is the entire original string." << endl;
}
```

```Output
The original string str1 is:
Heterological paradoxes are persistent.

The substring str1 copied is: logical

The default substring str3 is:
Heterological paradoxes are persistent.
which is the entire original string.
```

## <a name="basic_stringswap"></a><a name="swap"></a> `basic_string::swap`

2 つの文字列の内容を交換します。

```cpp
void swap(
    basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>パラメーター

*`str`*\
コピー先の文字列と要素を交換するソース文字列。

### <a name="remarks"></a>解説

交換される文字列に同じアロケーター オブジェクトがある場合、`swap` メンバー関数は以下のように動作します。

- 一定時間で発生します。
- 例外をスローしません。
- 2 つの文字列内の要素を指定する参照、ポインター、または反復子を無効にします。

それ以外の場合は、2つの被制御シーケンス内の要素の数に比例して、要素の割り当てとコンストラクターの呼び出しが行われます。

### <a name="example"></a>例

```cpp
// basic_string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << " The basic_string s1 = " << s1 << "." << endl;
   cout << " The basic_string s2 = " << s2 << "." << endl;

   s1.swap ( s2 );
   cout << "After swapping string s1 and s2:" << endl;
   cout << " The basic_string s1 = " << s1 << "." << endl;
   cout << " The basic_string s2 = " << s2 << "." << endl;
}
```

```Output
Before swapping string s1 and s2:
The basic_string s1 = Tweedledee.
The basic_string s2 = Tweedledum.
After swapping string s1 and s2:
The basic_string s1 = Tweedledum.
The basic_string s2 = Tweedledee.
```

## <a name="basic_stringtraits_type"></a><a name="traits_type"></a> `basic_string::traits_type`

文字列に格納されている要素の文字の特徴の型。

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>解説

この型は、2番目のテンプレートパラメーターのシノニムです `Traits` 。

型の場合 `string` は、と同じ `char_traits<char>` です。

### <a name="example"></a>例

の [`copy`](../standard-library/char-traits-struct.md#copy) 宣言方法や使用方法の例については、の例を参照してください `traits_type` 。

## <a name="basic_stringvalue_type"></a><a name="value_type"></a> `basic_string::value_type`

文字列に格納された文字の型を表す型。

```cpp
typedef typename allocator_type::value_type value_type;
```

### <a name="remarks"></a>解説

これ `traits_type::char_type` はと同じで `char` あり、型のオブジェクトのと同じです `string` 。

### <a name="example"></a>例

```cpp
// basic_string_value_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   basic_string<char>::value_type ch1 = 'G';

   char ch2 = 'H';

   cout << "The character ch1 is: " << ch1 << "." << endl;
   cout << "The character ch2 is: " << ch2 << "." << endl;
}
```

```Output
The character ch1 is: G.
The character ch2 is: H.
```

## <a name="see-also"></a>関連項目

[`<string>`](../standard-library/string.md)\
[C++ 標準ライブラリのスレッドセーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
