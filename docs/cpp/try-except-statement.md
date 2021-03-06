---
title: try-except ステートメント
description: __Try および __except の構造化例外処理ステートメントへの Microsoft C++ リファレンス。
ms.date: 08/25/2020
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- _exception_info
- __except
- _except
- _exception_code
- __except_cpp
- _exception_info_cpp
helpviewer_keywords:
- __try keyword [C++]
- EXCEPTION_CONTINUE_EXECUTION macro
- EXCEPTION_CONTINUE_SEARCH macro
- EXCEPTION_EXECUTE_HANDLER macro
- GetExceptionCode function
- try-catch keyword [C++], try-except keyword [C++]
- _exception_code keyword [C++]
- try-except keyword [C++]
- _exception_info keyword [C++]
- _abnormal_termination keyword [C++]
ms.assetid: 30d60071-ea49-4bfb-a8e6-7a420de66381
ms.openlocfilehash: 226c3a3df39f284d9c1267051114fc39db358f55
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898618"
---
# <a name="try-except-statement"></a>`try-except` ステートメント

`try-except`ステートメントは、C および C++ 言語の構造化例外処理をサポートする、 **Microsoft 固有**の拡張機能です。

```cpp
    // . . .
    __try {
        // guarded code
    }
    __except ( /* filter expression */ ) {
        // termination code
    }
    // . . .
```

## <a name="grammar"></a>文法

> *`try-except-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__except (`**  *`expression`*  **`)`** *`compound-statement`*

## <a name="remarks"></a>注釈

`try-except`ステートメントは、C および C++ 言語の Microsoft 拡張機能です。 これにより、通常はプログラムの実行を終了するイベントが発生したときに、対象アプリケーションで制御できるようになります。 このようなイベントは、 *構造化例外*、つまり短い *例外* と呼ばれます。 これらの例外を処理するメカニズムは、 *構造化例外処理* (SEH) と呼ばれます。

関連情報については、「 [try finally ステートメント](../cpp/try-finally-statement.md)」を参照してください。

例外は、ハードウェアベースまたはソフトウェアベースのいずれかです。 構造化例外処理は、アプリケーションがハードウェアまたはソフトウェアの例外から完全に回復できない場合でも役立ちます。 SEH を使用すると、エラー情報を表示し、問題の診断に役立つアプリケーションの内部状態をトラップすることができます。 これは、簡単に再現できない断続的な問題に特に役立ちます。

> [!NOTE]
> 構造化例外処理では、C と C++ のソース ファイルの両方で Win32 を使用します。 ただし、特に C++ 向けには設計されていません。 C++ 例外処理を使用して、コードの移植性を高めることができます。 また、C++ 例外処理は、任意の型の例外を処理できるという点で、より柔軟です。 C++ プログラムでは、ネイティブ C++ 例外処理 ( [try、catch、および throw](../cpp/try-throw-and-catch-statements-cpp.md) ステートメント) を使用することをお勧めします。

句の後の複合ステートメント **`__try`** は、 *本体* または *保護* されたセクションです。 **`__except`** 式は、*フィルター*式とも呼ばれます。 この値によって、例外の処理方法が決まります。 **`__except`** 句の後の複合ステートメントは、例外ハンドラーです。 ハンドラーは、本文セクションの実行中に例外が発生した場合に実行するアクションを指定します。 次のように実行されます。

1. 保護されたセクションが実行されます。

1. 保護されたセクションの実行中に例外が発生しなかった場合、実行は **`__except`** 句の後のステートメントから続行されます。

1. 保護されたセクションの実行中に例外が発生した場合、または保護されたセクションがを呼び出した場合は、 **`__except`** 式が評価されます。 指定可能な 3 つの値は次のとおりです。

   - `EXCEPTION_CONTINUE_EXECUTION` (-1)例外は破棄されます。 例外が発生した位置から実行を継続します。

   - `EXCEPTION_CONTINUE_SEARCH` (0) 例外が認識されません。 ハンドラーのスタックの検索を続行します。最初に、ステートメントを含めて `try-except` から、次に高い優先順位を持つハンドラーを検索します。

   - `EXCEPTION_EXECUTE_HANDLER` (1) 例外が認識されています。 複合ステートメントを実行して例外ハンドラーに制御を転送 **`__except`** し、ブロックの後に実行を継続し **`__except`** ます。

**`__except`** 式は、C 式として評価されます。 1つの値、条件式演算子、またはコンマ演算子に制限されています。 より広範な処理が必要な場合、前に挙げた 3 つの値の 1 つを返すルーチンを式で呼び出すことができます。

各アプリケーションが独自の例外ハンドラーを持つ場合があります。

