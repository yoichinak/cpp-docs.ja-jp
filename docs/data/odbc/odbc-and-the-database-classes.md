---
description: 詳細については、「ODBC とデータベースクラス」を参照してください。
title: ODBC とデータベース クラス
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 146170ddd97dfc2797fd1f755459f370be638ded
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326771"
---
# <a name="odbc-and-the-database-classes"></a>ODBC とデータベース クラス

MFC ODBC データベースクラスは、通常、 [CDatabase](../../mfc/reference/cdatabase-class.md) クラスおよび [CRecordset](../../mfc/reference/crecordset-class.md) クラスのメンバー関数に対して実行する odbc API 関数呼び出しをカプセル化します。 たとえば、複雑な ODBC 呼び出しシーケンス、返されたレコードのストレージの場所へのバインド、エラー条件の処理、およびその他の操作は、データベースクラスによって管理されます。 そのため、非常に単純なクラスインターフェイスを使用して、レコードセットオブジェクトを介してレコードを操作します。

> [!NOTE]
> ODBC データ ソースには、ここで説明するように、MFC ODBC クラス経由でアクセスできます。また、MFC DAO (Data Access Object) クラス経由でもアクセスできます。

データベースクラスは、ODBC 機能をカプセル化しますが、ODBC API 関数の一対一のマッピングを提供しません。 データベースクラスは、Microsoft Access および Microsoft Visual Basic に含まれるデータアクセスオブジェクトの後にモデル化された、より高いレベルの抽象化を提供します。 詳細については、「 [ODBC および MFC](../../data/odbc/odbc-and-mfc.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ODBC の基礎](../../data/odbc/odbc-basics.md)
