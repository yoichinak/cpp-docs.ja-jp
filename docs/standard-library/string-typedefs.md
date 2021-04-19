---
description: 詳細については、「 &lt; string typedef」を参照してください。 &gt;
title: '&lt;string&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 544d84b68b284b7da140d663b916277cc9156ab4
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721383"
---
# <a name="string-typedefs"></a>`<string>` typedefs

[`string`](#string)\
[`u16string`](#u16string)\
[`u32string`](#u32string)\
[`wstring`](#wstring)

## <a name="string"></a><a name="string"></a> `string`

[`basic_string`](../standard-library/basic-string-class.md)型の要素を持つクラステンプレートの特殊化を記述する型 **`char`** 。

特化された他の typedef には `basic_string` [`wstring`](../standard-library/string-typedefs.md#wstring) 、、 [`u16string`](../standard-library/string-typedefs.md#u16string) 、およびがあり [`u32string`](../standard-library/string-typedefs.md#u32string) ます。

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>解説

次の宣言は等価です。

```cpp
string str("");

basic_string<char> str("");
```

文字列コンストラクターの一覧については、「」を参照してください [`basic_string::basic_string`](../standard-library/basic-string-class.md#basic_string) 。

## <a name="u16string"></a><a name="u16string"></a> `u16string`

[`basic_string`](../standard-library/basic-string-class.md)型の要素を持つクラステンプレートの特殊化を記述する型 **`char16_t`** 。

特化された他の typedef には `basic_string` [`wstring`](../standard-library/string-typedefs.md#wstring) 、、 [`string`](../standard-library/string-typedefs.md#string) 、およびがあり [`u32string`](../standard-library/string-typedefs.md#u32string) ます。

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>解説

文字列コンストラクターの一覧については、「」を参照してください [`basic_string::basic_string`](../standard-library/basic-string-class.md#basic_string) 。

## <a name="u32string"></a><a name="u32string"></a> `u32string`

[`basic_string`](../standard-library/basic-string-class.md)型の要素を持つクラステンプレートの特殊化を記述する型 **`char32_t`** 。

特化された他の typedef には `basic_string` [`string`](../standard-library/string-typedefs.md#string) 、、 [`u16string`](../standard-library/string-typedefs.md#u16string) 、およびがあり [`wstring`](../standard-library/string-typedefs.md#wstring) ます。

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>解説

文字列コンストラクターの一覧については、「」を参照してください [`basic_string::basic_string`](../standard-library/basic-string-class.md#basic_string) 。

## <a name="wstring"></a><a name="wstring"></a> `wstring`

[`basic_string`](../standard-library/basic-string-class.md)型の要素を持つクラステンプレートの特殊化を記述する型 **`wchar_t`** 。

特化された他の typedef には `basic_string` [`string`](../standard-library/string-typedefs.md#string) 、、 [`u16string`](../standard-library/string-typedefs.md#u16string) 、およびがあり [`u32string`](../standard-library/string-typedefs.md#u32string) ます。

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>解説

次の宣言は等価です。

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

文字列コンストラクターの一覧については、「」を参照してください [`basic_string::basic_string`](../standard-library/basic-string-class.md#basic_string) 。

> [!NOTE]
> のサイズ **`wchar_t`** は実装で定義されています。 コードが特定のサイズに依存している場合は **`wchar_t`** 、プラットフォームの実装 (など) を確認し `sizeof(wchar_t)` ます。 すべてのプラットフォームで同じままであることが保証されている長さの文字列文字型が必要な場合は [`string`](../standard-library/string-typedefs.md#string) 、、 [`u16string`](../standard-library/string-typedefs.md#u16string) 、またはを使用し [`u32string`](../standard-library/string-typedefs.md#u32string) ます。

## <a name="see-also"></a>関連項目

[`<string>`](../standard-library/string.md)
