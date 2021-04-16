---
description: 詳細については、次を参照してください:/vmb,/vmg (表現メソッド)
title: /vmb、/vmg (処理形式)
ms.date: 04/12/2021
f1_keywords:
- /vmb
- /vmg
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.openlocfilehash: 54bff3787684906b6a932470abbfe8fb60e54cc1
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577159"
---
# <a name="vmb-vmg-representation-method"></a>`/vmb`、 `/vmg` (表現メソッド)

クラスメンバーへのポインターを表すためにコンパイラが使用するメソッドを選択します。

## <a name="syntax"></a>構文

> **`/vmb`**\
> **`/vmg`**

### <a name="options"></a>Options

**`/vmb`** は、コンパイラの既定の動作です。 その動作はと同じ `#pragma pointers_to_members(best_case)` です。 完全な型は必要ありません。 完全な型については、クラス型の継承に基づいて、単一、複数、または仮想の継承の中で最適な表現を使用します。 不完全な型の場合は、最も大きな、最も一般的な表現が使用されます。

**`/vmg`** では、クラスを定義する前に、クラスのメンバーへのポインターを宣言するために、コンパイラの動作を [ `/vmm` 、、 `/vms` `/vmv` (汎用表現)](./vmm-vms-vmv-general-purpose-representation.md)と組み合わせて指定できます。 このニーズは、互いを参照する2つの異なるクラスでメンバーを定義した場合に発生する可能性があります。 このような相互参照を行うクラスでは、定義する前に1つのクラスを参照する必要があります。

## <a name="remarks"></a>解説

[`#pragma pointers_to_members`](../../preprocessor/pointers-to-members.md)コード内でまたは[継承キーワード](../../cpp/inheritance-keywords.md)を使用して、ポインター表現を指定することもできます。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. [**構成プロパティ**] [  >  **C/c + +**  >  **コマンドライン**] プロパティページを選択します。

1. [ **追加オプション** ] ボックスにコンパイラオプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラオプション](compiler-options.md)<br/>
[MSVC コンパイラのコマンドライン構文](compiler-command-line-syntax.md)
