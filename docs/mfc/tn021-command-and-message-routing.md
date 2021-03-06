---
description: '詳細については、「テクニカルノート 21: コマンドとメッセージのルーティング」を参照してください。'
title: 'テクニカル ノート 21: コマンドとメッセージのルーティング'
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: 3cc481585fa2f1eacc3deb575e163d5a1644002c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215847"
---
# <a name="tn021-command-and-message-routing"></a>テクニカル ノート 21: コマンドとメッセージのルーティング

> [!NOTE]
> 次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

このメモでは、コマンドのルーティングとディスパッチのアーキテクチャについて説明します。また、一般的なウィンドウメッセージのルーティングに関する高度なトピックも紹介します。

ここで説明するアーキテクチャの全般的な詳細については、「Visual C++」を参照してください。特に、Windows メッセージ、コントロール通知、およびコマンドの違いについて説明します。 このメモでは、ドキュメントに記載されている問題についてよく理解していること、および高度なトピックのみを取り上げていることを前提としています。

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>コマンドルーティングとディスパッチ MFC 1.0 機能は、MFC 2.0 アーキテクチャに進化します。

Windows には、メニューコマンド、アクセラレータキー、およびダイアログコントロール通知の通知を提供するためにオーバーロードされた WM_COMMAND メッセージがあります。

MFC 1.0 では、派生クラスのコマンドハンドラー (たとえば、"OnFileNew") が `CWnd` 特定の WM_COMMAND に応答して呼び出されるようにすることで、そのことを少し上に構築しました。 これは、メッセージマップと呼ばれるデータ構造と共に結合され、非常に効率的なコマンドメカニズムになります。

MFC 1.0 には、コマンドメッセージからコントロール通知を分離するための追加機能も用意されています。 コマンドは、コマンド ID とも呼ばれる16ビット ID で表されます。 コマンドは、通常、 `CFrameWnd` (メニュー選択または変換されたアクセラレータ) から開始し、他のさまざまなウィンドウにルーティングされます。

MFC 1.0 では、マルチドキュメントインターフェイス (MDI) の実装に対して、限られた意味でコマンドルーティングを使用していました。 (MDI フレームウィンドウは、アクティブな MDI 子ウィンドウにコマンドをデリゲートします)。

この機能は、MFC 2.0 で一般化および拡張されており、コマンドをウィンドウオブジェクトだけでなく、より広い範囲のオブジェクトによって処理できるようになっています。 これにより、メッセージをルーティングするためのより正式で拡張可能なアーキテクチャが提供され、コマンドの処理だけでなく、UI オブジェクト (メニュー項目やツールバーボタンなど) を更新して、コマンドの現在の可用性を反映することができます。

## <a name="command-ids"></a>コマンド ID

コマンドのルーティングとバインドのプロセスの説明については、「Visual C++」を参照してください。 [テクニカルノート 20](../mfc/tn020-id-naming-and-numbering-conventions.md) には、ID の名前付けに関する情報が含まれています。

コマンド Id には、汎用プレフィックス "ID_" を使用します。 コマンド Id は >= 0x8000 です。 コマンド ID と同じ Id を持つ STRINGTABLE リソースがある場合、メッセージ行またはステータスバーにコマンドの説明の文字列が表示されます。

アプリケーションのリソースでは、コマンド ID がいくつかの場所に表示されます。

- メッセージ行プロンプトと同じ ID を持つ1つの STRINGTABLE リソース。

- 同じコマンドを呼び出すメニュー項目に関連付けられているメニューリソースが多数ある可能性があります。

- (詳細) GOSUB コマンドのダイアログボタン。

アプリケーションのソースコードでは、コマンド ID がいくつかの場所に表示されます。

- を使用します。H (またはその他のメインシンボルヘッダーファイル) を指定して、アプリケーション固有のコマンド Id を定義します。

- 場合によっては、ツールバーの作成に使用される ID 配列です。

- ON_COMMAND マクロ。

- おそらく、ON_UPDATE_COMMAND_UI マクロです。

現時点では、コマンド Id を必要とする MFC の唯一の実装は >= 0x8000 で、GOSUB ダイアログ/コマンドの実装です。

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>GOSUB コマンド、ダイアログでのコマンドアーキテクチャの使用

ルーティングと有効化コマンドのコマンドアーキテクチャは、フレームウィンドウ、メニュー項目、ツールバーボタン、ダイアログバーボタン、その他のコントロールバー、要求時に更新するように設計された他のユーザーインターフェイス要素、メインコマンドターゲット (通常はメインフレームウィンドウ) に対して適切に動作します。 このメインコマンドターゲットは、コマンドまたはコントロールの通知を、必要に応じて他のコマンドターゲットオブジェクトにルーティングできます。

