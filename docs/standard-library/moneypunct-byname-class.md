---
description: '詳細情報: moneypunct_byname クラス'
title: moneypunct_byname クラス
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct_byname
helpviewer_keywords:
- moneypunct_byname class
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
ms.openlocfilehash: b20293ac6788156f25f95878a5ab0098c178edec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277467"
---
# <a name="moneypunct_byname-class"></a>moneypunct_byname クラス

指定されたロケールのファセットとして使用できるオブジェクトを表す派生クラステンプレート `moneypunct` 。通貨入力フィールドまたは通貨出力フィールドの書式設定を有効にします。

## <a name="syntax"></a>構文

```cpp
template <class CharType, bool Intl = false>
class moneypunct_byname : public moneypunct<CharType, Intl>
{
public:
    explicit moneypunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit moneypunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~moneypunct_byname();

};
```

## <a name="remarks"></a>解説

その動作は名前付きのロケール `_Locname` で決まります。 各コンストラクターは、 [moneypunct](../standard-library/moneypunct-class.md#moneypunct)() を使用して、その基本オブジェクトを初期化 \<CharType, Intl> `_Refs` します。

## <a name="requirements"></a>要件

**ヘッダー:**\<locale>

**名前空間:** std

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリのスレッドセーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
