---
description: '詳細情報: CMenu クラス'
title: CMenu クラス
ms.date: 11/04/2016
f1_keywords:
- CMenu
- AFXWIN/CMenu
- AFXWIN/CMenu::CMenu
- AFXWIN/CMenu::AppendMenu
- AFXWIN/CMenu::Attach
- AFXWIN/CMenu::CheckMenuItem
- AFXWIN/CMenu::CheckMenuRadioItem
- AFXWIN/CMenu::CreateMenu
- AFXWIN/CMenu::CreatePopupMenu
- AFXWIN/CMenu::DeleteMenu
- AFXWIN/CMenu::DeleteTempMap
- AFXWIN/CMenu::DestroyMenu
- AFXWIN/CMenu::Detach
- AFXWIN/CMenu::DrawItem
- AFXWIN/CMenu::EnableMenuItem
- AFXWIN/CMenu::FromHandle
- AFXWIN/CMenu::GetDefaultItem
- AFXWIN/CMenu::GetMenuContextHelpId
- AFXWIN/CMenu::GetMenuInfo
- AFXWIN/CMenu::GetMenuItemCount
- AFXWIN/CMenu::GetMenuItemID
- AFXWIN/CMenu::GetMenuItemInfo
- AFXWIN/CMenu::GetMenuState
- AFXWIN/CMenu::GetMenuString
- AFXWIN/CMenu::GetSafeHmenu
- AFXWIN/CMenu::GetSubMenu
- AFXWIN/CMenu::InsertMenu
- AFXWIN/CMenu::InsertMenuItem
- AFXWIN/CMenu::LoadMenu
- AFXWIN/CMenu::LoadMenuIndirect
- AFXWIN/CMenu::MeasureItem
- AFXWIN/CMenu::ModifyMenu
- AFXWIN/CMenu::RemoveMenu
- AFXWIN/CMenu::SetDefaultItem
- AFXWIN/CMenu::SetMenuContextHelpId
- AFXWIN/CMenu::SetMenuInfo
- AFXWIN/CMenu::SetMenuItemBitmaps
- AFXWIN/CMenu::SetMenuItemInfo
- AFXWIN/CMenu::TrackPopupMenu
- AFXWIN/CMenu::TrackPopupMenuEx
- AFXWIN/CMenu::m_hMenu
helpviewer_keywords:
- CMenu [MFC], CMenu
- CMenu [MFC], AppendMenu
- CMenu [MFC], Attach
- CMenu [MFC], CheckMenuItem
- CMenu [MFC], CheckMenuRadioItem
- CMenu [MFC], CreateMenu
- CMenu [MFC], CreatePopupMenu
- CMenu [MFC], DeleteMenu
- CMenu [MFC], DeleteTempMap
- CMenu [MFC], DestroyMenu
- CMenu [MFC], Detach
- CMenu [MFC], DrawItem
- CMenu [MFC], EnableMenuItem
- CMenu [MFC], FromHandle
- CMenu [MFC], GetDefaultItem
- CMenu [MFC], GetMenuContextHelpId
- CMenu [MFC], GetMenuInfo
- CMenu [MFC], GetMenuItemCount
- CMenu [MFC], GetMenuItemID
- CMenu [MFC], GetMenuItemInfo
- CMenu [MFC], GetMenuState
- CMenu [MFC], GetMenuString
- CMenu [MFC], GetSafeHmenu
- CMenu [MFC], GetSubMenu
- CMenu [MFC], InsertMenu
- CMenu [MFC], InsertMenuItem
- CMenu [MFC], LoadMenu
- CMenu [MFC], LoadMenuIndirect
- CMenu [MFC], MeasureItem
- CMenu [MFC], ModifyMenu
- CMenu [MFC], RemoveMenu
- CMenu [MFC], SetDefaultItem
- CMenu [MFC], SetMenuContextHelpId
- CMenu [MFC], SetMenuInfo
- CMenu [MFC], SetMenuItemBitmaps
- CMenu [MFC], SetMenuItemInfo
- CMenu [MFC], TrackPopupMenu
- CMenu [MFC], TrackPopupMenuEx
- CMenu [MFC], m_hMenu
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
ms.openlocfilehash: 4bd5fac24313321fa7bc8cbe9447ca2e69b5685e
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577477"
---
# <a name="cmenu-class"></a>CMenu クラス

Windows の `HMENU`をカプセル化したものです。

## <a name="syntax"></a>構文

