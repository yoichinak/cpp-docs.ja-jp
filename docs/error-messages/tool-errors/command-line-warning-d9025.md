---
description: 詳細については、Command-Line Warning D9025 を参照してください。
title: コマンド ラインの警告 D9025
ms.date: 11/04/2016
f1_keywords:
- D9025
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
ms.openlocfilehash: 8cec7bdb5f3816c33d395e8ae93a861a29e94c64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115496"
---
# <a name="command-line-warning-d9025"></a>コマンド ラインの警告 D9025

' オプション 1 ' を ' option2 ' でオーバーライドしています

*オプション 1* オプションが指定されましたが、 *option2* によってオーバーライドされました。 *Option2* オプションが使用されました。

2つのオプションで矛盾するディレクティブまたは互換性のないディレクティブが指定されている場合は、コマンドラインの一番右にあるオプションで指定または暗黙的に指定されたディレクティブが使用されます。

開発環境からコンパイルするときにこの警告が表示され、競合するオプションがどこから取得されているかわからない場合は、次の点を考慮してください。

- オプションは、コードまたはプロジェクトのプロジェクト設定で指定できます。 コンパイラの [コマンドラインプロパティページ](../../build/reference/command-line-property-pages.md) を確認し、[ **すべてのオプション** ] フィールドに競合するオプションが表示されている場合は、プロジェクトのプロパティページでオプションが設定されます。そうでない場合、オプションはソースコードで設定されます。

   オプションがプロジェクトのプロパティページで設定されている場合は、コンパイラの [プリプロセッサ] プロパティページ (ソリューションエクスプローラーでプロジェクトノードが選択されている) を確認します。  このオプションが設定されていない場合は、各ソースコードファイルの [プリプロセッサ] プロパティページの設定 (ソリューションエクスプローラー) を確認して、追加されていないことを確認してください。

   これらのオプションがコードで設定されている場合は、コードまたは windows ヘッダーのいずれかで設定できます。  前処理されたファイル ([/p](../../build/reference/p-preprocess-to-a-file.md)) を作成し、シンボルを検索することができます。