ダイアログ (モーダルまたはモードレス) は、ダイアログコントロールのコントロール ID を適切なコマンド ID に割り当てると、コマンドアーキテクチャの一部の機能を利用できます。 ダイアログのサポートは自動的には行われないため、追加のコードを記述することが必要になる場合があります。

これらのすべての機能が正常に機能するためには、コマンド Id を >= 0x8000 にする必要があります。 多くのダイアログは同じフレームにルーティングされる可能性があるため、共有コマンドは >= 0x8000 である必要がありますが、特定のダイアログの非共有の IDCs は <= である必要があります。

通常のモーダルダイアログに通常のボタンを配置すると、そのボタンの IDC が適切なコマンド ID に設定されます。 ユーザーがボタンを選択すると、ダイアログの所有者 (通常はメインフレームウィンドウ) は、他のコマンドと同じようにコマンドを取得します。 これを GOSUB コマンドと呼びます。これは通常、別のダイアログ (最初のダイアログの GOSUB) を表示するために使用されるためです。

また、ダイアログで関数を呼び出して、 `CWnd::UpdateDialogControls` メインフレームウィンドウのアドレスを渡すこともできます。 この関数は、フレーム内にコマンドハンドラーがあるかどうかに基づいて、ダイアログコントロールを有効または無効にします。 この関数は、アプリケーションのアイドルループのコントロールバーに対して自動的に呼び出されますが、この機能を使用する通常のダイアログに対しては、この関数を直接呼び出す必要があります。

## <a name="when-on_update_command_ui-is-called"></a>ON_UPDATE_COMMAND_UI が呼び出されたとき

すべてのプログラムのメニュー項目の有効/チェック済みの状態を維持することは、時間のかかる負荷の高い問題になる可能性があります。 一般的な方法は、ユーザーがポップアップを選択した場合にのみ、メニュー項目を有効またはオンにすることです。 MFC 2.0 の実装では、 `CFrameWnd` WM_INITMENUPOPUP メッセージを処理し、コマンドルーティングアーキテクチャを使用して ON_UPDATE_COMMAND_UI ハンドラーを通じてメニューの状態を確認します。

`CFrameWnd` また、は、ステータスバー (メッセージ行とも呼ばれます) で選択されている現在のメニュー項目を説明するために WM_ENTERIDLE メッセージも処理します。

Visual C++ によって編集されたアプリケーションのメニュー構造は、WM_INITMENUPOPUP 時に使用可能なコマンドを表すために使用されます。 ON_UPDATE_COMMAND_UI ハンドラーでは、メニューの状態またはテキストを変更したり、高度な使用 ([MRU] の一覧や OLE 動詞のポップアップメニューなど) に対して、メニューを描画する前にメニューの構造を変更したりできます。

アプリケーションがアイドルループに入ると、同じ種類の ON_UPDATE_COMMAND_UI 処理が、ツールバー (およびその他のコントロールバー) に対して行われます。 コントロールバーの詳細については、「 *クラスライブラリリファレンス* 」および「 [テクニカルノート 31](../mfc/tn031-control-bars.md) 」を参照してください。

## <a name="nested-pop-up-menus"></a>入れ子になったポップアップメニュー

入れ子になったメニュー構造を使用している場合は、ポップアップメニューの最初のメニュー項目の ON_UPDATE_COMMAND_UI ハンドラーが2つの異なるケースで呼び出されていることがわかります。

まず、ポップアップメニュー自体に対してが呼び出されます。 ポップアップメニューには Id がないため、ポップアップメニューの最初のメニュー項目の ID を使用してポップアップメニュー全体を参照するため、この操作が必要になります。 この場合、オブジェクトの *m_pSubMenu* メンバー変数は NULL 以外の値になり、 `CCmdUI` ポップアップメニューをポイントします。

次に、ポップアップメニューのメニュー項目が描画される直前に呼び出されます。 この場合、ID は最初のメニュー項目だけを参照し、オブジェクトの *m_pSubMenu* メンバー変数は `CCmdUI` NULL になります。

これにより、ポップアップメニューをメニュー項目とは別に有効にすることができますが、メニューを認識するコードを記述する必要があります。 たとえば、次の構造を持つ入れ子になったメニューがあるとします。

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

