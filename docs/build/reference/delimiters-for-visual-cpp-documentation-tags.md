---
description: '詳細情報: Visual C++ ドキュメントタグの区切り記号'
title: Visual C++ ドキュメント タグの区切り記号
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
ms.openlocfilehash: 7878fa0454af9eb09c4aa537a3e59d8af4a3ee87
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201470"
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Visual C++ ドキュメント タグの区切り記号

ドキュメント タグでは区切り記号を使用し、ドキュメント コメントの開始位置と終了位置をコンパイラに示す必要があります。

XML ドキュメント タグでは、次の種類の区切り記号を使用できます。

| 区切り記号 | 説明 |
|-|-|
| `///` | これは、ドキュメントの例に示されており、Visual Studio C++ プロジェクトテンプレートで使用されるフォームです。  |
| `/** */`  | これらは複数行の区切り記号です。  |

`/** */` 区切り記号を使用する場合は、次のいくつかの書式設定規則があります。

- `/**` 区切り記号を含む行では、行の残りの部分が空白の場合、その行はコメントとして処理されません。 最初の文字が空白の場合、その空白文字は無視され、行の残りの部分が処理されます。 それ以外の場合、`/**` 区切り記号の後にある行のテキスト全体が、コメントの一部として処理されます。

- `*/` 区切り記号を含む行では、`*/` 区切り記号までの部分がすべて空白の場合、その行は無視されます。 それ以外の場合、以下の箇条書きで説明するパターン一致規則に従って、その行の `*/` 区切り記号までのテキストがコメントの一部として処理されます。

- `/**` 区切り記号で始まる行の後にある行では、コンパイラは各行の先頭で共通のパターンを検索します。このパターンは、空白 (省略可能) + アスタリスク (`*`) + 空白 (省略可能) で構成されます。 コンパイラは、各行の先頭で共通の文字セットを見つけた場合、`/**` 区切り記号の後にあるすべての行のそのパターンを無視します。これらの行には、`*/` 区切り記号がある行まで (その行を含む) が含まれることがあります。

次に例をいくつか示します。

- 次のコメントでは、`<summary>` で始まる行だけがコメントの一部として処理されます。 次の 2 つのタグ形式では同じコメントが生成されます。

    ```cpp
    /**
    <summary>text</summary>
    */
    /** <summary>text</summary> */
    ```

- コンパイラは、2 行目と 3 行目の先頭で無視するために " \* " というパターンを適用します。

    ```cpp
    /**
     * <summary>
     *  text </summary>*/
    ```

- 2 行目にはアスタリスクがないため、コンパイラはこのコメントでパターンを検出しません。 そのため、`*/` までの、2 行目と 3 行目のすべてのテキストは、コメントの一部として処理されます。

    ```cpp
    /**
     * <summary>
       text </summary>*/
    ```

- コンパイラでは、2 つの理由により、このコメントのパターンが検出されません。 まず、各行のアスタリスクの前の空白の数が一致していません。 次に、5 行目がタブで始まっています。空白とタブは一致しません。 そのため、2 行目から `*/` までのすべてのテキストはコメントの一部として処理されます。

    ```cpp
    /**
      * <summary>
      * text
     *  text2
       *  </summary>
    */
    ```

## <a name="see-also"></a>関連項目

[XML に関するドキュメント](xml-documentation-visual-cpp.md)
