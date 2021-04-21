---
title: CMake プリセットを使用した構成とビルド
description: CMake プリセットを使用して CMake プロジェクトを構成およびビルドするためのリファレンスです。
ms.topic: reference
ms.date: 04/13/2020
ms.openlocfilehash: ae4b57130fa70946db4cc04861431e97c5aa54e8
ms.sourcegitcommit: bac5dde649d5b0447de1d26a73365e36d74595f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2021
ms.locfileid: "107381425"
---
# <a name="configure-and-build-with-cmake-presets-in-visual-studio"></a>Visual Studio で CMake プリセットを使用して構成およびビルドする

CMake でサポートされている 2 つのファイル `CMakePresets.json` と `CMakeUserPresets.json` を使用すると、ユーザーは一般的な構成、ビルド、テストのオプションを指定し、他のユーザーと共有できます。

`CMakePresets.json` と `CMakeUserPresets.json` を使用して、Visual Studio、Visual Studio Code、継続的インテグレーション (CI) パイプライン、およびコマンド ラインから CMake を実行します。 `CMakePresets.json` はプロジェクト全体のビルドを保存することを目的としており、`CMakeUserPresets.json` は開発者が独自のローカル ビルドを保存することを目的としています。 `CMakePresets.json` は Visual Studio 2019 バージョン 16.10 以降でサポートされています。

