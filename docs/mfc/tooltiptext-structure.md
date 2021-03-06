---
description: '詳細については、次を参照してください: TOOLTIPTEXT 構造体'
title: TOOLTIPTEXT 構造体
ms.date: 11/04/2016
f1_keywords:
- TOOLTIPTEXT
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
ms.openlocfilehash: 077d4c27392b626a0e9665851eadf227245029b6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264298"
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT 構造体

[ツールヒントの通知ハンドラー](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)を記述するときは、 **TOOLTIPTEXT** 構造体を使用する必要があります。 **TOOLTIPTEXT** 構造体のメンバーは次のとおりです。

```cpp
typedef struct {
    NMHDR     hdr;        // required for all WM_NOTIFY messages
    LPTSTR    lpszText;   // see below
    TCHAR     szText[80]; // buffer for tool tip text
    HINSTANCE hinst;      // see below
    UINT      uflags;     // flag indicating how to interpret the
                          // idFrom member of the NMHDR structure
                          // that is included in the structure
} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;
```

*hdr*<br/>
テキストが必要なツールを識別します。 この構造体に必要な唯一のメンバーは、コントロールのコマンド ID です。 コントロールのコマンド ID は、構文でアクセスされる、 **NMHDR** 構造体の *idfrom* メンバーに含まれ `hdr.idFrom` ます。 **Nmhdr** 構造体のメンバーの説明については、「 [nmhdr](/windows/win32/api/richedit/ns-richedit-nmhdr) 」を参照してください。

*lpszText*<br/>
ツールのテキストを受信する文字列のアドレス。

*szText*<br/>
ツールヒントテキストを受け取るバッファー。 アプリケーションでは、文字列アドレスを指定する代わりに、このバッファーにテキストをコピーできます。

*hinst*<br/>
ツールヒントのテキストとして使用される文字列を含むインスタンスのハンドル。 *LpszText* がツールヒントテキストのアドレスの場合、このメンバーは NULL になります。

通知メッセージを処理するときは、 `TTN_NEEDTEXT` 次のいずれかの方法で表示される文字列を指定します。

- *Sztext* メンバーによって指定されたバッファーにテキストをコピーします。

- テキストが格納されているバッファーのアドレスを *lpszText* メンバーにコピーします。

- 文字列リソースの識別子を *lpszText* メンバーにコピーし、リソースが格納されているインスタンスのハンドルを *hinst* メンバーにコピーします。

## <a name="see-also"></a>関連項目

[CFrameWnd から派生していない Windows のツールヒント](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
