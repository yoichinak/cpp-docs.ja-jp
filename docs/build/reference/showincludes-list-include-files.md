---
description: 詳細情報:/showIncludes (インクルードファイルの一覧)
title: /showIncludes (インクルード ファイル一覧)
ms.date: 04/15/2021
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ShowIncludes
- VC.Project.VCCLCompilerTool.ShowIncludes
- /showincludes
helpviewer_keywords:
- include files
- /showIncludes compiler option [C++]
- include files, displaying in compilation
- -showIncludes compiler option [C++]
- showIncludes compiler option [C++]
ms.openlocfilehash: 3c960b7b88b9d96cde54f535bffbaf67dd3f67b6
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539250"
---
# <a name="showincludes-list-include-files"></a>`/showIncludes` (インクルードファイルの一覧表示)

コンパイラがインクルードファイルのリストを出力するようにします。 オプションには、入れ子になったインクルードファイル、つまり、含めるファイルに含まれるファイルも表示されます。

## <a name="syntax"></a>構文

> **`/showIncludes`**

## <a name="remarks"></a>解説

コンパイル中にコンパイラがインクルードファイルを取得すると、次の例のようにメッセージが出力されます。

```cmd
Note: including file: d:\MyDir\include\stdio.h
```

入れ子になったインクルードファイルは、次の例のように、入れ子のレベルごとに1つのスペースで、インデントによって示されます。

```cmd
Note: including file: d:\temp\1.h
Note: including file:  d:\temp\2.h
```

この場合、 *`2.h`* が内から追加され、 *`1.h`* インデントが発生します。

**`/showIncludes`** オプションは `stderr` 、ではなく、に出力され `stdout` ます。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. [**構成プロパティ**] [  >  **C/c + +**]  >  **[詳細設定**] プロパティページを選択します。

1. **Show インクルード** プロパティを変更します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラオプション](compiler-options.md)\
[MSVC コンパイラのコマンドライン構文](compiler-command-line-syntax.md)