この記事には、`CMakePresets.json` 統合 Visual Studio に関する情報が含まれています。
- `CMakePresets.json` の形式の詳細については、公式な [CMake のドキュメント](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html#id1)を参照してください。 
- Microsoft ベンダー マップとマクロ展開の詳細については、「[`CMakePresets.json` および `CMakeUserPresets.json` の Microsoft ベンダー マップ](cmake-presets-json-reference.md)」を参照してください。
- Visual Studio Code で `CMakePresets.json` を使用する方法の詳細については、[CMake プリセットを使用した構成とビルド](https://github.com/microsoft/vscode-cmake-tools/tree/develop/docs/cmake-presets.md)に関するページを参照してください。

 `CMakeSettings.json` の代替方法として、`CMakePresets.json` を使用することをお勧めします。 Visual Studio に `CMakePresets.json` と `CMakeSettings.json` の両方から同時に読み込みが行われることはありません。 Visual studio で `CMakePresets.json` 統合を有効または無効にするには、「[Visual Studio 2019 で `CMakePresets.json` を有効にする](#enable-cmakepresetsjson-integration-in-visual-studio-2019)」を参照してください。

## <a name="supported-cmake-and-cmakepresetsjson-versions"></a>サポートされている CMake と `CMakePresets.json` のバージョン

Visual Studio でサポートされているのは、`CMakePresets.json` および `CMakeUserPresets.json` ファイル バージョン 2 以降です。 ルート オブジェクトのバージョン フィールドの値を大きくすることで、ファイルのバージョンを更新できます。 例と詳細については、[`CMakePresets.json` の形式](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html#format)を参照してください。

コマンド ラインから `CMakePresets.json` (バージョン 2 以降) を使用して CMake を呼び出すときは、CMake バージョン 3.20 以降が必要です。 ただし、`CMakePresets.json` と `CMakeUserPresets.json` の読み取りと評価は Visual Studio 自体によって行われ、`--preset` オプションを使用して CMake が直接呼び出されることはありません。 つまり、Visual Studio 内部で `CMakePresets.json` を使用してビルドする場合は、CMake バージョン 3.20 以降は厳密には必要ありません。 少なくとも CMake バージョン 3.14 以降を使用することをお勧めします。

## <a name="enable-cmakepresetsjson-integration-in-visual-studio-2019"></a>Visual Studio 2019 で `CMakePresets.json` 統合を有効にする

`CMakePresets.json` 統合は、既定では Visual Studio 2019 で有効になっていません。 **[ツール]**  >  **[オプション]**  >  **[CMake]**  >  **[全般]** で、すべての CMake プロジェクトに対して有効にすることができます。

![CMake の [オプション] > [全般] で 'CMakePresets.json ' を有効にする](./media/enable-cmakepresets.png)

> [!Important]
> 統合をアクティブにするには、Visual Studio でフォルダーを閉じ、再度開きます。

`CMakePresets.json` 統合をすべての CMake プロジェクトに対して有効にするのではない場合は、開いたフォルダーのルートに `CMakePresets.json` ファイルを追加することで、`CMakePresets.json` 統合を 1 つの CMake プロジェクトに対して有効にすることができます。 統合をアクティブにするには、Visual Studio でフォルダーを閉じ、再度開く必要があります。

次の表は、`CMakeSettings.json` の代わりに `CMakePresets.json` を使用して CMake の構成とビルドを実行する場合を示しています。 構成ファイルが存在しない場合は、既定の構成プリセットが使用されます。

キー: " **[ツール]**  >  **[オプション]** で有効" は、 **[Use CMakePresets.json to drive CMake configure, build, and test]\(CMakePresets.json を使用して CMake で構成、ビルド、テストを実行する\)** が **[ツール]**  >  **[オプション]**  >  **[CMake]**  >  **[全般]** で選択されていることを意味します。

| 構成ファイル | [ツール] > [オプション] が無効 | [ツール] > [オプション] が有効 |
|--|--|--|
| 構成ファイルが存在しない | `CMakeSettings.json` | `CMakePresets.json` |
| `CMakeSettings.json` が存在する | `CMakeSettings.json` | `CMakePresets.json` |
| `CMakePresets.json` が存在する | `CMakePresets.json` | `CMakePresets.json` |
| 両方の構成ファイルが存在する | `CMakePresets.json` | `CMakePresets.json` |

## <a name="auto-configuration-and-cache-notifications"></a>自動構成とキャッシュ通知

既定では、アクティブなターゲット システムまたは構成プリセットが変更されるたびに、Visual Studio によって自動的に構成が呼び出されます。 この動作は、 **[ツール]**  >  **[オプション]**  >  **[CMake]**  >  **[全般]** で **[構成ステップを自動的に実行しない]** を選択することで変更できます。 また、 **[CMake キャッシュ通知を表示する]** をオフにすることで、すべての CMake キャッシュ通知 (金色のバー) を無効にすることができます。

## <a name="default-configure-presets"></a>既定の構成プリセット

`CMakePresets.json` または `CMakeUserPresets.json` ファイルが存在しないか、`CMakePresets.json` または `CMakeUserPresets.json` が無効な場合には、Visual Studio で以下の既定の構成プリセットが使用されます。

**Windows の場合の例**

```json
{
  "name": "windows-default",
  "displayName": "Windows x64 Debug",
  "description": "Sets Ninja generator, compilers, x64 architecture, build and install directory, debug build type",
  "generator": "Ninja",
  "binaryDir": "${sourceDir}/out/build/${presetName}",
  "architecture": {
    "value": "x64",
    "strategy": "external"
  },
  "cacheVariables": {
    "CMAKE_BUILD_TYPE": "Debug",
    "CMAKE_INSTALL_PREFIX": "${sourceDir}/out/install/${presetName}"
  },
  "vendor": {
    "microsoft.com/VisualStudioSettings/CMake/1.0": {
      "hostOS": [ "Windows" ]
    }
  }
},
```

**Linux の場合の例**

```json
{
  "name": "linux-default",
  "displayName": "Linux Debug",
  "description": "Sets Ninja generator, compilers, build and install directory, debug build type",
  "generator": "Ninja",
  "binaryDir": "${sourceDir}/out/build/${presetName}",
  "cacheVariables": {
    "CMAKE_BUILD_TYPE": "Debug",
    "CMAKE_INSTALL_PREFIX": "${sourceDir}/out/install/${presetName}"
  },
  "vendor": {
    "microsoft.com/VisualStudioSettings/CMake/1.0": {
      "hostOS": [ "Linux" ]
    },
    "microsoft.com/VisualStudioRemoteSettings/CMake/1.0": {
      "sourceDir": "$env{HOME}/.vs/$ms{projectDirName}"
   }
  }
}
```

存在しない `CMakePresets.json` ファイルを開こうとするか、変更しようとすると、既定の構成プリセットを含む `CMakePresets.json` ファイルが Visual Studio によってプロジェクトのルートに自動的に作成されます。

## <a name="configure-and-build"></a>構成とビルド

`CMakePresets.json` 統合が有効になっている場合、Visual Studio に 3 つのドロップダウンが表示されます。

![ターゲット システムのドロップダウン](./media/target-system-dropdown.png)

### <a name="select-a-target-system"></a>ターゲット システムの選択

左側のドロップダウンには、アクティブな **ターゲット システム** が示されます。 これは、プロジェクトを構成してビルドするために CMake が呼び出されるシステムです。 このドロップダウンには、ローカル コンピューター、**接続マネージャー** のすべての SSH 接続 (ホスト名別)、Visual Studio で検索できるすべての Linux 用 Windows サブシステム (WSL) のインストールが一覧表示されます。

![ターゲット システムのドロップダウン選択の例: ローカル コンピューター、SSH 接続、WSL ubuntu、WSL debian](./media/target-system-selections.png)
 
上の例では:
- **192.168.0.5** は、**接続マネージャー** に追加されたリモートの Linux システムです。
- **ubuntu2004** と **debian** は WSL のインストールです。

**[接続の管理]** を選択して **接続マネージャー** を開きます。

### <a name="select-a-configure-preset"></a>構成プリセットの選択

中央のドロップダウンには、アクティブな **構成プリセット** が示されます。 これは、プロジェクトのビルド システムを生成するために CMake が呼び出されたときに使用される `configurePreset` です。 このドロップダウンには、`CMakePresets.json` および `CMakeUserPresets.json` で定義されている非表示でない構成プリセットの和集合が一覧表示されます。

Visual Studio で、Microsoft Visual Studio 設定ベンダー マップにある `hostOS` の値が使用され、アクティブなターゲット システムに適用されない構成プリセットが非表示になります。 詳細については、「[Visual Studio 設定ベンダー マップ](cmake-presets-json-reference.md#visual-studio-settings-vendor-map)」にある表の `hostOS` のエントリを参照してください。

**[構成の管理]** を選択して、 プロジェクトのルートに配置されている `CMakePresets.json` ファイルを開きます。 `CMakePresets.json` がまだ存在しない場合は、作成されます。

### <a name="select-a-build-preset"></a>ビルド プリセットの選択

右側のドロップダウンには、アクティブな **ビルド プリセット** が示されます。 これは、プロジェクトをビルドするために CMake が呼び出されたときに使用される `buildPreset` です。 このドロップダウンには、`CMakePresets.json` および `CMakeUserPresets.json` で定義されている非表示でないビルド プリセットの和集合が一覧表示されます。
  
すべてのビルド プリセットには、関連付けられた `configurePreset` が指定されている必要があります。 アクティブな構成プリセットに適用されないビルド プリセットは、Visual Studio で非表示になります。 詳細については、「[Build Presets](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html#build-preset)」 (ビルド プリセット) を参照してください。 アクティブな構成プリセットに関連付けられているビルド プリセットがない場合、Visual Studio に既定のビルド プリセットが表示されます。 既定のビルド プリセットは、コマンド ラインから他の引数を指定せずに `cmake --build` を渡すことと同じです。

### <a name="configure"></a>構成

Visual Studio で CMake キャッシュが古くなったことが検出されると、自動的にプロジェクトの構成が試みられます。 手動で構成を呼び出すには、メイン メニューから **[プロジェクト]**  >  **[<プロジェクト名> の構成]** を選択します。 これは、コマンド ラインから `cmake --preset <configurePreset>` を実行するのと同じです。ここで、`<configurePreset>` はアクティブな構成プリセットの名前です。 自動キャッシュ生成を無効にするには、「[自動構成とキャッシュ通知](#auto-configuration-and-cache-notifications)」を参照してください。

### <a name="build"></a>Build

プロジェクト全体をビルドするには、メイン メニューから **[ビルド]**  >  **[すべてビルド]** を選択します。 これは、コマンド ラインから `cmake --build --preset <buildPreset>` を実行するのと同じです。ここで、`<buildPreset>` はアクティブなビルド プリセットの名前です。

1 つのターゲットをビルドするには、**ソリューション エクスプローラー** で **CMake ターゲット ビュー** に切り替えます。 次に、任意のターゲットを右クリックし、コンテキスト メニューの **[ビルド]** を選択します。

> [!NOTE]
> `CMakePresets.json` で指定されたターゲットのサブセットをビルドする `buildPresets.targets` オプションは、Visual Studio 2019 でサポートされていません。

## <a name="run-ctest"></a>CTest の実行

Visual Studio 2019 には、`CMakePresets.json` によってサポートされるメニュー オプションが 2 つあります。

- **[テスト]**  >  **[<プロジェクト名> に CTests を実行]** によって CTest が呼び出され、アクティブな構成プリセットとビルド プリセットに関連付けられているすべてのテストが実行されます。CTest に追加の引数は渡されません。
- **[テスト]**  >  **[<configurePreset> に関するテストの実行のプリセット]** を展開すると、アクティブな構成プリセットに関連付けられたすべてのテスト プリセットが表示されます。 1 つのテスト プリセットを選択することは、コマンド ラインから `ctest --preset <testPreset>` を実行するのと同じです。ここで、`<testPreset>` は選択したテスト プリセットの名前です。 アクティブな構成プリセットに対してテスト プリセットが定義されていない場合、このオプションは淡色表示されます。

Visual Studio 2019 でテスト エクスプローラーは `CMakePresets.json` と統合されていません。

## <a name="add-new-presets"></a>新しいプリセットの追加

Visual Studio 2019 のすべてのコマンドとプリセット テンプレートで `CMakePresets.json` が変更されます。 `CMakeUserPresets.json` を直接編集することで、ユーザー レベルの新しいプリセットを追加できます。

`CMakePresets.json` および `CMakeUserPresets.json` では、パスにスラッシュ (`/`) を使用します。

### <a name="add-new-configure-presets"></a>新しい構成プリセットの追加

`CMakePresets.json` に新しい構成プリセットを追加するには、**ソリューション エクスプローラー** の **フォルダー ビュー** で `CMakePresets.json` を右クリックし、 **[Add Configure Preset]\(構成プリセットの追加\)** を コンテキスト メニューから選択します。 構成プリセット テンプレートを選択するためのダイアログが表示されます。

![[`CMakePresets.json` への Configure Preset の追加] ダイアログ](./media/add-configure-preset-to-cmakepresets.png)

Windows システム上で構成するには、 **[Windows x64 Debug]\(Windows x64 デバッグ\)** テンプレートを選択します。 WSL およびリモートの Linux システム上で構成するには、 **[Linux Debug]\(Linux デバッグ\)** テンプレートを選択します。 `CMakePresets.json` の編集の詳細については、「[プリセットの編集](#edit-presets)」を参照してください。

選択したテンプレートが存在する場合は、それが `CMakePresets.json` に追加されます。 それ以外の場合は、そのテンプレートが新しい `CMakePresets.json` にコピーされます。

### <a name="add-new-build-presets-and-test-presets"></a>新しいビルド プリセットとテスト プリセットの追加

Visual Studio 2019 に新しいビルド プリセットとテスト プリセット用のテンプレートは用意されていません。 ビルド プリセットとテスト プリセットは、`CMakePresets.json` を直接編集することによって追加できます。 詳細については、「[Build Presets](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html#build-preset)」 (ビルド プリセット)、「[Test Presets](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html#test-preset)」 (テスト プリセット)、または [`CMakePresets.json` ファイルの例](#example-cmakepresetsjson-file)を参照してください。

## <a name="edit-presets"></a>プリセットの編集

公式な [CMake のドキュメント](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html#id1)は、構成プリセット、ビルド プリセット、テスト プリセットの編集に関する最良のリソースです。 次に示す情報は、Visual Studio 開発者に特に関連する CMake ドキュメントのサブセットです。

### <a name="select-your-compilers"></a>コンパイラの選択

C および C++ コンパイラは、`cacheVariables.CMAKE_C_COMPILER` と `cacheVariables.CMAKE_CXX_COMPILER` を使用して構成プリセットに設定できます。 これは、コマンド ラインから `-D CMAKE_C_COMPILER=<value> and -D CMAKE_CXX_COMPILER=<value>` を CMake に渡すことと同じです。 詳細については、「[CMAKE_<LANG>_COMPILER](https://cmake.org/cmake/help/latest/variable/CMAKE_LANG_COMPILER.html#cmake-lang-compiler)」を参照してください。

Visual Studio から `cl.exe` と `clang-cl.exe` を使用してビルドするには、次の例を使用します。 `clang-cl` を使用してビルドするには、Windows コンポーネント用の C++ Clang ツールがインストールされている必要があります。

**`cl.exe` でビルドする**
```json
"cacheVariables": {
  "CMAKE_BUILD_TYPE": "Debug",
  "CMAKE_INSTALL_PREFIX": "${sourceDir}/out/install/${presetName}",
  "CMAKE_C_COMPILER": "cl",
  "CMAKE_CXX_COMPILER": "cl"
},
```

**`clang` でビルドする**
```json
"cacheVariables": {
  "CMAKE_BUILD_TYPE": "Debug",
  "CMAKE_INSTALL_PREFIX": "${sourceDir}/out/install/${presetName}",
  "CMAKE_C_COMPILER": "clang-cl",
  "CMAKE_CXX_COMPILER": "clang-cl"
},

"vendor": {
  "microsoft.com/VisualStudioSettings/CMake/1.0": {
    "intelliSenseMode": "windows-clang-x64"
  }
}
```

> [!IMPORTANT]
> Visual Studio 2019 の場合、`clang` または `clang-cl` を使用してビルドするときは、Clang IntelliSense モードを明示的に指定する必要があります。

Visual Studio の外部でこれらのビルドを再現するには、「[コマンド ラインまたは継続的インテグレーション (CI) パイプラインからの CMake の実行](#run-cmake-from-the-command-line-or-a-continuous-integration-ci-pipeline)」を参照してください。

Linux 上でビルドする場合、または Visual C++ ツールセットを使用せずにビルドする場合は、`PATH` でコンパイラの名前を指定するか、コンパイラの完全なパスに評価される環境変数を指定します。 ファイルを共有可能に維持できるように、完全なパスは使用しないことをお勧めします。 GCC バージョン 8 でビルドするプリセットは次のようになります。

**GCC**
```json
"cacheVariables": {
  "CMAKE_BUILD_TYPE": "Debug",
  "CMAKE_INSTALL_PREFIX": "${sourceDir}/out/install/${presetName}",
  "CMAKE_C_COMPILER": "gcc-8",
  "CMAKE_CXX_COMPILER": "g++-8"
},
```

CMake ツールチェーン ファイルを使用してコンパイラを設定することもできます。 `cacheVariables.CMAKE_TOOLCHAIN_FILE` を使用してツールチェーン ファイルを設定できます。これは、コマンド ラインから ` -D CMAKE_TOOLCHAIN_FILE=<value>` を CMake に渡すことと同じです。 CMake のツールチェーン ファイルは、多くの場合、クロスコンパイルに使用されます。 CMake ツールチェーン ファイルの作成の詳細については、[CMake ツールチェーン](https://cmake.org/cmake/help/latest/manual/cmake-toolchains.7.html)に関するページを参照してください。

### <a name="select-your-generator"></a>ジェネレーターの選択

Windows と Linux の両方の構成プリセット テンプレートで、既定のジェネレーターとして Ninja が指定されています。 その他の一般的なジェネレーターは、Windows の場合は [Visual Studio ジェネレーター](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html?highlight=visual%20studio%20generators#visual-studio-generators)、Linux および macOS の場合は Unix Makefiles です。 `generator` オプションを使用して構成プリセットに新しいジェネレーターを指定できます。 これは、コマンド ラインから `-G` を CMake に渡すことと同じです。

Visual Studio ジェネレーターでビルドするときは、`architecture.strategy` と `toolset.strategy` を `set` に設定します。 詳細については、「[CMake generators](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html#:~:text=A%20CMake%20Generator%20is%20responsible%20for%20writing%20the,what%20native%20build%20system%20is%20to%20be%20used)」 (CMake ジェネレーター) を参照してください。

Visual Studio ジェネレーターでビルドするときは、`architecture.strategy` と `toolset.strategy` を `set` に設定します。

### <a name="select-your-configuration-type"></a>構成の種類の選択

単一構成ジェネレーターの構成の種類 (**デバッグまたはリリース**) は、`cacheVariables.CMAKE_BUILD_TYPE` を使用して設定できます。 これは、コマンド ラインから `-D CMAKE_BUILD_TYPE=<value>` を CMake に渡すことと同じです。 詳細については、「[ CMAKE_BUILD_TYPE](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html)」を参照してください。

### <a name="select-your-target-and-host-architecture-when-building-with-the-visual-c-toolset"></a>Visual C++ ツールセットを使用してビルドするときは、ターゲットとホストのアーキテクチャを選択します。

ターゲット アーキテクチャ (x64、Win32、ARM64、または ARM) は、`architecture.value` を使用して設定できます。 これは、コマンド ラインから ` -A` を CMake に渡すことと同じです。 詳細については、「[Platform Selection](https://cmake.org/cmake/help/latest/generator/Visual%20Studio%2016%202019.html#platform-selection)」 (プラットフォームの選択) を参照してください。

> [!NOTE]
> 現在、x86 用にビルドするときに、Visual Studio ジェネレーターでは Win32 の構文が、コマンド ライン ジェネレーター (Ninja など) では x86 の構文が想定されています。

ホスト アーキテクチャ (x64 または x86) とツールセットは、`toolset.value` を使用して設定できます。 これは、コマンド ラインから `-T` を CMake に渡すことと同じです。 詳細については、「[Toolset Selection](https://cmake.org/cmake/help/latest/generator/Visual%20Studio%2016%202019.html#toolset-selection)」 (ツールセットの選択) を参照してください。

`architecture.strategy` および `toolset.strategy` により、アーキテクチャとツールセットのフィールドをどのように処理するかを CMake に指示します。 `set` は CMake でそれぞれの値を設定することを意味し、`external` は CMake でそれぞれの値を設定しないことを意味します。

 Visual Studio ジェネレーターのような IDE ジェネレーターでは `set` を使用する必要があります。 Ninja のようなコマンド ライン ジェネレーターでは `external` を使用する必要があります。 これにより、CMake が呼び出される前に、Visual Studio などのベンダーで必要な環境を供給することができます。 アーキテクチャとツールセットのフィールドの詳細については、「[Configure Presets](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html#configure-preset)」 (プリセットの構成) を参照してください。

アーキテクチャのフィールドをサポートする IDE ジェネレーターの完全な一覧については、「[CMAKE_GENERATOR_PLATFORM](https://cmake.org/cmake/help/latest/variable/CMAKE_GENERATOR_PLATFORM.html)」を参照してください。 ツールセットのフィールドをサポートする IDE ジェネレーターの完全な一覧については、「[CMAKE_GENERATOR_TOOLSET](https://cmake.org/cmake/help/latest/variable/CMAKE_GENERATOR_TOOLSET.html)」を参照してください。

Ninja ジェネレーターで ARM64 を、または Visual Studio 16 2019 ジェネレーターで Win32 (x86) をターゲットにするには、以下の例を使用します。

```json
"generator": "Ninja",
"architecture": {
    "strategy": "external",
    "value": "arm64"
},

"generator": "Visual Studio 16 2019",
"architecture": {
    "strategy": "set",
     "value": "Win32"
},
```

### <a name="set-and-reference-environment-variables"></a>環境変数の設定と参照

環境マップを使用して環境変数を設定できます。 環境変数は `inherits` フィールドを通じて継承されますが、必要に応じてオーバーライドできます。 プリセットの環境は、それ独自の環境とすべての親の環境との和集合になります。 `inherits` の複数のプリセットで同じ変数に対して競合する値が提供されている場合は、`inherits` 内で先に出現するプリセットが優先されます。 別のプリセットから継承された変数は、`null` に設定することによって設定を解除できます。 構成プリセットで設定された環境変数は、`inheritConfigureEnvironment` が `false` に設定されていない限り、関連付けられたビルド プリセットおよびテスト プリセットにも自動的に反映されます。 詳細については、「[Configure Presets](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html#configure-preset)」 (プリセットの構成) を参照してください。

`$env{<variable-name>}` および `$penv{<variable-name>}` の構文を使用して環境変数を参照できます。 詳細については、「[Macro Expansion](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html#macro-expansion)」 (マクロ展開) を参照してください。

### <a name="configure-intellisense-for-a-cross-compiler"></a>クロスコンパイラ用 IntelliSense の構成

Visual Studio の既定では、指定したツールセットとターゲット アーキテクチャに一致する IntelliSense モードが使用されます。 クロスコンパイルを行う場合は、Visual Studio 設定ベンダー マップで `intelliSenseMode` オプションを指定して、正しい IntelliSense モードを手動で指定することが必要になる場合があります。 詳細については、「[Visual Studio 設定ベンダー マップ](cmake-presets-json-reference.md#visual-studio-settings-vendor-map)」にある表の `intelliSenseMode` のエントリを参照してください。

## <a name="configure-and-build-on-a-remote-system-or-the-windows-subsystem-for-linux-wsl"></a>リモート システムまたは Linux 用 Windows サブシステム (WSL) での構成とビルド

Visual Studio での `CMakePresets.json` のサポートにより、Windows、WSL、およびリモート システムで簡単にプロジェクトを構成し、ビルドすることができます。 プロジェクトを[構成してビルドする](#configure-and-build)手順は、Windows、リモート システム、WSL のいずれでも同じです。 ただし、リモート開発に固有の動作がいくつかあります。

### <a name="sourcedir-behavior-in-remote-copy-scenarios"></a>リモート コピー シナリオにおける `${sourceDir}` の動作

ローカル シナリオ (WSL1 を含む) においては、`${sourceDir}` は、Visual Studio で開かれているプロジェクト ソース ディレクトリへのパスに評価されます。 リモート コピー シナリオの場合、`${sourceDir}` は、ローカル コンピューター上のプロジェクト ソース ディレクトリではなく、ターゲット システム上のプロジェクト ソース ディレクトリに評価されます。 ターゲット システム上のプロジェクト ソース ディレクトリは、Visual Studio リモート設定ベンダー マップでの `sourceDir` の値によって決まります (既定値は `$env{HOME}/.vs/$ms{projectDirName}`)。 詳細については、「[Visual Studio 設定ベンダー マップ](cmake-presets-json-reference.md#visual-studio-settings-vendor-map)」にある表の `sourceDir` のエントリを参照してください。

### <a name="local-folder-for-remote-output"></a>リモート出力用のローカル フォルダー

リモート コピーのシナリオでは、Visual Studio リモート設定ベンダー マップで `copyBuildOutput` が `true` に設定されている場合、CMake ファイル API 応答ファイルやビルド ファイルなどの一部のリモート ファイルをコピーするために、ローカル ディレクトリが必要です。 これらのファイルは、自動的に `<local-source-directory>/out/<remote-connection-ID>/build/${presetName}` にコピーされます。

### <a name="invoke-the-same-configure-preset-on-windows-and-wsl1"></a>Windows と WSL1 で同じ構成プリセットを呼び出す

Windows と WSL1 で同じ構成プリセットを使用しようとすると、エラーが表示されます。 Windows と WSL1 の両方に Windows ファイル システムが使用されているため、Windows と WSL1 の両方のビルド ツリーに同じ出力ディレクトリ (`binaryDir`) を使用することが CMake によって試みられます。 Windows と WSL1 の両方のツールセットで同じ構成プリセットを使用する場合は、元のプリセットから継承して新しい `binaryDir` を指定する 2 番目の構成プリセットを作成します。 次の例では、Windows の場合は `windows-preset` を使用でき、WSL1 の場合は `base-preset` を使用できます。

```json
{
  "name": "windows-preset",
  "inherits": "base-preset",
  "binaryDir": "${sourceDir}/out/build/${presetName}",
  "vendor": {
    "microsoft.com/VisualStudioSettings/CMake/1.0": {
      "hostOS": "Windows"
    }
  }
}
```

> [!NOTE]
> Visual Studio 2019 でサポートされているのは、WSL1 ツールセットのみです。 この動作は、Windows と WSL の両方で構成を呼び出すと常に表示されます。

## <a name="vcpkg-integration"></a>Vcpkg の統合

vcpkg は、Windows、Linux、macOS で C および C++ ライブラリを管理するのに役立ちます。 vcpkg 統合を有効にするには、vcpkg ツールチェーン ファイル (`vcpkg.cmake`) を CMake に渡す必要があります。 詳細については、[vcpkg のドキュメント](https://github.com/microsoft/vcpkg#vcpkg-overview)を参照してください。

`CMakePresets.json` 統合が有効になっている場合、Visual Studio で vcpkg ツールチェーン ファイルが自動的に CMake に渡されることはなくなりました。 これにより、Visual Studio 固有の動作がなくなり、ビルドをコマンド ラインから確実に再現できます。

代わりに、`CMakePresets.json` で `VCPKG_ROOT` 環境変数を使用して `vcpkg.cmake` へのパスを設定します。

```json
"cacheVariables": {
   "CMAKE_TOOLCHAIN_FILE": {
      "value": "$env{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake",
       "type": "FILEPATH"
    }
 },
```

`VCPKG_ROOT` は、vcpkg のインストール先のルートに設定する必要があります。 詳細については、[vcpkg の環境変数](https://github.com/microsoft/vcpkg/blob/master/docs/users/config-environment.md)のページを参照してください。

既に CMake ツールチェーン ファイルを使用している場合に vcpkg 統合を有効にするときは、「[複数のツールチェーン ファイルの使用](https://github.com/microsoft/vcpkg/blob/master/docs/users/integration.md#using-multiple-toolchain-files)」を参照し、それらの手順に従って、vcpkg を使用するプロジェクトで外部ツールチェーン ファイルを使用します。

## <a name="variable-substitution-in-launchvsjson-and-tasksvsjson"></a>`launch.vs.json` および `tasks.vs.json` での変数置換

`launch.vs.json` および `tasks.vs.json` での変数置換が `CMakePresets.json` でサポートされています。

* アクティブな構成プリセットに設定されている環境変数は、`launch.vs.json` および `tasks.vs.json` に自動的に反映されます。 `launch.vs.json` および `tasks.vs.json` 内の個々の環境変数は、`null` に設定することによって設定を解除できます。 次の例では、`launch.vs.json` で変数 `DEBUG_LOGGING_LEVEL` を `null` に設定しています: `"env": { "DEBUG_LOGGING_LEVEL":  null }`

* `launch.vs.json` および `tasks.vs.json` で構文 `${cmake.<KEY-NAME>}` を使用して、アクティブな構成プリセットに設定されているキー値を使用できます。 たとえば、` ${cmake.binaryDir}` を使用して、アクティブな構成プリセットの出力ディレクトリを参照します。
* `launch.vs.json` および `tasks.vs.json` で構文 `${env.<VARIABLE-NAME>}` を使用して、アクティブな構成プリセットの環境マップに設定されている個々の環境変数を使用できます。

`launch.vs.json`および `task.vs.json` ファイルを、`CMakeSettings.json` 構文ではなく `CMakePresets.json` 構文を参照するように更新します。 `CMakePresets.json` がアクティブな構成ファイルであるときに古い `CMakeSettings.json` 構文を参照するマクロは、今後のリリースで非推奨とされる予定です。 たとえば、`CMakePresets.json` には `binaryDir` 構文が使用されるため、アクティブな構成プリセットの出力ディレクトリを参照するには、`${cmake.buildRoot}` ではなく `${cmake.binaryDir}` を使用します。

## <a name="troubleshooting"></a>トラブルシューティング

動作が想定どおりにならない場合に実行できる、いくつかのトラブルシューティング手順があります。

`CMakePrests.json` または `CMakeUserPresets.json` のいずれかが無効である場合には、Visual Studio は既定の動作に戻り、既定の構成プリセットのみが表示されます。 Visual Studio の IntelliSense は、これらの JSON エラーの多くをキャッチするのに役立ちますが、`inherits` または `configurePreset` で間違った名前を使用してプリセットを参照しているかどうかはわかりません。 プリセット ファイルが有効かどうかを確認するには、コマンド ラインからプロジェクト ディレクトリのルートで `cmake --list-presets` を実行します (CMake 3.20 以上が必要)。 いずれかのファイルが無効な場合は、次のエラーが表示されます。

```DOS
CMake Error: Could not read presets from
C:/Users/<user>/source/repos/<project-name>: JSON parse error
```

その他に次のようなトラブルシューティングの手順があります。
* キャッシュを削除し、プロジェクトを再構成します (**CMake: [キャッシュの削除]** と **[プロジェクト]**  >  **[<プロジェクト名> の構成]** )
* Visual Studio でフォルダーを閉じ、再度開きます ( **[ファイル]**  >  **[フォルダーを閉じる]** )
* プロジェクトのルートにある `.vs` フォルダーを削除します

問題を特定した場合、Visual Studio の右上隅にある **[フィードバックの送信]** ボタンをクリックして報告することをお勧めします。

## <a name="logging-for-remote-connections"></a>リモート接続のログを記録する

リモート システムへの接続またはファイルのコピーに問題が発生している場合は、リモート接続のログ記録を有効にすることができます。 詳細については、「[リモート接続のログを記録する](https://docs.microsoft.com/cpp/linux/connect-to-your-remote-linux-computer#logging-for-remote-connections)」を参照してください。

## <a name="enable-addresssanitizer-for-windows-and-linux"></a>Windows および Linux で AddressSanitizer を有効にする

AddressSanitizer (`ASan`) は、Windows と Linux の両方での開発向けに Visual Studio でサポートされている、C および C++ 用のランタイム メモリ エラー検出機能です。 AddressSanitizer は、`CMakeSettings.json` でオプション (`addressSanitizerEnabled`) を使用して有効にされていました。 この動作は `CMakePresets.json` でサポートされていません。
 
代わりに、必要なコンパイラとリンカーのフラグを自分で設定して、AddressSanitizer を有効または無効にします。 これにより、Visual Studio 固有の動作がなくなり、同じ `CMakePresets.json` ファイルでコマンド ラインからビルドを確実に再現できます。 次のサンプルを `CMakeLists.txt` に追加して、ターゲットに対して AddressSanitizer を有効または無効にすることができます。

```
option(ASAN_ENABLED "Build this target with AddressSanitizer" ON)

if(ASAN_ENABLED)
    if(MSVC)
        target_compile_options(<target> PUBLIC /fsanitize=address)
    else()
        target_compile_options(<target> PUBLIC -fsanitize=address <additional-options>)
        target_link_options(<target> PUBLIC -fsanitize=address)
    endif()
endif()
```

`<additional-options>` は、`"-fno-omit-frame-pointer"` のような他のコンパイル フラグです。 Linux 用 `ASan` の詳細については「[Using AddressSanitizer](https://github.com/google/sanitizers/wiki/AddressSanitizer#using-addresssanitizer)」 (AddressSanitizer の使用) を、MSVC での `ASan` の詳細については「[開発者コマンド プロンプトから AddressSanitizer を使用する](https://docs.microsoft.com/cpp/sanitizers/asan#command-prompt)」を参照してください。

追加のランタイム フラグを AddressSanitizer に渡すには、`launch.vs.json`の `ASAN_OPTIONS` フィールドを使用します。 LeakSanitizer は Visual Studio でサポートされていないため、`ASAN_OPTIONS` は、その他のランタイム オプションが指定されていない場合は既定で `detect_leaks=0` になります。

## <a name="run-cmake-from-the-command-line-or-a-continuous-integration-ci-pipeline"></a>コマンド ラインまたは継続的インテグレーション (CI) パイプラインからの CMake の実行

同じ `CMakePresets.json` および `CMakeUserPresets.json` ファイルを使用して、Visual Studio とコマンド ラインで CMake を呼び出すことができます。 [CMake](https://cmake.org/cmake/help/latest/manual/cmake.1.html) と [CTest](https://cmake.org/cmake/help/latest/manual/ctest.1.html) のドキュメントは、`--preset` での CMake と CTest の呼び出しに関する最良のリソースです。 CMake バージョン 3.20 以降が必要です。

### <a name="sourcing-the-environment-when-building-with-command-line-generators-on-windows"></a>Windows でコマンド ライン ジェネレーターを使用してビルドする場合の環境の供給

コマンド ライン ジェネレーターでビルドするとき、CMake が呼び出される前に環境を構成することは、ユーザーの責任です。 Windows で Ninja と Visual C++ ツールセットを使用してビルドする場合は、CMake を呼び出してビルド システムを生成する前に、環境を供給する必要があります。 `vcvarsall.bat` メソッドに `architecture` 引数を付けて呼び出すことで、これを行うことができます。 `architecture` には、使用するホストとターゲットのアーキテクチャを指定します。 詳細については、「[vcvarsall 構文](https://docs.microsoft.com/cpp/build/building-on-the-command-line#vcvarsall-syntax)」を参照してください。 Linux または Windows 上で Visual Studio ジェネレーターを使用してビルドする場合は、この手順を実行する必要はありません。

これは、IDE によって CMake が呼び出されたときに Visual Studio で実行される手順と同じです。 Visual Studio によってアクティブな構成プリセットが解析され、`toolset` と `architecture` で指定したホストとターゲットのアーキテクチャが取得された後、指定した環境が `vcvarsall.bat` から供給されます。 Ninja を使用して Windows コマンド ラインからビルドする場合は、この手順を自分で実行する必要があります。

`vcvarsall.bat` は、Build Tools for Visual Studio と共にインストールされます。 `vcvarsall.bat` は、既定で `C:\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\VC\Auxiliary\Build` にインストールされます。 コマンドライン ワークフローを頻繁に使用する場合は、`vcvarsall.bat` を `PATH` に追加することをお勧めします。

### <a name="example-command-line-workflow"></a>コマンドライン ワークフローの例

次のコマンドを使用すると、x64 ビルド ツールを使用して arm64 をターゲットにする CMake プロジェクトを、Ninja を使用して構成し、ビルドすることができます。 CMake バージョン 3.20 以降が必要です。 `CMakePresets.json` が配置されているディレクトリから次のコマンドを実行します。

```DOS
/path/to/vcvarsall.bat x64_arm64 
cmake --list-presets=all .
cmake --preset <configurePreset-name>
cmake --build --preset <buildPreset-name> 
```

## <a name="example-cmakepresetsjson-file"></a>`CMakePresets.json` ファイルの例

[box2d-lite](https://github.com/esweet431/box2d-lite/blob/main/CMakePresets.json) の `CMakePresets.json` ファイルに、構成プリセット、ビルド プリセット、テスト プリセットの例が含まれています。

## <a name="next-steps"></a>次の手順

Visual Studio での CMake プロジェクトの構成とデバッグについてさらに学習します。

> [!div class="nextstepaction"]
> [Visual Studio の CMake プロジェクト](cmake-projects-in-visual-studio.md)<br/><br/>
> [CMake のビルド設定をカスタマイズする](customize-cmake-settings.md)<br/><br/>
> [CMake デバッグ セッションを構成する](configure-cmake-debugging-sessions.md)<br/><br/>
> [CMake 定義済み構成リファレンス](cmake-predefined-configuration-reference.md)
>