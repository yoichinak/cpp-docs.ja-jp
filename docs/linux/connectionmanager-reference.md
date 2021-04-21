---
title: ConnectionManager リファレンス
description: コマンドライン ツールからリモート SSH 接続を管理する方法。
ms.date: 10/7/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 88b072bfe9415ba83b88ad9320e24729c54440ad
ms.sourcegitcommit: 81bc4e45590893b4067f21716c208926d3d53c17
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2021
ms.locfileid: "107002860"
---
# <a name="connectionmanager-reference"></a>ConnectionManager リファレンス

::: moniker range="<=msvc-150"

ConnectionManager.exe は、Visual Studio 2019 バージョン 16.5 以降で使用できます。

::: moniker-end

::: moniker range="msvc-160"

ConnectionManager.exe は、Visual Studio 外でのリモート開発の接続を管理するためのコマンドライン ユーティリティです。 これは、新しい開発マシンをプロビジョニングするなどのタスクに役立ちます。 または、これを利用して Visual Studio で継続的インテグレーションを設定することもできます。 これは、[開発者コマンド プロンプト] ウィンドウで使用することができます。 開発者コマンド プロンプトの詳細については、「[コマンドラインから C++ Microsoft ツールセットを使用する](../build/building-on-the-command-line.md)」を参照してください。

ConnectionManager.exe は、Visual Studio 2019 バージョン 16.5 以降で使用できます。 これは、Visual Studio インストーラーの **[C++ による Linux 開発]** ワークロードに含まれています。 インストーラーで **接続マネージャー** を選択した場合も、自動的にインストールされます。 これは、*%VCIDEInstallDir%\\Linux\\bin\\ConnectionManagerExe\\ConnectionManager.exe* にインストールされます。

ConnectionManager.exe の機能は Visual Studio でも利用することができます。 IDE 内でリモート開発の接続を管理するには、メニュー バーで **[ツール]**  >  **[オプション]** を選択して、[オプション] ダイアログを開きます。 [オプション] ダイアログで、 **[クロス プラットフォーム]**  >  **[接続マネージャー]** を選択します。

## <a name="syntax"></a>構文

> **`ConnectionManager.exe`** *command* \[*arguments*] \[*options*]

### <a name="commands-and-arguments"></a>コマンドと引数

- **`add`** *user\@host* \[ **`--port`** *port*] \[ **`--password`** *password*] \[ **`--privatekey`** *privatekey_file*]

  新しい接続を認証し、追加します。 既定では、ポート 22 とパスワード認証を使用します。 (パスワードを入力するように求められます。) **-`-password`** および **`--privatekey`** の両方を使用して、秘密キーのパスワードを指定します。

- **`remove`** \[*connection_id* \| *user\@host* \[ **`--port`** *port*]]

  接続を削除します。 引数が指定されていない場合、削除する接続を指定するよう求められます。
  
- **`modify`** \[*default* \| *connection_id* \| *user\@host* \[ **`--port`** *port*]] \[ **`--property`** *key=value*]

  接続のプロパティを定義または変更します。\
  *value* が空の場合、プロパティ *key* は削除されます。\
  認証が失敗した場合、変更は行われません。\
  接続が指定されていない場合 (上記の *default* で意図されているもの)、ユーザーの既定のリモート接続が使用されます。

- **`remove-all`**

  すべての保存されている接続を削除します。
  
- **`clean`**

  存在しなくなった接続のヘッダー キャッシュを削除します。 

- **`list`** \[**`--properties`**]

  保存されているすべての接続の情報、ID、およびプロパティを表示します。 

- **`help`**

  ヘルプ画面を表示します。

- **`version`**

  バージョン情報を表示します。
  
- **`update`** \[*default* \| *all* \| *connection_id* \| *user\@host* \[ **`--port`** *port*]] \[ **`--previous`** ] [ **`--fingerprint`** ]

  Visual Studio 16.10 で追加されました。 指定した接続のホスト キーのフィンガープリントを更新します。 

### <a name="options"></a>オプション

- **`-q`**, **`--quiet`**

  `stdout` または `stderr` への出力を抑止します。

- **`--no-prompt`**

  適切な場合、プロンプトを表示せず失敗します。

- **`--no-verify`**

  認証せずに接続を追加または変更します。

- **`--file`** *filename*

  指定された *filename* から接続情報を読み取ります。

- **`--no-telemetry`**

  利用状況データの Microsoft への送信を無効にします。 **`--no-telemetry`** フラグが渡されない限り、利用状況データは収集されて Microsoft に送信されます。  

- **`-n`**, **`--dry-run`**

  コマンドのドライ ランを実行します。
 
- **`--p`**

  **`--password`** と同じ。

- **`-i`**

  **`--privatekey`** と同じ。
  
- **`--previous`**

  接続が以前のバージョンの接続マネージャーから読み取られ、更新され、新しいバージョンに書き込まれることを示します。 
  
- **`--fingerprint`**

  サーバーによって提示されたホスト キーのフィンガープリント。 接続のフィンガープリントを表示するには、このオプションを **`list`** と共に使用します。

## <a name="examples"></a>例

このコマンドは、localhost で "user" という名前のユーザーの接続を追加します。 この接続では、*%USERPROFILE%\.ssh\id_rsa* にあるキー ファイルを認証に使用します。

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

このコマンドは、接続のリストから ID 1975957870 の接続を削除します。

```cmd
ConnectionManager.exe remove 1975957870
```

このコマンドを使用すると、接続 ID が 21212121 である接続について、シェルの選択がオーバーライドされます。 サポートされるシェルは **`sh, csh, bash, tcsh, ksh, zsh, dash`** です。 Linux システム上で見つかったシェルがサポートされていない場合は、フォールバックして、すべてのコマンドに **`sh`** を明示的に使用します。

```cmd
ConnectionManager.exe modify 21212121 --property shell=csh
```

## <a name="see-also"></a>関連項目

[Visual Studio でターゲットの Linux システムに接続する](connect-to-your-remote-linux-computer.md)

::: moniker-end
