---
description: '詳細情報: Platform:: IntPtr value クラス'
title: Platform::IntPtr 値クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformIntPtr::IntPtr
- VCCORLIB/PlatformIntPtr::op_explicit Operator
- VCCORLIB/PlatformIntPtr::ToInt32
helpviewer_keywords:
- Platform::IntPtr Struct
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
ms.openlocfilehash: 18c5316eaae84b1e6af4e54d86ef876d81a866ed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295264"
---
# <a name="platformintptr-value-class"></a>Platform::IntPtr 値クラス

サイズがプラットフォームに特有の (32 ビットまたは 64 ビット)、符号付きポインターまたはハンドルを表します。

## <a name="syntax"></a>構文

```cpp
public value struct IntPtr
```

### <a name="members"></a>メンバー

IntPtr には、次のメンバーがあります。

|メンバー|説明|
|------------|-----------------|
|[IntPtr:: IntPtr](#ctor)|IntPtr の新しいインスタンスを初期化します。|
|[IntPtr:: op_explicit 演算子](#op-explicit)|指定されたパラメーターを IntPtr、または IntPtr 値へのポインターに変換します。|
|[IntPtr:: ToInt32](#toint32)|現在の IntPtr を 32 ビット整数に変換します。|

### <a name="requirements"></a>要件

**サポートされている最低限のクライアント:** Windows 8

**サポートされる最小サーバー:** Windows Server 2012

**名前空間:** Platform

**メタデータ:** platform. winmd

## <a name="intptrintptr-constructor"></a><a name="ctor"> </a> IntPtr::IntPtr コンストラクター

指定された値を持つ IntPtr の新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
IntPtr( __int64 handle-or-pointer );   IntPtr( void* value );   IntPtr( int 32-bit_value );
```

### <a name="parameters"></a>パラメーター

*value*<br/>
64 ビットのハンドルまたはポインター、または 64 ビット値へのポインター、または 64 ビット値に変換できる 32 ビット値。

## <a name="intptrop_explicit-operator"></a><a name="op-explicit"> </a> IntPtr::op_explicit 演算子

指定されたパラメーターを IntPtr、または IntPtr 値へのポインターに変換します。

### <a name="syntax"></a>構文

```cpp
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );
```

### <a name="parameters"></a>パラメーター

*value1*<br/>
ハンドルまたは IntPtr へのポインター。

*value2*<br/>
IntPtr に変換できる 32 ビット整数。

*value3*<br/>
IntPtr。

### <a name="return-value"></a>戻り値

1 番目と 2 番目の演算子は IntPtr を返します。 3 番目の演算子は、現在の IntPtr によって表される値へのポインターを返します。

## <a name="intptrtoint32-method"></a><a name="toint32"></a> IntPtr:: ToInt32 メソッド

現在の IntPtr 値を 32 ビット整数に変換します。

### <a name="syntax"></a>構文

```cpp
int32 IntPtr::ToInt32();
```

### <a name="return-value"></a>戻り値

32 ビットの整数。

## <a name="see-also"></a>関連項目

[プラットフォーム名前空間](../cppcx/platform-namespace-c-cx.md)
