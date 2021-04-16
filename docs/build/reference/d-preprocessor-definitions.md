---
description: 詳細情報:/D (プリプロセッサの定義)
title: /D (プリプロセッサの定義)
ms.date: 09/18/2019
f1_keywords:
- VC.Project.VCNMakeTool.PreprocessorDefinitions
- VC.Project.VCCLCompilerTool.PreprocessorDefinitions
- /d
helpviewer_keywords:
- preprocessor definition symbols
- constants, defining
- macros, compiling
- /D compiler option [C++]
- -D compiler option [C++]
- D compiler option [C++]
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
ms.openlocfilehash: 2e94c28c094f6ea03eacdb04c452785511fb3a3f
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539665"
---
# <a name="d-preprocessor-definitions"></a>/D (プリプロセッサの定義)

ソース ファイルのプリプロセッサ シンボルを定義します。

## <a name="syntax"></a>Syntax

> **`/D`**\[]_名前_ \[ `=` &vert; `#` \[ {*文字列* &vert; *数値*}]] \
> **`/D`**\[] `"` _名前_ \[ `=` &vert; `#` \[ {*文字列* &vert; *数値*}]]`"`

## <a name="remarks"></a>注釈

このシンボルを `#if` または `#ifdef` と一緒に使用すると、ソース コードを条件付きでコンパイルできます。 シンボル定義は、コード内で再定義されるか、ディレクティブによってコード内で定義されるまで、有効なままです `#undef` 。

**`/D`** は、 `#define` ソースコードファイルの先頭にあるディレクティブと同じ効果があります。 違いは、 **`/D`** コマンドラインで引用符を取り除くことと、ディレクティブを保持することです `#define` 。 と記号の間には空白を含めることができ **`/D`** ます。 記号と等号の間、または等号と代入された値の間に空白を入れることはできません。

既定では、シンボルに関連付けられる値は 1 です。 たとえば、`/D name` は、`/D name=1` と同じです。 この記事の最後にある例では、の定義を `TEST` 印刷するように示してい `1` ます。

を使用してコンパイル `/D name=` すると、シンボル *名* に関連付けられた値がないことになります。 シンボルは引き続きコードの条件コンパイルに使用できますが、何も指定されていないものとして評価されます。 この例では、を使用してコンパイルすると `/DTEST=` 、エラーが発生します。 この動作は、値を指定して、または値を指定せずに `#define` を使用する場合と似ています。

オプションでは、 **`/D`** 関数に似たマクロ定義がサポートされていません。 コマンドラインで定義できない定義を挿入するには、 [ `/FI` (強制インクルードファイルの名前の指定)](fi-name-forced-include-file.md)コンパイラオプションを使用することをお勧めします。

**`/D`** コマンドラインで複数回使用して、さらに多くのシンボルを定義することができます。 同じシンボルが複数回定義されている場合は、最後の定義が使用されます。

次のコマンドを実行すると、TEST.c で DEBUG シンボルが定義されます。

```cmd
CL /DDEBUG TEST.C
```

このコマンドを実行すると、 **`__far`** TEST. c でキーワードがすべて削除されます。

```cmd
CL /D __far= TEST.C
```

**CL** 環境変数を等号を含む文字列に設定することはできません。 環境変数と共に使用するには、 **`/D`** **`CL`** 等号 () ではなくシャープ記号 () を指定する必要があり `#` ます。

```cmd
SET CL=/DTEST#0
```

コマンド プロンプトでプリプロセッサ シンボルを定義する場合は、コンパイラ解析規則とシェル解析規則の両方を考慮してください。 たとえば、プログラムでパーセント記号のプリプロセスシンボル () を定義するには、 `%` コマンドプロンプトで2つのパーセント記号 () を指定し `%%` ます。 1つだけを指定した場合は、解析エラーが生成されます。

```cmd
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳しくは、「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](../working-with-project-properties.md)」をご覧ください。

1. [**構成プロパティ**] [  >  **C/c + +**] [  >  **プリプロセッサ**] プロパティページを選択します。

1. [ **プリプロセッサの定義** ] プロパティのドロップダウンメニューを開き、[ **編集**] を選択します。

1. [ **プリプロセッサの定義** ] ダイアログボックスで、1行につき1つ以上の定義を追加、変更、または削除します。 **[OK]** を選択して変更を保存します。

   ここで指定する定義に '/D ' オプションプレフィックスを含める必要はありません。 プロパティページでは、定義はセミコロン () で区切られ `;` ます。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>

## <a name="example"></a>例

```cpp
// cpp_D_compiler_option.cpp
// compile with: cl /EHsc /DTEST cpp_D_compiler_option.cpp
#include <stdio.h>

int main( )
{
#ifdef TEST
    printf_s("TEST defined %d\n", TEST);
#else
    printf_s("TEST not defined\n");
#endif
}
```

```Output
TEST defined 1
```

## <a name="see-also"></a>関連項目

[MSVC コンパイラオプション](compiler-options.md)\
[MSVC コンパイラのコマンドライン構文](compiler-command-line-syntax.md)\
[`/FI` (強制インクルードファイルの名前の指定)](fi-name-forced-include-file.md)\
[`/U`、 `/u` (シンボルの未定義)](u-u-undefine-symbols.md)\
[`#undef` ディレクティブ (C/c + +)](../../preprocessor/hash-undef-directive-c-cpp.md)\
[`#define` ディレクティブ (C/c + +)](../../preprocessor/hash-define-directive-c-cpp.md)
