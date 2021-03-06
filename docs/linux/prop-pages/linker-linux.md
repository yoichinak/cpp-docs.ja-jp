---
description: '詳細情報: リンカー プロパティ (Linux C++)'
title: リンカー プロパティ (Linux C++)
ms.date: 06/07/2019
ms.assetid: a0243a94-8164-425b-b2fe-b84ff363d546
ms.openlocfilehash: 93ded9016cecb629fe17d171387260179b208f77
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169750"
---
# <a name="linker-properties-linux-c"></a>リンカー プロパティ (Linux C++)

::: moniker range="msvc-140"

Linux サポートは Visual Studio 2017 以降で使用できます。

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="general"></a>全般

| プロパティ | 説明 | オプション |
|--|--|--|
| 出力ファイル | このオプションは、リンカーによって作成されるプログラムの既定の名前と場所をオーバーライドします。 (-o) |
| 進行状況の表示 | リンカーの進行状況メッセージを出力します。 |
| Version | -version オプションは、実行ファイルのヘッダーにバージョン番号を付けるようにリンカーを設定します。 |
| 詳細出力の有効にする | -verbose オプションは、デバッグ用に詳細メッセージを出力するようにリンカーを設定します。 |
| Trace | --trace オプションは、処理中の入力ファイルを出力するようにリンカーを設定します。 |
| トレース シンボル | シンボルを表示するファイルの一覧を印刷します。 (--trace-symbol=symbol) |
| マップの印刷 | --print-map オプションはリンク マップを出力するようにリンカーを設定します。 |
| 未解決のシンボル参照の報告 | このオプションを有効にすると未解決のシンボル参照が報告されます。 |
| メモリ使用量の最適化 | 必要に応じてシンボル テーブルを再度読み取ることでメモリの使用量を最適化します。 |
| 共有ライブラリの検索パス | 共有ライブラリの検索パスをユーザーが設定できるようにします。 (-rpath-link=path) |
| 追加のライブラリ ディレクトリ | 環境のライブラリ パスをユーザーがオーバーライドできるようにします。 (-L フォルダー) |
| リンカー | リンク中に起動するプログラムか、またはリモート システム上のリンカーへのパスを指定します。 |
| リンクのタイムアウト | リモート リンクのタイムアウト (ミリ秒)。 |
| 出力データをコピーします | リモート システムからローカル コンピューターにビルドの出力ファイルをコピーするかどうかを指定します。 |

## <a name="input"></a>入力

| プロパティ | 説明 | オプション |
|--|--|--|
| 特定の既定のライブラリの無視 | 無視する既定のライブラリの名前を 1 つ以上指定します。 (--exclude-libs lib,lib) |
| 既定のライブラリを無視する | 既定のライブラリを無視して、明示的に指定されたライブラリのみを検索します。 |
| 未定義のシンボル参照の強制 | 出力ファイルに未定義のシンボルとしてシンボルを入力するように強制します。 (-u symbol --undefined=symbol) |
| ライブラリの依存ファイル | このオプションでは、リンカー コマンド ラインに追加する追加ライブラリを指定できます。 追加ライブラリは、'lib' で始まり、拡張子 '.a' で終わるリンカー コマンド ラインの終わりに追加されます。  (-lFILE) |
| 追加の依存ファイル | リンク コマンド ラインに追加する項目を指定します。 |

## <a name="debugging"></a>デバッグ

| プロパティ | 説明 | オプション |
|--|--|--|
| デバッガー シンボル情報 | 出力ファイルのデバッガー シンボル情報。 | **Include All (すべて含める)**<br>**デバッガー シンボル情報のみを除外**<br>**すべてのシンボル情報を除外**<br> |
| マップ ファイル名 | マップ オプションは、ユーザーが指定した名前を使用してマップ ファイルを作成するようにリンカーを設定します。 (-Map=) |

## <a name="advanced"></a>詳細設定

| プロパティ | 説明 | オプション |
|--|--|--|
| 再配置後に変数を読み取り専用としてマーク | このオプションは、再配置後に変数を読み取り専用としてマークします。 |
| 即時関数バインディングの有効化 | このオプションは、即時関数バインディング用にオブジェクトをマークします。 |
| 実行可能スタックは必要ありません | このオプションは、実行可能スタックを必要としないものとして出力をマークします。 |
| アーカイブ全体 | アーカイブ全体は、ソースおよびその他の依存関係のすべてのコードを使用します。 |

::: moniker-end
