---
description: '詳細情報: インラインアセンブリのデバッグと一覧表示'
title: インライン アセンブリのデバッグと一覧表示
ms.date: 08/30/2018
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
ms.openlocfilehash: b4608a0176de5e061d7dc7f15b8758d9bd3a94b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117871"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>インライン アセンブリのデバッグと一覧表示

**Microsoft 固有の仕様**

[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)オプションを使用してコンパイルした場合は、インラインアセンブリコードを含むプログラムをソースレベルのデバッガーでデバッグできます。

デバッガー内では、C または C++ とアセンブリ言語の両方の行にブレークポイントを設定できます。 アセンブリとソースの混合モードを有効にすると、アセンブリコードのソースと逆アセンブルの両方の形式を表示できます。

複数のアセンブリ命令またはソース言語ステートメントを1行に配置すると、デバッグが阻害される可能性があることに注意してください。 ソースモードでは、デバッガーを使用して、1行にブレークポイントを設定できますが、同じ行の個々のステートメントには設定できません。 同じ原則が、 **`__asm`** C マクロとして定義されているブロックに適用され、1つの論理行に展開されます。

[/Fa](../../build/reference/fa-fa-listing-file.md)コンパイラオプションを使用して、混合ソースとアセンブリリストを作成した場合、一覧には各アセンブリ言語行のソースとアセンブリの両方の形式が含まれます。 マクロは、一覧では展開されませんが、コンパイル中に展開されます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__Asm ブロックでのアセンブリ言語の使用](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
