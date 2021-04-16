---
description: '詳細情報: コンパイラの警告 (レベル 1) C4407'
title: コンパイラの警告 (レベル 1) C4407
ms.date: 04/13/2021
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.openlocfilehash: cd54b6328a94277187958181689db1d443a53416
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577465"
---
# <a name="compiler-warning-level-1-c4407"></a>コンパイラの警告 (レベル 1) C4407

> 異なるポインター間でメンバー表現がキャストされると、コンパイラが正しくないコードを生成する可能性があります

メンバーへのポインター型の間の不適切なキャストが検出されました。

## <a name="remarks"></a>解説

C4407 は、Visual Studio 2005 で実行されたコンパイラ準拠作業のために生成されます。 Pointer-to-member には、修飾名とアドレス演算子 (&) が必要になりました。

C4407 は、多重継承 pointer-to-member を単一継承 pointer-to-member にキャストすると発生する可能性があります。 これが機能する場合もありますが、単一継承の pointer-to-member 表現が十分な情報を保持していないことが原因である場合があります。 を使用してコンパイルすると、 **`/vmm`** 役に立ちます。 詳細については、「」、「」 [ `/vmm` `/vms` `/vmv` (汎用表現)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)を参照してください。 また、基底クラスを再配置することもできます。基底クラスが派生したからの0以外のオフセットにあるため、コンパイラは変換の情報が失われていることを検出しています。

## <a name="example"></a>例

次の例では、C4407 を生成し、その修正方法を示しています。

```cpp
// C4407.cpp
// compile with: /W1 /c
struct C1 {};
struct C2 {};
struct C3 : C1, C2 {};

typedef void(C3::*PMF_C3)();
typedef void(C2::*PMF_C2)();

PMF_C2 f1(PMF_C3 pmf) {
   return (PMF_C2)pmf;   // C4407, change type of cast,
   // or reverse base class inheritance of C3 (i.e. : C2, C1)
}
```
