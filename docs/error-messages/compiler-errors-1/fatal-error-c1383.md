---
description: '詳細情報: 致命的なエラー C1383'
title: 致命的なエラー C1383
ms.date: 11/04/2016
f1_keywords:
- C1383
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
ms.openlocfilehash: df20ac07cb3a6c94ff04b42b48ce23f168bb78c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276505"
---
# <a name="fatal-error-c1383"></a>致命的なエラー C1383

コンパイラ オプション /GL は、インストールされた共通言語ランタイムのバージョンと互換性がありません

C1383 は、共通言語ランタイムの以前のバージョンをそれより新しいコンパイラで使用しているときに、 **/clr** と **/GL.** を指定してコンパイルすると発生します。

解決するには、 **/GL** を **/clr** と共に使用しないようにするか、使用しているコンパイラに付属している共通言語ランタイムのバージョンをインストールします。

詳細については、 [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) および [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md)を参照してください。
