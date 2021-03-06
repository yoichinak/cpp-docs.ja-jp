---
description: '詳細情報: IPersistStreamInitImpl クラス'
title: IPersistStreamInitImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
ms.openlocfilehash: f60483435be750c7031f2e7bf7f3f18cba36a023
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158154"
---
# <a name="ipersiststreaminitimpl-class"></a>IPersistStreamInitImpl クラス

このクラス `IUnknown` はを実装し、 [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) インターフェイスの既定の実装を提供します。

> [!IMPORTANT]
> このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から派生したクラス `IPersistStreamInitImpl` 。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IPersistStreamInitImpl:: GetClassID](#getclassid)|オブジェクトの CLSID を取得します。|
|[IPersistStreamInitImpl:: GetSizeMax](#getsizemax)|オブジェクトのデータを保存するために必要なストリームのサイズを取得します。 ATL 実装は E_NOTIMPL を返します。|
|[IPersistStreamInitImpl:: InitNew](#initnew)|新しく作成されたオブジェクトを初期化します。|
|[IPersistStreamInitImpl:: IsDirty](#isdirty)|オブジェクトのデータが最後に保存されてから変更されたかどうかを確認します。|
|[IPersistStreamInitImpl:: Load](#load)|指定したストリームからオブジェクトのプロパティを読み込みます。|
|[IPersistStreamInitImpl:: Save](#save)|オブジェクトのプロパティを指定したストリームに保存します。|

## <a name="remarks"></a>解説

[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)インターフェイスを使用すると、クライアントは、オブジェクトがその永続データを読み込んで1つのストリームに保存するように要求できます。 クラス `IPersistStreamInitImpl` は、このインターフェイスの既定の実装を提供し、 `IUnknown` デバッグビルドでダンプデバイスに情報を送信することによってを実装します。

**関連記事** [ATL チュートリアル](../../atl/active-template-library-atl-tutorial.md)、 [atl プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>継承階層

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>要件

**ヘッダー:** atlcom. h

## <a name="ipersiststreaminitimplgetclassid"></a><a name="getclassid"></a> IPersistStreamInitImpl:: GetClassID

オブジェクトの CLSID を取得します。

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>解説

Windows SDK の「 [IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) 」を参照してください。

## <a name="ipersiststreaminitimplgetsizemax"></a><a name="getsizemax"></a> IPersistStreamInitImpl:: GetSizeMax

オブジェクトのデータを保存するために必要なストリームのサイズを取得します。

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

### <a name="remarks"></a>解説

Windows SDK の「 [IPersistStreamInit:: GetSizeMax](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) 」を参照してください。

## <a name="ipersiststreaminitimplinitnew"></a><a name="initnew"></a> IPersistStreamInitImpl:: InitNew

新しく作成されたオブジェクトを初期化します。

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>解説

Windows SDK の「 [IPersistStreamInit:: InitNew](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) 」を参照してください。

## <a name="ipersiststreaminitimplisdirty"></a><a name="isdirty"></a> IPersistStreamInitImpl:: IsDirty

オブジェクトのデータが最後に保存されてから変更されたかどうかを確認します。

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>解説

Windows SDK の「 [IPersistStreamInit:: IsDirty](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) 」を参照してください。

## <a name="ipersiststreaminitimplload"></a><a name="load"></a> IPersistStreamInitImpl:: Load

指定したストリームからオブジェクトのプロパティを読み込みます。

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>解説

ATL では、オブジェクトのプロパティマップを使用してこの情報を取得します。

Windows SDK の「 [IPersistStreamInit:: Load](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-load) 」を参照してください。

## <a name="ipersiststreaminitimplsave"></a><a name="save"></a> IPersistStreamInitImpl:: Save

オブジェクトのプロパティを指定したストリームに保存します。

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>解説

ATL では、オブジェクトのプロパティマップを使用してこの情報を格納します。

Windows SDK の「 [IPersistStreamInit:: Save](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-save) 」を参照してください。

## <a name="see-also"></a>関連項目

[ストレージとストリーム](/windows/win32/Stg/storages-and-streams)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
