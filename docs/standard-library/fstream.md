---
description: '詳細情報: &lt; fstream&gt;'
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: ad6bb7bc319ba25e174f9c65e09f7f35db667167
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539707"
---
# `<fstream>`

外部ファイルに格納されているシーケンスの iostream の操作をサポートする複数のクラスを定義します。

## <a name="syntax"></a>Syntax

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedefs

|型名|説明|
|-|-|
|[`filebuf`](../standard-library/fstream-typedefs.md#filebuf)|`basic_filebuf`テンプレートパラメーターに特殊化された型 **`char`** 。|
|[`fstream`](../standard-library/fstream-typedefs.md#fstream)|`basic_fstream`テンプレートパラメーターに特殊化された型 **`char`** 。|
|[`ifstream`](../standard-library/fstream-typedefs.md#ifstream)|`basic_ifstream`テンプレートパラメーターに特殊化された型 **`char`** 。|
|[`ofstream`](../standard-library/fstream-typedefs.md#ofstream)|`basic_ofstream`テンプレートパラメーターに特殊化された型 **`char`** 。|
|[`wfstream`](../standard-library/fstream-typedefs.md#wfstream)|`basic_fstream`テンプレートパラメーターに特殊化された型 **`wchar_t`** 。|
|[`wifstream`](../standard-library/fstream-typedefs.md#wifstream)|`basic_ifstream`テンプレートパラメーターに特殊化された型 **`wchar_t`** 。|
|[`wofstream`](../standard-library/fstream-typedefs.md#wofstream)|`basic_ofstream`テンプレートパラメーターに特殊化された型 **`wchar_t`** 。|
|[`wfilebuf`](../standard-library/fstream-typedefs.md#wfilebuf)|`basic_filebuf`テンプレートパラメーターに特殊化された型 **`wchar_t`** 。|

### <a name="classes"></a>クラス

|クラス|説明|
|-|-|
|[`basic_filebuf`](../standard-library/basic-filebuf-class.md)|クラステンプレートは、 `Elem` 文字の特徴がクラスによって決定される型の要素の転送を、 `Tr` 外部ファイルに格納されている要素のシーケンスとの間で制御するストリームバッファーを記述します。|
|[`basic_fstream`](../standard-library/basic-fstream-class.md)|クラステンプレートは、クラスのストリームバッファーを使用して、要素とエンコードされたオブジェクトの挿入と抽出を制御するオブジェクトを記述し [`basic_filebuf`](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> `Elem` ます。これは、文字の特徴がクラスによって決定される型の要素を使用し `Tr` ます。|
|[`basic_ifstream`](../standard-library/basic-ifstream-class.md)|クラステンプレートは、クラスのストリームバッファーからの要素とエンコードされたオブジェクトの抽出を制御するオブジェクトを記述し [`basic_filebuf`](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> `Elem` ます。これは、文字の特徴がクラスによって決定される型の要素を使用し `Tr` ます。|
|[`basic_ofstream`](../standard-library/basic-ofstream-class.md)|クラステンプレートは、要素とエンコードされたオブジェクトのストリームバッファーへの挿入を制御するオブジェクトを記述し [`basic_filebuf`](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> ます。これは、型の要素を持ち、その `Elem` 文字特性はクラスによって決定され `Tr` ます。|

## <a name="see-also"></a>こちらもご覧ください

[ヘッダーファイルのリファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリのスレッドセーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
