---
title: モジュール、インポート、エクスポート
ms.date: 12/12/2019
f1_keywords:
- module_cpp
- import_cpp
- export_cpp
helpviewer_keywords:
- modules [C++]
- modules [C++], import
- modules [C++], export
description: Import および export 宣言を使用して、指定したモジュールで定義されている型と関数にアクセスし、発行します。
ms.openlocfilehash: 360f940f2633641e13c93ecb9083d7e785794381
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577193"
---
# <a name="module-import-export"></a>モジュール、インポート、エクスポート

**モジュール**、**インポート**、および **`export`** 宣言は c++ 20 で使用でき、/[実験的: モジュール](../build/reference/experimental-module.md)コンパイラスイッチと共に、/ [std: C + + latest](../build/reference/std-specify-language-standard-version.md)が必要です。 詳細については、「 [C++ のモジュールの概要](modules-cpp.md)」を参照してください。

## <a name="module"></a>name

モジュールの実装ファイルの先頭に **モジュール** 宣言を配置し、ファイルの内容が名前付きモジュールに属していることを指定します。

```cpp
module ModuleA;
```

## <a name="export"></a>エクスポート

モジュールのプライマリインターフェイスファイルに **エクスポートモジュール** 宣言を使用します。このファイルには拡張子を付ける必要があり **ます。 ixx**:

```cpp
export module ModuleA;
```

インターフェイスファイルでは、 **`export`** パブリックインターフェイスの一部として意図されている名前に修飾子を使用します。

```cpp
// ModuleA.ixx

export module ModuleA;

namespace Bar
{
   export int f();
   export double d();
   double internal_f(); // not exported
}
```

エクスポートされていない名前は、モジュールをインポートするコードからは参照できません。

```cpp
//MyProgram.cpp

import module ModuleA;

int main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

キーワードは、 **`export`** モジュールの実装ファイルには記述できません。 **`export`** が名前空間名に適用されると、名前空間内のすべての名前がエクスポートされます。

## <a name="import"></a>import

**インポート** 宣言を使用して、モジュールの名前がプログラムに表示されるようにします。 インポート宣言は、モジュール宣言の後、任意の #include ディレクティブの後、ファイル内の宣言の前に記述する必要があります。

```cpp
module ModuleA;

#include "custom-lib.h"
import std.core;
import std.regex;
import ModuleB;

// begin declarations here:
template <class T>
class Baz
{...};
```

## <a name="remarks"></a>解説

**インポート** と **モジュール** は、論理行の先頭に出現する場合にのみキーワードとして扱われます。

```cpp

// OK:
module ;
module module-name
import :
import <
import "
import module-name
export module ;
export module module-name
export import :
export import <
export import "
export import module-name

// Error:
int i; module ;
```

**Microsoft 固有の仕様**

Microsoft C++ では、トークンの **インポート** と **モジュール** は常に識別子であり、マクロの引数として使用される場合はキーワードではありません。

### <a name="example"></a>例

```cpp
#define foo(...) __VA_ARGS__
foo(
import // Always an identifier, never a keyword
)
```

**End Microsoft 固有の仕様**

## <a name="see-also"></a>参照

[C++ のモジュールの概要](modules-cpp.md)
