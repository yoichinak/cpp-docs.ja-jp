---
description: 詳細については、「BSCMAKE エラー BK1503」を参照してください。
title: BSCMAKE エラー BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: 0e789aa54241df5245f4c3a02a9307a97d51730c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323000"
---
# <a name="bscmake-error-bk1503"></a>BSCMAKE エラー BK1503

ファイル ' filename ' に書き込めません [: reason]

BSCMAKE では、コンパイル中に生成された .sbr ファイルを1つのブラウザーデータベースに結合します。 結果として得られるブラウザーデータベースが 64 MB を超える場合、または入力 (.sbr) ファイルの数が4092を超える場合、このエラーが生成されます。

4092以上の .sbr ファイルが原因で問題が発生した場合は、入力ファイルの数を減らす必要があります。 これは、Visual Studio 内でプロジェクト全体を [実行して](../../build/reference/fr-fr-create-dot-sbr-file.md) から、ファイルごとに再確認することで実現できます。

この問題の原因が、64 MB を超える .bsc ファイルの場合、入力として .sbr ファイルの数を減らすと、結果として得られる .bsc ファイルのサイズが小さくなります。 さらに、ブラウザー情報の量は、/Em (マクロの拡張シンボルの除外)、/El (ローカル変数を除く)、および/Es (システムファイルを除外する) を使用して減らすことができます。

## <a name="see-also"></a>関連項目

[BSCMAKE オプション](../../build/reference/bscmake-options.md)
