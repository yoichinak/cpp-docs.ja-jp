---
description: 詳細については、「C++ での UWP アプリ用の非同期操作の作成」を参照してください。
title: C++ での UWP アプリ用の非同期操作の作成
ms.date: 11/19/2018
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
ms.openlocfilehash: 36205eb6749dd8aebb89caa6cc80ba256657e86a
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107576964"
---
# <a name="creating-asynchronous-operations-in-c-for-uwp-apps"></a>C++ での UWP アプリ用の非同期操作の作成

このドキュメントでは、task クラスを使用してユニバーサル Windows ランタイム (UWP) アプリで Windows ThreadPool ベースの非同期操作を生成する際に留意すべき重要な点について説明します。

非同期プログラミングの使用は、アプリがユーザー入力に対する応答性を維持できるようにするため、Windows ランタイムアプリモデルの重要なコンポーネントです。 UI スレッドをブロックすることなく、長時間実行されるタスクを開始することができ、後でタスクの結果を受け取ることができます。 また、タスクを取り消したり、タスクがバックグラウンドで実行される間に進行状況の通知を受け取ることができます。 ドキュメント「 [C++ での非同期プログラミング](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) 」では、UWP アプリを作成するために Visual C++ で使用できる非同期パターンの概要を説明しています。 このドキュメントでは、非同期 Windows ランタイム操作のチェーンを使用して作成する方法について説明します。 このセクションでは、ppltasks.h の型を使用して、別の Windows ランタイムコンポーネントで使用できる非同期操作を生成する方法と、非同期処理の実行方法を制御する方法について説明します。 また、Hilo での非同期 [プログラミングパターンとヒント (c++ と xaml を使用した Windows ストアアプリ)](/previous-versions/windows/apps/jj160321(v=win.10)) を使用して、hilo で非同期操作を実装する方法、および C++ および xaml を使用する Windows ランタイムアプリについても説明します。

> [!NOTE]
> UWP アプリでは、 [並列パターンライブラリ](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) と [非同期エージェントライブラリ](../../parallel/concrt/asynchronous-agents-library.md) を使用できます。 ただし、タスク スケジューラとリソース マネージャーを使用することはできません。 このドキュメントでは、PPL が提供するその他の機能について説明します。これは、デスクトップアプリではなく、UWP アプリでのみ使用できます。

## <a name="key-points"></a>重要なポイント

- 他のコンポーネントで使用する非同期操作 (C++ 以外の言語で記述される場合があります) を作成するには、[concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) を使用します。

- 非同期操作を呼び出すコンポーネントに進行状況の通知をレポートするためには、[concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) を使用します。

- 内部非同期操作の取り消しを可能にするには、キャンセル トークンを使用します。

- `create_async` の関数の動作は、渡される処理関数の戻り値の型によって異なります。 タスク ( `task<T>` または `task<void>`) を返す処理関数は、 `create_async`を呼び出したコンテキストで同期的に実行されます。 `T`任意のコンテキストでを返すか、または実行する処理関数 **`void`** 。

