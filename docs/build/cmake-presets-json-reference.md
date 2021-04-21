---
description: Microsoft ベンダー マップ `CMakePresets.json` と `CMakeUserPresets.json` のスキーマ リファレンス
title: CMakeUserPresets.json
ms.date: 4/13/2021
helpviewer_keywords:
- CMake in Visual C++
ms.openlocfilehash: 08e8fd756ce070fa9abf1647336fcaaa5d653534
ms.sourcegitcommit: bac5dde649d5b0447de1d26a73365e36d74595f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2021
ms.locfileid: "107381417"
---
# <a name="cmakepresetsjson-and-cmakeuserpresetsjson-microsoft-vendor-maps"></a>`CMakePresets.json` および `CMakeUserPresets.json` Microsoft ベンダー マップ

CMake でサポートされている 2 つのファイル `CMakePresets.json` と `CMakeUserPresets.json` を使用すると、ユーザーは一般的な構成、ビルド、テストのオプションを指定し、他のユーザーと共有できます。

`CMakePresets.json` と `CMakeUserPresets.json` を使用して、Visual Studio、Visual Studio Code、継続的インテグレーション (CI) パイプライン、およびコマンド ラインから CMake を実行できます。

`CMakePresets.json` はプロジェクト全体のビルドを保存することを目的としており、`CMakeUserPresets.json` は開発者が独自のローカル ビルドを保存することを目的としています。 スキーマはどちらのファイルも同じです。

`CMakePresets.json` と `CMakeUserPresets.json` では、ベンダー固有の情報を格納するためのベンダー マップがサポートされます。 Microsoft は、Visual Studio と Visual Studio Code に固有のオプションを含む 2 つのベンダー マップを保持しています。 ここでは、2 つの Microsoft ベンダー マップとベンダー マクロについて説明します。 構成プリセット、ビルド プリセット、テスト プリセットなど、スキーマの残りの部分に関するドキュメントについては、[CMake の公式ドキュメント](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html)を参照してください。

Visual Studio で `CMakePresets.json` を使用する方法の詳細については、「[Visual Studio で CMake プリセットを使用して構成およびビルドする](cmake-presets-vs.md)」を参照してください

