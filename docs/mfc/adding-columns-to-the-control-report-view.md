---
description: 詳細については、「コントロールへの列の追加 (レポートビュー)」を参照してください。
title: コントロールへの列の追加 (レポート ビュー)
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding columns
- report view in CListCtrl class [MFC]
- views [MFC], report
- columns [MFC], adding to CListCtrl
- CListCtrl class [MFC], report view
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
ms.openlocfilehash: 62e874f77d326b80a362791888e75df0a92781d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339097"
---
# <a name="adding-columns-to-the-control-report-view"></a>コントロールへの列の追加 (レポート ビュー)

> [!NOTE]
> 次の手順は、 [CListView](reference/clistview-class.md) オブジェクトまたは [CListCtrl](reference/clistctrl-class.md) オブジェクトのいずれかに適用されます。

リストコントロールがレポートビューの場合、列が表示され、各リストコントロール項目のさまざまなサブ項目を整理することができます。 この組織は、リストコントロール内の列とリストコントロール項目の関連するサブ項目の間に1対1の対応が実装されています。 サブ項目の詳細については、「 [コントロールへの項目の追加](adding-items-to-the-control.md)」を参照してください。 レポートビューのリストコントロールの例は、Windows 95 および Windows 98 Explorer の詳細ビューによって提供されます。 最初の列には、フォルダー、ファイルアイコン、およびラベルが一覧表示されます。 他の列の一覧ファイルのサイズ、ファイルの種類、最終更新日など。

いつでも列をリストコントロールに追加できますが、列は、コントロールのスタイルビットがオンになっている場合にのみ表示され `LVS_REPORT` ます。

各列には、関連付けられたヘッダー項目 (「 [CHeaderCtrl](reference/cheaderctrl-class.md)」を参照) があります。このオブジェクトは、列にラベルを付け、ユーザーが列のサイズを変更できるようにします

リストコントロールでレポートビューがサポートされている場合は、リストコントロール項目で、使用可能な各サブ項目の列を追加する必要があります。 列を追加するには、 [LVCOLUMN](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw) 構造体を準備してから、 [insertcolumn](reference/clistctrl-class.md#insertcolumn)を呼び出します。 必要な列 (ヘッダー項目と呼ばれることもあります) を追加した後は、埋め込みヘッダーコントロールに属しているメンバー関数とスタイルを使用して、列を並べ替えることができます。 詳細については、「 [ヘッダーコントロールの項目の順序付け](ordering-items-in-the-header-control.md)」を参照してください。

> [!NOTE]
> リストコントロールが **LVS_NOCOLUMNHEADER** スタイルで作成された場合、列を挿入しようとしても無視されます。

## <a name="see-also"></a>関連項目

[CListCtrl の使い方](using-clistctrl.md)<br/>
[コントロール](controls-mfc.md)
