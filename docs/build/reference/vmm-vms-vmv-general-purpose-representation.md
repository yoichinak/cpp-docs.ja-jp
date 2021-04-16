---
description: 詳細については、次を参照してください:/vmm、/dns、/vmv (General Purpose 表現)
title: /vmm、/vms、/vmv (通常の最適化)
ms.date: 04/12/2021
f1_keywords:
- /vms
- /vmm
- /vmv
helpviewer_keywords:
- Virtual Inheritance compiler option
- general purpose representation compiler options
- vms compiler option [C++]
- vmm compiler option [C++]
- /vmm compiler option [C++]
- -vmm compiler option [C++]
- -vms compiler option [C++]
- /vms compiler option [C++]
- vmv compiler option [C++]
- /vmv compiler option [C++]
- Single Inheritance compiler option
- -vmv compiler option [C++]
ms.openlocfilehash: 28845fffe50b64e028b39fe92c82070ed4d188fa
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577120"
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>`/vmm`、 `/vms` 、 `/vmv` (General Purpose 表現)

[`/vmg`](vmb-vmg-representation-method.md)が[表現方法](vmb-vmg-representation-method.md)として選択されている場合に使用されます。 これらのオプションは、まだ検出されていないクラス定義の継承モデルを示します。

## <a name="syntax"></a>構文

> **`/vmm`**\
> **`/vms`**\
> **`/vmv`**

### <a name="options"></a>Options

**`/vmm`**\
クラスのメンバーへのポインターの最も一般的な表現を、多重継承を使用するクラスとして指定します。

に対応する [継承キーワード](../../cpp/inheritance-keywords.md) および引数 [`#pragma pointers_to_members`](../../preprocessor/pointers-to-members.md) が **`multiple_inheritance`** です。

この表現は、単一継承に必要な表現よりも大きくなります。

を使用 **`/vmm`** し、仮想継承モデルを持つクラスのメンバーへのポインターを宣言すると、コンパイラによってエラーが生成されます。

**`/vms`**\
クラスのメンバーへのポインターを、継承も単一継承も使用しない場合の最も一般的な表現を指定します。に対応する [継承キーワード](../../cpp/inheritance-keywords.md) および引数 [`#pragma pointers_to_members`](../../preprocessor/pointers-to-members.md) が **`single_inheritance`** です。

このオプションを使用すると、クラスのメンバーへのポインターの最小の表現が生成されます。

を使用 **`/vms`** し、複数のまたは仮想継承モデルを持つクラスのメンバーへのポインターを宣言すると、コンパイラによってエラーが生成されます。

**`/vmv`**\
仮想継承を使用するクラスのメンバーへのポインターの最も一般的な表現を指定します。 このポインター表現ではエラーは発生せず、既定値です。

に対応する [継承キーワード](../../cpp/inheritance-keywords.md) および引数 [`#pragma pointers_to_members`](../../preprocessor/pointers-to-members.md) が **`virtual_inheritance`** です。

このオプションでは、他のオプションよりも大きなポインターと、ポインターを解釈するためのコードが必要です。

## <a name="remarks"></a>解説

Visual Studio 2019 以前のバージョンでは、Microsoft は pointer-to-member 型に対して異なる表現 (異なるサイズの) を使用しています。 継承または単一継承のないクラスのメンバーへのポインターは、最小の表現です。 複数の継承を持つクラスのメンバーへのポインターは大きくなります。 仮想継承を持つクラスのメンバーへのポインターが最も大きくなります。 コンパイラに対して表現モデルが指定されていない場合、既定で最も大きい、最も一般的な表現が使用されます。

これらの継承モデルのオプションのいずれかを指定すると、そのモデルは、継承の種類に関係なく、クラスメンバーへのすべてのポインターに使用されます。また、クラスの前または後にポインターを宣言するかどうかも指定します。 常に単一継承クラスを使用する場合は、を使用してコンパイルすることで、コードサイズを減らすことができ **`/vms`** ます。 ただし、最も一般的なケースを使用する場合は (最大のデータ表現を使用した場合)、を使用してコンパイルし **`/vmv`** ます。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. [**構成プロパティ**] [  >  **C/c + +**  >  **コマンドライン**] プロパティページを選択します。

1. [ **追加オプション** ] ボックスにコンパイラオプションを入力します。


### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[`/vmb`、 `/vmg` (表現メソッド)](vmb-vmg-representation-method.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラのコマンドライン構文](compiler-command-line-syntax.md)
