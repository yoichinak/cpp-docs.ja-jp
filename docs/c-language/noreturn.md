---
title: _Noreturn キーワードと noreturn マクロ (C11)
description: '`_Noreturn` キーワードと `noreturn` マクロについて説明します。'
ms.date: 10/19/2020
f1_keywords:
- _Noreturn_c
- noreturn
helpviewer_keywords:
- keywords [C]
ms.openlocfilehash: 68448d8b8c999c92fb240100c25048fa94a559b9
ms.sourcegitcommit: 19016630f9d35f365e9ba249e0f3617515d7ca33
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92274692"
---
# <a name="_noreturn-keyword-and-noreturn-macro-c11"></a>`_Noreturn` キーワードと `noreturn` マクロ (C11)

`_Noreturn` キーワードは C11 で導入されました。 これにより、コンパイラに、適用される関数が呼び出し元に戻らないことが伝えられます。 このコンパイラは、`_Noreturn` 関数の呼び出しに続くコードは制御が渡らないことを認識します。 戻らない関数にはたとえば、[abort](../c-runtime-library/reference/abort.md) があります。 制御フローが呼び出し元に戻る可能性がある場合、関数には `_Noreturn` 属性を与えないでください。

このキーワードは一般的に、<stdnoreturn.h> で提供され、`_Noreturn` キーワードにマッピングされる便利なマクロ `noreturn` を経由して利用されます。

`_Noreturn` (またはそれに等しい `noreturn`) を使用することの主な利点は、今後それを読む人のために関数の意図を明確にすることであり、意図せず到達できないコードを検出することです。

`noreturn` の印が付いた関数により、戻り値は呼び出し元に返されないため、値の型を含めることはできません。 `void` になっている必要があります。

## <a name="example-using-noreturn-macro-and-_noreturn-keyword"></a>`noreturn` マクロと `_Noreturn ` キーワードの使用例

次の例は、`_Noreturn` キーワードとそれに等しい `noreturn` マクロを示しています。

無視できるマクロ `noreturn` を使用する場合、IntelliSense からは不適切なエラー `E0065` が生成されることがあります。 これは、サンプルの実行を妨げるものではありません。

```C
// Compile with Warning Level4 (/W4) and /std:c11
#include <stdio.h>
#include <stdlib.h>
#include <stdnoreturn.h>

noreturn void fatal_error(void)
{
    exit(3);
}

_Noreturn void not_coming_back(void)
{
    puts("There's no coming back");
    fatal_error();
    return; // warning C4645 - function declared with noreturn has a return statement
}

void done(void)
{
    puts("We'll never get here");
}

int main(void)
{
    not_coming_back();
    done(); // warning c4702 - unreachable code

    return 0;
}
```

## <a name="requirements"></a>必要条件

|マクロ|必須ヘッダー|
|-------------|---------------------|
|**`noreturn`**|\<stdnoreturn.h>|

## <a name="see-also"></a>関連項目

[/std (言語の標準バージョンを指定します)](../build/reference/std-specify-language-standard-version.md)\
[/W4 (警告レベルを指定します)](../build/reference/compiler-option-warning-level.md)\
[C4702 警告](../error-messages\compiler-warnings\compiler-warning-level-4-c4702.md)\
[__declspec(noreturn)](../cpp/noreturn.md)
