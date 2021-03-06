---
description: '詳細情報: Rubber-Banding とトラッカー'
title: ラバー バンド処理とトラッカー
ms.date: 11/04/2016
helpviewer_keywords:
- trackers [MFC]
- CRectTracker class [MFC], implementing trackers
- OLE objects [MFC], selecting
- rubber banding [MFC]
- WM_LBUTTONDOWN [MFC]
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
ms.openlocfilehash: 5d641e7553a2891e0319484558f025c6998f9693
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217836"
---
# <a name="rubber-banding-and-trackers"></a>ラバー バンド処理とトラッカー

トラッカーに用意されているもう1つの機能は "ラバーバンド" の選択です。これにより、ユーザーは、選択する項目の周囲にサイズ変更の四角形をドラッグすることで、複数の OLE 項目を選択できます。 ユーザーがマウスの左ボタンを離すと、ユーザーが選択した領域内の項目が選択され、ユーザーが操作できるようになります。 たとえば、ユーザーが選択項目を別のコンテナーアプリケーションにドラッグする場合があります。

この機能を実装するには、アプリケーションの WM_LBUTTONDOWN ハンドラー関数に追加のコードが必要です。

次のコードサンプルでは、ラバーバンドの選択と追加機能を実装しています。

[!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]

ラバーバンド処理中にトラッカーの向きを元に戻せるようにするには、3番目のパラメーターを **TRUE** に設定して [CRectTracker:: TrackRubberBand](../mfc/reference/crecttracker-class.md#trackrubberband)を呼び出す必要があります。 向きを反転可能にすると、 [CRectTracker:: m_rect](../mfc/reference/crecttracker-class.md#m_rect) が逆になる場合があることに注意してください。 これは、 [CRect:: NormalizeRect](../atl-mfc-shared/reference/crect-class.md#normalizerect)を呼び出すことによって修正できます。

詳細については、「 [コンテナークライアントアイテム](../mfc/containers-client-items.md) 」および「 [OLE ドラッグアンドドロップ: カスタマイズドラッグアンドドロップ](../mfc/drag-and-drop-ole.md#customize-drag-and-drop)」を参照してください。

## <a name="see-also"></a>関連項目

[トラッカー: OLE アプリケーションでのトラッカーの実装](../mfc/trackers-implementing-trackers-in-your-ole-application.md)<br/>
[CRectTracker クラス](../mfc/reference/crecttracker-class.md)
