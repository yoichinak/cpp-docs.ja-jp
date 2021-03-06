---
description: '詳細については、「レコードセット: ブックマークと絶対位置 (ODBC)」を参照してください。'
title: 'レコードセット: ブックマークと絶対位置 (ODBC)'
ms.date: 11/04/2016
f1_keywords:
- SetAbsolutePosition
helpviewer_keywords:
- CDBVariant class, bookmarks
- absolute positions, ODBC recordsets
- bookmarks, CDBVariant
- bookmarks, ODBC recordsets
- ODBC recordsets, absolute positions
- ODBC recordsets, bookmarks
- cursors [ODBC], absolute position in recordsets
- recordsets, bookmarks
- bookmarks
- SetAbsolutePosition method
- recordsets, absolute positions
- positioning records
- SetBookmark method
- record positioning
- GetBookmark method
- SetAbsolutePosition method, bookmarks
ms.assetid: 189788d6-33c1-41c5-9265-97db2a5d43cc
ms.openlocfilehash: b52ca2e43a89a6cab0e9197d8dbf32c321feca5e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186117"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>レコードセット: ブックマークと絶対位置 (ODBC)

このトピックの内容は、MFC ODBC クラスに該当します。

レコードセット内を移動するときは、多くの場合、特定のレコードに戻る方法が必要になります。 レコードのブックマークと絶対位置には、このような2つのメソッドが用意されています。

このトピックでは、次の内容について説明します。

- [ブックマークの使用方法](#_core_bookmarks_in_mfc_odbc)。

- [絶対位置を使用して現在のレコードを設定する方法](#_core_absolute_positions_in_mfc_odbc)。

## <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a> MFC ODBC でのブックマーク

ブックマークは、レコードを一意に識別します。 レコードセット内を移動すると、レコードセットからレコードを削除できるため、レコードの絶対位置を常に使用することはできません。 レコードの位置を追跡する信頼できる方法は、そのブックマークを使用することです。 クラスは `CRecordset` 、次のためのメンバー関数を提供します。

- 現在のレコードのブックマークを取得して、変数 ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)) に保存できるようにします。

- 変数 ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)) で前に保存したブックマークを指定することにより、特定のレコードにすばやく移動します。

次の例では、これらのメンバー関数を使用して、現在のレコードをマークし、後でそれに戻る方法を示します。

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

[CDBVariant クラス](../../mfc/reference/cdbvariant-class.md)オブジェクトから基になるデータ型を抽出する必要はありません。 値をに代入し、を使用して `GetBookmark` そのブックマークに戻り `SetBookmark` ます。

> [!NOTE]
> ODBC ドライバーとレコードセットの種類によっては、ブックマークがサポートされていない場合があります。 [CRecordset:: CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark)を呼び出すことで、ブックマークがサポートされているかどうかを簡単に判断できます。 さらに、ブックマークがサポートされている場合は、 `CRecordset::useBookmarks` [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) メンバー関数でオプションを指定することによって、ブックマークを実装することを明示的に選択する必要があります。 また、特定のレコードセット操作の後にブックマークが永続化されていることを確認する必要もあります。 たとえば、 `Requery` レコードセットでは、ブックマークが無効になっている可能性があります。 を安全に呼び出すことができるかどうかを確認するには、 [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) を呼び出し `SetBookmark` ます。

## <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a> 絶対位置 (MFC ODBC)

ブックマークに加えて、クラスでは、 `CRecordset` 序数位置を指定することによって現在のレコードを設定することができます。 これは絶対配置と呼ばれます。

> [!NOTE]
> 順方向専用のレコードセットでは、絶対配置は使用できません。 前方参照専用レコードセットの詳細については、「 [レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)」を参照してください。

絶対位置を使用して現在のレコードポインターを移動するには、 [CRecordset:: SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition)を呼び出します。 に値を渡すと `SetAbsolutePosition` 、その序数位置に対応するレコードが現在のレコードになります。

> [!NOTE]
> レコードの絶対位置が信頼できない可能性があります。 ユーザーがレコードセットからレコードを削除した場合、後続のレコードの順序が変更されます。 ブックマークは、現在のレコードを移動するために推奨される方法です。 詳細については、「 [MFC ODBC のブックマーク](#_core_bookmarks_in_mfc_odbc)」を参照してください。

レコードセットナビゲーションの詳細については、「 [レコードセット: スクロール (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)」を参照してください。

## <a name="see-also"></a>関連項目

[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md)
