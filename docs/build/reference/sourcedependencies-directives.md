---
title: '/sourceDependencies: ディレクティブ (モジュールとヘッダー ユニットの依存関係一覧)'
description: 'Microsoft C++ の/sourceDependencies: ディレクティブコンパイラオプションのリファレンスガイド。'
ms.date: 04/13/2020
author: tylermsft
ms.author: twhitney
f1_keywords:
- /sourceDependencies:directives
helpviewer_keywords:
- /sourceDependencies:directives compiler option
- /sourceDependencies:directives
ms.openlocfilehash: 6ac33db30a007226382d3ac331ab5f2699a85c8c
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577133"
---
# <a name="sourcedependenciesdirectives-list-module-and-header-unit-dependencies"></a>`/sourceDependencies:directives` (List モジュールとヘッダーユニットの依存関係)

このコマンドラインスイッチでは、モジュールとヘッダーの単位の依存関係を一覧表示する JSON ファイルが生成されます。

このメソッドは、コンパイルする必要があるモジュールとヘッダーユニットを識別してから、それらを使用するプロジェクトがコンパイルされるようにします。 たとえば、 `import <library>;` は、ヘッダー単位の依存関係として、または `import "library";` `import name;` モジュールの依存関係として一覧表示されます。

このコマンドラインオプションはと似 [`/sourceDependencies`](sourcedependencies.md) ていますが、次の点が異なります。

- コンパイラはコンパイルされた出力を生成しません。 代わりに、モジュールディレクティブのファイルがスキャンされます。 コンパイル済みのコード、モジュール、またはヘッダー単位は生成されません。
- *`.ifc`* このスイッチではコンパイルではなくプロジェクトファイルのスキャンが行われるため、出力 JSON ファイルにはインポートされたモジュールとインポートされたヘッダーユニット (ファイル) の一覧が表示されません。 そのため、一覧に作成されたモジュールまたはヘッダーユニットはありません。
- 直接インポートされたモジュールまたはヘッダーユニットのみが一覧表示されます。 インポートされたモジュールまたはヘッダーユニット自体の依存関係は表示されません。
- ヘッダーファイルの依存関係は表示されません。 つまり、 `#include <file>` または `#include "file"` 依存関係は表示されません。
- `/sourceDependencies:directives` は、ファイルをビルドする前に使用することを意図してい *`.ifc`* ます。

## <a name="syntax"></a>構文

> **`/sourceDependencies:directives`** -\
> **`/sourceDependencies:directives`***ファイル名*\
> **`/sourceDependencies:directives`***ディレクトリ*\

## <a name="arguments"></a>引数

*`-`*\
単一点ダッシュが指定されている場合、コンパイラは、ソースの依存関係 JSON をに出力し `stdout` ます。または、コンパイラ出力がにリダイレクトされる場所に出力します。

*`filename`*\
コンパイラは、指定されたファイル名にソースの依存関係の出力を書き込みます。このファイルには、相対パスまたは絶対パスを含めることができます。

*`directory`*\
引数がディレクトリの場合、コンパイラは指定されたディレクトリにソース依存関係ファイルを生成します。 出力ファイル名は、入力ファイルの完全な名前に基づき、拡張子が追加され *`.json`* ます。 たとえば、コンパイラに指定されたファイルがの場合、 *`main.cpp`* 生成される出力ファイル名はに *`main.cpp.json`* なります。

## <a name="remarks"></a>解説

**`/sourceDependencies:directives`** は、Visual Studio 2019 バージョン 16.10 Preview 2 以降で使用できます。 既定では有効になっていません。

コンパイラオプションを指定する場合は **`/MP`** 、 **`/sourceDependencies`** ディレクトリ引数と共にを使用することをお勧めします。 1つのファイル名引数を指定すると、コンパイラの2つのインスタンスが同時に出力ファイルを開こうとしてエラーが発生する可能性があります。 の詳細につい **`/MP`** ては、「 [ `/MP` (複数のプロセスを使用したビルド)](mp-build-with-multiple-processes.md)」を参照してください。

致命的ではないコンパイラエラーが発生した場合でも、依存関係情報は出力ファイルに書き込まれます。

すべてのファイルパスは、出力に絶対パスとして表示されます。

### <a name="examples"></a>使用例

次のサンプルコードを指定します。

```cpp
//main.cpp:
#include <vector>

import m;
import std.core;

import <utility>;

import "t.h";

int main() {}
```

> `cl /std:c++latest /sourceDependencies:directives output.json main.cpp`

このコマンドラインでは、 *`output.json`* 次のような内容の JSON ファイルが生成されます。

```JSON
{
   "Version":"1.1",
   "Data":{
      "Source":"C:\\a\\b\\main.cpp",
      "ProvidedModule":"",
      "ImportedModules":[
         "m",
         "std.core"
      ],
      "ImportedHeaderUnits":[
         "C:\\...\\utility",
         "C:\\a\\b\\t.h"
      ]
   }
}
```

報告される `...` パスを省略するために使用しました。 レポートには絶対パスが含まれます。 報告されるパスは、コンパイラが依存関係を検出した場所によって異なります。 結果が予期しないものである場合は、プロジェクトのインクルードパス設定を確認することをお勧めします。

`ProvidedModule` エクスポートされたモジュールまたはモジュールのパーティション名を一覧表示します。

*`.ifc`* 作成されていないため、出力にはファイルが一覧表示されません。 とは異なり、 `/sourceDependencies` が指定されている場合、コンパイラはコンパイル済みの出力を生成しない `/sourceDependencies:directives` ため、インポートするコンパイル済みモジュールまたはヘッダー単位は生成されません。

## <a name="to-set-this-compiler-option-in-visual-studio"></a>このコンパイラ オプションを Visual Studio で使用するには

通常、Visual Studio 開発環境でこれを設定することはできません。 これは、ビルドシステムによって設定されます。

## <a name="see-also"></a>関連項目

[MSVC コンパイラオプション](compiler-options.md)\
[MSVC コンパイラのコマンドライン構文](compiler-command-line-syntax.md)