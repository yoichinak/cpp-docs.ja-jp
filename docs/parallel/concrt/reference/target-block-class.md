---
description: '詳細情報: target_block クラス'
title: target_block クラス
ms.date: 11/04/2016
f1_keywords:
- target_block
- AGENTS/concurrency::target_block
- AGENTS/concurrency::target_block::target_block
- AGENTS/concurrency::target_block::propagate
- AGENTS/concurrency::target_block::send
- AGENTS/concurrency::target_block::async_send
- AGENTS/concurrency::target_block::decline_incoming_messages
- AGENTS/concurrency::target_block::enable_batched_processing
- AGENTS/concurrency::target_block::initialize_target
- AGENTS/concurrency::target_block::link_source
- AGENTS/concurrency::target_block::process_input_messages
- AGENTS/concurrency::target_block::process_message
- AGENTS/concurrency::target_block::propagate_message
- AGENTS/concurrency::target_block::register_filter
- AGENTS/concurrency::target_block::remove_sources
- AGENTS/concurrency::target_block::send_message
- AGENTS/concurrency::target_block::sync_send
- AGENTS/concurrency::target_block::unlink_source
- AGENTS/concurrency::target_block::unlink_sources
- AGENTS/concurrency::target_block::wait_for_async_sends
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
ms.openlocfilehash: 0860ff7b185eef997d7c76f61d67ad10056ca9cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188418"
---
# <a name="target_block-class"></a>target_block クラス

`target_block` クラスは、基本的なリンク管理機能と、ターゲットのみのブロックのエラー チェック機能を実現する抽象基底クラスです。

## <a name="syntax"></a>構文

```cpp
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

### <a name="parameters"></a>パラメーター

*_SourceLinkRegistry*<br/>
ソースリンクを保持するために使用されるリンクレジストリ。

*_MessageProcessorType*<br/>
メッセージ処理のプロセッサの種類。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|`source_iterator`|このオブジェクトのの反復子の型 `source_link_manager` `target_block` 。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[target_block](#ctor)|`target_block` オブジェクトを構築します。|
|[~ target_block デストラクター](#dtor)|`target_block` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[伝](#propagate)|ソースブロックからこのターゲットブロックにメッセージを非同期的に渡します。|
|[送信](#send)|送信元ブロックからこのターゲットブロックにメッセージを同期的に渡します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[async_send](#async_send)|処理するメッセージを非同期に送信します。|
|[decline_incoming_messages](#decline_incoming_messages)|新しいメッセージを拒否するブロックを示します。|
|[enable_batched_processing](#enable_batched_processing)|このブロックのバッチ処理を有効にします。|
|[initialize_target](#initialize_target)|基本オブジェクトを初期化します。 具体的には、 `message_processor` オブジェクトを初期化する必要があります。|
|[link_source](#link_source)|指定されたソースブロックをこのオブジェクトにリンク `target_block` します。|
|[process_input_messages](#process_input_messages)|入力として受信されたメッセージを処理します。|
|[process_message](#process_message)|派生クラスでオーバーライドされると、このオブジェクトによって受け入れられたメッセージを処理し `target_block` ます。|
|[propagate_message](#propagate_message)|派生クラスでオーバーライドされた場合、このメソッドは、ブロックからこのオブジェクトにメッセージを非同期的に渡し `ISource` `target_block` ます。 これは、 `propagate` ソースブロックによって呼び出されたときに、メソッドによって呼び出されます。|
|[register_filter](#register_filter)|受信したすべてのメッセージに対して呼び出されるフィルターメソッドを登録します。|
|[remove_sources](#remove_sources)|未処理の非同期送信操作が完了するのを待機した後、すべてのソースのリンクを解除します。|
|[send_message](#send_message)|派生クラスでオーバーライドされた場合、このメソッドは、ブロックからこのオブジェクトにメッセージを同期的に渡し `ISource` `target_block` ます。 これは、 `send` ソースブロックによって呼び出されたときに、メソッドによって呼び出されます。|
|[sync_send](#sync_send)|処理するメッセージを同期的に送信します。|
|[unlink_source](#unlink_source)|指定したソースブロックをこのオブジェクトからリンク解除 `target_block` します。|
|[unlink_sources](#unlink_sources)|このオブジェクトからすべてのソースブロックのリンクを解除 `target_block` します。 ( [ITarget:: unlink_sources](itarget-class.md#unlink_sources)よりも優先されます)。|
|[wait_for_async_sends](#wait_for_async_sends)|すべての非同期伝達が完了するまで待機します。|

## <a name="inheritance-hierarchy"></a>継承階層

[ITarget](itarget-class.md)

`target_block`

## <a name="requirements"></a>要件

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="async_send"></a><a name="async_send"></a> async_send

処理するメッセージを非同期に送信します。

```cpp
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
送信されるメッセージへのポインター。

## <a name="decline_incoming_messages"></a><a name="decline_incoming_messages"></a> decline_incoming_messages

新しいメッセージを拒否するブロックを示します。

```cpp
void decline_incoming_messages();
```

### <a name="remarks"></a>解説

このメソッドは、破棄の実行中に新しいメッセージが拒否されるようにするために、デストラクターによって呼び出されます。

## <a name="enable_batched_processing"></a><a name="enable_batched_processing"></a> enable_batched_processing

このブロックのバッチ処理を有効にします。

```cpp
void enable_batched_processing();
```

## <a name="initialize_target"></a><a name="initialize_target"></a> initialize_target

基本オブジェクトを初期化します。 具体的には、 `message_processor` オブジェクトを初期化する必要があります。

