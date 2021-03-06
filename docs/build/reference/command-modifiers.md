---
description: 詳細については、「コマンド修飾子」を参照してください。
title: コマンド修飾子
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
ms.openlocfilehash: d17d5f25719dfe5638ca6688105517d385bdf68e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182373"
---
# <a name="command-modifiers"></a>コマンド修飾子

コマンドの前に1つ以上のコマンド修飾子を指定できます。オプションで、スペースまたはタブで区切ることができます。 コマンドと同様に、修飾子をインデントする必要があります。

|修飾子|目的|
|--------------|-------------|
|\@*メニュー*|コマンドが表示されないようにします。 コマンドによる表示は抑制されません。 既定では、NMAKE は実行されたすべてのコマンドをエコーします。 /S を使用して、メイクファイル全体の表示を抑制します。を使用 **します。サイレント** 。メイクファイルの一部の表示を抑制します。|
|**-**\[*number*] *コマンド*|*コマンド* のエラーチェックをオフにします。 既定では、コマンドが0以外の終了コードを返すと NMAKE は停止します。 -*Number* が使用されている場合、終了コードが *number* を超えると NMAKE は停止します。 ダッシュと数字の間にスペースまたはタブを含めることはできません *。* とコマンドの間には、少なくとも1つのスペースまたはタブを含める必要があり `number` ます。  /I を使用して、メイクファイル全体のエラーチェックをオフにします。を使用 **します。** メイクファイルの一部のエラーチェックをオフにするには、[無視] を使用します。|
|**!** *command*|*コマンド* で <strong>$\*\*</strong> (依存関係にあるすべての依存ファイル) または $? を使用する場合、各依存ファイルに対してコマンドを実行し **ます。** (ターゲットより後のタイムスタンプを持つ依存関係にあるすべての依存ファイル)。|

## <a name="see-also"></a>関連項目

[メイクファイル内のコマンド](commands-in-a-makefile.md)
