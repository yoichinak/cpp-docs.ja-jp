---
description: '詳細については、次を参照してください: __faststorefence'
title: __faststorefence
ms.date: 09/02/2019
f1_keywords:
- __faststorefence_cpp
- __faststorefence
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
ms.openlocfilehash: f12d16232e034c562f564d851da08c62cb59c34f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337027"
---
# <a name="__faststorefence"></a>__faststorefence

**Microsoft 固有の仕様**

メモリ参照の読み込みと格納の両方を含む、以前の各メモリ参照が、後続のメモリ参照の前に全体に対して参照可能になっていることを保証します。

## <a name="syntax"></a>構文

```C
void __faststorefence();
```

## <a name="requirements"></a>必要条件

|Intrinsic|アーキテクチャ|
|---------------|------------------|
|`__faststorefence`|X64|

**ヘッダー ファイル** \<intrin.h>

## <a name="remarks"></a>解説

実行を続行する前に、組み込みがグローバルに参照できるようになる前に発行された読み込みおよび格納操作を保証する、完全なメモリバリア命令シーケンスを生成します。 効果は、すべての x64 プラットフォームにおける `_mm_mfence` の組み込みと同等ですが、それよりも高速になります。

AMD64 プラットフォームでは、このルーチンは、`sfence` 命令よりも高速なストア フェンスである命令を生成します。 タイム クリティカル コードでは、`_mm_sfence` ではなくこの組み込みを使用します (AMD64 プラットフォームのみ)。 Intel x64 プラットフォームでは、 `_mm_sfence` 命令は高速化します。

このルーチンは、組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
