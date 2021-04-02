---
description: 詳細については、「 &lt; &lt; 独自のクラスの演算子のオーバーロード」を参照してください。
title: 独自クラスのための &lt;&lt; 演算子のオーバーロード
ms.date: 11/04/2016
helpviewer_keywords:
- operator<<, overloading for your own classes
- operator <<, overloading for your own classes
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
ms.openlocfilehash: 10b5191c291676319ff461932e595811744a384d
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099210"
---
# <a name="overloading-the--operator-for-your-own-classes"></a>独自クラスのための `<<` 演算子のオーバーロード

出力ストリームは、標準型に挿入 (`<<`) 演算子を使用します。 独自クラスのための `<<` 演算子をオーバーロードすることもできます。

## <a name="example"></a>例

`write` 関数の例では、`Date` 構造体の使用について説明しました。 日付は、データ メンバー (月、日、および年) をビューから非表示にする C++ クラスにとって最適な候補です。 出力ストリームは、このような構造体を表示するための論理出力先です。 このコードは、`cout` オブジェクトを使用して日付を表示します。

```cpp
Date dt(1, 2, 92);

cout <<dt;
```

`cout` が挿入演算子の後に `Date` オブジェクトを受け入れるようにするには、挿入演算子をオーバーロードして、左辺の `ostream` オブジェクトと右辺の `Date` オブジェクトを認識するようにします。 次に、オーバーロードした `<<` 演算子関数をクラス `Date` のフレンドとして宣言し、`Date` オブジェクト内のプライベート データにアクセスできるようにします。

```cpp
// overload_date.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Date
{
    int mo, da, yr;
public:
    Date(int m, int d, int y)
    {
        mo = m; da = d; yr = y;
    }
    friend ostream& operator<<(ostream& os, const Date& dt);
};

ostream& operator<<(ostream& os, const Date& dt)
{
    os << dt.mo << '/' << dt.da << '/' << dt.yr;
    return os;
}

int main()
{
    Date dt(5, 6, 92);
    cout << dt;
}
```

```Output
5/6/92
```

## <a name="remarks"></a>解説

オーバーロードされた演算子は元の `ostream` オブジェクトに参照を返すため、挿入を組み合わせることができます。

```cpp
cout <<"The date is" <<dt <<flush;
```

## <a name="see-also"></a>関連項目

[出力ストリーム](../standard-library/output-streams.md)
