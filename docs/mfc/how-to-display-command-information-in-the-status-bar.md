---
description: '詳細については、「方法: ステータスバーにコマンド情報を表示する」を参照してください。'
title: ステータス バーにコマンド情報を表示する方法
ms.date: 11/04/2016
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
ms.openlocfilehash: 568e8d356659d5267e8c4947f2981cd6243a7056
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330225"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>ステータス バーにコマンド情報を表示する方法

アプリケーションウィザードを実行してアプリケーションのスケルトンを作成する場合は、ツールバーとステータスバーをサポートできます。 アプリケーションウィザードの1つのオプションで両方をサポートしています。 ステータスバーが表示されている場合、ユーザーがポインターをメニューの項目の上に移動すると、アプリケーションにより有用なフィードバックが自動的に提供されます。 メニュー項目が強調表示されると、アプリケーションはステータスバーにプロンプト文字列を自動的に表示します。 たとえば、ユーザーが [**編集**] メニューの [**切り取り**] コマンドの上にポインターを移動すると、ステータスバーに "選択範囲を切り取ってクリップボードに配置する" というメッセージがステータスバーのメッセージ領域に表示されることがあります。 プロンプトは、ユーザーがメニュー項目の目的を理解するのに役立ちます。 これは、ユーザーがツールバーボタンをクリックしたときにも機能します。

このステータスバーのヘルプを追加するには、プログラムに追加するメニュー項目のプロンプト文字列を定義します。 これを行うには、メニューエディターでメニュー項目のプロパティを編集するときに、プロンプト文字列を指定します。 定義した文字列は、アプリケーションリソースファイルに格納されます。これらのコマンドは、説明したコマンドと同じ Id を持ちます。

既定では、アプリケーションウィザードによって、標準の "準備完了" メッセージの ID **AFX_IDS_IDLEMESSAGE** が追加されます。これは、プログラムが新しいメッセージを待機しているときに表示されます。 アプリケーションウィザードで [ヘルプの Context-Sensitive] オプションを指定した場合、メッセージは "ヘルプのために F1 キーを押してください" に変更されます。

## <a name="see-also"></a>関連項目

[メッセージの処理とマッピング](message-handling-and-mapping.md)