```
class CMenu : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMenu:: CMenu](#cmenu)|`CMenu` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMenu::AppendMenu](#appendmenu)|このメニューの末尾に新しい項目を追加します。|
|[CMenu:: Attach](#attach)|Windows のメニューハンドルをオブジェクトにアタッチ `CMenu` します。|
|[CMenu:: CheckMenuItem](#checkmenuitem)|ポップアップメニューのメニュー項目の横にチェックマークを付けたり、チェックマークを削除したりします。|
|[CMenu:: Checkmenuro Item](#checkmenuradioitem)|メニュー項目の横にラジオボタンを配置し、グループ内の他のすべてのメニュー項目からオプションボタンを削除します。|
|[CMenu:: CreateMenu](#createmenu)|空のメニューを作成し、オブジェクトにアタッチし `CMenu` ます。|
|[CMenu:: CreatePopupMenu](#createpopupmenu)|空のポップアップメニューを作成し、オブジェクトにアタッチし `CMenu` ます。|
|[CMenu::D eleteMenu](#deletemenu)|指定した項目をメニューから削除します。 メニュー項目にポップアップメニューが関連付けられている場合、はポップアップメニューへのハンドルを破棄し、それによって使用されているメモリを解放します。|
|[CMenu::D eleteTempMap](#deletetempmap)|`CMenu`メンバー関数によって作成された一時オブジェクトを削除 `FromHandle` します。|
|[CMenu::D estroyMenu](#destroymenu)|オブジェクトに関連付けられているメニューを破棄し、メニューによっ `CMenu` て占有されているすべてのメモリを解放します。|
|[CMenu::D etach](#detach)|Windows のメニューハンドルをオブジェクトからデタッチ `CMenu` し、ハンドルを返します。|
|[CMenu: rawItem:D](#drawitem)|オーナー描画メニューの外観が変化したときにフレームワークによって呼び出されます。|
|[CMenu:: EnableMenuItem](#enablemenuitem)|メニュー項目を有効または無効にしたり、淡色 (灰色) したりします。|
|[CMenu:: FromHandle](#fromhandle)|`CMenu`Windows のメニューハンドルを指定して、オブジェクトへのポインターを返します。|
|[CMenu:: GetDefaultItem](#getdefaultitem)|指定したメニューの既定のメニュー項目を決定します。|
|[CMenu:: GetMenuContextHelpId](#getmenucontexthelpid)|メニューに関連付けられたヘルプコンテキスト ID を取得します。|
|[CMenu:: GetMenuInfo](#getmenuinfo)|特定のメニューに関する情報を取得します。|
|[CMenu:: GetMenuItemCount](#getmenuitemcount)|ポップアップメニューまたはトップレベルメニュー内の項目数を決定します。|
|[CMenu:: GetMenuItemID](#getmenuitemid)|指定した位置にあるメニュー項目のメニュー項目の識別子を取得します。|
|[CMenu:: GetMenuItemInfo](#getmenuiteminfo)|メニュー項目に関する情報を取得します。|
|[CMenu:: GetMenuState](#getmenustate)|指定されたメニュー項目のステータス、またはポップアップメニュー内の項目数を返します。|
|[CMenu:: GetMenuString](#getmenustring)|指定したメニュー項目のラベルを取得します。|
|[CMenu:: GetSafeHmenu](#getsafehmenu)|`m_hMenu`このオブジェクトによってラップされたを返し `CMenu` ます。|
|[CMenu:: GetSubMenu メニュー](#getsubmenu)|ポップアップメニューへのポインターを取得します。|
|[CMenu::InsertMenu](#insertmenu)|新しいメニュー項目を指定した位置に挿入し、他の項目をメニューの下に移動します。|
|[CMenu:: InsertMenuItem](#insertmenuitem)|メニュー内の指定した位置に新しいメニュー項目を挿入します。|
|[CMenu:: LoadMenu](#loadmenu)|実行可能ファイルからメニューリソースを読み込み、それをオブジェクトにアタッチし `CMenu` ます。|
|[CMenu:: LoadMenuIndirect](#loadmenuindirect)|メニューをメモリ内のメニューテンプレートから読み込み、オブジェクトにアタッチし `CMenu` ます。|
|[CMenu:: MeasureItem](#measureitem)|オーナー描画メニューが作成されたときにメニューのサイズを決定するために、フレームワークによって呼び出されます。|
|[CMenu::ModifyMenu](#modifymenu)|指定した位置にある既存のメニュー項目を変更します。|
|[CMenu:: RemoveMenu](#removemenu)|指定したメニューから、関連付けられたポップアップメニューを含むメニュー項目を削除します。|
|[CMenu:: SetDefaultItem](#setdefaultitem)|指定したメニューの既定のメニュー項目を設定します。|
|[CMenu:: SetMenuContextHelpId](#setmenucontexthelpid)|メニューに関連付けられるヘルプコンテキスト ID を設定します。|
|[CMenu:: SetMenuInfo](#setmenuinfo)|特定のメニューに関する情報を設定します。|
|[CMenu:: SetMenuItemBitmaps](#setmenuitembitmaps)|指定されたチェックマークビットマップをメニュー項目に関連付けます。|
|[CMenu:: SetMenuItemInfo](#setmenuiteminfo)|メニュー項目に関する情報を変更します。|
|[CMenu:: TrackPopupMenu](#trackpopupmenu)|指定した位置にフローティングポップアップメニューを表示し、ポップアップメニュー上の項目の選択を追跡します。|
|[CMenu:: TrackPopupMenuEx](#trackpopupmenuex)|指定した位置にフローティングポップアップメニューを表示し、ポップアップメニュー上の項目の選択を追跡します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CMenu:: operator HMENU](#operator_hmenu)|メニューオブジェクトのハンドルを取得します。|
|[CMenu:: operator! =](#operator_neq)|2つのメニューオブジェクトが等しくないかどうかを判断します。|
|[CMenu:: operator = =](#operator_eq_eq)|2つのメニューオブジェクトが等しいかどうかを判断します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CMenu:: m_hMenu](#m_hmenu)|オブジェクトに関連付けられている Windows メニューへのハンドルを指定し `CMenu` ます。|

## <a name="remarks"></a>解説

これには、メニューを作成、追跡、更新、および破棄するためのメンバー関数が用意されています。

`CMenu`ローカルとしてスタックフレームにオブジェクトを作成し、その後 `CMenu` 、のメンバー関数を呼び出して、必要に応じて新しいメニューを操作します。 次に、 [CWnd:: SetMenu](../../mfc/reference/cwnd-class.md#setmenu) を呼び出して、メニューをウィンドウに設定し、その直後に `CMenu` オブジェクトの [Detach](#detach) メンバー関数を呼び出します。 この `CWnd::SetMenu` メンバー関数は、ウィンドウのメニューを新しいメニューに設定し、メニューの変更を反映するようにウィンドウを再描画します。また、メニューの所有権をウィンドウに渡します。 を呼び出すと、 `Detach` オブジェクトから HMENU が切り離され `CMenu` ます。これにより、ローカル変数がスコープ外に出ると、 `CMenu` オブジェクトデストラクターは、 `CMenu` 所有していないメニューを破棄しようとしません。 メニュー自体は、ウィンドウが破棄されると自動的に破棄されます。

[Loadmenuindirect](#loadmenuindirect)メンバー関数を使用すると、メモリ内のテンプレートからメニューを作成できますが、 [loadmenu](#loadmenu)の呼び出しによってリソースから作成されたメニューはより簡単に管理でき、メニューリソース自体はメニューエディターで作成および変更できます。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>要件

**ヘッダー:** afxwin.h

## <a name="cmenuappendmenu"></a><a name="appendmenu"></a> CMenu:: AppendMenu

メニューの末尾に新しい項目を追加します。

```
BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>パラメーター

*nFlags*<br/>
メニューに追加されたときの新しいメニュー項目の状態に関する情報を指定します。 これは、「解説」に記載されている1つ以上の値で構成されます。

*nIDNewItem*<br/>
新しいメニュー項目のコマンド ID を指定するか、または *nFlags* が MF_POPUP に設定されている場合は、ポップアップメニューのメニューハンドル () を指定し `HMENU` ます。 *NFlags* が MF_SEPARATOR に設定されている場合、 *nIDNewItem* パラメーターは無視されます (必要ありません)。

*lpszNewItem*<br/>
新しいメニュー項目の内容を指定します。 *NFlags* パラメーターは、次の方法で *lpszNewItem* を解釈するために使用されます。

|nFlags|LpszNewItem の解釈|
|------------|-----------------------------------|
|MF_OWNERDRAW|アプリケーションが、メニュー項目に関連付けられた追加データを保持するために使用できる32ビット値を格納します。 この32ビット値は、アプリケーションが WM_MEASUREITEM メッセージと WM_DRAWITEM メッセージを処理するときに使用できます。 値は、 `itemData` これらのメッセージと共に提供される構造体のメンバーに格納されます。|
|MF_STRING|Null で終わる文字列へのポインターが含まれています。 これが既定の解釈です。|
|MF_SEPARATOR|*LpszNewItem* パラメーターは無視されます (不要)。|

*.Pbmp*<br/>
`CBitmap`メニュー項目として使用されるオブジェクトを指します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>解説

アプリケーションでは、値を *nFlags* に設定することによって、メニュー項目の状態を指定できます。 *NIDNewItem* がポップアップメニューを指定すると、それが追加されるメニューの一部になります。 このメニューが破棄された場合、追加されたメニューも破棄されます。 競合を回避するには、追加されたメニューをオブジェクトからデタッチする必要があり `CMenu` ます。 MF_STRING と MF_OWNERDRAW は、のビットマップバージョンでは有効ではないことに注意して `AppendMenu` ください。

次の一覧では、 *nFlags* で設定できるフラグについて説明します。

