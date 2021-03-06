---
description: '詳細情報: CMFCRibbonApplicationButton クラス'
title: CMFCRibbonApplicationButton クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::SetImage
helpviewer_keywords:
- CMFCRibbonApplicationButton [MFC], CMFCRibbonApplicationButton
- CMFCRibbonApplicationButton [MFC], SetImage
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
ms.openlocfilehash: 391274c7540e7e52a19c20e17a09b25f37badcd6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289804"
---
# <a name="cmfcribbonapplicationbutton-class"></a>CMFCRibbonApplicationButton クラス

アプリケーション ウィンドウの左上隅に表示される特殊なボタンを実装します。 このボタンがクリックされると、通常は、一般的な **[ファイル]** メニューのコマンド ( **[開く]**、 **[上書き保存]**、 **[終了]** など) を含むメニューが開かれます。

## <a name="syntax"></a>構文

```
class CMFCRibbonApplicationButton : public CMFCRibbonButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonApplicationButton:: CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|`CMFCRibbonApplicationButton` オブジェクトを構築して初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|`CMFCRibbonApplicationButton::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|`CMFCRibbonApplicationButton::GetThisClass`|このクラス型に関連付けられている [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|[CMFCRibbonApplicationButton:: SetImage](#setimage)|リボンアプリケーションボタンにイメージを割り当てます。|

## <a name="example"></a>例

`CMFCRibbonApplicationButton` クラスのさまざまなメソッドの使用方法を次の例に示します。 この例では、イメージをアプリケーションボタンに割り当てる方法と、そのツールヒントを設定する方法を示します。 このコード スニペットは、「 [クライアント サンプルの描画](../../overview/visual-cpp-samples.md)」の一部です。

[!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

## <a name="requirements"></a>要件

**ヘッダー:** afxribbonbar.h

## <a name="cmfcribbonapplicationbuttoncmfcribbonapplicationbutton"></a><a name="cmfcribbonapplicationbutton"></a> CMFCRibbonApplicationButton:: CMFCRibbonApplicationButton

[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)オブジェクトを構築し、初期化します。

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>パラメーター

*uiBmpResID*<br/>
アプリケーションボタンに表示するイメージのリソース ID。

*hBmp*<br/>
アプリケーションボタンに表示するビットマップを処理するハンドル。

### <a name="remarks"></a>解説

リボンアプリケーションボタンは、アプリケーションウィンドウの左上隅にある特別なボタンです。 ユーザーがこのボタンをクリックすると、[**開く**]、[**保存**]、[**終了**] など、一般的な **ファイル** コマンドを含むメニューが表示されます。

## <a name="cmfcribbonapplicationbuttonsetimage"></a><a name="setimage"></a> CMFCRibbonApplicationButton:: SetImage

アプリケーションボタンにイメージを割り当てます。

```cpp
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>パラメーター

*uiBmpResID*<br/>
からアプリケーションボタンに表示するイメージのリソース ID。

*hBmp*<br/>
からアプリケーションボタンに表示するビットマップを処理するハンドル。

### <a name="remarks"></a>解説

このメソッドを使用すると、ボタンを作成した後、リボンアプリケーションのボタンに新しいイメージを割り当てることができます。 アプリケーションボタンは、アプリケーションウィンドウの左上隅にあります。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton クラス](../../mfc/reference/cmfcribbonbutton-class.md)