ID_NEW_SHEET コマンドと ID_NEW_CHART コマンドは、個別に有効または無効にすることができます。 2つのいずれかが有効になっている場合は、 **新しい** ポップアップメニューを有効にする必要があります。

ID_NEW_SHEET のコマンドハンドラー (ポップアップの最初のコマンド) は次のようになります。

```cpp
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)
{
    if (pCmdUI->m_pSubMenu != NULL)
    {
        // enable entire pop-up for "New" sheet and chart
        BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;
        // CCmdUI::Enable is a no-op for this case, so we
        // must do what it would have done.
        pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex,
            MF_BYPOSITION |
            (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

        return;
    }
    // otherwise just the New Sheet command
    pCmdUI->Enable(m_bCanCreateSheet);
}
```

ID_NEW_CHART のコマンドハンドラーは通常の更新コマンドハンドラーであり、次のようになります。

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="on_command-and-on_bn_clicked"></a>ON_COMMAND と ON_BN_CLICKED

**ON_COMMAND** と **ON_BN_CLICKED** のメッセージマップマクロは同じです。 MFC コマンドおよびコントロールの通知ルーティングメカニズムでは、コマンド ID を使用して、ルーティング先を決定します。 コントロール通知コードゼロ (**BN_CLICKED**) を使用したコントロール通知は、コマンドとして解釈されます。

> [!NOTE]
> 実際、すべてのコントロール通知メッセージは、コマンドハンドラーチェーンを経由します。 たとえば、ドキュメントクラスで **EN_CHANGE** のコントロール通知ハンドラーを記述することは技術的に可能です。 この機能の実際の応用はあまりありません。この機能は ClassWizard でサポートされていないため、機能を使用するとコードが脆弱になる可能性があります。

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>ボタンコントロールの自動無効化を無効にする

ボタンコントロールをダイアログバーに配置した場合、または自分で **CWnd:: UpdateDialogControls** を呼び出す場所を使用しているダイアログボックスで、 **ON_COMMAND** または **ON_UPDATE_COMMAND_UI** のハンドラーを持たないボタンが、フレームワークによって自動的に無効になることがわかります。 場合によっては、ハンドラーが必要になることはありませんが、ボタンを有効なままにしておく必要があります。 これを実現する最も簡単な方法は、ダミーのコマンドハンドラーを追加することです (ClassWizard で簡単に実行できます)。

## <a name="window-message-routing"></a>ウィンドウメッセージのルーティング

ここでは、MFC クラスに関するいくつかの高度なトピックと、Windows メッセージルーティングとその他のトピックに対する影響について説明します。 ここに記載されている情報については、簡単に説明します。 パブリック Api の詳細については、 *クラスライブラリリファレンス* を参照してください。 実装の詳細については、MFC ライブラリのソースコードを参照してください。

すべての **CWnd** の派生クラスに関する非常に重要なトピックであるウィンドウのクリーンアップの詳細については、[テクニカルノート 17](../mfc/tn017-destroying-window-objects.md)を参照してください。

## <a name="cwnd-issues"></a>CWnd の問題

実装メンバー関数 **CWnd:: OnChildNotify** は、子ウィンドウ (コントロールとも呼ばれます) に対して強力で拡張可能なアーキテクチャを提供し、親 (または "所有者") に送られるメッセージ、コマンド、およびコントロール通知をフックまたは通知します。 子ウィンドウ (/コントロール) が C++ の **CWnd** オブジェクトである場合、仮想関数 **OnChildNotify** は、最初に元のメッセージのパラメーター (つまり、 **MSG** 構造体) を使用して呼び出されます。 子ウィンドウは、メッセージをそのままにしたり、食べたり、親のメッセージを変更したりできます (まれ)。

既定の **CWnd** 実装は次のメッセージを処理し、 **OnChildNotify** フックを使用して、子ウィンドウ (コントロール) がメッセージで最初にアクセスできるようにします。

- **WM_MEASUREITEM** と **WM_DRAWITEM** (自己描画用)

- **WM_COMPAREITEM** と **WM_DELETEITEM** (自己描画用)

- **WM_HSCROLL** と **WM_VSCROLL**

- **WM_CTLCOLOR**

- **WM_PARENTNOTIFY**

**OnChildNotify** フックは、オーナー描画メッセージを自己描画メッセージに変更するために使用されます。

**OnChildNotify** フックに加え、スクロールメッセージにはさらにルーティング動作があります。 スクロールバーと **WM_HSCROLL** と **WM_VSCROLL** メッセージのソースの詳細については、以下を参照してください。