```cpp
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>パラメーター

*_PScheduler*<br/>
タスクをスケジュールするために使用するスケジューラ。

*_PScheduleGroup*<br/>
タスクをスケジュールするために使用されるスケジュールグループ。

## <a name="link_source"></a><a name="link_source"></a> link_source

指定されたソースブロックをこのオブジェクトにリンク `target_block` します。

```cpp
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>パラメーター

*_PSource*<br/>
リンクされるブロックへのポインター `ISource` 。

### <a name="remarks"></a>解説

この関数は、オブジェクトで直接呼び出すことはできません `target_block` 。 ブロックは、 `link_target` `ISource` 対応するターゲットに対してメソッドを呼び出すブロックに対して、メソッドを使用して一緒に接続する必要があり `link_source` ます。

## <a name="process_input_messages"></a><a name="process_input_messages"></a> process_input_messages

入力として受信されたメッセージを処理します。

```cpp
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
処理するメッセージへのポインター。

## <a name="process_message"></a><a name="process_message"></a> process_message

派生クラスでオーバーライドされると、このオブジェクトによって受け入れられたメッセージを処理し `target_block` ます。

```cpp
virtual void process_message(message<_Source_type> *);
```

## <a name="propagate"></a><a name="propagate"></a> 伝

ソースブロックからこのターゲットブロックにメッセージを非同期的に渡します。

```cpp
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
`message` オブジェクトを指すポインター。

*_PSource*<br/>
メッセージを提供するソースブロックへのポインター。

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した [message_status](concurrency-namespace-enums.md) を示します。

### <a name="remarks"></a>解説

パラメーターまたはパラメーターのいずれかがの場合、メソッドは [invalid_argument](../../../standard-library/invalid-argument-class.md) 例外をスローし `_PMessage` `_PSource` `NULL` ます。

## <a name="propagate_message"></a><a name="propagate_message"></a> propagate_message

派生クラスでオーバーライドされた場合、このメソッドは、ブロックからこのオブジェクトにメッセージを非同期的に渡し `ISource` `target_block` ます。 これは、 `propagate` ソースブロックによって呼び出されたときに、メソッドによって呼び出されます。

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
`message` オブジェクトを指すポインター。

*_PSource*<br/>
メッセージを提供するソースブロックへのポインター。

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した [message_status](concurrency-namespace-enums.md) を示します。

## <a name="register_filter"></a><a name="register_filter"></a> register_filter

受信したすべてのメッセージに対して呼び出されるフィルターメソッドを登録します。

```cpp
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>パラメーター

*_Filter*<br/>
フィルターメソッド。

## <a name="remove_sources"></a><a name="remove_sources"></a> remove_sources

未処理の非同期送信操作が完了するのを待機した後、すべてのソースのリンクを解除します。

```cpp
void remove_sources();
```

### <a name="remarks"></a>解説

すべてのターゲットブロックは、デストラクター内のソースを削除するために、このルーチンを呼び出す必要があります。

## <a name="send"></a><a name="send"></a> 送信

送信元ブロックからこのターゲットブロックにメッセージを同期的に渡します。

```cpp
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
`message` オブジェクトを指すポインター。

*_PSource*<br/>
メッセージを提供するソースブロックへのポインター。

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した [message_status](concurrency-namespace-enums.md) を示します。

### <a name="remarks"></a>解説

パラメーターまたはパラメーターのいずれかがの場合、メソッドは [invalid_argument](../../../standard-library/invalid-argument-class.md) 例外をスローし `_PMessage` `_PSource` `NULL` ます。

`send`メッセージの開始時以外にメソッドを使用し、ネットワーク内でメッセージを伝達することは危険であり、デッドロックにつながる可能性があります。

`send`がを返した場合、メッセージは既に受け入れられていて、ターゲットブロックに転送されているか、ターゲットによって拒否されています。

## <a name="send_message"></a><a name="send_message"></a> send_message

派生クラスでオーバーライドされた場合、このメソッドは、ブロックからこのオブジェクトにメッセージを同期的に渡し `ISource` `target_block` ます。 これは、 `send` ソースブロックによって呼び出されたときに、メソッドによって呼び出されます。

```cpp
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した [message_status](concurrency-namespace-enums.md) を示します。

### <a name="remarks"></a>解説

既定では、 `declined` 派生クラスによってオーバーライドされない限り、このブロックはを返します。

## <a name="sync_send"></a><a name="sync_send"></a> sync_send

処理するメッセージを同期的に送信します。

```cpp
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
送信されるメッセージへのポインター。

## <a name="target_block"></a><a name="ctor"></a> target_block

`target_block` オブジェクトを構築します。

```cpp
target_block();
```

## <a name="target_block"></a><a name="dtor"></a> ~ target_block

`target_block` オブジェクトを破棄します。

```cpp
virtual ~target_block();
```

## <a name="unlink_source"></a><a name="unlink_source"></a> unlink_source

指定したソースブロックをこのオブジェクトからリンク解除 `target_block` します。

```cpp
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>パラメーター

*_PSource*<br/>
リンク解除するブロックへのポインター `ISource` 。

## <a name="unlink_sources"></a><a name="unlink_sources"></a> unlink_sources

このオブジェクトからすべてのソースブロックのリンクを解除 `target_block` します。

```cpp
virtual void unlink_sources();
```

## <a name="wait_for_async_sends"></a><a name="wait_for_async_sends"></a> wait_for_async_sends

すべての非同期伝達が完了するまで待機します。

```cpp
void wait_for_async_sends();
```

### <a name="remarks"></a>解説

このメソッドは、すべての非同期操作がブロックを破棄する前に完了するまでの時間があることを確認するために、メッセージブロックデストラクターによって使用されます。

## <a name="see-also"></a>関連項目

[concurrency 名前空間](concurrency-namespace.md)<br/>
[ITarget クラス](itarget-class.md)
