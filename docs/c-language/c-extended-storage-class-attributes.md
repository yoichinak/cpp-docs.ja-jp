---
description: '詳細情報: C 拡張ストレージ クラス属性'
title: C の拡張ストレージ クラス属性
ms.date: 04/14/2021
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.openlocfilehash: 6c77760997d2952a299efda90f2dbbe4eb46e629
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539326"
---
# <a name="c-extended-storage-class-attributes"></a>C の拡張ストレージ クラス属性

**Microsoft 固有の仕様**

ストレージ クラス属性のその他の最新情報については、[`__declspec` (C++ リファレンス)](../cpp/declspec.md) に関するページを参照してください。

拡張属性構文は、Microsoft 固有の C 言語拡張機能を簡略化し、標準化します。 拡張属性構文を使用するストレージ クラス属性には、 **`thread`** 、 **`naked`** 、 **`dllimport`** および **`dllexport`** があります。

拡張属性構文でストレージ クラス情報を指定する場合、 **`__declspec`** キーワードを使用します。これでは、特定の型のインスタンスを Microsoft 固有のストレージ クラス属性 ( **`thread`** 、 **`naked`** **`dllimport`** 、または **`dllexport`** ) と共に保存することを指定します。 ストレージ クラス修飾子の例には、他に **`static`** および **`extern`** キーワードがあります。 ただし、これらのキーワードは ISO C 標準の一部であり、拡張属性構文では扱われません。

## <a name="syntax"></a>構文

*`storage-class-specifier`*:<br/>
&emsp; **`__declspec (`** *`extended-decl-modifier-seq`* **`)`**  /\* Microsoft 固有の仕様 \*/

*`extended-decl-modifier-seq`* :&emsp;/\* Microsoft 固有の仕様 \*/<br/>
&emsp; *`extended-decl-modifier`* <sub>opt</sub><br/>
&emsp;*`extended-decl-modifier-seq`* *`extended-decl-modifier`*

*`extended-decl-modifier`* :&emsp;/\* Microsoft 固有の仕様 \*/<br/>
&emsp;**`thread`**<br/>
&emsp;**`naked`**<br/>
&emsp;**`dllimport`**<br/>
&emsp;**`dllexport`**

空白は、宣言修飾子を区切ります。 *`extended-decl-modifier-seq`* は空白にできます。この場合、 **`__declspec`** による影響はありません。

**`thread`** 、 **`naked`** 、 **`dllimport`** 、および **`dllexport`** ストレージ クラス属性は、適用先のオブジェクトまたは関数の宣言のプロパテでしかありません。 関数自体の型属性は再定義しません。 **`thread`** 属性はデータにのみ影響を与えます。 **`naked`** 属性は関数にのみ影響を与えます。 **`dllimport`** および **`dllexport`** 属性は関数とデータに影響を与えます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[宣言と型](../c-language/declarations-and-types.md)