## <a name="cframewnd-issues"></a>CFrameWnd の問題

**CFrameWnd** クラスは、ほとんどのコマンドルーティングとユーザーインターフェイス更新の実装を提供します。 これは主にアプリケーションのメインフレームウィンドウ (**CWinApp:: m_pMainWnd**) に使用されますが、すべてのフレームウィンドウに適用されます。

メインフレームウィンドウは、メニューバーのあるウィンドウで、ステータスバーまたはメッセージ行の親です。 コマンドのルーティングと WM_INITMENUPOPUP については、上記の説明を参照してください **。**

**CFrameWnd** クラスは、アクティブなビューの管理を提供します。 次のメッセージは、アクティブなビューを通じてルーティングされます。

- すべてのコマンドメッセージ (アクティブビューは、それらに対する最初のアクセス権を取得します)。

- 兄弟スクロールバーからメッセージを **WM_HSCROLL** して **WM_VSCROLL** します (下記を参照)。

- **WM_ACTIVATE** (および MDI の **WM_MDIACTIVATE** ) は、仮想関数 **CView:: onアクティブビュー** への呼び出しを有効にします。

## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFrameWnd/CMDIChildWnd の問題

どちらの MDI フレームウィンドウクラスも **cframewnd** から派生しているため、同じ種類のコマンドルーティングと、 **cframewnd** で提供されるユーザーインターフェイスの更新に対して両方が有効になります。 一般的な MDI アプリケーションでは、メインフレームウィンドウ (つまり **CMDIFrameWnd** オブジェクト) のみがメニューバーとステータスバーを保持するため、コマンドルーティング実装の主要なソースとなります。

一般的なルーティングスキームでは、アクティブな MDI 子ウィンドウがコマンドに最初にアクセスします。 既定の **PreTranslateMessage** 関数は、mdi 子ウィンドウ (最初) と mdi フレーム (2 番目) の両方のアクセラレータテーブル、および通常は **TranslateMDISysAccel** (last) によって処理される標準の mdi システムコマンドアクセラレータを処理します。

## <a name="scroll-bar-issues"></a>スクロールバーの問題

スクロールメッセージ (**WM_HSCROLL** / **OnHScroll** や **WM_VSCROLL** / **onvscroll**) を処理するときは、スクロールバーのメッセージの送信元の場所に依存しないようにハンドラーコードを記述する必要があります。 これは、一般的な Windows の問題ではありません。これは、スクロールメッセージは、 true のスクロールバーコントロール、またはスクロール / バーコントロールではない WS_HSCROLL **WS_VSCROLL** スクロールバーから取得できるためです。

MFC では、スクロールバーコントロールをスクロールするウィンドウの子または兄弟として使用できるように拡張されています (実際には、スクロールバーとスクロール中のウィンドウの間の親子関係は何でもかまいません)。 これは、スプリッターウィンドウを使用した共有スクロールバーに特に重要です。 **CSplitterWnd** の実装の詳細については、「[テクニカルノート 29](../mfc/tn029-splitter-windows.md) 」を参照してください。

ミニノートでは、作成時に指定されたスクロールバーのスタイルがトラップされ、Windows に渡されない、2つの **CWnd** 派生クラスがあります。 作成ルーチンに渡されると、 **WS_HSCROLL** と **WS_VSCROLL** を個別に設定できますが、作成後に変更することはできません。 もちろん、作成したウィンドウの WS_SCROLL スタイルビットは、直接テストしたり設定したりしないでください。

**CMDIFrameWnd** の場合は、 **LoadFrame** を作成するために渡す **、または** MDICLIENT を作成するために使用するスクロールバーのスタイルを使用します。 スクロール可能な MDICLIENT 領域 (Windows プログラムマネージャーなど) を使用する場合は、 **CMDIFrameWnd** の作成に使用したスタイルに対して、スクロールバーのスタイル (**WS_HSCROLL** &#124; **WS_VSCROLL**) の両方を設定してください。

**CSplitterWnd** の場合、スクロールバーのスタイルは、スプリッター領域の特殊な共有スクロールバーに適用されます。 静的な分割ウィンドウでは、通常、スクロールバーのスタイルは設定されません。 動的分割ウィンドウでは、通常、分割する方向に対してスクロールバーのスタイルを設定します。つまり、行を分割できる場合は **WS_HSCROLL** 、列を分割できる場合は **WS_VSCROLL** ます。

## <a name="see-also"></a>関連項目

[番号別テクニカルノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカルノート](../mfc/technical-notes-by-category.md)
