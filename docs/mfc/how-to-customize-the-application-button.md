---
description: '詳細については、「方法: アプリケーションボタンをカスタマイズする」を参照してください。'
title: '方法: アプリケーション ボタンをカスタマイズする'
ms.date: 09/07/2019
helpviewer_keywords:
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
ms.openlocfilehash: 72db627c6a4efef711ea7cc3163d0266e0a6c219
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253456"
---
# <a name="how-to-customize-the-application-button"></a>方法: アプリケーション ボタンをカスタマイズする

[アプリケーション] ボタンをクリックすると、コマンドのメニューが表示されます。 通常、[ **開く**]、[ **保存**]、[ **印刷**]、[ **終了**] などのファイル関連のコマンドがメニューに表示されます。

![MFC リボン アプリケーション ボタン](../mfc/media/application_button.png "MFC リボン アプリケーション ボタン")

アプリケーションボタンをカスタマイズするには、[ **プロパティ** ] ウィンドウ ( **リソースビュー**) で開き、プロパティを変更してから、リボンコントロールをプレビューします。

### <a name="to-open-the-application-button-in-the-properties-window"></a>プロパティウィンドウで [アプリケーション] ボタンを開くには

1. Visual Studio の [ **表示** ] メニューで、[ **リソースビュー**] をクリックします。

1. **リソースビュー** で、リボンリソースをダブルクリックしてデザイン画面に表示します。

1. デザイン画面で、アプリケーションボタンメニューを右クリックし、[ **プロパティ**] をクリックします。

## <a name="application-button-properties"></a>アプリケーションボタンのプロパティ

次の表は、アプリケーションボタンのプロパティを定義しています。

|プロパティ|定義|
|--------------|----------------|
|**ボタン**|[アプリケーション] メニューの右下隅に表示される最大3つのボタンのコレクションを格納します。|
|**Caption**|コントロールのテキストを指定します。 他のリボン要素とは異なり、[アプリケーション] ボタンにはキャプションテキストは表示されません。 代わりに、テキストがアクセシビリティに使用されます。|
|**HDPI イメージ**|高ドット/インチ (HDPI) アプリケーションボタンアイコンの識別子を指定します。 高 DPI モニターでアプリケーションを実行すると、**イメージ** の代わりに **hdpi イメージ** が使用されます。|
|**HDPI の大きな画像**|高 DPI の大きなイメージの識別子を指定します。 高 DPI モニターでアプリケーションを実行すると、**大きな画像** の代わりに **Hdpi の大きな画像** が使用されます。|
|**HDPI 小さいイメージ**|高 DPI の小さいイメージの識別子を指定します。 高 DPI モニターでアプリケーションを実行すると、**小さい画像** の代わりに **Hdpi の小さい画像** が使用されます。|
|**ID**|コントロールの識別子を指定します。|
|**イメージ**|アプリケーションボタンアイコンの識別子を指定します。 アイコンは、アルファの透明度を持つ32ビットの26x26 ビットマップです。 アイコンの透明部分は、[アプリケーション] ボタンをクリックするか、カーソルを置いたときに強調表示されます。|
|**[キー]**|キーヒントナビゲーションが有効になっている場合に表示される文字列を指定します。 キーヒントナビゲーションは、ALT キーを押したときに有効になります。|
|**大きな画像**|一連の32x32 のアイコンを含むイメージの識別子を指定します。 アイコンは、メイン項目コレクション内のボタンによって使用されます。|
|**メイン項目**|アプリケーションメニューに表示されるメニュー項目のコレクションを格納します。|
|**MRU キャプション**|[最近使ったリスト] パネルに表示されるテキストを指定します。|
|**小さい画像**|一連の16x16 アイコンを含むイメージの識別子を指定します。 アイコンは、ボタンのコレクション内のボタンによって使用されます。|
|**用途**|最近使用したリストパネルを有効または無効にします。 [最近使ったリスト] パネルが [アプリケーション] メニューに表示されます。|
|**Width**|最近使用したリストパネルの幅をピクセル単位で指定します。|

[アプリケーション] メニューはデザイン画面に表示されません。 これを表示するには、リボンをプレビューするか、アプリケーションを実行する必要があります。

#### <a name="to-preview-the-ribbon-control"></a>リボンコントロールをプレビューするには

- **リボンエディターのツールバー** で、[テスト] [**リボン**] の順にクリックします。

## <a name="see-also"></a>関連項目

[リボンデザイナー (MFC)](ribbon-designer-mfc.md)
