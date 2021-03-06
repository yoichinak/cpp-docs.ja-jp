---
description: 詳細については、「リンカツール Error LNK1168」を参照してください。
title: リンカ ツール エラー LNK1168
ms.date: 11/04/2016
f1_keywords:
- LNK1168
helpviewer_keywords:
- LNK1168
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
ms.openlocfilehash: 692bfbcc744307f32c8017b41ec27f5f421ea17c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253495"
---
# <a name="linker-tools-error-lnk1168"></a>リンカ ツール エラー LNK1168

書き込みモードで 'filename' を開けません。

リンカーは `filename` に書き込むことができません。 ファイルが使用中で、そのファイル ハンドルが別のプロセスによってロックされている可能性があります。または、ファイルに対する書き込みアクセス許可、あるいはファイルが配置されているディレクトリやネットワーク共有に対する書き込みアクセス許可がない可能性があります。 このエラーは、多くの場合、ウイルス対策プログラムによって保持されているロック、ファイル検索インデックス作成プロセス、または Visual Studio ビルドシステムによって保持されているロックの解放の遅延など、一時的な状態が原因で発生します。

この問題を解決するには、`filename` ファイル ハンドルがロックされていないこと、およびファイルに対する書き込みアクセス許可があることを確認します。 実行可能ファイルの場合は、そのファイルが実行されていないことを確認します。

Windows の SysInternals ユーティリティ [ハンドル](/sysinternals/downloads/handle) または [プロセスエクスプローラー](/sysinternals/downloads/process-explorer) を使用して、どのプロセスにファイルハンドルロックが適用されているかを判断でき `filename` ます。 また、プロセス エクスプローラーを使用して、開いているファイル ハンドルのロックを解除することもできます。 これらのユーティリティの使用方法については、そのユーティリティに付属のヘルプ ファイルを参照してください。

ファイルがウイルス対策プログラムによってロックされている場合、この問題を解決するには、ウイルス対策プログラムによる自動スキャンの対象からビルド出力ディレクトリを除外します。 ウイルス対策スキャナーは、多くの場合、ファイル システムで新しいファイルを作成することにより実行され、スキャンの実行中は、このスキャナーによりファイルがロックされます。 特定のディレクトリをスキャン対象から除外する方法の詳細については、ウイルス対策プログラムのドキュメントを参照してください。

ファイルが検索インデックス作成サービスによってロックされている場合、この問題を解決するには、自動インデックス作成の対象からビルド出力ディレクトリを除外します。 詳細については、インデックス作成サービスのドキュメントを参照してください。 Windows search インデックスサービスを変更するには、Windows の **コントロールパネル** の [**インデックスのオプション**] を使用します。 詳細については、「 [Windows 10 でのインデックスの検索: よく寄せ](https://support.microsoft.com/help/4098843/windows-10-search-indexing-faq)られる質問」を参照してください。

ビルド処理で実行可能ファイルを上書きできない場合、そのファイルは、ファイル エクスプローラーによってロックされている可能性があります。 **アプリケーションエクスペリエンス** サービスが無効になっている場合、ファイルエクスプローラーは、長時間に対して実行可能ファイルハンドルロックを保持することがあります。 この問題を解決するには、 **services.msc** を実行し、**アプリケーションエクスペリエンス** サービスの [**プロパティ**] ダイアログボックスを開きます。 スタートアップの **種類** を " **無効** " から " **手動**" に変更します。
