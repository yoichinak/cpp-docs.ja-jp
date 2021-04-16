---
description: 詳細については、「型変換とタイプセーフ」を参照してください。
title: 型変換とタイプ セーフ
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 629b361a-2ce1-4700-8b5d-ab4f57b245d5
ms.openlocfilehash: 1b36663fd913022c3b5542986d2d3085f9c8b8cf
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577439"
---
# <a name="type-conversions-and-type-safety"></a>型変換とタイプ セーフ

このドキュメントでは、共通型の変換に伴う問題を識別し、C++ コードでそれらを回避する方法を説明します。

C ++.のプログラムを作成するときは、そのプログラムがタイプ セーフであることを確認することが重要です。 これは、すべての変数、関数の引数、および関数の戻り値が適切な種類のデータを格納すること、異なる型の値が関係する操作が "意味のある" 処理を行うこと、さらにデータ損失、ビット パターンの誤った解釈、メモリ破損を発生させないことを意味します。 プログラムが、明示的または暗黙的に、ある型の値を他の型に変換しないことが、定義上のタイプ セーフです。 ただし、型の変換、また場合によっては安全でない変換が必須になることもあります。 たとえば、浮動小数点演算の結果を型の変数に格納する必要がある場合 **`int`** や、 **`unsigned int`** を受け取る関数にの値を渡す必要がある場合があり **`signed int`** ます。 どちらの例も、データ損失や値の再解釈を引き起こす可能性があるため、安全ではない変換を示していると言えます。

コンパイラが安全ではない変換を検出した場合は、エラーまたは警告を発行します。 エラーが生じた場合はコンパイルが中止されます。警告が生じた場合は、コンパイルは続行されますが、コード内にエラーが存在する可能性が示されます。 ただし、警告なしでプログラムがコンパイルされた場合でも、正しくない結果を生成する暗黙の型変換につながるコードが存在している可能性があります。 型エラーは、コード内の明示的な変換、またはキャストによって発生する可能性があります。

## <a name="implicit-type-conversions"></a>暗黙的な型変換

式に異なる組み込み型のオペランドが含まれており、明示的なキャストが存在しない場合、コンパイラは、組み込みの *標準変換* を使用してオペランドの1つを変換し、型が一致するようにします。 コンパイラはいずれかが成功するまで、適切に定義された一連の変換を試みます。 選択した変換が上位変換である場合、コンパイラは警告を発行しません。 変換が縮小変換である場合は、コンパイラは、データ損失の可能性に関する警告を発行します。 実際のデータ損失が発生するかどうかは、関与する実際の値に依存しますが、この警告をエラーとして扱うことをお勧めします。 ユーザー定義型が関与している場合は、コンパイラは、ユーザーがクラス定義の中で指定した変換を使用しようとします。 許容される変換が見つからない場合、コンパイラはエラーを発行し、プログラムをコンパイルしません。 標準変換を制御する規則の詳細については、「 [標準変換](../cpp/standard-conversions.md)」を参照してください。 ユーザー定義変換の詳細については、「 [ユーザー定義変換 (C++/cli)](../dotnet/user-defined-conversions-cpp-cli.md)」を参照してください。

### <a name="widening-conversions-promotion"></a>拡大変換 (上位変換)

拡大変換では、より小さい変数内の値が、より大きい変数に代入され、データは失われません。 拡大変換は常に安全であるため、コンパイラはそれらをサイレントで実行し、警告を発行しません。 次の変換は、拡大変換です。

|差出人|終了|
|----------|--------|
|またはを **`signed`** 除く任意または **`unsigned`** 整数型 **`long long`****`__int64`**|**`double`**|
|**`bool`** または **`char`**|他のすべての組み込み型|
|**`short`** または **`wchar_t`**|**`int`**, **`long`**, **`long long`**|
|**`int`**, **`long`**|**`long long`**|
|**`float`**|**`double`**|

### <a name="narrowing-conversions-coercion"></a>縮小変換 (強制型)

コンパイラは、暗黙的に縮小変換を実行しますが、データ損失の可能性に関する警告を発行します。 これらの警告を重大なものとして受け止めてください。 大きい変数の中にある値が、小さい変数の中に必ず収容でき、データ損失が発生しないことが確実な場合は、コンパイラが今後警告を発行しないように、明示的なキャストを追加してください。 変換が安全であることが確実でない場合は、コードに何らかのランタイムチェックを追加して、データ損失の可能性を処理します。これにより、プログラムが正しくない結果を生成することはありません。

