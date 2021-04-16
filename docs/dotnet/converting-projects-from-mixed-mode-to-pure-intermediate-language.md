---
description: 詳細については、「混合モードから純粋な中間言語へのプロジェクトの変換」を参照してください。
title: 混合モードから純粋な中間言語へのプロジェクトの変換
ms.date: 04/15/2021
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.openlocfilehash: af16c9f179aa9bb6cc88ba3e47debbcdcc63cb04
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539229"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>混合モードから純粋な中間言語へのプロジェクトの変換

すべての Visual C++ CLR プロジェクトは、既定で C ランタイムライブラリにリンクされます。 その結果、これらのプロジェクトは、共通言語ランタイム (マネージコード) を対象とするコードとネイティブコードを組み合わせるため、 *混合モード* アプリケーションとして分類されます。 コンパイルされると、中間言語 (IL) にコンパイルされます。これは、Microsoft 中間言語 (MSIL) とも呼ばれます。

> [!IMPORTANT]
> Visual Studio 2015 の非推奨とされた Visual Studio 2017 で **`/clr:pure`** は、CLR アプリケーションのまたはコードの作成がサポートされなくなりました **`/clr:safe`** 。 純粋または安全なアセンブリが必要な場合は、アプリケーションを C# に変換することをお勧めします。

またはをサポートする以前のバージョンの Microsoft C++ コンパイラツールセットを使用している場合は **`/clr:pure`** **`/clr:safe`** 、次の手順を使用してコードを純粋 MSIL に変換できます。

### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>混合モードアプリケーションを純粋中間言語に変換するには

1. [C ランタイムライブラリ](../c-runtime-library/crt-library-features.md)へのリンクを削除する (CRT):

   1. アプリケーションのエントリポイントを定義する .cpp ファイルで、エントリポイントをに変更し `Main()` ます。 を使用する `Main()` と、プロジェクトが CRT にリンクされていないことを示します。

   1. ソリューションエクスプローラーで、プロジェクトを右クリックし、ショートカットメニューの [ **プロパティ** ] を選択して、アプリケーションのプロパティページを開きます。

   1. **リンカー** の **[** プロジェクトの詳細プロパティ] ページで、**エントリポイント** を選択し、このフィールドに「 **Main** 」と入力します。

   1. コンソールアプリケーションの場合は、**リンカー** の **システム** プロジェクトプロパティページで、[**サブシステム**] フィールドを選択し、をに変更し **`Console (/SUBSYSTEM:CONSOLE)`** ます。

      > [!NOTE]
      > [ **サブシステム** ] フィールドが既定でに設定されているため、Windows フォームアプリケーションに対してこのプロパティを設定する必要はありません **`Windows (/SUBSYSTEM:WINDOWS)`** 。

   1. で、 *`stdafx.h`* すべてのステートメントをコメントアウト `#include` します。 たとえば、コンソールアプリケーションでは次のようになります。

      ```cpp
      // #include <iostream>
      // #include <tchar.h>
      ```

       - または -

       たとえば、Windows フォームアプリケーションの場合は、次のようになります。

      ```cpp
      // #include <stdlib.h>
      // #include <malloc.h>
      // #include <memory.h>
      // #include <tchar.h>
      ```

   1. Windows フォームアプリケーションの場合は、「」で、を *`Form1.cpp`* 参照するステートメントをコメントアウトし `#include` *`windows.h`* ます。 次に例を示します。

      ```cpp
      // #include <windows.h>
      ```

1. に次のコードを追加し *`stdafx.h`* ます。

   ```cpp
   #ifndef __FLTUSED__
   #define __FLTUSED__
      extern "C" __declspec(selectany) int _fltused=1;
   #endif
   ```

1. すべてのアンマネージ型を削除します。

   必要に応じて、アンマネージ型を名前空間の構造体への参照に置き換え [`System`](/dotnet/api/system) ます。 一般的なマネージ型を次の表に示します。

   |構造体|Description|
   |---------------|-----------------|
   |[`Boolean`](/dotnet/api/system.boolean)|ブール値を表します。|
   |[`Byte`](/dotnet/api/system.byte)|8 ビット符号なし整数を表します。|
   |[`Char`](/dotnet/api/system.char)|Unicode 文字を表します。|
   |[`DateTime`](/dotnet/api/system.datetime)|通常、日付や時刻として表現される瞬間を表します。|
   |[`Decimal`](/dotnet/api/system.decimal)|10 進数を表します。|
   |[`Double`](/dotnet/api/system.double)|倍精度浮動小数点数を表します。|
   |[`Guid`](/dotnet/api/system.guid)|グローバル一意識別子 (GUID) を表します。|
   |[`Int16`](/dotnet/api/system.int16)|16 ビット符号付き整数を表します。|
   |[`Int32`](/dotnet/api/system.int32)|32 ビット符号付き整数を表します。|
   |[`Int64`](/dotnet/api/system.int64)|64 ビット符号付き整数を表します。|
   |[`IntPtr`](/dotnet/api/system.intptr)|ポインターまたはハンドルを表すときに使用されるプラットフォーム固有の型。|
   |[`SByte`](/dotnet/api/system.byte)|8 ビット符号付き整数を表します。|
   |[`Single`](/dotnet/api/system.single)|単精度浮動小数点数を表します。|
   |[`TimeSpan`](/dotnet/api/system.timespan)|時間間隔を表します。|
   |[`UInt16`](/dotnet/api/system.uint16)|16 ビット符号なし整数を表します。|
   |[`UInt32`](/dotnet/api/system.uint32)|32 ビット符号なし整数を表します。|
   |[`UInt64`](/dotnet/api/system.uint64)|64 ビット符号なし整数を表します。|
   |[`UIntPtr`](/dotnet/api/system.uintptr)|ポインターまたはハンドルを表すときに使用されるプラットフォーム固有の型。|
   |[`Void`](/dotnet/api/system.void)|値を返さないメソッドを示します。つまり、メソッドに `void` 戻り値の型があります。|