- [concurrency::task::then](reference/task-class.md#then) メソッドを使用すると、順次実行タスクのチェーンを作成できます。 UWP アプリでは、タスクの継続の既定のコンテキストは、そのタスクがどのように構築されたかによって異なります。 非同期アクションをタスク コンストラクターに渡すことによってタスクが作成されている場合、または非同期アクションを返すラムダ式を渡すことによってタスクが作成されている場合は、そのタスクのすべての継続の既定のコンテキストは、現在のコンテキストです。 タスクが非同期アクションから構築されていない場合、既定ではタスクの継続に任意のコンテキストが使用されます。 既定のコンテキストを [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) クラスでオーバーライドできます。

## <a name="in-this-document"></a>このドキュメントの内容

- [非同期操作を作成する](#create-async)

- [例: C++ での Windows ランタイム コンポーネントの作成](#example-component)

- [実行スレッドを制御する](#exethread)

- [例: C++ および XAML を使用した Windows ランタイムアプリでの実行の制御](#example-app)

## <a name="creating-asynchronous-operations"></a><a name="create-async"></a> 非同期操作の作成

並列パターン ライブラリ (PPL) でタスクや継続のモデルを使用して、バックグラウンド タスクを定義したり、前のタスクが完了すると実行される追加のタスクを定義することができます。 この機能は [concurrency::task](../../parallel/concrt/reference/task-class.md) クラスによって提供されます。 このモデルの詳細および `task` クラスの詳細については、「 [Task Parallelism](../../parallel/concrt/task-parallelism-concurrency-runtime.md)を呼び出したコンテキストで同期的に実行されます。

Windows ランタイムは、特別なオペレーティングシステム環境でのみ実行される UWP アプリを作成するために使用できるプログラミングインターフェイスです。 このようなアプリは、承認された機能、データ型、およびデバイスを使用し、Microsoft Store から配布されます。 Windows ランタイムは、 *アプリケーションバイナリインターフェイス* (ABI) によって表されます。 ABI は、Visual C++ などのプログラミング言語で Windows ランタイム Api を使用できるようにする、基になるバイナリコントラクトです。

Windows ランタイムを使用すると、さまざまなプログラミング言語の最適な機能を使用して1つのアプリにまとめることができます。 たとえば、JavaScript で UI を作成し、C ++ のコンポーネントで計算量が非常に多い演算を行うことができます。 計算量が非常に多い演算をバックグラウンドで行うことができるのは、UI の応答性を保つための重要な要素です。 `task`クラスは c++ に固有であるため、Windows ランタイムインターフェイスを使用して、非同期操作を他のコンポーネント (c++ 以外の言語で記述されている可能性があります) に伝達する必要があります。 Windows ランタイムには、非同期操作を表すために使用できる4つのインターフェイスが用意されています。

[Windows::Foundation::IAsyncAction](/uwp/api/windows.foundation.iasyncaction)<br/>
非同期アクションを表します。

[Windows:: Foundation:: IAsyncActionWithProgress\<TProgress>](/uwp/api/windows.foundation.iasyncactionwithprogress-1)<br/>
進行状況を報告する非同期アクションを表します。

[Windows:: Foundation:: IAsyncOperation\<TResult>](/uwp/api/windows.foundation.iasyncoperation-1)<br/>
結果を返す非同期操作を表します。

[Windows:: Foundation:: IAsyncOperationWithProgress\<TResult, TProgress>](/uwp/api/windows.foundation.iasyncoperationwithprogress-2)<br/>
結果を返し、進行状況を報告する、非同期操作を表します。

*アクション* の概念は、非同期タスクが値を生成しないことを意味します (を返す関数を考えてみ **`void`** ます)。 *操作* の概念は、非同期タスクが値を生成することを意味します。 *進行状況* の概念は、タスクが呼び出し元に進行状況を報告できることを意味します。 JavaScript、.NET Framework および Visual C++ はそれぞれ、ABI の境界を越えて使用するため、これらのインターフェイスのインスタンスを作成する独自の方法を提供します。 Visual C++ では、PPL は [concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) 関数を提供します。 この関数は、タスクの完了を表す Windows ランタイム非同期アクションまたは操作を作成します。 関数は、 `create_async` 処理関数 (通常はラムダ式) を受け取り、内部的にオブジェクトを作成 `task` し、4つの非同期 Windows ランタイムインターフェイスのいずれかでそのタスクをラップします。

> [!NOTE]
> `create_async`別の言語または別の Windows ランタイムコンポーネントからアクセスできる機能を作成する必要がある場合にのみ、を使用します。 同じコンポーネントの C++ コードで操作が生成、実行されることがわかっている場合には、 `task` クラスを直接使用します。

`create_async` の戻り値の型は、引数の型によって決まります。 たとえば、作業関数が値を返さず、進行状況を報告しない場合、 `create_async` は `IAsyncAction`を返します。 作業関数が値を返さず、進行状況を報告する場合、 `create_async` は `IAsyncActionWithProgress`を返します。 進行状況を報告するには、作業関数のパラメーターとして [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) オブジェクトを提供します。 進行状況を報告する機能により、実行された作業量と残りの作業量を報告できます (たとえば、パーセントにより)。 結果が使用できるようになったらそれを報告することができます。

`IAsyncAction`、 `IAsyncActionWithProgress<TProgress>`、 `IAsyncOperation<TResult>`、および `IAsyncActionOperationWithProgress<TProgress, TProgress>` インターフェイスはそれぞれ、非同期操作を取り消すことができるように `Cancel` メソッドを提供しています。 `task` クラスは、キャンセル トークンを使用します。 作業を取り消すためにキャンセル トークンを使用すると、ランタイムはそのトークンをサブスクライブする新しい作業を開始しません。 既にアクティブである作業はそのキャンセル トークンを監視でき、可能な場合には停止できます。 この機構については、ドキュメント「 [Cancellation in the PPL](cancellation-in-the-ppl.md)」で詳しく説明します。 Windows ランタイムメソッドを使用してタスクのキャンセルを接続するには、 `Cancel` 次の2つの方法があります。 最初に、`create_async` に渡す処理関数が [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) オブジェクトとなるように定義できます。 `Cancel`メソッドが呼び出されると、このキャンセルトークンは取り消され、通常のキャンセル規則は呼び出しをサポートする基になるオブジェクトに適用され `task` `create_async` ます。 `cancellation_token` オブジェクトを指定しない場合、基になる `task` オブジェクトが暗黙的に定義します。 処理関数の取り消しに協調的に応答する必要がある場合は `cancellation_token` オブジェクトを定義します。 「 [例: c++ および xaml を使用した Windows ランタイムアプリでの実行の制御](#example-app) 」では、カスタム Windows ランタイム C++ コンポーネントを使用する C# および xaml を使用するユニバーサル WINDOWS プラットフォーム (UWP) アプリでキャンセルを実行する方法の例を示します。

> [!WARNING]
> タスクの継続のチェーンでは、キャンセルトークンが取り消されたときに、常に状態をクリーンアップし、 [concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) を呼び出します。 `cancel_current_task`を呼び出す代わりにすぐに制御を返す場合は、操作は、取り消された状態でなく、完了の状態に遷移します。

次の表では、アプリケーションの非同期操作を定義するために使用できる組み合わせを示します。

|この Windows ランタイムインターフェイスを作成するには|`create_async`|これらのパラメーターの型を処理関数に渡して、暗黙的なキャンセル トークンを使用する|これらのパラメーターの型を処理関数に渡して、明示的なキャンセル トークンを使用する|
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|`IAsyncAction`|**`void`** もしくは `task<void>`|(なし)|(`cancellation_token`)|
|`IAsyncActionWithProgress<TProgress>`|**`void`** もしくは `task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|
|`IAsyncOperation<TResult>`|`T` または `task<T>`|(なし)|(`cancellation_token`)|
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T` または `task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|

`task` 関数に渡す処理関数から、値または `create_async` オブジェクトを返すことができます。 これらのバリエーションによって異なる動作になります。 値が返されたら、処理関数はバックグラウンド スレッドで実行できるように、 `task` にラップされます。 また、基になる `task` は、暗黙的なキャンセル トークンを使用します。 逆に `task` オブジェクトを返した場合、処理関数は同期的に実行されます。 したがって `task` オブジェクトを返す場合は、処理関数で時間のかかる操作はすべてタスクとして実行され、アプリケーションの応答性を保てるようにします。 また、基になる `task` は、暗黙的なキャンセル トークンを使用しません。 したがって、 `cancellation_token` から `task` オブジェクトを返す場合に取り消しをサポートする必要がある場合、 `create_async`オブジェクトを受け取るように処理関数を定義する必要があります。

次の例は、 `IAsyncAction` 別の Windows ランタイムコンポーネントで使用できるオブジェクトを作成するさまざまな方法を示しています。

[!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]

## <a name="example-creating-a-c-windows-runtime-component-and-consuming-it-from-c"></a><a name="example-component"></a> 例: C++ Windows ランタイムコンポーネントの作成と C からの使用\#

多くのコンピューティング処理を要する操作を実行するために、XAML と C# を使用して UI と C++ Windows ランタイムコンポーネントを定義するアプリを考えてみましょう。 この例では、C++ コンポーネントは特定の範囲での素数を計算します。 4つの Windows ランタイム非同期タスクインターフェイスの違いを説明するために、Visual Studio で、空の **ソリューション** を作成して名前を付けることによって、を開始し `Primes` ます。 次に、ソリューションに **[Windows ランタイム コンポーネント]** プロジェクトを追加し、名前を `PrimesLibrary`とします。 生成された C++ ヘッダー ファイル (この例では Class1.h の名前を Primes.h に変更しています) に次のコードを追加します。 各 **`public`** メソッドは、4つの非同期インターフェイスのいずれかを定義します。 値を返すメソッドは、 [Windows:: Foundation:: Collections:: IVector \<int> ](/uwp/api/windows.foundation.collections.ivector-1)オブジェクトを返します。 進行状況を報告するメソッドは、 **`double`** 完了した作業全体の割合を定義する値を生成します。

[!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]

> [!NOTE]
> 慣例により、Windows ランタイムの非同期メソッド名は、通常、"Async" で終わります。

生成された C++ ソース ファイル (この例では Class1.cpp の名前を Primes.cpp に変更しています) に次のコードを追加します。 `is_prime` 関数は、入力が素数かどうかを判定します。 残りのメソッドは `Primes` クラスを実装します。 `create_async` への呼び出しはそれぞれ、呼び出されるメソッドと互換性のあるシグネチャを使用します。 たとえば、 `Primes::ComputePrimesAsync` は `IAsyncAction`を返すため、 `create_async` に指定された処理関数は値を返さず、パラメーターとして `progress_reporter` オブジェクトを受け取りません。

[!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]

各メソッドは最初に検証を実行して、入力パラメーターが負でないことを確認します。 入力値が負数の場合、メソッドは [Platform::InvalidArgumentException](../../cppcx/platform-invalidargumentexception-class.md)をスローします。 エラー処理は、このセクションで後述します。

UWP アプリからこれらのメソッドを使用するには、Visual C# の [ **空のアプリ (XAML)** ] テンプレートを使用して、visual Studio ソリューションに2つ目のプロジェクトを追加します。 この例では、プロジェクトの名前を `Primes`とします。 次に、 `Primes` プロジェクトから `PrimesLibrary` プロジェクトへの参照を追加します。

MainPage.xaml に次のコードを追加します。 このコードは C++ コンポーネントを呼び出して結果を表示する UI を定義します。

[!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]

MainPage.xaml で、次のコードを `MainPage` クラスに追加します。 このコードは `Primes` オブジェクトとボタンのイベント ハンドラーを定義します。

[!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]

これらのメソッドは `async` と `await` のキーワードを使用して、非同期操作が完了した後で UI を更新します。 UWP アプリの非同期コーディングの詳細については、「 [スレッド処理と非同期プログラミング](/windows/uwp/threading-async)」を参照してください。

`getPrimesCancellation` および `cancelGetPrimes` メソッドは連携して、ユーザーが操作の取り消しをできるようにします。 ユーザーが **[キャンセル** ] ボタンを選択すると、 `cancelGetPrimes` メソッドは [IAsyncOperationWithProgress \<TResult, TProgress> :: cancel](/uwp/api/windows.foundation.iasyncinfo.cancel) を呼び出して操作を取り消します。 基になる非同期操作を管理する同時実行ランタイムは、取り消しが完了したことを通知するために Windows ランタイムによってキャッチされる内部例外の種類をスローします。 取り消しモデルの詳細については、「 [キャンセル](../../parallel/concrt/cancellation-in-the-ppl.md)」を参照してください。

> [!IMPORTANT]
> PPL が操作をキャンセルした Windows ランタイムに正しく報告できるようにするには、この内部例外の種類をキャッチしないでください。 これは、すべての例外 (`catch (...)`) をキャッチしないことを意味します。 すべての例外をキャッチする必要がある場合は、例外を再スローして、Windows ランタイムが取り消し操作を完了できるようにします。

次の図は、各オプションが選択された後の `Primes` アプリケーションを示しています。

![Windows ランタイム Primes アプリ](../../parallel/concrt/media/concrt_windows_primes.png "Windows ランタイム Primes アプリ")

を使用して、 `create_async` 他の言語で使用できる非同期タスクを作成する例については、「 [Bing マップトリップオプティマイザーのサンプルでの C++ の使用](/previous-versions/windows/apps/hh699891(v=vs.140))」を参照してください。

## <a name="controlling-the-execution-thread"></a><a name="exethread"></a> 実行スレッドの制御

Windows ランタイムは COM スレッドモデルを使用します。 このモデルでは、オブジェクトは、同期を扱う方法によって、異なるアパートメント内でホストされます。 スレッド セーフなオブジェクトは、マルチスレッド アパートメント (MTA) でホストされます。 1 つのスレッドによりアクセスされる必要があるオブジェクトは、シングルスレッド アパートメント (STA) でホストされます。

UI があるアプリケーションでは、ASTA (アプリケーション STA) スレッドはウィンドウ メッセージをポンプする必要があり、STA によりホストされた UI コントロールを更新できるプロセスでの唯一のスレッドです。 これにより次の 2 つの結果を生じます。 最初に、アプリケーションの応答性を保つためには、すべての CPU 負荷の高い操作および I/O 操作は ASTA のスレッドで実行しないようにします。 第 2 に、バックグラウンド スレッドからの結果は、UI を更新する ASTA にマーシャリングされる必要があります。 C++ UWP アプリでは、 `MainPage` および他の XAML ページはすべて ATSA で実行されます。 したがって、ASTA で宣言されるタスクの継続は、既定ではその場で実行されるため、継続の本体でコントロールを直接更新できます。 ただし、タスクが別のタスクの入れ子になっている場合、入れ子のタスクのすべての継続は MTA で実行されます。 したがって、継続が実行されるコンテキストを明示的に指定するかどうかを検討する必要があります。

`IAsyncOperation<TResult>`など、非同期操作から作成されたタスクは、特別な意味を使用するので、スレッド処理の詳細に注意する必要はありません。 操作はバックグラウンド スレッドで実行できますが (またはスレッドにまったくサポートされない場合もあります)、継続は既定では継続の操作を開始したアパートメントでの実行を保証されています (つまり `task::then`を呼び出したアパートメントから実行されます)。 [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) クラスを使用して、継続の実行コンテキストを制御できます。 これらの静的ヘルパー メソッドを使用して `task_continuation_context` オブジェクトを作成します。

- [concurrency::task_continuation_context::use_arbitrary](reference/task-continuation-context-class.md#use_arbitrary) を使用して、継続がバックグラウンド スレッドで実行されるように指定します。

- [concurrency::task_continuation_context::use_current](reference/task-continuation-context-class.md#use_current) を使用して、継続が `task::then`を呼び出したスレッドで実行されるように指定します。

`task_continuation_context` オブジェクトを [task::then](reference/task-class.md#then) メソッドに渡して、継続の実行コンテキストを明示的に制御できます。またはタスクを別のアパートメントに渡してから `task::then` メソッドを呼び出して、暗黙的に実行コンテキストを制御できます。

> [!IMPORTANT]
> UWP アプリのメイン UI スレッドは STA で実行されるため、sta で作成した継続は既定で STA で実行されます。 したがって、MTA に作成した継続は MTA 内で実行されます。

次のセクションでは、ディスクからファイルを読み込み、そのファイルで最もよく使われている単語を検索し、結果を UI に表示するアプリケーションを示します。 UI を更新する最後の操作は、UI スレッドで発生します。

> [!IMPORTANT]
> この動作は、UWP アプリに固有です。 デスクトップ アプリケーションでは、継続が実行される場所を制御できません。 その代わりに、各継続が実行されるワーカー スレッドをスケジューラが選択します。

> [!IMPORTANT]
> STA で実行される継続の本体で [concurrency::task::wait](reference/task-class.md#wait) を呼び出さないでください。 そうしないと、このメソッドが現在のスレッドをブロックして、アプリケーションが応答しなくなる場合があるため、ランタイムは [concurrency::invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) をスローします。 ただし、タスク ベースの継続で継続元タスクの結果を受け取るために [concurrency::task::get](reference/task-class.md#get) のメソッドを呼び出すことができます。

## <a name="example-controlling-execution-in-a-windows-runtime-app-with-c-and-xaml"></a><a name="example-app"></a> 例: C++ および XAML を使用した Windows ランタイムアプリでの実行の制御

ディスクからファイルを読み込み、そのファイルで最もよく使われている単語を検索し、結果を UI に表示する C++ XAML アプリケーションを考えてみます。 このアプリを作成するには、Visual Studio で、空の **アプリ (ユニバーサル Windows)** プロジェクトを作成して名前を付け `CommonWords` ます。 アプリケーション マニフェストで、 **[ドキュメント ライブラリ]** の機能を指定して、アプリケーションがドキュメント フォルダーにアクセスできるようにします。 また、アプリケーション マニフェストの宣言セクションにテキスト (.txt) ファイルの種類を追加します。 アプリの機能と宣言の詳細については、「 [Windows アプリのパッケージ化、配置、およびクエリ](/windows/win32/appxpkg/appx-portal)」を参照してください。

`Grid` 要素と `ProgressRing` 要素を含めるように、MainPage.xaml の `TextBlock` 要素を更新します。 `ProgressRing` は操作が進行中であることを示し、 `TextBlock` は計算の結果を示します。

[!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]

次の `#include` ステートメントを *.pch* に追加します。

[!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]

次のメソッド宣言を `MainPage` クラス (MainPage.h) に追加します。

[!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]

次の **`using`** ステートメントを mainpage.xaml に追加します。

[!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]

MainPage.cpp で、 `MainPage::MakeWordList`、 `MainPage::FindCommonWords`、および `MainPage::ShowResults` のメソッドを実装します。 `MainPage::MakeWordList` と `MainPage::FindCommonWords` は計算量が非常に多い演算操作を行います。 `MainPage::ShowResults` メソッドは演算の結果を UI に表示します。

[!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]

`MainPage` コンストラクターを変更し、Homer による著書 *The Iliad* でよく使われている単語を UI に表示する継続タスクのチェーンを作成します。 最初の 2 つの継続タスクは、テキストを個々の単語に分割し、よく使われている単語を検索します。これには時間がかかるため、バックグラウンドで実行されるように明示的に設定されています。 最後の継続タスクは UI を更新します。これは継続コンテキストを指定していないので、アパートメント スレッドの規則に従います。

[!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]

> [!NOTE]
> この例では、実行コンテキストを指定する方法と、継続のチェーンを構成する方法を示します。 非同期操作から作成されたタスクは、既定では `task::then`を呼び出したアパートメントで継続を実行することを思い出してください。 したがって、この例では `task_continuation_context::use_arbitrary` を使用して、UI が含まれていない操作をバックグラウンド スレッドで実行するように指定しています。

次の図は `CommonWords` アプリケーションの結果を示しています。

![CommonWords アプリの Windows ランタイム](../../parallel/concrt/media/concrt_windows_common_words.png "CommonWords アプリの Windows ランタイム")

この例では、を `task` サポートするオブジェクトが暗黙的なキャンセルトークンを使用するため、キャンセルをサポートでき `create_async` ます。 タスクが協調的に取り消しに応答する必要がある場合には、 `cancellation_token` オブジェクトを受け取るように処理関数を定義します。 PPL での取り消し処理の詳細については、「 [Cancellation in the PPL](cancellation-in-the-ppl.md)」を参照してください。

## <a name="see-also"></a>関連項目

[コンカレンシー ランタイム](../../parallel/concrt/concurrency-runtime.md)
