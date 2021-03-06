---
description: 詳細については、「in (C++)」を参照してください。
title: in (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: c4d19fcf7adc767986306a3ef55b26a2cc91dccf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321377"
---
# <a name="in-c"></a>in (C++)

呼び出し元プロシージャから呼び出されたプロシージャにパラメーターが渡されることを示します。

## <a name="syntax"></a>構文

```cpp
[in]
```

## <a name="remarks"></a>解説

C++ **属性のは** 、の [in](/windows/win32/Midl/in) MIDL 属性と同じ機能を持ちます。

## <a name="example"></a>例

**で** を使用する方法の例については、「[バインド](bindable.md)可能」を参照してください。

## <a name="requirements"></a>要件

| 属性コンテキスト | 値 |
|-|-|
|**適用対象**|インターフェイスパラメーター、インターフェイスメソッド|
|**Repeatable**|いいえ|
|**必須属性**|なし|
|**無効な属性**|**retval**|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[パラメーター属性](parameter-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[既定](defaultvalue.md)<br/>
[id](id.md)<br/>
[out](out-cpp.md)
