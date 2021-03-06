---
title: StartTracingSessionA
description: C++ Build Insights SDK の StartTracingSessionA 関数のリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 388ccbe58ab5cc59d995601536a2034e847e2e1d
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920009"
---
# <a name="starttracingsessiona"></a>StartTracingSessionA

::: moniker range="<=msvc-140"

C++ Build Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio **Version** セレクター コントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。 このページの目次の一番上にあります。

::: moniker-end
::: moniker range=">=msvc-150"

`StartTracingSessionA` 関数により、トレース セッションが開始されます。 この関数を呼び出す実行可能ファイルには、管理者権限が必要です。

## <a name="syntax"></a>構文

```cpp
enum RESULT_CODE StartTracingSessionA(
    const char*                    sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>パラメーター

*sessionName*\
開始するトレース セッションの名前。 [StopTracingSessionA](stop-tracing-session.md) または他のトレース停止関数を呼び出すときは、同じ名前を使用します。

*options*\
[TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md) オブジェクトへのポインター。 トレース セッションによって収集する必要があるイベントを選択するには、このオブジェクトを使用します。

### <a name="return-value"></a>戻り値

[RESULT_CODE](../other-types/result-code-enum.md) 列挙型の結果コード。

::: moniker-end