浮動小数点型から整数型へのあらゆる変換は、浮動小数点値の小数部が破棄されて失われるため、縮小変換です。

次のコード例では、いくつかの暗黙的な縮小変換と、それらに関してコンパイラが発行する警告を示します。

```cpp
int i = INT_MAX + 1; //warning C4307:'+':integral constant overflow
wchar_t wch = 'A'; //OK
char c = wch; // warning C4244:'initializing':conversion from 'wchar_t'
              // to 'char', possible loss of data
unsigned char c2 = 0xfffe; //warning C4305:'initializing':truncation from
                           // 'int' to 'unsigned char'
int j = 1.9f; // warning C4244:'initializing':conversion from 'float' to
              // 'int', possible loss of data
int k = 7.7; // warning C4244:'initializing':conversion from 'double' to
             // 'int', possible loss of data
```

### <a name="signed---unsigned-conversions"></a>符号付き - 符号なしの変換

符号付き整数型と符号なし整数型は常に同じサイズですが、値変換の目的でビット パターンを解釈する方法が異なります。 次のコード例は、同じビット パターンが符号付きの値、および符号なしの値として解釈されるときの動作を示します。 `num` と `num2` の両方に格納されているビット パターンは、前の図から決して変化していません。

```cpp
using namespace std;
unsigned short num = numeric_limits<unsigned short>::max(); // #include <limits>
short num2 = num;
cout << "unsigned val = " << num << " signed val = " << num2 << endl;
// Prints: "unsigned val = 65535 signed val = -1"

// Go the other way.
num2 = -1;
num = num2;
cout << "unsigned val = " << num << " signed val = " << num2 << endl;
// Prints: "unsigned val = 65535 signed val = -1"
```

値の再解釈が双方向で発生することに注意してください。 期待される値に対して、符号が反転したように思える奇妙な結果をプログラムが返した場合は、符号付き整数型と符号なし整数型の間で暗黙的な変換が実行された可能性に注目してください。 次の例では、式 (0-1) の結果が **`int`** **`unsigned int`** に格納されている場合、からに暗黙的に変換され `num` ます。 この結果、ビット パターンの再解釈が発生します。

```cpp
unsigned int u3 = 0 - 1;
cout << u3 << endl; // prints 4294967295
```

コンパイラは、符号付き整数型と符号なし整数型の間の暗黙的な変換について警告しません。 そのため、符号付きから符号なしへの変換をすべて回避することをお勧めします。 それを回避できない場合は、変換対象の値が0以上で符号付きの型の最大値以下であるかどうかを検出するランタイムチェックを追加します。 この範囲内にある値は、再解釈なしで、符号付きから符号なし、および符号なしから符号付きへと変換されます。

### <a name="pointer-conversions"></a>ポインター変換

多くの式では、C 形式の配列は、配列内の最初の要素へのポインターに暗黙的に変換され、また定数変換が警告なしで実施される可能性があります。 これは便利ですが、場合によってはエラーが発生しやすくなります。 たとえば、不適切に設計された次のコード例は、無意味のように見えますが、コンパイルして ' p ' の結果を生成します。 まず、"Help" 文字列定数リテラルは、 **`char*`** 配列の最初の要素を指すに変換されます。このポインターは、最後の要素 ' p ' を指すように、3つの要素によってインクリメントされます。

```cpp
char* s = "Help" + 3;
```

## <a name="explicit-conversions-casts"></a>明示的な変換 (キャスト)

キャスト操作を使用すると、ある型の値を別の型に変換するようにコンパイラに指示できます。 2つの型が完全に無関係である場合、コンパイラはエラーを生成しますが、操作がタイプセーフでない場合でもエラーは発生しません。 キャストは控えめに使用してください。ある型から別の型への変換は、プログラム エラーの原因となる可能性があるためです。 ただし、時にはキャストが必須であり、すべてのキャストが等しく危険というわけでもありません。 キャストの有効な使用方法の1つは、コードが縮小変換を実行し、変換によってプログラムが間違った結果を生成しないことがわかっている場合です。 実際には、何を実行するかを開発者が理解していて、その点に関する警告を発行しないようにコンパイラに指示することになります。 別の使用法は、ポインターから派生クラス、およびポインターから基底クラスへのキャストです。 もう1つの用途は、変数の型をキャストして、非定数の引数を必要とする関数に渡すことです。 これらのキャスト操作のほとんどには、ある程度のリスクが存在します。

C スタイルのプログラミングでは、同じ C スタイルのキャスト演算子が、あらゆる種類のキャストに使用されます。

