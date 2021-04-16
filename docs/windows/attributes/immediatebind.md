---
description: '詳細情報: イミディエイト atebind (C++ COM 属性)'
title: イミディエイトの atebind (C++ COM 属性)
ms.date: 04/15/2021
f1_keywords:
- vc-attr.immediatebind
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
ms.openlocfilehash: b4bd8ddd61de7bc249fef2e6b0a140f4ee5cff95
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539756"
---
# `immediatebind`

データバインドオブジェクトのプロパティに対するすべての変更が、すぐにデータベースに通知されることを示します。

## <a name="syntax"></a>構文

```cpp
[immediatebind]
```

## <a name="remarks"></a>解説

C++ 属性には、 **`immediatebind`** MIDL 属性と同じ機能があり [`immediatebind`](/windows/win32/Midl/immediatebind) ます。

## <a name="example"></a>例

直 [`bindable`](bindable.md) **ちに atebind** を使用する方法の例については、「」を参照してください。

## <a name="requirements"></a>要件

| 属性コンテキスト | 値 |
|-|-|
|**適用対象**|インターフェイス メソッド|
|**反復可能**|No|
|**必須属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>こちらもご覧ください

[IDL 属性](idl-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[`defaultbind`](defaultbind.md)<br/>
[`displaybind`](displaybind.md)<br/>
[`requestedit`](requestedit.md)
