---
description: 詳細については、「defaultvalue」を参照してください。
title: defaultvalue (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvalue
helpviewer_keywords:
- defaultvalue attribute
ms.assetid: efa5d050-b2cc-4d9e-9b8e-79954f218d3a
ms.openlocfilehash: 907c736861d39064103af28917f35a97c0c7b1e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122162"
---
# <a name="defaultvalue"></a>defaultvalue

型指定された省略可能なパラメーターの既定値を指定できます。

## <a name="syntax"></a>構文

```cpp
[ defaultvalue= value ]
```

### <a name="parameters"></a>パラメーター

*value*<br/>
パラメーターの既定値です。

## <a name="remarks"></a>解説

**Defaultvalue** C++ 属性には、 [defaultvalue](/windows/win32/Midl/defaultvalue) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

次のコードは、 **defaultvalue** 属性を使用したインターフェイスメソッドを示しています。

```cpp
// cpp_attr_ref_defaultvalue.cpp
// compile with: /LD
#include <windows.h>

[export] typedef long HRESULT;
[export, ptr, string] typedef unsigned char * MY_STRING_TYPE;

[  uuid("479B29EE-9A2C-11D0-B696-00A0C903487A"), dual, oleautomation, helpstring("IFireTabCtrl Interface"), helpcontext(122), pointer_default(unique) ]

__interface IFireTabCtrl : IDispatch {
   [bindable, propget] HRESULT get_Size([out, retval, defaultvalue("33")] long *nSize);
   [bindable, propput] HRESULT put_Size([in] int nSize);
};

[ module(name="ATLFIRELib", uuid="479B29E1-9A2C-11D0-B696-00A0C903487A",    version="1.0", helpstring="ATLFire 1.0 Type Library") ];
```

## <a name="requirements"></a>要件

| 属性コンテキスト | 値 |
|-|-|
|**適用対象**|インターフェイス パラメーター|
|**Repeatable**|いいえ|
|**必須属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[パラメーター属性](parameter-attributes.md)<br/>
[out](out-cpp.md)<br/>
[retval](retval.md)<br/>
[in](in-cpp.md)<br/>
[pointer_default](pointer-default.md)<br/>
[unique](unique-cpp.md)
