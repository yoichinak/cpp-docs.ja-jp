---
description: '詳細情報: 解析ツリーについて'
title: ATL レジストラーと解析ツリー
ms.date: 04/15/2021
helpviewer_keywords:
- parse trees
ms.openlocfilehash: b9442651d8d6e04ee6c309c9d93b76135fe05c57
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539541"
---
# <a name="understanding-parse-trees"></a>パース ツリーを理解する

レジストラースクリプトでは、1つまたは複数の解析ツリーを定義できます。各解析ツリーには次の形式があります。

> \<root-key>{\<registry expression>}+

各値の説明:

> *\<root-key>* ::=\
> &emsp;**`HKEY_CLASSES_ROOT`** &vert; **`HKEY_CURRENT_USER`** &vert;\
> &emsp;**`HKEY_LOCAL_MACHINE`** &vert; **`HKEY_USERS`** &vert;\
> &emsp;**`HKEY_PERFORMANCE_DATA`** &vert; **`HKEY_DYN_DATA`** &vert;\
> &emsp;**`HKEY_CURRENT_CONFIG`** &vert; **`HKCR`** &vert; **`HKCU`** &vert;\
> &emsp;**`HKLM`** &vert; **`HKU`** &vert; **`HKPD`** &vert; **`HKDD`** &vert; **`HKCC`**
>
> *\<registry-expression>* ::=\
> &emsp; *\<Add-Key>* &vert; *\<Delete-Key>*
>
> *\<Add-Key>* ::=\
> &emsp; \[**`ForceRemove`** &vert; **`NoRemove`** &vert; **`val`**] *\<Key-Name>* \[*\<Key-Value>*] \[ **`{`** *\<Add-Key>* **`}`** ]
>
> *\<Delete-Key>* ::=\
> &emsp; **`Delete`** *\<Key-Name>*
>
> *\<Key-Name>* ::=\
> &emsp; **`'`**_\<AlphaNumeric>_+**`'`**
>
> *\<AlphaNumeric>* ::=\
> &emsp; null 以外の任意の文字。
>
> *\<Key-Value>* ::=\
> &emsp; *\<Key-Type>* *\<Key-Name>*
>
> *\<Key-Type>* ::=\
> &emsp; **`s`** &vert; **`d`**

> [!NOTE]
> **`HKEY_CLASSES_ROOT`** とは同等であり、と **`HKCR`** **`HKEY_CURRENT_USER`** **`HKCU`** は等価です。

解析ツリーでは、に複数のキーとサブキーを追加でき \<root-key> ます。 レジストラーは、各サブキーのハンドルを、パーサーがすべてのサブキーの解析を完了するまで開いたままにします。 一度に1つのキーを操作するよりも効率的です。 次に例を示します。

```rgs
HKEY_CLASSES_ROOT
{
    'MyVeryOwnKey'
    {
        'HasASubKey'
        {
            'PrettyCool'
        }
    }
}
```

ここでは、最初にレジストラーが開きます (作成し `HKEY_CLASSES_ROOT\MyVeryOwnKey` ます)。 次に、サブキーがあることを確認し `MyVeryOwnKey` ます。 に対してキーを閉じるのではなく `MyVeryOwnKey` 、レジストラーはハンドルを保持し、 `HasASubKey` この親ハンドルを使用してを開きます (作成します)。 (親ハンドルが開いていない場合は、システムレジストリの速度が低下する可能性があります)。そのため、を開い `HKEY_CLASSES_ROOT\MyVeryOwnKey` て `HasASubKey` から `MyVeryOwnKey` 親としてを開く方が、開始、 `MyVeryOwnKey` 終了 `MyVeryOwnKey` 、および開くよりも高速です `MyVeryOwnKey\HasASubKey` 。

## <a name="see-also"></a>こちらもご覧ください

[レジストラースクリプトの作成](../atl/creating-registrar-scripts.md)