ステートメントにジャンプすることはできません **`__try`** が、1つのステートメントからジャンプすることは有効です。 ステートメントの実行中にプロセスが終了した場合、例外ハンドラーは呼び出されません `try-except` 。

以前のバージョンとの互換性を維持するために、 **_try**、 **_except**、および **_leave** は、、、およびのシノニムと **`__try`** **`__except`** **`__leave`** なります。ただし、コンパイラオプションでは、 [ \( 言語拡張機能を無効に](../build/reference/za-ze-disable-language-extensions.md) します。

### <a name="the-__leave-keyword"></a><a name="__leave"></a>`__leave`キーワード

キーワードは、 **`__leave`** ステートメントの保護されたセクション内でのみ有効で `try-except` あり、その結果、保護されたセクションの末尾に移動します。 実行は、例外ハンドラーの後の最初のステートメントから続行されます。

ステートメントは、 **`goto`** 保護されたセクションからジャンプすることもできます。また、 **finally** ステートメントの場合と同様にパフォーマンスが低下することもありません。 これは、スタックアンワインドが発生しないためです。 ただし、ステートメントではなく、キーワードを使用することをお勧めし **`__leave`** **`goto`** ます。 その理由は、保護されたセクションが大規模または複雑な場合にプログラミングの間違いを犯す可能性が低いためです。

### <a name="structured-exception-handling-intrinsic-functions"></a>構造化例外処理組み込み関数

構造化例外処理には、 `try-except` [Getexceptioncode](/windows/win32/Debug/getexceptioncode) と [getexceptioncode](/windows/win32/Debug/getexceptioninformation)ステートメントで使用できる2つの組み込み関数が用意されています。

`GetExceptionCode` 例外のコード (32 ビット整数) を返します。

組み込み関数は、 `GetExceptionInformation` 例外に関する追加情報を含む [EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) 構造体へのポインターを返します。 このポインターを使用して、ハードウェア例外のときに存在していたコンピューターの状態にアクセスできます。 構造は次のとおりです。

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

ポインター型 `PEXCEPTION_RECORD` とは `PCONTEXT` インクルードファイルで定義され、と \<winnt.h> `_EXCEPTION_RECORD` `_CONTEXT` はインクルードファイルで定義されます。 \<excpt.h>

は `GetExceptionCode` 、例外ハンドラー内で使用できます。 ただし、は `GetExceptionInformation` 例外フィルター式内でのみ使用できます。 参照先の情報は、通常はスタック上にあり、制御が例外ハンドラーに転送されるときには使用できなくなります。

組み込み関数 [Abnormaltermination](/windows/win32/Debug/abnormaltermination) は、終了ハンドラー内で使用できます。 **Try finally**ステートメントの本体が連続して終了する場合は、0を返します。 その他の場合は、1 を返します。

\<excpt.h> では、これらの組み込みの代替名を定義しています。

`GetExceptionCode` は `_exception_code` と同じです。

`GetExceptionInformation` は `_exception_info` と同じです。

`AbnormalTermination` は `_abnormal_termination` と同じです。

## <a name="example"></a>例

```cpp
// exceptions_try_except_Statement.cpp
// Example of try-except and try-finally statements
#include <stdio.h>
#include <windows.h> // for EXCEPTION_ACCESS_VIOLATION
#include <excpt.h>

int filter(unsigned int code, struct _EXCEPTION_POINTERS *ep)
{
    puts("in filter.");
    if (code == EXCEPTION_ACCESS_VIOLATION)
    {
        puts("caught AV as expected.");
        return EXCEPTION_EXECUTE_HANDLER;
    }
    else
    {
        puts("didn't catch AV, unexpected.");
        return EXCEPTION_CONTINUE_SEARCH;
    };
}

int main()
{
    int* p = 0x00000000;   // pointer to NULL
    puts("hello");
    __try
    {
        puts("in try");
        __try
        {
            puts("in try");
            *p = 13;    // causes an access violation exception;
        }
        __finally
        {
            puts("in finally. termination: ");
            puts(AbnormalTermination() ? "\tabnormal" : "\tnormal");
        }
    }
    __except(filter(GetExceptionCode(), GetExceptionInformation()))
    {
        puts("in except");
    }
    puts("world");
}
```

### <a name="output"></a>出力

```Output
hello
in try
in try
in filter.
caught AV as expected.
in finally. termination:
        abnormal
in except
world
```

## <a name="see-also"></a>関連項目

[例外ハンドラーの記述](../cpp/writing-an-exception-handler.md)<br/>
[構造化例外処理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[キーワード](../cpp/keywords-cpp.md)
