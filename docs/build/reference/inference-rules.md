---
description: '詳細情報: 推論規則'
title: 推論規則
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: fc063f71ff88442ce6f7fc02c5b22f015ce0010c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199754"
---
# <a name="inference-rules"></a>推論規則

推論規則は、ターゲットを更新し、ターゲットの依存を推論するコマンドを提供します。 推論規則に含まれる拡張機能は、同じ基本名を持つ1つのターゲットと依存に一致します。 推論規則は、ユーザー定義または定義済みです。定義済みの規則は再定義できます。

古い依存関係にコマンドがない場合は。それ以外の場合は [。サフィックス](dot-directives.md) には、依存する拡張子が含まれています。 NMAKE は、現在のディレクトリまたは指定したディレクトリ内のターゲットと既存のファイルに一致する拡張機能を持つ規則を使用します。 複数の規則が既存のファイルと一致する場合は、 **。サフィックス** の一覧で、使用するものを決定します。リストの優先順位は左から右へとなります。 依存ファイルが存在せず、別の説明ブロックのターゲットとしてリストされていない場合、推論規則によって、同じ基本名を持つ別のファイルから不足しているを作成できます。 説明ブロックのターゲットに依存関係またはコマンドがない場合は、推論規則によってターゲットを更新できます。 説明ブロックが存在しない場合でも、推論規則はコマンドラインターゲットを作成できます。 明示的に依存するが指定されている場合でも、NMAKE は、推定される依存関係に対してルールを呼び出すことができます。

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

[規則の定義](defining-a-rule.md)

[バッチモード規則](batch-mode-rules.md)

[定義済み規則](predefined-rules.md)

[推論による依存ファイルと推論規則](inferred-dependents-and-rules.md)

[推論規則の優先順位](precedence-in-inference-rules.md)

## <a name="see-also"></a>関連項目

[NMAKE のリファレンス](nmake-reference.md)
