---
description: コマンドラインエラー D8048 の原因と解決方法について説明します。
title: Command-Line エラー D8048
ms.date: 04/18/2021
f1_keywords:
- D8048
helpviewer_keywords:
- D8048
ms.openlocfilehash: 5de7a6db69124190b56b203d9cd9deed8b060408
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107723387"
---
# <a name="command-line-error-d8048"></a>コマンドラインエラー D8048

> C ファイル '*file-name*' を/ZW オプションと共にコンパイルできません

[ `/ZW` (Windows ランタイムコンパイル)](../../build/reference/zw-windows-runtime-compilation.md)コンパイラオプションを使用すると、コンパイラには C++ ソースコードファイルのみを渡すことができます。

## <a name="remarks"></a>解説

既定では、C++ ユニバーサル Windows プラットフォーム (UWP) プロジェクト内のすべてのファイルは、コンパイラオプションを使用してコンパイルされ **`/ZW`** ます。 オプションを使用すると、 **`/ZW`** Windows ランタイムコンパイラ拡張機能または C++/cx が有効になります。 残念ながら、は **`/ZW`** C ソースファイルでは機能しません。

C++/CX コンパイルは、Visual Studio プロジェクトの C ファイルに対して選択的に無効にすることができます。 ソリューションエクスプローラーで C ファイルを選択し、右クリックしてショートカットメニューの [ **プロパティ** ] を選択します。 [**プロパティページ**] ダイアログで、[**構成プロパティ**] [  >  **C/c + +**  ->  **全般**] プロパティページを選択します。 **使用 Windows ランタイム拡張** プロパティをに設定し *`No`* ます。 **[OK]** を選択して変更を保存します。

詳細については、「 [.net および UWP 用のコンポーネント拡張](../../extensions/component-extensions-for-runtime-platforms.md)」を参照してください。

## <a name="see-also"></a>関連項目

[`/ZW` (Windows ランタイムのコンパイル)](../../build/reference/zw-windows-runtime-compilation.md)