- MF_CHECKED は、MF_UNCHECKED の切り替えとして機能し、項目の横に既定のチェックマークを配置します。 アプリケーションがチェックマークビットマップ ( [Setmenuitembitmaps](#setmenuitembitmaps) メンバー関数を参照) を提供する場合は、[チェックマーク] ビットマップが表示されます。

- MF_UNCHECKED は、項目の横にあるチェックマークを解除するための MF_CHECKED の切り替えとして機能します。 アプリケーションがチェックマークビットマップ (メンバー関数を参照) を提供する場合 `SetMenuItemBitmaps` 、[チェックマークをオフにする] ビットマップが表示されます。

- メニュー項目を選択できないように MF_DISABLED 無効にしますが、淡色は設定されません。

- MF_ENABLED では、メニュー項目を選択して、淡色表示の状態から復元することができます。

- メニュー項目を無効にして、選択できないように MF_GRAYED します。

- MF_MENUBARBREAK は、静的メニューまたはポップアップメニューの新しい列に項目を新しい行に配置します。 新しいポップアップメニュー列は、前の列から垂直の区切り線で区切られます。

- MF_MENUBREAK は、静的メニューまたはポップアップメニューの新しい列に項目を新しい行に配置します。 列の間には、分割線は挿入されません。

- MF_OWNERDRAW 項目がオーナー描画項目であることを指定します。 メニューが初めて表示されるとき、メニューを所有するウィンドウは、メニュー項目の高さと幅を取得する WM_MEASUREITEM メッセージを受け取ります。 WM_DRAWITEM メッセージは、オーナーがメニュー項目の外観を更新する必要があるときに送信されるメッセージです。 このオプションは、トップレベルのメニュー項目に対しては無効です。

- MF_POPUP メニュー項目にポップアップメニューが関連付けられていることを指定します。 ID パラメーターは、項目に関連付けられるポップアップメニューへのハンドルを指定します。 これは、トップレベルのポップアップメニューまたは階層のポップアップメニューをポップアップメニュー項目に追加するために使用されます。

- MF_SEPARATOR は、水平方向の区切り線を描画します。 ポップアップメニューでのみ使用できます。 この行を淡色表示、無効、または強調表示することはできません。 その他のパラメーターは無視されます。

- MF_STRING メニュー項目が文字列であることを指定します。

次の各グループには、相互に排他的で、同時に使用できないフラグが一覧表示されます。

- MF_DISABLED、MF_ENABLED、および MF_GRAYED

- MF_STRING、MF_OWNERDRAW、MF_SEPARATOR、およびビットマップバージョン

- MF_MENUBARBREAK と MF_MENUBREAK

- MF_CHECKED と MF_UNCHECKED

ウィンドウに表示されているメニューが変更された場合 (ウィンドウが表示されているかどうかにかかわらず)、アプリケーションは [CWnd::D rawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)を呼び出す必要があります。

### <a name="example"></a>例

  「 [CMenu:: CreateMenu](#createmenu)」の例を参照してください。

## <a name="cmenuattach"></a><a name="attach"></a> CMenu:: Attach

既存の Windows メニューをオブジェクトにアタッチ `CMenu` します。

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>パラメーター

*hMenu*<br/>
Windows メニューのハンドルを指定します。

### <a name="return-value"></a>戻り値

操作が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

メニューが既にオブジェクトにアタッチされている場合、この関数を呼び出すことはできません `CMenu` 。 メニューハンドルは、データメンバーに格納され `m_hMenu` ます。

操作するメニューが既にウィンドウに関連付けられている場合は、 [CWnd:: getmenu](../../mfc/reference/cwnd-class.md#getmenu) 関数を使用して、メニューへのハンドルを取得できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenucheckmenuitem"></a><a name="checkmenuitem"></a> CMenu:: CheckMenuItem

ポップアップメニューのメニュー項目からチェックマークを追加または削除します。

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>パラメーター

*nIDCheckItem*<br/>
*N* によって決定される、チェックするメニュー項目を指定します。

*n*<br/>
メニュー項目を確認する方法、およびメニュー内の項目の位置を確認する方法を指定します。 *N* パラメーターは、MF_BYPOSITION または MF_BYCOMMAND フラグを持つ MF_CHECKED または MF_UNCHECKED の組み合わせにすることができます。 これらのフラグは、ビットごとの OR 演算子を使用して組み合わせることができます。 これらの意味は次のとおりです。

- MF_BYCOMMAND は、パラメーターが既存のメニュー項目のコマンド ID を与えることを指定します。 既定値です。

- MF_BYPOSITION は、パラメーターが既存のメニュー項目の位置を示すことを指定します。 最初の項目の位置は0です。

- MF_CHECKED は、MF_UNCHECKED の切り替えとして機能し、項目の横に既定のチェックマークを配置します。

- MF_UNCHECKED は、項目の横にあるチェックマークを解除するための MF_CHECKED の切り替えとして機能します。

### <a name="return-value"></a>戻り値

項目の以前の状態: MF_CHECKED または MF_UNCHECKED、またはメニュー項目が存在しない場合は0xFFFFFFFF。

### <a name="remarks"></a>解説

*NIDCheckItem* パラメーターは、変更する項目を指定します。

*NIDCheckItem* パラメーターは、ポップアップメニュー項目およびメニュー項目を識別できます。 ポップアップメニュー項目をチェックするために特別な手順は必要ありません。 トップレベルのメニュー項目を確認することはできません。 ポップアップメニュー項目は、メニュー項目識別子が関連付けられていないため、位置によって確認する必要があります。

### <a name="example"></a>例

  「 [CMenu:: GetMenuState](#getmenustate)」の例を参照してください。

## <a name="cmenucheckmenuradioitem"></a><a name="checkmenuradioitem"></a> CMenu:: Checkmenuro Item

指定されたメニュー項目をチェックし、それをラジオ項目にします。

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>パラメーター

*nIDFirst*<br/>
オプションボタングループの最初のメニュー項目を、( *nFlags* の値に応じて) ID またはオフセットとして指定します。

*nIDLast*<br/>
オプションボタングループの最後のメニュー項目を、( *nFlags* の値に応じて) ID またはオフセットとして指定します。

*nIDItem*<br/>
オプションボタンを使用してチェックするグループ内の項目を、(値が *nFlags* の場合は ID またはオフセットとして) 指定します。

*nFlags*<br/>
次のように、 *nIDFirst*、 *NIDLast*、および *nIDItem* の解釈を指定します。

|nFlags|解釈|
|------------|--------------------|
|MF_BYCOMMAND|パラメーターが既存のメニュー項目のコマンド ID を与えることを指定します。 これは、MF_BYCOMMAND も MF_BYPOSITION も設定されていない場合の既定値です。|
|MF_BYPOSITION|パラメーターが既存のメニュー項目の位置を指定することを指定します。 最初の項目の位置は0です。|

### <a name="return-value"></a>戻り値

成功した場合は0以外の。それ以外の場合は0

### <a name="remarks"></a>解説

同時に、関数は、関連付けられているグループ内の他のすべてのメニュー項目をオフにし、それらの項目のオプション項目の種類フラグをクリアします。 チェックマークの付いた項目は、チェックマークのビットマップの代わりに、オプションボタン (または箇条書き) のビットマップを使用して表示されます。

### <a name="example"></a>例

  [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range)の例を参照してください。

## <a name="cmenucmenu"></a><a name="cmenu"></a> CMenu:: CMenu

空のメニューを作成し、オブジェクトにアタッチし `CMenu` ます。

```
CMenu();
```

### <a name="remarks"></a>解説

メニューは、の create または load メンバー関数のいずれかを呼び出すまでは作成されません。 `CMenu:`

- [CreateMenu](#createmenu)

- [CreatePopupMenu](#createpopupmenu)

- [LoadMenu](#loadmenu)

- [LoadMenuIndirect](#loadmenuindirect)

- [[アタッチ]](#attach)

## <a name="cmenucreatemenu"></a><a name="createmenu"></a> CMenu:: CreateMenu

メニューを作成し、オブジェクトにアタッチし `CMenu` ます。

```
BOOL CreateMenu();
```

### <a name="return-value"></a>戻り値

メニューが正常に作成された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

このメニューは、最初は空です。 メニュー項目を追加するには、 `AppendMenu` またはメンバー関数を使用し `InsertMenu` ます。

メニューがウィンドウに割り当てられている場合は、ウィンドウが破棄されると自動的に破棄されます。

終了する前に、メニューがウィンドウに割り当てられていない場合は、アプリケーションでメニューに関連付けられているシステムリソースを解放する必要があります。 アプリケーションは、 [destroymenu](#destroymenu) メンバー関数を呼び出すことによってメニューを解放します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

## <a name="cmenucreatepopupmenu"></a><a name="createpopupmenu"></a> CMenu:: CreatePopupMenu

ポップアップメニューを作成し、オブジェクトにアタッチし `CMenu` ます。

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>戻り値

ポップアップメニューが正常に作成された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

このメニューは、最初は空です。 メニュー項目を追加するには、 `AppendMenu` またはメンバー関数を使用し `InsertMenu` ます。 アプリケーションでは、既存のメニューまたはポップアップメニューにポップアップメニューを追加できます。 `TrackPopupMenu`このメンバー関数を使用すると、このメニューをフローティングポップアップメニューとして表示したり、ポップアップメニューで選択を追跡したりできます。

メニューがウィンドウに割り当てられている場合は、ウィンドウが破棄されると自動的に破棄されます。 メニューが既存のメニューに追加されると、メニューが破棄されると自動的に破棄されます。

メニューがウィンドウに割り当てられていない場合、終了する前に、アプリケーションでポップアップメニューに関連付けられているシステムリソースを解放する必要があります。 アプリケーションは、 [destroymenu](#destroymenu) メンバー関数を呼び出すことによってメニューを解放します。

### <a name="example"></a>例

  「 [CMenu:: CreateMenu](#createmenu)」の例を参照してください。

## <a name="cmenudeletemenu"></a><a name="deletemenu"></a> CMenu::D eleteMenu

メニューから項目を削除します。

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>パラメーター

*nPosition*<br/>
*NFlags* によって決定される、削除するメニュー項目を指定します。

*nFlags*<br/>
は、次のように *nPosition* を解釈するために使用されます。

|nFlags|NPosition の解釈|
|------------|---------------------------------|
|MF_BYCOMMAND|パラメーターが既存のメニュー項目のコマンド ID を与えることを指定します。 これは、MF_BYCOMMAND も MF_BYPOSITION も設定されていない場合の既定値です。|
|MF_BYPOSITION|パラメーターが既存のメニュー項目の位置を指定することを指定します。 最初の項目の位置は0です。|

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>解説

メニュー項目にポップアップメニューが関連付けられている場合は、ポップアップメニュー `DeleteMenu` のハンドルを破棄し、ポップアップメニューによって使用されているメモリを解放します。

ウィンドウに表示されているメニューが変更された場合 (ウィンドウが表示されているかどうかにかかわらず)、アプリケーションは [CWnd::D rawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)を呼び出す必要があります。

### <a name="example"></a>例

  [CWnd:: GetMenu](../../mfc/reference/cwnd-class.md#getmenu)の例を参照してください。

## <a name="cmenudeletetempmap"></a><a name="deletetempmap"></a> CMenu::D eleteTempMap

アイドルタイムハンドラーによって自動的に呼び出され `CWinApp` 、 `CMenu` [FromHandle](#fromhandle) メンバー関数によって作成された一時オブジェクトを削除します。

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>解説

`DeleteTempMap` オブジェクトを削除する前に、一時オブジェクトにアタッチされている Windows メニューオブジェクトをデタッチし `CMenu` `CMenu` ます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

## <a name="cmenudestroymenu"></a><a name="destroymenu"></a> CMenu::D estroyMenu

メニューと、使用されたすべての Windows リソースを破棄します。

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>戻り値

メニューが破棄された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

メニューは、 `CMenu` 破棄される前にオブジェクトからデタッチされます。 Windows の `DestroyMenu` 関数は、デストラクターで自動的に呼び出され `CMenu` ます。

### <a name="example"></a>例

  「 [CMenu:: CreateMenu](#createmenu)」の例を参照してください。

## <a name="cmenudetach"></a><a name="detach"></a> CMenu::D etach

Windows メニューをオブジェクトからデタッチ `CMenu` し、ハンドルを返します。

```
HMENU Detach();
```

### <a name="return-value"></a>戻り値

成功した場合は、HMENU 型のハンドルを Windows メニューに返します。それ以外の場合は NULL。

### <a name="remarks"></a>解説

`m_hMenu`データメンバーが NULL に設定されています。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenudrawitem"></a><a name="drawitem"></a> CMenu: rawItem:D

オーナー描画メニューの外観が変化したときにフレームワークによって呼び出されます。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>パラメーター

*lpDrawItemStruct*<br/>
必要な描画の種類に関する情報を格納している [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) 構造体へのポインター。

### <a name="remarks"></a>解説

`itemAction`構造体のメンバーは、 `DRAWITEMSTRUCT` 実行する描画アクションを定義します。 オーナー描画オブジェクトの描画を実装するには、このメンバー関数をオーバーライドし `CMenu` ます。 アプリケーションは、このメンバー関数が終了する前に、 *lpDrawItemStruct* で指定された表示コンテキスト用に選択されたすべてのグラフィックスデバイスインターフェイス (GDI) オブジェクトを復元する必要があります。

構造の説明については、「 [CWnd:: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) 」を参照してください `DRAWITEMSTRUCT` 。

### <a name="example"></a>例

次のコードは、MFC [CTRLTEST](../../overview/visual-cpp-samples.md) サンプルからのものです。

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

## <a name="cmenuenablemenuitem"></a><a name="enablemenuitem"></a> CMenu:: EnableMenuItem

メニュー項目を有効、無効、または暗くします。

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>パラメーター

*nIDEnableItem*<br/>
*NEnable* によって決定される、有効にするメニュー項目を指定します。 このパラメーターでは、ポップアップメニュー項目だけでなく、標準のメニュー項目を指定できます。

*nEnable*<br/>
実行するアクションを指定します。 MF_BYCOMMAND または MF_BYPOSITION を使用して、MF_DISABLED、MF_ENABLED、または MF_GRAYED の組み合わせにすることができます。 これらの値は、ビットごとの OR 演算子を使用して組み合わせることができます。 これらの値には次の意味があります。

- MF_BYCOMMAND は、パラメーターが既存のメニュー項目のコマンド ID を与えることを指定します。 既定値です。

- MF_BYPOSITION は、パラメーターが既存のメニュー項目の位置を示すことを指定します。 最初の項目の位置は0です。

- メニュー項目を選択できないように MF_DISABLED 無効にしますが、淡色は設定されません。

- MF_ENABLED では、メニュー項目を選択して、淡色表示の状態から復元することができます。

- メニュー項目を無効にして、選択できないように MF_GRAYED します。

### <a name="return-value"></a>戻り値

以前の状態 (MF_DISABLED、MF_ENABLED、または MF_GRAYED)、または有効でない場合は-1。

### <a name="remarks"></a>解説

[CreateMenu](#createmenu)、 [insertmenu](#insertmenu)、 [Modifymenu](#modifymenu)、および[loadmenuindirect](#loadmenuindirect)メンバー関数は、メニュー項目の状態 (有効、無効、または淡色表示) を設定することもできます。

MF_BYPOSITION 値を使用するには、アプリケーションが正しいを使用する必要があり `CMenu` ます。 メニューバーのが使用されている場合は、 `CMenu` トップレベルのメニュー項目 (メニューバーの項目) が影響を受けます。 ポップアップメニューまたは入れ子になったポップアップメニューの位置によって項目の状態を設定するには、アプリケーションでポップアップメニューのを指定する必要があり `CMenu` ます。

アプリケーションで MF_BYCOMMAND フラグが指定されている場合、Windows はの下位にあるすべてのポップアップメニュー項目をチェックします `CMenu` 。したがって、重複するメニュー項目が存在しない場合 `CMenu` は、メニューバーのを使用するだけで十分です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

## <a name="cmenufromhandle"></a><a name="fromhandle"></a> CMenu:: FromHandle

メニューへの Windows ハンドルを指定して、オブジェクトへのポインターを返し `CMenu` ます。

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>パラメーター

*hMenu*<br/>
メニューを対象とした Windows ハンドル。

### <a name="return-value"></a>戻り値

`CMenu`一時的または永続的なへのポインター。

### <a name="remarks"></a>解説

`CMenu`オブジェクトが Windows メニューオブジェクトにまだアタッチされていない場合は、一時 `CMenu` オブジェクトが作成され、アタッチされます。

この一時 `CMenu` オブジェクトは、アプリケーションが次にそのイベントループ内でアイドル状態になるまで有効です。その時点で、すべての一時オブジェクトが削除されます。

### <a name="example"></a>例

  「 [CMenu:: CreateMenu](#createmenu)」の例を参照してください。

## <a name="cmenugetdefaultitem"></a><a name="getdefaultitem"></a> CMenu:: GetDefaultItem

指定したメニューの既定のメニュー項目を決定します。

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>パラメーター

*gmdiFlags*<br/>
関数がメニュー項目を検索する方法を指定する値。 このパラメーターには、none、1、または次の値の組み合わせを指定できます。

|値|説明|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|既定の項目がサブメニューを開く場合は、対応するサブメニュー内を再帰的に検索することを指定します。 サブメニューに既定の項目がない場合は、そのサブメニューを開く項目が戻り値によって識別されます。<br /><br /> 既定では、この関数は、サブメニューを開く項目であるかどうかに関係なく、指定されたメニューの最初の既定の項目を返します。|
|GMDI_USEDISABLED|関数が無効になっている場合でも、既定の項目を返すことを指定します。<br /><br /> 既定では、この関数は、無効またはグレーの項目をスキップします。|

*fByPos*<br/>
メニュー項目の識別子またはその位置を取得するかどうかを指定する値。 このパラメーターが FALSE の場合は、識別子が返されます。 それ以外の場合は、位置が返されます。

### <a name="return-value"></a>戻り値

関数が成功した場合、戻り値はメニュー項目の識別子または位置になります。 関数が失敗した場合、戻り値は-1 になります。

### <a name="remarks"></a>解説

このメンバー関数は、Windows SDK で説明されているように、Win32 関数 [Getmenudefaultitem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem)の動作を実装します。

### <a name="example"></a>例

  「 [CMenu:: InsertMenu](#insertmenu)」の例を参照してください。

## <a name="cmenugetmenucontexthelpid"></a><a name="getmenucontexthelpid"></a> CMenu:: GetMenuContextHelpId

に関連付けられているコンテキストヘルプ ID を取得 `CMenu` します。

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>戻り値

現在に関連付けられているコンテキストヘルプ ID がある場合は、 `CMenu` それ以外の場合は0。

### <a name="example"></a>例

  「 [CMenu:: InsertMenu](#insertmenu)」の例を参照してください。

## <a name="cmenugetmenuinfo"></a><a name="getmenuinfo"></a> CMenu:: GetMenuInfo

メニューの情報を取得します。

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>パラメーター

*lpcmi*<br/>
メニューの情報を格納している [Menuinfo](/windows/win32/api/winuser/ns-winuser-menuinfo) 構造体へのポインター。

### <a name="return-value"></a>戻り値

関数が成功した場合、戻り値は0以外になります。それ以外の場合、戻り値は0です。

### <a name="remarks"></a>解説

メニューに関する情報を取得するには、この関数を呼び出します。

## <a name="cmenugetmenuitemcount"></a><a name="getmenuitemcount"></a> CMenu:: GetMenuItemCount

ポップアップメニューまたはトップレベルメニュー内の項目数を決定します。

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>戻り値

関数が成功した場合のメニュー内の項目数。それ以外の場合は-1。

### <a name="example"></a>例

  [CWnd:: GetMenu](../../mfc/reference/cwnd-class.md#getmenu)の例を参照してください。

## <a name="cmenugetmenuitemid"></a><a name="getmenuitemid"></a> CMenu:: GetMenuItemID

*NPos* で定義された位置にあるメニュー項目のメニュー項目識別子を取得します。

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
ID を取得するメニュー項目の位置 (0 から始まる) を指定します。

### <a name="return-value"></a>戻り値

関数が成功した場合のポップアップメニュー内の指定された項目の項目 ID。 ポップアップメニュー内の項目ではなく、指定した項目がポップアップメニューの場合、戻り値は-1 です。 *NPos* が SEPARATOR メニュー項目に対応している場合、戻り値は0です。

### <a name="example"></a>例

  「 [CMenu:: InsertMenu](#insertmenu)」の例を参照してください。

## <a name="cmenugetmenuiteminfo"></a><a name="getmenuiteminfo"></a> CMenu:: GetMenuItemInfo

メニュー項目に関する情報を取得します。

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>パラメーター

*uItem*<br/>
情報を取得するメニュー項目の識別子または位置。 このパラメーターの意味は、の値によって異なり `ByPos` ます。

*lpMenuItemInfo*<br/>
Windows SDK で説明されているように、メニューに関する情報を格納している [MENUITEMINFO](/windows/win32/api/winuser/ns-winuser-menuiteminfow)へのポインター。

*fByPos*<br/>
の意味を指定する値 `nIDItem` 。 既定で `ByPos` は、は FALSE です。これは、uItem がメニュー項目識別子であることを示します。 `ByPos`が FALSE に設定されていない場合は、メニュー項目の位置を示します。

### <a name="return-value"></a>戻り値

関数が成功すると、戻り値は 0 以外になります。 関数が失敗した場合は、0 を返します。 拡張エラー情報を取得するには、Windows SDK で説明されているように、Win32 関数 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を使用します。

### <a name="remarks"></a>解説

このメンバー関数は、Windows SDK で説明されているように、Win32 関数 [GetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow)のの動作を実装します。 の MFC 実装では、メニューへのハンドルを使用しないことに注意してください `GetMenuItemInfo` 。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

## <a name="cmenugetmenustate"></a><a name="getmenustate"></a> CMenu:: GetMenuState

指定されたメニュー項目のステータス、またはポップアップメニュー内の項目数を返します。

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
*NFlags* によって決定されるメニュー項目 ID を指定します。

*nFlags*<br/>
*NID* の性質を指定します。 次のいずれかの値を指定できます。

- MF_BYCOMMAND は、パラメーターが既存のメニュー項目のコマンド ID を与えることを指定します。 既定値です。

- MF_BYPOSITION は、パラメーターが既存のメニュー項目の位置を示すことを指定します。 最初の項目の位置は0です。

### <a name="return-value"></a>戻り値

指定した項目が存在しない場合は0xFFFFFFFF。 *NId* がポップアップメニューを識別する場合、上位バイトにはポップアップメニュー内の項目の数が含まれ、下位バイトにはポップアップメニューに関連付けられているメニューフラグが格納されます。 それ以外の場合、戻り値は次の一覧の値のマスク (ブール値または) になります (このマスクは、 *nId* が識別するメニュー項目の状態を示します)。

- MF_CHECKED は、MF_UNCHECKED の切り替えとして機能し、項目の横に既定のチェックマークを配置します。 アプリケーションがチェックマークビットマップ (メンバー関数を参照) を提供する場合 `SetMenuItemBitmaps` 、[チェックマーク] ビットマップが表示されます。

- メニュー項目を選択できないように MF_DISABLED 無効にしますが、淡色は設定されません。

- MF_ENABLED では、メニュー項目を選択して、淡色表示の状態から復元することができます。 この定数の値が0であることに注意してください。アプリケーションでは、この値を使用しているときにエラーが発生した場合、0に対してテストしないでください。

- メニュー項目を無効にして、選択できないように MF_GRAYED します。

- MF_MENUBARBREAK は、静的メニューまたはポップアップメニューの新しい列に項目を新しい行に配置します。 新しいポップアップメニュー列は、前の列から垂直の区切り線で区切られます。

- MF_MENUBREAK は、静的メニューまたはポップアップメニューの新しい列に項目を新しい行に配置します。 列の間には、分割線は挿入されません。

- MF_SEPARATOR は、水平方向の区切り線を描画します。 ポップアップメニューでのみ使用できます。 この行を淡色表示、無効、または強調表示することはできません。 その他のパラメーターは無視されます。

- MF_UNCHECKED は、項目の横にあるチェックマークを解除するための MF_CHECKED の切り替えとして機能します。 アプリケーションがチェックマークビットマップ (メンバー関数を参照) を提供する場合 `SetMenuItemBitmaps` 、[チェックマークをオフにする] ビットマップが表示されます。 この定数の値が0であることに注意してください。アプリケーションでは、この値を使用しているときにエラーが発生した場合、0に対してテストしないでください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

## <a name="cmenugetmenustring"></a><a name="getmenustring"></a> CMenu:: GetMenuString

指定したメニュー項目のラベルを指定したバッファーにコピーします。

```
int GetMenuString(
    UINT nIDItem,
    LPTSTR lpString,
    int nMaxCount,
    UINT nFlags) const;

int GetMenuString(
    UINT nIDItem,
    CString& rString,
    UINT nFlags) const;
```

### <a name="parameters"></a>パラメーター

*nIDItem*<br/>
*NFlags* の値に応じて、メニュー項目の整数識別子、またはメニュー項目のオフセットを指定します。

*lpString*<br/>
は、ラベルを受け取るバッファーを指します。

*rString*<br/>
コピーされた `CString` メニュー文字列を受け取るオブジェクトへの参照。

*nMaxCount*<br/>
コピーするラベルの最大長 (文字数) を指定します。 ラベルが *nMaxCount* で指定された最大値より長い場合は、余分な文字が切り捨てられます。

*nFlags*<br/>
*NIDItem* パラメーターの解釈を指定します。 次のいずれかの値を指定できます。

|nFlags|NIDItem の解釈|
|------------|-------------------------------|
|MF_BYCOMMAND|パラメーターが既存のメニュー項目のコマンド ID を与えることを指定します。 これは、MF_BYCOMMAND も MF_BYPOSITION も設定されていない場合の既定値です。|
|MF_BYPOSITION|パラメーターが既存のメニュー項目の位置を指定することを指定します。 最初の項目の位置は0です。|

### <a name="return-value"></a>戻り値

Null 終端文字を含まない、バッファーにコピーされる実際の文字数を指定します。

### <a name="remarks"></a>解説

*NMaxCount* パラメーターは、文字列を終了する null 文字を格納するために、ラベル内の文字数よりも1つ大きい値にする必要があります。

### <a name="example"></a>例

  「 [CMenu:: InsertMenu](#insertmenu)」の例を参照してください。

## <a name="cmenugetsafehmenu"></a><a name="getsafehmenu"></a> CMenu:: GetSafeHmenu

このオブジェクトによってラップされた HMENU、 `CMenu` または NULL ポインターを返し `CMenu` ます。

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>例

  「 [CMenu:: LoadMenu](#loadmenu)」の例を参照してください。

## <a name="cmenugetsubmenu"></a><a name="getsubmenu"></a> CMenu:: GetSubMenu メニュー

`CMenu`ポップアップメニューのオブジェクトを取得します。

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
メニューに表示されるポップアップメニューの位置を指定します。 最初のメニュー項目の位置の値は0から始まります。 ポップアップメニューの識別子は、この関数では使用できません。

### <a name="return-value"></a>戻り値

指定された `CMenu` `m_hMenu` 位置にポップアップメニューが存在する場合は、そのメンバーにポップアップメニューへのハンドルを格納しているオブジェクトへのポインター。それ以外の場合は NULL。 オブジェクトが存在しない場合は、 `CMenu` 一時的なものが作成されます。 返された `CMenu` ポインターを格納することはできません。

### <a name="example"></a>例

  「 [CMenu:: TrackPopupMenu](#trackpopupmenu)」の例を参照してください。

## <a name="cmenuinsertmenu"></a><a name="insertmenu"></a> CMenu:: InsertMenu

*NPosition* で指定した位置に新しいメニュー項目を挿入し、他の項目をメニューの下に移動します。

```
BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>パラメーター

*nPosition*<br/>
新しいメニュー項目を挿入する前のメニュー項目を指定します。 *NFlags* パラメーターを使用すると、次の方法で *nPosition* を解釈できます。

|nFlags|NPosition の解釈|
|------------|---------------------------------|
|MF_BYCOMMAND|パラメーターが既存のメニュー項目のコマンド ID を与えることを指定します。 これは、MF_BYCOMMAND も MF_BYPOSITION も設定されていない場合の既定値です。|
|MF_BYPOSITION|パラメーターが既存のメニュー項目の位置を指定することを指定します。 最初の項目の位置は0です。 *NPosition* が-1 の場合、新しいメニュー項目がメニューの最後に追加されます。|

*nFlags*<br/>
*NPosition* をどのように解釈するかを指定し、メニューに追加されたときの新しいメニュー項目の状態に関する情報を指定します。 設定できるフラグの一覧については、「 [Appendmenu](#appendmenu) メンバー関数」を参照してください。 複数の値を指定するには、ビットごとの OR 演算子を使用して、MF_BYCOMMAND または MF_BYPOSITION フラグと結合します。

*nIDNewItem*<br/>
新しいメニュー項目のコマンド ID を指定するか、または *nFlags* が MF_POPUP に設定されている場合は、ポップアップメニューのメニューハンドル (HMENU) を指定します。 *NFlags* が MF_SEPARATOR に設定されている場合、 *nIDNewItem* パラメーターは無視されます (必要ありません)。

*lpszNewItem*<br/>
新しいメニュー項目の内容を指定します。 *nFlags* は、次の方法で *lpszNewItem* を解釈するために使用できます。

|nFlags|LpszNewItem の解釈|
|------------|-----------------------------------|
|MF_OWNERDRAW|アプリケーションが、メニュー項目に関連付けられた追加データを保持するために使用できる32ビット値を格納します。 この32ビット値は、 `itemData` [WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem) および [WM_DRAWITEM](/windows/win32/Controls/wm-drawitem) メッセージによって提供される構造体のメンバー内のアプリケーションで使用できます。 これらのメッセージは、メニュー項目が最初に表示されたとき、または変更されたときに送信されます。|
|MF_STRING|Null で終わる文字列への long ポインターを格納します。 これが既定の解釈です。|
|MF_SEPARATOR|*LpszNewItem* パラメーターは無視されます (不要)。|

*.Pbmp*<br/>
`CBitmap`メニュー項目として使用されるオブジェクトを指します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>解説

アプリケーションでは、値を *nFlags* に設定することによって、メニュー項目の状態を指定できます。

ウィンドウに表示されているメニューが変更された場合 (ウィンドウが表示されているかどうかにかかわらず)、アプリケーションはを呼び出す必要があり `CWnd::DrawMenuBar` ます。

*NIDNewItem* がポップアップメニューを指定すると、それが挿入されるメニューの一部になります。 このメニューが破棄されると、挿入されたメニューも破棄されます。 競合を回避するには、挿入されたメニューをオブジェクトからデタッチする必要があり `CMenu` ます。

アクティブなマルチドキュメントインターフェイス (MDI) 子ウィンドウが最大化されていて、アプリケーションがこの関数を呼び出して MF_BYPOSITION フラグを指定することによって、MDI アプリケーションのメニューにポップアップメニューを挿入する場合、メニューは予想よりも1つ上の位置に挿入されます。 これは、アクティブな MDI 子ウィンドウのコントロールメニューが MDI フレームウィンドウのメニューバーの最初の位置に挿入されるために発生します。 メニューを適切に配置するには、アプリケーションで、使用する位置の値に1を追加する必要があります。 アプリケーションでは、WM_MDIGETACTIVE メッセージを使用して、現在アクティブな子ウィンドウが最大化されているかどうかを判断できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

## <a name="cmenuinsertmenuitem"></a><a name="insertmenuitem"></a> CMenu:: InsertMenuItem

メニュー内の指定した位置に新しいメニュー項目を挿入します。

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>パラメーター

*uItem*<br/>
Windows SDK の [Insertmenuitem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw)の *uitem* の説明を参照してください。

*lpMenuItemInfo*<br/>
Windows SDK の「 *lpmii* in」を参照してください `InsertMenuItem` 。

*fByPos*<br/>
Windows SDK の「」の *Fbyposition* の説明を参照してください `InsertMenuItem` 。

### <a name="remarks"></a>解説

この関数は、Windows SDK で説明されている [Insertmenuitem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw)をラップします。

## <a name="cmenuloadmenu"></a><a name="loadmenu"></a> CMenu:: LoadMenu

アプリケーションの実行可能ファイルからメニューリソースを読み込み、それをオブジェクトにアタッチし `CMenu` ます。

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>パラメーター

*lpszResourceName*<br/>
読み込むメニューリソースの名前を含む、null で終わる文字列を指します。

*nIDResource*<br/>
読み込むメニューリソースのメニュー ID を指定します。

### <a name="return-value"></a>戻り値

メニューリソースが正常に読み込まれた場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

終了する前に、メニューがウィンドウに割り当てられていない場合は、アプリケーションでメニューに関連付けられているシステムリソースを解放する必要があります。 アプリケーションは、 [destroymenu](#destroymenu) メンバー関数を呼び出すことによってメニューを解放します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

## <a name="cmenuloadmenuindirect"></a><a name="loadmenuindirect"></a> CMenu:: LoadMenuIndirect

メモリ内のメニューテンプレートからリソースを読み込み、それをオブジェクトにアタッチし `CMenu` ます。

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>パラメーター

*lpMenuTemplate*<br/>
メニューテンプレート (1 つの [Menuitemtemplateheader](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader) 構造体と1つ以上の [menuitemtemplate](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) 構造体のコレクション) をポイントします。 これらの2つの構造体の詳細については、Windows SDK を参照してください。

### <a name="return-value"></a>戻り値

メニューリソースが正常に読み込まれた場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

メニューテンプレートとは、1つまたは複数のメニュー項目とポップアップメニューを含む、1つ以上の [Menuitemtemplate](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) 構造体で構成されるヘッダーです。

バージョン番号は0にする必要があります。

フラグには、 `mtOption` ポップアップリストの最後の項目、およびメインリストの最後の項目の MF_END が含まれている必要があります。 `AppendMenu`他のフラグについては、メンバー関数を参照してください。 `mtId`で MF_POPUP が指定されている場合は、MENUITEMTEMPLATE 構造体からメンバーを省略する必要があり `mtOption` ます。

MENUITEMTEMPLATE 構造体に割り当てられた領域は、 `mtString` メニュー項目の名前を null で終わる文字列として格納するのに十分な大きさである必要があります。

終了する前に、メニューがウィンドウに割り当てられていない場合は、アプリケーションでメニューに関連付けられているシステムリソースを解放する必要があります。 アプリケーションは、 [destroymenu](#destroymenu) メンバー関数を呼び出すことによってメニューを解放します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

## <a name="cmenum_hmenu"></a><a name="m_hmenu"></a> CMenu:: m_hMenu

オブジェクトに関連付けられている Windows メニューの HMENU ハンドルを指定し `CMenu` ます。

```
HMENU m_hMenu;
```

### <a name="example"></a>例

  「 [CMenu:: LoadMenu](#loadmenu)」の例を参照してください。

## <a name="cmenumeasureitem"></a><a name="measureitem"></a> CMenu:: MeasureItem

オーナー描画スタイルのメニューが作成されたときにフレームワークによって呼び出されます。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>パラメーター

*lpMeasureItemStruct*<br/>
構造体へのポインター `MEASUREITEMSTRUCT` 。

### <a name="remarks"></a>解説

既定では、このメンバー関数は何も行いません。 このメンバー関数をオーバーライドし、構造体に入力して `MEASUREITEMSTRUCT` 、メニューの次元をウィンドウに通知します。

構造の説明については、「 [CWnd:: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) 」を参照してください `MEASUREITEMSTRUCT` 。

### <a name="example"></a>例

次のコードは、MFC [CTRLTEST](../../overview/visual-cpp-samples.md) サンプルからのものです。

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

## <a name="cmenumodifymenu"></a><a name="modifymenu"></a> CMenu:: ModifyMenu

*NPosition* によって指定された位置にある既存のメニュー項目を変更します。

```
BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>パラメーター

*nPosition*<br/>
変更するメニュー項目を指定します。 *NFlags* パラメーターを使用すると、次の方法で *nPosition* を解釈できます。

|nFlags|NPosition の解釈|
|------------|---------------------------------|
|MF_BYCOMMAND|パラメーターが既存のメニュー項目のコマンド ID を与えることを指定します。 これは、MF_BYCOMMAND も MF_BYPOSITION も設定されていない場合の既定値です。|
|MF_BYPOSITION|パラメーターが既存のメニュー項目の位置を指定することを指定します。 最初の項目の位置は0です。|

*nFlags*<br/>
*NPosition* をどのように解釈するかを指定し、メニュー項目に加えられる変更に関する情報を提供します。 設定できるフラグの一覧については、「 [Appendmenu](#appendmenu) メンバー関数」を参照してください。

*nIDNewItem*<br/>
変更したメニュー項目のコマンド ID を指定するか、または *nFlags* が MF_POPUP に設定されている場合は、ポップアップメニューのメニューハンドル (HMENU) を指定します。 *NFlags* が MF_SEPARATOR に設定されている場合、 *nIDNewItem* パラメーターは無視されます (必要ありません)。

*lpszNewItem*<br/>
新しいメニュー項目の内容を指定します。 *NFlags* パラメーターを使用すると、次の方法で *lpszNewItem* を解釈できます。

|nFlags|LpszNewItem の解釈|
|------------|-----------------------------------|
|MF_OWNERDRAW|アプリケーションが、メニュー項目に関連付けられた追加データを保持するために使用できる32ビット値を格納します。 この32ビット値は、アプリケーションが MF_MEASUREITEM と MF_DRAWITEM を処理するときに使用できます。|
|MF_STRING|Null で終わる文字列またはへの long ポインターを格納し `CString` ます。|
|MF_SEPARATOR|*LpszNewItem* パラメーターは無視されます (不要)。|

*.Pbmp*<br/>
`CBitmap`メニュー項目として使用されるオブジェクトを指します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>解説

アプリケーションでは、値を *nFlags* に設定することによって、メニュー項目の新しい状態を指定します。 この関数がメニュー項目に関連付けられているポップアップメニューを置き換える場合は、古いポップアップメニューを破棄し、ポップアップメニューで使用されているメモリを解放します。

*NIDNewItem* がポップアップメニューを指定すると、それが挿入されるメニューの一部になります。 このメニューが破棄されると、挿入されたメニューも破棄されます。 競合を回避するには、挿入されたメニューをオブジェクトからデタッチする必要があり `CMenu` ます。

ウィンドウに表示されているメニューが変更された場合 (ウィンドウが表示されているかどうかにかかわらず)、アプリケーションはを呼び出す必要があり `CWnd::DrawMenuBar` ます。 既存のメニュー項目の属性を変更するには、 `CheckMenuItem` およびメンバー関数を使用する方がはるかに高速です `EnableMenuItem` 。

### <a name="example"></a>例

  「 [CMenu:: InsertMenu](#insertmenu)」の例を参照してください。

## <a name="cmenuoperator-hmenu"></a><a name="operator_hmenu"></a> CMenu:: operator HMENU

オブジェクトのハンドルを取得するには、この演算子を使用し `CMenu` ます。

```
operator HMENU() const;
```

### <a name="return-value"></a>戻り値

成功した場合は、オブジェクトのハンドル `CMenu` 。それ以外の場合は NULL。

### <a name="remarks"></a>解説

ハンドルを使用すると、Windows Api を直接呼び出すことができます。

## <a name="cmenuoperator-"></a><a name="operator_neq"></a> CMenu:: operator! =

2つのメニューが論理的に等しくないかどうかを判断します。

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>パラメーター

*メニュー*<br/>
比較対象の `CMenu` オブジェクトです。

### <a name="remarks"></a>解説

左側のメニューオブジェクトが右側のメニューオブジェクトと等しくないかどうかをテストします。

## <a name="cmenuoperator-"></a><a name="operator_eq_eq"></a> CMenu:: operator = =

2つのメニューが論理的に等しいかどうかを判断します。

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>パラメーター

*メニュー*<br/>
比較対象の `CMenu` オブジェクトです。

### <a name="remarks"></a>解説

左側のメニューオブジェクトが右側のメニューオブジェクトに等しいかどうかをテストします (HMENU 値の観点から)。

## <a name="cmenuremovemenu"></a><a name="removemenu"></a> CMenu:: RemoveMenu

メニューから、関連付けられたポップアップメニューを含むメニュー項目を削除します。

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>パラメーター

*nPosition*<br/>
削除するメニュー項目を指定します。 *NFlags* パラメーターを使用すると、次の方法で *nPosition* を解釈できます。

|nFlags|NPosition の解釈|
|------------|---------------------------------|
|MF_BYCOMMAND|パラメーターが既存のメニュー項目のコマンド ID を与えることを指定します。 これは、MF_BYCOMMAND も MF_BYPOSITION も設定されていない場合の既定値です。|
|MF_BYPOSITION|パラメーターが既存のメニュー項目の位置を指定することを指定します。 最初の項目の位置は0です。|

*nFlags*<br/>
*NPosition* をどのように解釈するかを指定します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>解説

ポップアップメニューのハンドルは破棄されないため、メニューを再利用できます。 この関数を呼び出す前に、アプリケーションはメンバー関数を呼び出して、 `GetSubMenu` 再利用のためにポップアップオブジェクトを取得することがあり `CMenu` ます。

ウィンドウに表示されているメニューが変更された場合 (ウィンドウが表示されているかどうかにかかわらず)、アプリケーションはを呼び出す必要があり `CWnd::DrawMenuBar` ます。

### <a name="example"></a>例

  「 [CMenu:: InsertMenu](#insertmenu)」の例を参照してください。

## <a name="cmenusetdefaultitem"></a><a name="setdefaultitem"></a> CMenu:: SetDefaultItem

指定したメニューの既定のメニュー項目を設定します。

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>パラメーター

*uItem*<br/>
新しい既定のメニュー項目の識別子または位置。既定の項目がない場合は-1。 このパラメーターの意味は、 *fByPos* の値によって異なります。

*fByPos*<br/>
*Uitem* の意味を指定する値。 このパラメーターが FALSE の場合、 *Uitem* はメニュー項目識別子です。 それ以外の場合は、メニュー項目の位置になります。

### <a name="return-value"></a>戻り値

関数が成功すると、戻り値は 0 以外になります。 関数が失敗した場合は、0 を返します。 拡張エラー情報を取得するには、Windows SDK で説明されているように、Win32 関数 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を使用します。

### <a name="remarks"></a>解説

このメンバー関数は、Windows SDK で説明されているように、Win32 関数 [Setmenudefaultitem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem)の動作を実装します。

### <a name="example"></a>例

  「 [CMenu:: InsertMenu](#insertmenu)」の例を参照してください。

## <a name="cmenusetmenucontexthelpid"></a><a name="setmenucontexthelpid"></a> CMenu:: SetMenuContextHelpId

コンテキストヘルプ ID をに関連付け `CMenu` ます。

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>パラメーター

*dwContextHelpId*<br/>
に関連付けるコンテキストヘルプ ID `CMenu` 。

### <a name="return-value"></a>戻り値

成功した場合は0以外の。それ以外の場合は0

### <a name="remarks"></a>解説

メニュー内のすべての項目はこの識別子を共有します。個々のメニュー項目にヘルプコンテキスト識別子をアタッチすることはできません。

### <a name="example"></a>例

  「 [CMenu:: InsertMenu](#insertmenu)」の例を参照してください。

## <a name="cmenusetmenuinfo"></a><a name="setmenuinfo"></a> CMenu:: SetMenuInfo

メニューの情報を設定します。

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>パラメーター

*lpcmi*<br/>
メニューの情報を格納している [Menuinfo](/windows/win32/api/winuser/ns-winuser-menuinfo) 構造体へのポインター。

### <a name="return-value"></a>戻り値

関数が成功した場合、戻り値は0以外になります。それ以外の場合、戻り値は0です。

### <a name="remarks"></a>解説

この関数を呼び出して、メニューに関する特定の情報を設定します。

## <a name="cmenusetmenuitembitmaps"></a><a name="setmenuitembitmaps"></a> CMenu:: SetMenuItemBitmaps

指定したビットマップをメニュー項目に関連付けます。

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>パラメーター

*nPosition*<br/>
変更するメニュー項目を指定します。 *NFlags* パラメーターを使用すると、次の方法で *nPosition* を解釈できます。

|nFlags|NPosition の解釈|
|------------|---------------------------------|
|MF_BYCOMMAND|パラメーターが既存のメニュー項目のコマンド ID を与えることを指定します。 これは、MF_BYCOMMAND も MF_BYPOSITION も設定されていない場合の既定値です。|
|MF_BYPOSITION|パラメーターが既存のメニュー項目の位置を指定することを指定します。 最初の項目の位置は0です。|

*nFlags*<br/>
*NPosition* をどのように解釈するかを指定します。

*pBmpUnchecked*<br/>
チェックされていないメニュー項目に使用するビットマップを指定します。

*pBmpChecked*<br/>
チェックされるメニュー項目に使用するビットマップを指定します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>解説

メニュー項目がチェックされているかどうかにかかわらず、Windows ではメニュー項目の横に適切なビットマップが表示されます。

*Pbmpunchecked* または *pbmpunchecked* が NULL の場合は、対応する属性のメニュー項目の横に何も表示されません。 両方のパラメーターが NULL の場合、項目がチェックされるときに既定のチェックマークが使用され、項目がオフの場合はチェックマークが削除されます。

メニューが破棄されても、これらのビットマップは破棄されません。アプリケーションでそれらを破棄する必要があります。

Windows 関数は、 `GetMenuCheckMarkDimensions` メニュー項目に使用される既定のチェックマークの寸法を取得します。 アプリケーションでは、これらの値を使用して、この関数で提供されるビットマップの適切なサイズを決定します。 サイズを取得し、ビットマップを作成して、設定します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

## <a name="cmenusetmenuiteminfo"></a><a name="setmenuiteminfo"></a> CMenu:: SetMenuItemInfo

メニュー項目に関する情報を変更します。

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>パラメーター

*uItem*<br/>
Windows SDK の「 [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow)の *uitem* の説明」を参照してください。

*lpMenuItemInfo*<br/>
Windows SDK の「 *lpmii* in」を参照してください `SetMenuItemInfo` 。

*fByPos*<br/>
Windows SDK の「」の *Fbyposition* の説明を参照してください `SetMenuItemInfo` 。

### <a name="remarks"></a>解説

この関数は、Windows SDK で説明されている [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow)をラップします。

## <a name="cmenutrackpopupmenu"></a><a name="trackpopupmenu"></a> CMenu:: TrackPopupMenu

指定した位置にフローティングポップアップメニューを表示し、ポップアップメニュー上の項目の選択を追跡します。

```
BOOL TrackPopupMenu(
    UINT nFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPCRECT lpRect = 0);
```

### <a name="parameters"></a>パラメーター

*nFlags*<br/>
画面位置とマウス位置のフラグを指定します。 使用可能なフラグの一覧については、「 [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) 」を参照してください。

*x*<br/>
ポップアップメニューの画面座標の水平位置を指定します。 *NFlags* パラメーターの値に応じて、この位置を基準として左揃え、右揃え、または中央揃えにすることができます。

*y*<br/>
画面上のメニューの上部の画面座標での垂直位置を指定します。

*pWnd*<br/>
ポップアップメニューを所有するウィンドウを識別します。 TPM_NONOTIFY フラグが指定されている場合でも、このパラメーターを NULL にすることはできません。 このウィンドウは、メニューからすべての WM_COMMAND メッセージを受信します。 Windows バージョン3.1 以降では、が返されるまで、ウィンドウは WM_COMMAND メッセージを受信しません `TrackPopupMenu` 。 Windows 3.0 では、ウィンドウはを返す前に WM_COMMAND メッセージを受信し `TrackPopupMenu` ます。

*lpRect*<br/>
無視されます。

### <a name="return-value"></a>戻り値

このメソッドは、Windows SDK で [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) を呼び出した結果を返します。

### <a name="remarks"></a>解説

フローティングポップアップメニューは、画面上の任意の場所に表示されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

## <a name="cmenutrackpopupmenuex"></a><a name="trackpopupmenuex"></a> CMenu:: TrackPopupMenuEx

指定した位置にフローティングポップアップメニューを表示し、ポップアップメニュー上の項目の選択を追跡します。

```
BOOL TrackPopupMenuEx(
    UINT fuFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPTPMPARAMS lptpm);
```

### <a name="parameters"></a>パラメーター

*Futex フラグ*<br/>
拡張メニューのさまざまな機能を指定します。 すべての値とその意味の一覧については、「 [Trackpopupmenuex](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex)」を参照してください。

*x*<br/>
ポップアップメニューの画面座標の水平位置を指定します。

*y*<br/>
画面上のメニューの上部の画面座標での垂直位置を指定します。

*pWnd*<br/>
ポップアップメニューを所有し、作成されたメニューからメッセージを受信するウィンドウへのポインター。 このウィンドウは、現在のアプリケーションの任意のウィンドウにすることができますが、NULL にすることはできません。 *Futex フラグ* パラメーターに TPM_NONOTIFY を指定した場合、この関数は、メッセージを *pWnd* に送信しません。 この関数は、WM_COMMAND メッセージを受信するために、 *pWnd* が指すウィンドウに対してを返す必要があります。

*lptpm*<br/>
メニューを重ねることができない画面の領域を指定する [TPMPARAMS](/windows/win32/api/winuser/ns-winuser-tpmparams) 構造体へのポインター。 このパラメーターには NULL を指定できます。

### <a name="return-value"></a>戻り値

*Futex フラグ* パラメーターに TPM_RETURNCMD を指定した場合、戻り値は、ユーザーが選択した項目のメニュー項目識別子になります。 ユーザーが選択を行わずにメニューをキャンセルした場合、またはエラーが発生した場合、戻り値は0になります。

*Futex フラグ* パラメーターに TPM_RETURNCMD を指定しなかった場合、戻り値は、関数が成功した場合は0以外の値になり、失敗した場合は0になります。 詳細なエラー情報を得るには、[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) を呼び出します。

### <a name="remarks"></a>解説

フローティングポップアップメニューは、画面上の任意の場所に表示されます。 ポップアップメニューを作成するときのエラー処理の詳細については、「 [Trackpopupmenuex](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex)」を参照してください。

## <a name="see-also"></a>関連項目

[MFC のサンプル CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[MFC のサンプル DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)
