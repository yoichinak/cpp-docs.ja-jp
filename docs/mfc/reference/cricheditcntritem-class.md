---
description: '詳細情報: CRichEditCntrItem クラス'
title: CRichEditCntrItem クラス
ms.date: 11/04/2016
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
helpviewer_keywords:
- CRichEditCntrItem [MFC], CRichEditCntrItem
- CRichEditCntrItem [MFC], SyncToRichEditObject
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
ms.openlocfilehash: 9e65e70a3fb03b65ebf9af7a619a5c4fbd3dba32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342961"
---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem クラス

[CRichEditView](../../mfc/reference/cricheditview-class.md)と[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)を使用すると、は、MFC のドキュメントビューアーキテクチャのコンテキスト内で、リッチエディットコントロールの機能を提供します。

## <a name="syntax"></a>構文

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CRichEditCntrItem:: CRichEditCntrItem](#cricheditcntritem)|`CRichEditCntrItem` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CRichEditCntrItem:: SyncToRichEditObject](#synctoricheditobject)|項目を別の型としてアクティブにします。|

## <a name="remarks"></a>解説

"リッチエディットコントロール" は、ユーザーがテキストを入力して編集できるウィンドウです。 テキストには、文字や段落の書式を割り当てることができ、埋め込み OLE オブジェクトを含めることができます。 リッチエディットコントロールは、テキストを書式設定するためのプログラミングインターフェイスを提供します。 ただし、アプリケーションは、ユーザーが書式設定操作を使用できるようにするために必要なユーザーインターフェイスコンポーネントを実装する必要があります。

`CRichEditView` テキストのテキストと書式設定の特性を維持します。 `CRichEditDoc` ビュー内の OLE クライアントアイテムの一覧を保持します。 `CRichEditCntrItem` OLE クライアントアイテムへのコンテナー側のアクセスを提供します。

この Windows コモンコントロール (および [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) および関連クラス) は、windows 95/98 および windows NT バージョン3.51 以降で実行されているプログラムに対してのみ使用できます。

MFC アプリケーションでリッチエディットコンテナー項目を使用する例については、「 [ワードパッド](../../overview/visual-cpp-samples.md) サンプルアプリケーション」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>要件

**ヘッダー:** afxrich

## <a name="cricheditcntritemcricheditcntritem"></a><a name="cricheditcntritem"></a> CRichEditCntrItem:: CRichEditCntrItem

オブジェクトを作成 `CRichEditCntrItem` し、コンテナードキュメントに追加するには、この関数を呼び出します。

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>パラメーター

*preo*<br/>
OLE 項目を記述する [Reobject](/windows/win32/api/richole/ns-richole-reobject) 構造体へのポインター。 新しい `CRichEditCntrItem` オブジェクトは、この OLE 項目を中心に構築されます。 *Preo* が NULL の場合、クライアントアイテムは空になります。

*pContainer*<br/>
この項目を格納するコンテナードキュメントへのポインター。 *Pcontainer* が NULL の場合、このクライアント項目をドキュメントに追加するには、 [COleDocument:: AddItem](../../mfc/reference/coledocument-class.md#additem)を明示的に呼び出す必要があります。

### <a name="remarks"></a>解説

この関数では、OLE の初期化は実行されません。

詳細については、Windows SDK の「 [Reobject](/windows/win32/api/richole/ns-richole-reobject) 構造体」を参照してください。

## <a name="cricheditcntritemsynctoricheditobject"></a><a name="synctoricheditobject"></a> CRichEditCntrItem:: SyncToRichEditObject

この関数を呼び出して、デバイスの縦横比 ( [Dvaspect](/windows/win32/api/wtypes/ne-wtypes-dvaspect)) を、 `CRichEditCntrltem` *reo* で指定されたものに同期します。

```cpp
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>パラメーター

*reo*<br/>
OLE 項目を記述する [Reobject](/windows/win32/api/richole/ns-richole-reobject) 構造体への参照。

### <a name="remarks"></a>解説

詳細については、Windows SDK の [Dvaspect](/windows/win32/api/wtypes/ne-wtypes-dvaspect) に関する説明を参照してください。

## <a name="see-also"></a>関連項目

[MFC のサンプルワードパッド](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem クラス](../../mfc/reference/coleclientitem-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc クラス](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditView クラス](../../mfc/reference/cricheditview-class.md)
