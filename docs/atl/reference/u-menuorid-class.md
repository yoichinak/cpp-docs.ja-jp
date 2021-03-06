---
description: '詳細情報: _U_MENUorID クラス'
title: _U_MENUorID クラス
ms.date: 11/04/2016
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
ms.openlocfilehash: 4418e9db455e72643c497925c19900b41c9b9f38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138789"
---
# <a name="_u_menuorid-class"></a>_U_MENUorID クラス

このクラスは、およびのラッパーを提供し `CreateWindow` `CreateWindowEx` ます。

> [!IMPORTANT]
> このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class _U_MENUorID
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[_U_MENUorID:: _U_MENUorID](#_u_menuorid___u_menuorid)|コンストラクターです。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[_U_MENUorID:: m_hMenu](#_u_menuorid__m_hmenu)|メニューへのハンドル。|

## <a name="remarks"></a>解説

この引数アダプタークラスを使用すると、呼び出し元の部分に明示的なキャストを必要とせずに、Id (UINTs) またはメニューハンドル (HMENUs) を関数に渡すことができます。

このクラスは、Windows API (特に、 [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 関数と [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 関数) にラッパーを実装するように設計されています。どちらも、メニューハンドルではなく子ウィンドウ識別子 (UINT) である HMENU 引数を受け取ります。 たとえば、このクラスは、 [CWindowImpl:: Create](cwindowimpl-class.md#create)のパラメーターとして使用されていることがわかります。

クラスは、2つのコンストラクターオーバーロードを定義します。1つは UINT 引数を受け取り、もう1つは HMENU 引数を受け取ります。 UINT 引数は、コンストラクター内の HMENU と、クラスの単一のデータメンバー [m_hMenu](#_u_menuorid__m_hmenu)に格納されている結果にキャストするだけです。 HMENU コンストラクターの引数は、変換せずに直接格納されます。

## <a name="requirements"></a>要件

**ヘッダー:** atlwin. h

## <a name="_u_menuoridm_hmenu"></a><a name="_u_menuorid__m_hmenu"></a> _U_MENUorID:: m_hMenu

クラスは、コンストラクターのいずれかに渡された値をパブリックな HMENU データメンバーとして保持します。

```
HMENU m_hMenu;
```

## <a name="_u_menuorid_u_menuorid"></a><a name="_u_menuorid___u_menuorid"></a> _U_MENUorID:: _U_MENUorID

UINT 引数は、コンストラクター内の HMENU と、クラスの単一のデータメンバー [m_hMenu](#_u_menuorid__m_hmenu)に格納されている結果にキャストするだけです。

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
子ウィンドウの識別子。

*hMenu*<br/>
メニューハンドル。

### <a name="remarks"></a>解説

HMENU コンストラクターの引数は、変換せずに直接格納されます。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
