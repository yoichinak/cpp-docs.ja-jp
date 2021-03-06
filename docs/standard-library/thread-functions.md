---
description: '詳細情報: &lt; スレッド &gt; 関数'
title: '&lt;thread&gt; 関数'
ms.date: 11/04/2016
f1_keywords:
- thread/std::get_id
- thread/std::sleep_for
- thread/std::sleep_until
- thread/std::swap
- thread/std::yield
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
helpviewer_keywords:
- std::get_id [C++]
- std::sleep_for [C++]
- std::sleep_until [C++]
- std::swap [C++]
- std::yield [C++]
ms.openlocfilehash: 37e1f745b66c45f5e3ad6bd4be2a2837042b8433
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207437"
---
# <a name="ltthreadgt-functions"></a>&lt;thread&gt; 関数

[get_id](#get_id)\
[sleep_for](#sleep_for)\
[sleep_until](#sleep_until)\
[フォト](#swap)\
[yield](#yield)

## <a name="get_id"></a><a name="get_id"></a> get_id

現在の実行スレッドを一意に識別します。

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>戻り値

現在の実行のスレッドを一意に識別する [thread::id](../standard-library/thread-class.md) 型のオブジェクト。

## <a name="sleep_for"></a><a name="sleep_for"></a> sleep_for

呼び出し元のスレッドをブロックします。

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>パラメーター

*Rel_time*\
期間を指定する [duration](../standard-library/duration-class.md) オブジェクト。

### <a name="remarks"></a>解説

関数は、 *Rel_time* によって指定された時間以上、呼び出し元スレッドをブロックします。 この関数では、例外がスローされません。

## <a name="sleep_until"></a><a name="sleep_until"></a> sleep_until

少なくとも指定された時間まで、呼び出し元スレッドをブロックします。

```cpp
template <class Clock, class Duration>
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```

### <a name="parameters"></a>パラメーター

*Abs_time*\
特定の時点を表します。

### <a name="remarks"></a>解説

この関数では、例外がスローされません。

## <a name="swap"></a><a name="swap"></a> フォト

2 つの `thread` オブジェクトの状態を交換します。

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>パラメーター

*左側*\
左側の `thread` オブジェクト。

*そうです*\
右側の `thread` オブジェクト。

### <a name="remarks"></a>解説

関数は `Left.swap(Right)` を呼び出します。

## <a name="yield"></a><a name="yield"></a> 得

現在のスレッドが通常引き続き実行される場合であっても、他のスレッドを実行するようオペレーティング システムに通知します。

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>関連項目

[\<thread>](../standard-library/thread.md)
