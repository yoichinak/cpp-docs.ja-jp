---
description: '詳細情報: C 定数式'
title: C 定数式
ms.date: 04/14/2021
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.openlocfilehash: bec55ed077a14a5d38cc934a9a755f846dd59877
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539249"
---
# <a name="c-constant-expressions"></a>C 定数式

定数式は、実行時ではなくコンパイル時に評価され、定数を使用できるすべての場所で使用できます。 定数式は、その型の表現可能な値の範囲にある定数として評価される必要があります。 定数式のオペランドは、整数定数、文字定数、浮動小数点定数、列挙定数、型キャスト、 **`sizeof`** 式、およびその他の定数式にすることができます。

## <a name="syntax"></a>構文

*`constant-expression`*:\
&emsp;*`conditional-expression`*

*`conditional-expression`*:\
&emsp;*`logical-OR-expression`*\
&emsp;*`logical-OR-expression`* **`?`** *`expression`* **`:`** *`conditional-expression`*

*`expression`*:\
&emsp;*`assignment-expression`*\
&emsp;*`expression`* **`,`** *`assignment-expression`*

*`assignment-expression`*:\
&emsp;*`conditional-expression`*\
&emsp;*`unary-expression`* *`assignment-operator`* *`assignment-expression`*

*`assignment-operator`* : 次のいずれか\
&emsp;**`=`** **`*=`** **`/=`** **`%=`** **`+=`** **`-=`** **`<<=`** **`>>=`** **`&=`** **`^=`** **`|=`**

構造体宣言子、列挙子、直接宣言子、直接抽象宣言子、およびラベル付きステートメントの非終端要素には、 *`constant-expression`* 非終端要素が含まれます。

整数定数式は、構造体のビット フィールド メンバーのサイズ、列挙定数の値、配列のサイズ、または **`case`** 定数の値を指定するために使用する必要があります。

プリプロセッサ ディレクティブに使用される定数式には、いくつかの制限があります。 これらは、*制限付き* 定数式と呼ばれています。 制限付き定数式には、 **`sizeof`** 式、列挙の定数、任意の型への型キャスト、または浮動小数点型の定数を含めることはできません。 ただし、特別な定数式 **`defined (`** _identifier_ **`)`** は含めることができます。

## <a name="see-also"></a>関連項目

[オペランドおよび式](../c-language/operands-and-expressions.md)
