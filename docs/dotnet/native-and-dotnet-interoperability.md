---
description: 詳細については、「ネイティブと .NET の相互運用性」を参照してください。
title: ネイティブと .NET の相互運用性
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++]
- .NET Framework [C++], interoperability with Visual C++
- interoperability [C++], about .NET interoperability
- interop [C++], about .NET interoperability
- managed code [C++], interoperability
- native code [C++]
- interoperability [C++]
- MFC [C++], .NET integration
- unmanaged code interoperability [C++]
- Visual C++, interoperability
- native code [C++], .NET interoperatibility
ms.assetid: f3ec6c99-c745-4256-b95b-f1d12ba17a5a
ms.openlocfilehash: 0276c4401b56f453549cf31433cc6f558daf1c02
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255640"
---
# <a name="native-and-net-interoperability"></a>ネイティブと .NET の相互運用性

Visual C++ では相互運用機能をサポートしており、マネージド構造とアンマネージド構造が共存して同じアセンブリ内ではもちろん、同じファイル内でも相互運用できます。 この機能の小さなサブセット (P/Invoke など) は他の .NET 言語でもサポートされていますが、Visual C++ が提供する相互運用性サポートのほとんどは他の言語では使用できません。

## <a name="in-this-section"></a>このセクションの内容

[混合 (ネイティブおよびマネージ) アセンブリ](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
マネージ機能とアンマネージ機能の両方を含む [/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md) コンパイラオプションを使用して生成されたアセンブリについて説明します。

[MFC での Windows フォームユーザーコントロールの使用](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
MFC Windows フォーム サポート クラスを使用して MFC アプリケーション内で Windows フォーム コントロールをホストする方法について説明します。

[呼び出し (マネージコードからネイティブ関数を)](../dotnet/calling-native-functions-from-managed-code.md)<br/>
非 CLR DLL を .NET アプリケーションから使用する方法について説明します。