Visual Studio Code で `CMakePresets.json` を使用する方法の詳細については、「[VS Code で CMake プリセットを使用して構成およびビルドする](https://github.com/microsoft/vscode-cmake-tools/blob/develop/docs/cmake-presets.md)」を参照してください

## <a name="visual-studio-settings-vendor-map"></a>Visual Studio 設定ベンダー マップ

ベンダー URI が `microsoft.com/VisualStudioSettings/CMake/<version>` である 1 つのベンダー マップは、構成プリセットごとに許可され、Visual Studio と Visual Studio Code での CMake 統合に固有のオプションが含まれています。 ベンダー マップのすべてのオプションは、Visual Studio に適用されます。 Visual Studio と Visual Studio Code の両方に適用されるオプションは、明示的にマークされています。

Visual Studio 設定ベンダー マップのすべての設定はオプションであり、`inherits` キーによって指定された構成プリセットから継承されます。 変更されたオプションのみがファイルに書き込まれます。 Visual Studio 設定ベンダー マップは、`CMakePresets.json` と `CMakeUserPresets.json` の両方でサポートされています。

Visual Studio 設定ベンダー マップのオプションは、CMake または CTest コマンド ラインの構築に影響しません。 これにより、同じ `CMakePresets.json` ファイルを使用して、Visual Studio、Visual Studio Code、およびコマンド ラインから CMake を実行できます。 これに対する例外は、`cacheRoot` および `cmakeGenerateCommand` オプションです。 これらのオプションは、Visual Studio の[既存のキャッシュを開く](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/)シナリオに固有であり、コマンド ラインから再現することはできません。

| 設定 | 説明 |
|--|--|
| `hostOS` | サポートされているオペレーティング システム (OS) の配列。 指定できる値は `Windows`、`Linux`、`macOS` です。<br><br>`hostOS` の値は、Visual Studio と Visual Studio Code によって、ターゲット システムの OS に適用されない構成プリセットを非表示にし、より優れたユーザー エクスペリエンスを提供するために使用されます。<br><br>`hostOS` が指定されていない場合、Visual Studio と Visual Studio Code には常に、すべての構成プリセットが選択するために表示されます。 このフィールドは、1 つの文字列を含む配列に相当する文字列にすることもできます<br><br>このオプションは、Visual Studio と Visual Studio Code の両方でサポートされています。 |
| `intelliSenseMode` | Visual Studio で IntelliSense 情報を計算するために使用されるモードを、`<target>-<toolset>-<arch>` という形式で指定します。 <br><br>指定できる値:<br><br> `android-clang-arm`<br> `android-clang-arm64`<br> `android-clang-x6`<br> `android-clang-x86`<br> `ios-clang-ar`<br> `ios-clang-arm64`<br> `ios-clang-x6`<br> `ios-clang-x86`<br> `linux-gcc-arm`<br> `linux-gcc-x64`<br> `linux-gcc-x86`<br> `windows-clang-arm`<br> `windows-clang-arm64`<br> `windows-clang-x64`<br> `windows-clang-x86`<br> `windows-msvc-arm`<br> `windows-msvc-arm64`<br> `windows-msvc-x64`<br> `windows-msvc-x86`<br><br>`intelliSenseMode` が指定されていない場合は、指定したコンパイラとターゲット アーキテクチャに一致する IntelliSense モードが Visual Studio で使用されます。 `intelliSenseMode` は、通常、クロスコンパイルに対して正確な IntelliSense を提供するために使用されます。<br><br>Visual Studio 2019 では、clang または clang-cl でビルドするときは、clang IntelliSense モードを明示的に指定する必要があります。 |
| `intelliSenseOptions` | 追加の IntelliSense 構成オプションのマップ。<br><br>`useCompilerDefaults`: IntelliSense でコンパイラの既定の defines と include のパスを使用するかどうかを指定する `bool`。 使用中のコンパイラで GCC スタイルの引数がサポートされていない場合に限り、`false` にする必要があります。 既定値は `true` です。<br><br>`additionalCompilerArgs`: Visual Studio で IntelliSense を制御するための追加オプションの配列。 このオプションではマクロ展開がサポートされます。 |
| `enableMicrosoftCodeAnalysis` | `cl` または `clang-cl` を使用してビルドするときに、Visual Studio 内で Microsoft コード分析を有効にする `bool`。 既定値は `false` です。 |
| `codeAnalysisRulset` | Visual Studio で Microsoft コード分析を実行するときに使用するルールセットを指定します。 これには、ルールセット ファイルのパス、または Visual Studio と共にインストールされたルールセット ファイルの名前を指定できます。 このオプションではマクロ展開がサポートされます。 |
| `disableExternalAnalysis` | Visual Studio の外部ヘッダーでコード分析を実行するかどうかを指定する `bool`。 |
| `codeAnalysisExternalRuleset` | Visual Studio で外部ヘッダーの Microsoft コード分析を実行するときに使用するルールセットを指定します。 これには、ルールセット ファイルのパス、または Visual Studio と共にインストールされたルールセット ファイルの名前を指定できます。 このオプションではマクロ展開がサポートされます。 |
| `enableClangTidyCodeAnalysis` | `clang-cl` を使用してビルドするときに、Visual Studio 内で Clang-Tidy コード分析を有効にする bool。 既定値は `false` です。 |
| `clangTidyChecks` | Visual Studio で Clang-Tidy コード分析を実行するときに、Clang-Tidy に渡される警告のコンマ区切りリスト。 ワイルドカードを使用でき、`–` プレフィックスを指定するとチェックが削除されます。 |
| `cacheRoot` | CMake キャッシュへのパスを指定します。 このディレクトリには、既存の `CMakeCache.txt` ファイルが含まれている必要があります。 このキーは、Visual Studio の "既存のキャッシュを開く" シナリオでのみサポートされています。 このオプションではマクロ展開がサポートされます。 |
| `cmakeGenerateCommand` | CMake キャッシュを生成するためのコマンドライン ツール (コマンドライン プログラムと引数で指定します。例: "gencache.bat debug")。 このコマンドは、CMake 構成が呼び出されるときに、プリセットの指定された環境でシェルから実行されます。 このキーは、Visual Studio の[既存のキャッシュを開く](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/)シナリオでのみサポートされています。 このオプションではマクロ展開がサポートされます |

## <a name="visual-studio-remote-settings-vendor-map"></a>Visual Studio リモート設定ベンダー マップ

ベンダー URI が ` microsoft.com/VisualStudioRemoteSettings/CMake/<version>` である 1 つのベンダー マップが、構成プリセットごとに許可され、Visual Studio でのリモート開発に固有のオプションが含まれています。 リモート開発とは、リモート SSH 接続または WSL で CMake を呼び出すことを意味します。 Visual Studio リモート設定ベンダー マップのどのオプションも、Visual Studio Code には適用されません。

Visual Studio リモート設定ベンダー マップのすべての設定はオプションであり、`inherits` キーによって指定された構成プリセットから継承されます。 変更されたオプションのみがファイルに書き込まれます。 Visual Studio リモート設定ベンダー マップは、`CMakePresets.json` と `CMakeUserPresets.json` の両方でサポートされています。

Visual Studio 設定ベンダー マップのオプションは、CMake または CTest コマンド ラインの構築に影響しません。 これにより、同じ `CMakePresets.json` ファイルを使用して、Visual Studio、Visual Studio Code、およびコマンド ラインから CMake を実行できます。

Visual Studio リモート設定ベンダー マップの多くのオプションは、WSL1 が対象のときは無視されます。 これは、WSL1 ツールセットではすべてのコマンドがローカルで実行され、WSL1 からローカル ソース ファイルにアクセスするために、`/mnt` フォルダーの下にマウントされている Windows ドライブに依存しているためです。 ソース ファイルのコピーは必要ありません。 WSL1 を対象とする場合に無視されるオプションは、明示的にマークされています。

| 設定 | 説明 |
|--|--|
|`sourceDir` | プロジェクトがコピーされるリモート システム上のディレクトリへのパス。 既定値は `$env{HOME}/.vs/$ms{projectDirName}` です。 このオプションではマクロ展開がサポートされます。<br><br>リモート コピーのシナリオでは、マクロ ` ${sourceDir}` によって、Windows コンピューター上のプロジェクト ソース ディレクトリではなく、リモート システム上のプロジェクト ソース ディレクトリに評価されます。 リモート コピーのシナリオには、リモート SSH 接続のターゲット設定が含まれます。 このような場合、リモート システム上のプロジェクト ソース ディレクトリは、Visual Studio リモート設定ベンダー マップの sourceDir の値によって決定されます。 対象が WSL1 の場合、このオプションは無視されます。 |
|`copySources`  | `true` の場合、Visual Studio によって Windows からリモート システムにソースがコピーされます。 自分でファイルの同期を管理する場合は、`false` に設定します。 既定値は true です。 対象が WSL1 の場合、このオプションは無視されます。 |
|`copySourcesOptions` | Windows からリモート システムへのソース コピーに関連するオプションのオブジェクト。 対象が WSL1 の場合、このオブジェクトは無視されます。<br><br>`copySourcesOptions.exclusionList`: ソース ファイルをリモート システムにコピーするときに除外するパスの一覧。 パスには、ファイルまたはディレクトリの名前、またはコピーのルートを基準とした相対パスを指定できます。 既定値は `[ ".vs", ".git", "out" ]` です。 このオプションではマクロ展開がサポートされます。<br><br>`copySourcesOptions.method`: ソース ファイルをリモート システムにコピーするために使用される方法。 指定できる値は、`rsync` と `sftp` です。 既定値は `rsync` です。<br><br>`copySourcesOptions.concurrentCopies`: ソースからリモート システムへの同期中に使用される同時コピー数。 既定値は `5` です。<br><br>`copySourcesOptions.outputVerbosity`: リモート システムへのソース コピー操作の詳細レベル。 指定できるレベルは、`Normal`、`Verbose`、`Diagnostic` です。 既定値は `Normal` です。|
|`rsyncCommandArgs` | `rsync` に渡される追加のコマンドライン引数の一覧。 既定値は `[ "-t", "--delete", "--delete-excluded" ]` です。 このオプションはマクロ展開をサポートし、WSL1 が対象のときは無視されます。 |
|`copyBuildOutput` | リモート システムから Windows にビルドの出力をコピーして戻すかどうかを指定します。 既定値は `false` です。 対象が WSL1 の場合、このオプションは無視されます。 |
|`copyOptimizations`  | ソース コピーの最適化に関連するオプションのオブジェクト。 WSL1 が対象のときは、これらのオプションは無視されます。<br><br>`copyOptimizations.maxSmallChange`: rsync の代わりに sftp を使用してコピーするファイルの最大数。 既定値は 10 です。<br><br>`copyOptimizations.useOptimizations`: 使用されるコピーの最適化を指定します。 指定できる値は、コピー最適化なし (`None`)、rsync のみの最適化 (`RsyncOnly`)、または rsync と sftp の最適化 (`RsyncAndSftp`) です。 既定値は `RsyncAndSftp` です。<br><br>`copyOptimizations.rsyncSingleDirectoryCommandArgs`: 1 つのディレクトリの内容をリモート システムにコピーするときに rsync に渡される追加のコマンド ライン引数の一覧。 既定値は `[ "-t", "-d" ]` です。 このオプションではマクロ展開がサポートされます。 |
|`copyAdditionalIncludeDirectoriesList`     | IntelliSense 用にローカルにコピーされるリモート ヘッダー ディレクトリへのパスのリスト。 このオプションではマクロ展開がサポートされます。 |
|`copyExcludeDirectoriesList` |  IntelliSense 用にローカルにコピーされないリモート ヘッダー ディレクトリへのパスのリスト。 このオプションではマクロ展開がサポートされます。 |
|`forceWSL1Toolset` | `true` の場合、Visual Studio から WSL を対象とするときは常に、WSL1 ツールセットが Visual Studio で使用されます。 WSL1 ツールセットによってすべてのコマンドがローカルで実行され、WSL からローカル ソース ファイルへのアクセスは、`/mnt` フォルダーの下にマウントされている Windows ドライブに依存して行われます。 これらのオプションは、WSL2 では速度が低下する可能性があります。 既定値は `false` です。<br><br>Visual Studio 2019 バージョン 16.10 では、WSL1 ツールセットが常に使用されます。 このオプションは、WSL2 のネイティブ サポートが利用可能になった後に関連します。 |

## <a name="remote-pre-build-and-post-build-events"></a>リモートのビルド前およびビルド後のイベント

`remotePrebuildEvent` と `remotePostbuildEvent` のオプションは、`CMakePresets.json` の導入に伴い非推奨になっています。

 ビルド前、リンク前、ビルド後のイベントを CMakeLists.txt にエンコードするには、[add_custom_command](https://cmake.org/cmake/help/latest/command/add_custom_command.html#build-events) を使用します。 これにより、Visual Studio でのビルドとコマンド ラインからのビルドで、同じ動作が保証されます。

Visual Studio に固有の動作が必要な場合は、` tasks.vs.json` でカスタム リモート タスクを追加できます。 始めるには、**ソリューション エクスプローラー** の **フォルダー ビュー** でルート `CMakeLists.txt` を右クリックし、 **[タスクの構成]** を選択します。  その後、`tasks.vs.json` ファイルに[新しいリモート タスクを追加する](https://docs.microsoft.com/cpp/build/tasks-vs-json-schema-reference-cpp#remote-properties)ことができます。

次のリモート タスクにより、リモート Linux システム上に test という名前のディレクトリが作成されます。

```json
{
      "taskLabel": "mkdir",
      "appliesTo": "CMakeLists.txt",
      "type": "remote",
      "command": "mkdir test",
      "remoteMachineName": "localhost"
  }
```

任意の `CMakeLists.txt` を右クリックし、**mkdir** オプションを選択してこのタスクを実行します。

`remoteMachineName` の値は、**接続マネージャー** での接続のホスト名と一致している必要があります。

## <a name="microsoft-vendor-macros"></a>Microsoft ベンダー マクロ

2 つの Microsoft ベンダー マップ `Visual Studio Settings` と `Visual Studio Remote Settings` により、CMake で定義されたすべてのマクロがサポートされます。 Microsoft のベンダー マップでは、CMake で定義されたすべてのマクロがサポートされます。 詳細については、[、cmake-presets のマクロ展開](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html#macro-expansion)に関するページを参照してください。 すべてのマクロと環境変数は、`cmake.exe` に渡される前に展開されます。

Visual Studio により、プレフィックス `ms` の付いたベンダー マクロがサポートされています。 Microsoft ベンダー マクロは、Microsoft ベンダー マップでのみ使用できます。 ベンダー マップに含まれないベンダー マクロを使用するプリセットは、CMake で使用できません。

|マクロ  |説明  |
|---------|---------|
|`$ms{projectDirName}`|  Visual Studio で開いているフォルダーの名前に評価されます。 このマクロは、リモート コピーのシナリオで `sourceDir` の既定値を設定するために使用されます。 このマクロは、Visual Studio Code ではサポートされていません。 代わりに `${sourceDirName}` を使用してください |

## <a name="environment-variables"></a>環境変数

|マクロ  |説明  |
|---------|---------|
| `$env{<variable-name>}`<br>`$penv{<variable-name>}`| CMake によってサポートされている、この構文を使用する環境変数を参照します。 詳細については、[、cmake-presets のマクロ展開](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html#macro-expansion)に関するページを参照してください。 |

## <a name="deprecated-macros"></a>非推奨のマクロ

CMakeSettings.json でサポートされていたいくつかのマクロは、`CMakePresets.json` の導入により非推奨になりました。

ファイル パスを作成するには、CMake でサポートされているマクロを使用してください。 これにより、Visual Studio 内とコマンド ラインで、同じ `CMakePresets.json` ファイルが動作することが保証されます。

| 非推奨のマクロ  | 推奨  |
|---------|---------|
|`${projectFile} `  | `${sourceDir}/CMakeLists.txt` |
| `${thisFile}` | ` ${sourceDir}/CMakePresets.json` |

## <a name="accepted-shell-syntax"></a>使用できるシェル構文

Microsoft ベンダー マップで Linux パスを作成するとき、`$HOME` を参照するには `$env{HOME}` 構文を使用します。