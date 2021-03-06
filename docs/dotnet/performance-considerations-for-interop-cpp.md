---
description: '詳細情報: 相互運用機能のパフォーマンスに関する考慮事項 (C++)'
title: Interop (C++) のパフォーマンスに関する考慮事項
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
ms.openlocfilehash: 29723f0ea5c7b745100ab4c7abb7f59abce47db6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255562"
---
# <a name="performance-considerations-for-interop-c"></a>Interop (C++) のパフォーマンスに関する考慮事項

このトピックでは、実行時のパフォーマンスに対するマネージ/アンマネージ相互運用遷移の影響を軽減するためのガイドラインを示します。

Visual C++ は、Visual Basic や C# (P/Invoke) などの他の .NET 言語と同じ相互運用性メカニズムをサポートしますが、Visual C++ (C++ interop) に固有の相互運用サポートも提供します。 パフォーマンスが重要なアプリケーションでは、各相互運用機能のパフォーマンスへの影響を理解しておくことが重要です。

使用する相互運用手法に関係なく、マネージ関数がアンマネージ関数を呼び出すたびに、サンクと呼ばれる特殊な遷移シーケンスが必要になります。 これらのサンクは Microsoft C++ コンパイラによって自動的に挿入されますが、これらの遷移はパフォーマンスの面でコストが高くなる可能性があることに注意してください累積的。

## <a name="reducing-transitions"></a>遷移の削減

相互運用サンクのコストを回避または削減する方法の1つは、マネージ/アンマネージ遷移を最小化するために必要なインターフェイスをリファクターすることです。 高いインターフェイスをターゲットにすることで、大幅なパフォーマンスの向上を実現できます。これは、マネージ/アンマネージ境界を越えて頻繁に呼び出されるインターフェイスです。 たとえば、厳密なループでアンマネージ関数を呼び出すマネージ関数は、リファクタリングの候補として適しています。 ループ自体がアンマネージ側に移動された場合、またはアンマネージ呼び出しのマネージ代替が作成された場合 (たとえば、マネージ側でデータをキューに配置し、ループの後で一度にアンマネージ API にマーシャリングする場合)、遷移の数を大幅に減らすことができます。

## <a name="pinvoke-vs-c-interop"></a>P/Invoke と C++ Interop

Visual Basic や C# などの .NET 言語の場合、ネイティブコンポーネントとの相互運用のために指定されたメソッドは、P/Invoke です。 P/Invoke は .NET Framework でサポートされているため、Visual C++ でもサポートされていますが Visual C++ 独自の相互運用性のサポートも提供されています。これを C++ Interop と呼びます。 P/Invoke はタイプセーフではないため、P/Invoke よりも c + + 相互運用をお勧めします。 その結果、エラーは主に実行時に報告されますが、c + + の相互運用機能では、P/Invoke よりもパフォーマンス上の利点があります。

どちらの手法でも、マネージ関数がアンマネージ関数を呼び出すたびに、いくつかの処理が必要になります。

- 関数呼び出しの引数は、CLR からネイティブ型にマーシャリングされます。

- アンマネージサンクが実行されます。

- アンマネージ関数が呼び出されます (引数のネイティブバージョンを使用)。

- アンマネージサンクが実行されます。

- 戻り値の型と任意の "out" または "in, out" 引数は、ネイティブ型から CLR 型にマーシャリングされます。

相互運用機能を使用するにはマネージド/アンマネージサンクが必要ですが、必要なデータのマーシャリングは、関連するデータ型、関数シグネチャ、およびデータの使用方法によって異なります。

C++ Interop によって実行されるデータマーシャリングは、最も単純な形式です。パラメーターはマネージ/アンマネージ境界を越えてビットごとにコピーするだけです。変換は一切実行されません。 P/Invoke の場合、これは、すべてのパラメーターが単純な blittable 型である場合にのみ当てはまります。 それ以外の場合、P/Invoke は、各マネージパラメーターを適切なネイティブ型に変換するための非常に堅牢な手順を実行します。また、引数が "out" または "in, out" とマークされている場合は、その逆も行われます。

言い換えると、C++ Interop ではデータマーシャリングの最速のメソッドが使用されるのに対し、P/Invoke では最も信頼性の高いメソッドが使用されます。 これは、C++ の相互運用 (C++ の標準的な形式) が既定で最適なパフォーマンスを提供することを意味します。プログラマは、この動作が安全でない場合や適切でない場合に対処する責任があります。

そのため、C++ Interop ではデータのマーシャリングを明示的に指定する必要がありますが、その利点は、データの性質と使用方法に応じて、プログラマが適切なものを自由に決定できることです。 さらに、P/Invoke データマーシャリングの動作は、カスタマイズされた方法で変更できますが、C++ Interop では、呼び出しごとにデータマーシャリングをカスタマイズできます。 これは、P/Invoke では実行できません。

C++ Interop の詳細については、「 [C++ interop の使用 (暗黙的な PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)」を参照してください。

## <a name="see-also"></a>関連項目

[混合 (ネイティブおよびマネージ) アセンブリ](../dotnet/mixed-native-and-managed-assemblies.md)
