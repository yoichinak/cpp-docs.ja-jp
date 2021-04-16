---
title: /exportHeader (ヘッダー ユニットの作成)
description: /ExportHeader コンパイラオプションを使用して、指定したヘッダー名またはインクルードファイルのモジュールヘッダー単位を作成します。
ms.date: 04/13/2020
author: tylermsft
ms.author: twhitney
f1_keywords:
- /exportHeader
helpviewer_keywords:
- /exportHeader
- Create header units
ms.openlocfilehash: 41b7d35b5468aade9515aab151b9090dcc1fb665
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577166"
---
# <a name="exportheader-create-header-units"></a>`/exportHeader` (ヘッダー ユニットの作成)

入力引数で指定されたヘッダー単位を作成するようにコンパイラに指示します。 コンパイラは、ヘッダー単位を IFC () ファイルとして生成し *`.ifc`* ます。

## <a name="syntax"></a>構文

> **`/exportHeader /headerName:angle`** *`header-name`*
> **`/exportHeader /headerName:quote`** *`header-name`*
> **`/exportHeader`** *`full path to header file`*

### <a name="arguments"></a>引数

の引数 `/exportHeader` は、 `/headerName`  *`header-name`* エクスポートするヘッダーファイルの名前を指定するコマンドラインオプションです。  

## <a name="remarks"></a>解説

**`/exportHeader`** は、Visual Studio 2019 バージョン 16.10 Preview 2 以降で使用できます。

**`/exportHeader`** コンパイラオプションでは、 [/std: c + + latest](std-specify-language-standard-version.md)オプションを有効にする必要があります。 

1つの **`/exportHeader`** コンパイラオプションで、ビルドに必要な数のヘッダー名引数を指定できます。 個別に指定する必要はありません。

コンパイラは、このスイッチを使用するときに、新しいプリプロセッサを暗黙的に有効にします。 つまり、 [`/Zc:preprocessor`](zc-preprocessor.md) コマンドラインで任意の形式のが使用されている場合、はコンパイラによってコマンドラインに追加され `/exportHeader` ます。 暗黙のを除外するには `/Zc:preprocessor` 、次のように使用します。 `/Zc:preprocessor-`

既定では、ヘッダーユニットがコンパイルされるときに、コンパイラはオブジェクトファイルを生成しません。 オブジェクトファイルを生成するには、 **`/Fo`** コンパイラオプションを指定します。 詳細については、「 [ `/Fo` (オブジェクトファイル名)](fo-object-file-name.md)」を参照してください。

補完的なオプションを使用すると役立つ場合があり **`/showResolvedHeader`** ます。 オプションは、 **`/showResolvedHeader`** 引数が解決されるファイルへの絶対パスを出力 *`header-name`* します。

**`/exportHeader`** でも、一度に複数の入力を処理でき **`/MP`** ます。 を使用し **`/ifcOutput  <directory>`** *`.ifc`* て、コンパイルごとに個別のファイルを作成することをお勧めします。

### <a name="examples"></a>使用例

などのヘッダー単位を作成するには、 `<vector>` 次のようになります。

```cmd
cl . . . /std:c++latest /exportHeader /headerName:angle vector
```

などのローカルプロジェクトヘッダーをビルドすることは、 `"utils/util.h"` 次のようになります。

```cmd
cl . . . /std:c++latest /exportHeader /headerName:quote util/util.h
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

通常、Visual Studio 開発環境ではこれを設定しないでください。 これは、ビルドシステムによって設定されます。

## <a name="see-also"></a>関連項目

[`/headerUnit` (Use header unit IFC)](headerunit.md)\
[`/reference` (名前付きモジュール IFC を使用)](module-reference.md)\
[`/translateInclude` (インクルード ディレクティブをインポート ディレクティブに変換する)](translateinclude.md)