```cpp
(int) x; // old-style cast, old-style syntax
int(x); // old-style cast, functional syntax
```

つまり、C スタイルのキャスト演算子は、呼び出し演算子 () と同じものであり、したがって、コードの中で目立たず、簡単に見過ごす可能性があります。 どちらも、ひとめで認識したり、検索したりするのは困難で、 **`static`** 、、およびの任意の組み合わせを呼び出すのに十分な違いがあるため、どちらも悪くありません **`const`** **`reinterpret_cast`** 。 古いスタイルのキャストの実際の動作を理解するのは困難で、エラーが発生しやすくなります。 これらすべての理由により、キャストがどうしても必要な場合は、次の C++ スタイルのキャスト操作のいずれかを使用することをお勧めします。特定の状況では、かなりタイプ セーフであり、プログラミングの意図を非常に明確に表現できるからです。

- **`static_cast`**。コンパイル時にのみチェックされるキャストの場合。 **`static_cast`** 完全に互換性のない型間でキャストしようとしていることをコンパイラが検出すると、エラーが返されます。 これを、基本型へのポインターと、派生形へのポインターの間でのキャストに使用することもできますが、コンパイラはこのような変換が実行時に安全かどうかを必ず判定できるわけではありません。

    ```cpp
    double d = 1.58947;
    int i = d;  // warning C4244 possible loss of data
    int j = static_cast<int>(d);       // No warning.
    string s = static_cast<string>(d); // Error C2440:cannot convert from
                                       // double to std:string

    // No error but not necessarily safe.
    Base* b = new Base();
    Derived* d2 = static_cast<Derived*>(b);
    ```

   詳細については、「[`static_cast`](../cpp/static-cast-operator.md)」を参照してください。

- **`dynamic_cast`** 安全なランタイムチェックのキャストの場合は、ポインターから派生クラスへのポインター。 は、 **`dynamic_cast`** downcasts の場合よりも安全です **`static_cast`** が、ランタイムチェックでオーバーヘッドが発生します。

    ```cpp
    Base* b = new Base();

    // Run-time check to determine whether b is actually a Derived*
    Derived* d3 = dynamic_cast<Derived*>(b);

    // If b was originally a Derived*, then d3 is a valid pointer.
    if(d3)
    {
       // Safe to call Derived method.
       cout << d3->DoSomethingMore() << endl;
    }
    else
    {
       // Run-time check failed.
       cout << "d3 is null" << endl;
    }

    //Output: d3 is null;
    ```

   詳細については、「[`dynamic_cast`](../cpp/dynamic-cast-operator.md)」を参照してください。

- **`const_cast`**。変数の値をキャストする場合、 **`const`** または非変数をに変換する場合に使用 **`const`** **`const`** します。 **`const`** この演算子を使用した非表示のキャストは、C スタイルのキャストを使用した場合と同様に、エラーが発生しやすくなります。ただし、を使用すると、 **`const_cast`** 誤ってキャストを実行する可能性は低くなります。 場合によっては、変数を **`const`** 非パラメーターを受け取る関数に渡すために、変数の値をキャストする必要があり **`const`** **`const`** ます。 次の例は、その方法を示したものです。

    ```cpp
    void Func(double& d) { ... }
    void ConstCast()
    {
       const double pi = 3.14;
       Func(const_cast<double&>(pi)); //No error.
    }
    ```

   詳細については、「[`const_cast`](../cpp/const-cast-operator.md)」を参照してください。

- **`reinterpret_cast`** ポインター型やなどの関連のない型間でキャストを行う場合は **`int`** 。

    > [!NOTE]
    > このキャスト演算子は、他の演算子とは頻繁に使用されないため、他のコンパイラに移植できるとは限りません。

   次の例は、と **`reinterpret_cast`** の違いを示してい **`static_cast`** ます。

    ```cpp
    const char* str = "hello";
    int i = static_cast<int>(str);//error C2440: 'static_cast' : cannot
                                  // convert from 'const char *' to 'int'
    int j = (int)str; // C-style cast. Did the programmer really intend
                      // to do this?
    int k = reinterpret_cast<int>(str);// Programming intent is clear.
                                       // However, it is not 64-bit safe.
    ```

   詳細については、「 [ `reinterpret_cast` Operator](../cpp/reinterpret-cast-operator.md)」を参照してください。

## <a name="see-also"></a>関連項目

[C++ の型システム](../cpp/cpp-type-system-modern-cpp.md)<br/>
[C++ へようこそ](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[C++ 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)
