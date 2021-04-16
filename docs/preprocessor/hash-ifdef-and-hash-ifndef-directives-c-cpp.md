---
description: '詳細情報: #ifdef ディレクティブと #ifndef ディレクティブ (C/c + +)'
title: '#ifdef および #ifndef ディレクティブ (C/C++)'
ms.date: 04/14/2021
f1_keywords:
- '#ifndef'
- '#ifdef'
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.openlocfilehash: 8a5d65f22e3ea5d7324c5c4c2d1222f74140ebc0
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577413"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>`#ifdef``#ifndef`ディレクティブとディレクティブ (C/c + +)

**`#ifdef`** および **`#ifndef`** プリプロセッサディレクティブは、演算子と共に使用する場合、ディレクティブと同じ効果があり [`#if`](hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) **`defined`** ます。

## <a name="syntax"></a>構文

> **`#ifdef`** *`identifier`*\
> **`#ifndef`** *`identifier`*

これらのディレクティブは次のようになります。

> **`#if defined`** *`identifier`*\
> **`#if !defined`** *`identifier`*

## <a name="remarks"></a>解説

任意の場所で **`#ifdef`** 使用できるディレクティブとディレクティブを使用でき **`#ifndef`** `#if` ます。 **`#ifdef`** *`identifier`* ステートメントは、 `#if 1` *`identifier`* が定義されている場合と同じです。 これ `#if 0` *`identifier`* は、が定義されていない場合、またはディレクティブによって未定義になっている場合に相当し **`#undef`** ます。 これらのディレクティブは、C または C++ ソース コードで宣言された識別子ではなく、`#define` で定義された識別子の有無を調べます。

これらのディレクティブは、言語の以前のバージョンとの互換性を維持するために用意されています。 **`defined(`** *`identifier`* **`)`** ディレクティブと共に使用される定数式 `#if` が推奨されます。

ディレクティブは、チェックされた **`#ifndef`** 条件の反対をチェックし **`#ifdef`** ます。 識別子が定義されていない場合、または定義がで削除されている場合 `#undef` 、条件は true (0 以外) になります。 それ以外の場合、条件は False (0) です。

**Microsoft 固有の仕様**

この *識別子* は、オプションを使用してコマンドラインから渡すことができ [`/D`](../build/reference/d-preprocessor-definitions.md) ます。 では、最大30個のマクロを指定でき `/D` ます。

ディレクティブは、定義が **`#ifdef`** 存在するかどうかを確認する場合に役立ちます。これは、コマンドラインから定義を渡すことができるためです。 次に例を示します。

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[プリプロセッサ ディレクティブ](../preprocessor/preprocessor-directives.md)
