---
description: '詳細情報: メッセージ'
title: メッセージ
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: dbfec2794cc0dae5a7358b3c2ba39553643fb7c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203095"
---
# <a name="messages"></a>メッセージ

`Run`クラスのメンバー関数のメッセージループは、 `CWinApp` さまざまなイベントによって生成されるキューに置かれたメッセージを取得します。 たとえば、ユーザーがマウスをクリックすると、Windows はマウスに関連するいくつかのメッセージを送信します。たとえば、マウスの左ボタンを押したときに、マウスの左ボタンが離されたときに WM_LBUTTONUP WM_LBUTTONDOWN などです。 フレームワークのアプリケーションメッセージループの実装により、メッセージが適切なウィンドウにディスパッチされます。

メッセージの重要なカテゴリについては、「 [メッセージのカテゴリ](message-categories.md)」を参照してください。

## <a name="see-also"></a>関連項目

[フレームワークのメッセージとコマンド](messages-and-commands-in-the-framework.md)
