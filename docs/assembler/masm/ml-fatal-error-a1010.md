---
description: '詳細情報: ML の致命的なエラー A1010'
title: ML の致命的なエラー A1010
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: 4a00d9594c71c8a22942e869d109bf51176394c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97129507"
---
# <a name="ml-fatal-error-a1010"></a>ML の致命的なエラー A1010

**一致しないブロックの入れ子:**

最初のブロックの終わりに一致するものがないか、またはブロックの末尾に一致する先頭がありませんでした。 次のいずれかが関係している可能性があります。

- などの高レベルのディレクティブ [。の場合は](dot-if.md) [。](dot-repeat.md)またはを繰り返し [ます。しばらくお待ち](dot-while.md)ください。

- [IF](if-masm.md)、 [REPEAT](repeat.md)、 **WHILE** などの条件付きアセンブリディレクティブ。

- 構造体または共用体の定義。

- プロシージャの定義。

- セグメントの定義。

- [Popcontext](popcontext.md)ディレクティブ。

- [If](if-masm.md)と一致することのない、 [ELSE](else-masm.md)、 [ELSEIF](elseif-masm.md)、または **ENDIF** などの条件付きアセンブリディレクティブ。

## <a name="see-also"></a>関連項目

[ML エラー メッセージ](ml-error-messages.md)
