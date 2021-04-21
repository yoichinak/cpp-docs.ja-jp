---
title: Visual Studio でターゲットの Linux システムに接続する
description: Visual Studio の C++ プロジェクト内からリモートの Linux マシンまたは Linux 用 Windows サブシステムに接続する方法です。
ms.date: 01/8/2021
ms.openlocfilehash: b906b8f0b59742eec175e620a3f8c0394d46fe84
ms.sourcegitcommit: 81bc4e45590893b4067f21716c208926d3d53c17
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2021
ms.locfileid: "107002873"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>Visual Studio でターゲットの Linux システムに接続する

::: moniker range="msvc-140"

Linux サポートは Visual Studio 2017 以降で使用できます。

::: moniker-end

::: moniker range="msvc-150"

Linux プロジェクトのターゲットは、リモート マシンとなるように構成することも、Windows Subsystem for Linux (WSL) とすることもできます。 両方のリモート マシンと WSL に対して、Visual Studio 2017 でリモート接続を設定する必要があります。

::: moniker-end

::: moniker range="msvc-160"

Linux プロジェクトのターゲットは、リモート マシンとなるように構成することも、Windows Subsystem for Linux (WSL) とすることもできます。 リモート マシンの場合は、Visual Studio でリモート接続を設定する必要があります。 WSL に接続するには、[WSL への接続](#connect-to-wsl)に関するセクションに進んでください。

::: moniker-end

::: moniker range=">=msvc-150"

リモート接続を使用する場合、Visual Studio はリモート マシンで C++ Linux プロジェクトをビルドします。 物理マシン、クラウド内の VM、WSL のいずれであるかは関係ありません。
プロジェクトをビルドするために、Visual Studio はソース コードをリモートの Linux コンピューターにコピーします。 その後、コードは Visual Studio の設定に基づいてコンパイルされます。

::: moniker-end

::: moniker range="msvc-160"

> [!NOTE]
> Visual Studio 2019 バージョン 16.5 以降でも、リモート開発のために、Linux システムへの安全な Federal Information Processing Standard (FIPS) 140-2 準拠の暗号化接続がサポートされています。 FISP 準拠の接続を使用するには、代わりに「[FIPS 準拠の安全なリモート Linux 開発のセットアップ](set-up-fips-compliant-secure-remote-linux-development.md)」のステップに従ってください。

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="set-up-the-ssh-server-on-the-remote-system"></a>リモート システム上で SSH サーバーを設定する

Linux システム上でまだ ssh が設定および実行されていない場合、次のステップに従ってインストールします。 この記事の例では、Ubuntu 18.04 LTS と OpenSSH サーバー バージョン 7.6 を使用します。 ただし、比較的最近のバージョンの OpenSSH を使用する任意のディストリビューションでも同じ手順を使用できます。

1. Linux システム上で、OpenSSH サーバーをインストールして起動します。

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. システム起動時に自動的に ssh サーバーを起動したい場合、systemctl を使用して有効にします。

   ```bash
   sudo systemctl enable ssh
   ```

## <a name="set-up-the-remote-connection"></a>リモート接続を設定する

1. Visual Studio のメニュー バーで **[ツール] > [オプション]** を選択して、 **[オプション]** ダイアログを開きます。 その後、 **[クロス プラットフォーム] > [接続マネージャー]** を選択して [接続マネージャー] ダイアログを開きます。

   まだ Visual Studio で接続を設定したことがない場合、プロジェクトを初めてビルドする際に、Visual Studio によって [接続マネージャー] ダイアログが開かれます。

1. [接続マネージャー] ダイアログで、 **[追加]** ボタンを選択して新しい接続を追加します。

   ![接続マネージャー](media/settings_connectionmanager.png)

   いずれの場合も、 **[リモート システムへの接続]** ウィンドウが表示されます。

   ![リモート システムへの接続](media/connect.png)

1. 次の情報を入力します。

   | 入力 | 説明
   | ----- | ---
   | **ホスト名**           | ターゲット デバイスの名前または IP アドレス
   | **ポート**                | SSH サービスが実行されているポート (通常は 22)
   | **ユーザー名**           | 認証するユーザー
   | **認証の種類** | パスワードと秘密キーの両方がサポートされます
   | **パスワード**            | 入力したユーザー名のパスワード
   | **秘密キー ファイル**    | ssh 接続用に作成された秘密キー ファイル
   | **パスフレーズ**          | 上で選択した秘密キーで使用されるパスフレーズ

   認証には、パスワードまたはキー ファイルとパスフレーズを使用することができます。 多くの開発シナリオではパスワード認証で十分ですが、キー ファイルはさらに安全です。 既にキーの組があるなら、それを再利用できます。 現在、Visual Studio のリモート接続では RSA と DSA キーのみがサポートされています。

1. **[接続]** ボタンを選択すると、リモート コンピューターへの接続が試行されます。

   接続が成功すると、Visual Studio ではリモートのヘッダーを使うように IntelliSense が構成されます。 詳しくは、「[リモート システムのヘッダーでの IntelliSense](configure-a-linux-project.md#remote_intellisense)」をご覧ください。

   接続に失敗した場合は、変更する必要がある入力ボックスが赤色で示されます。

   ![接続マネージャーのエラー](media/settings_connectionmanagererror.png)

   キー ファイルを認証に使う場合は、ターゲット マシンの SSH サーバーが実行され、正しく構成されていることを確認します。

   ::: moniker-end

   ::: moniker range="msvc-160"
   
## <a name="host-key-verification"></a>ホスト キーの検証

Visual Studio バージョン 16.10 以降では、Visual Studio がリモート システムに初めて接続するときに、サーバーによって提示されたホスト キーのフィンガープリントを確認するように求められます。 以前に OpenSSH のコマンドライン クライアントまたは PuTTY を使用している方は、これを熟知していることでしょう。 フィンガープリントは、サーバーを識別し、Visual Studio が意図した信頼されたサーバーに接続していることを保証するために使用されます。 

新しいリモート接続を最初に確立するとき、またはキャッシュされたフィンガープリントが変更されるたびに、サーバーによって提示されたホスト キーのフィンガープリントを、受け入れるか拒否するか確認するメッセージが表示されます。 接続マネージャーで接続を選択し、[確認] をクリックすることで、必要に応じてフィンガープリントを確認することもできます。 

以前のバージョンの Visual Studio から Visual Studio 16.10 にアップグレードすると、既存のすべてのリモート接続は新しい接続として処理されます。 ホスト キーのフィンガープリントの受け入れを求めるメッセージが接続の確立前に表示され、承認されたフィンガープリントがキャッシュされます。 

また、`update` 引数を使用して ConnectionManager.exe からリモート接続を更新することもできます。 


## <a name="supported-ssh-algorithms"></a>サポートされている SSH アルゴリズム

Visual Studio バージョン 16.9 以降では、データの暗号化とキーの交換に使用される、セキュリティで保護されていない古い SSH アルゴリズムのサポートは削除されています。 サポートされているのは以下のアルゴリズムのみです。 これらは、クライアントとサーバー間、およびサーバーとクライアント間の両方の SSH 通信でサポートされています。

|アルゴリズムの種類|サポートされているアルゴリズム|
|---|---|
| 暗号化| aes128-cbc</br>aes128-cbc</br>aes192-cbc</br>aes192-ctr</br>aes256-cbc</br>aes256-ctr|
| HMAC | hmac-sha2-256</br>hmac-sha2-256 |
| キーの交換| diffie-hellman-group14-sha256</br>diffie-hellman-group16-sha512</br>diffie-hellman-group-exchange-sha256</br>ecdh-sha2-nistp256</br>ecdh-sha2-nistp384</br>ecdh-sha2-nistp521|
|ホスト キー|ecdsa-sha2-nistp256</br>ecdsa-sha2-nistp384</br>ecdsa-sha2-nistp521</br>ssh-dss</br>ssh-rsa|

### <a name="configure-the-ssh-server"></a>SSH サーバーを構成する

最初に、背景を少々説明します。 あなたは、Visual Studio から使用する SSH アルゴリズムを選択することができません。 代わりに、SSH サーバーとの最初のハンドシェイク中にアルゴリズムが決定されます。 クライアントとサーバーのそれぞれで、サポートするアルゴリズムの一覧が提供され、その両方に共通する最初のアルゴリズムが選択されます。 暗号化、HMAC、キー交換などのために、Visual Studio とサーバーの間に共通するアルゴリズムが少なくとも 1 つあれば、接続は成功します。

OpenSSH 構成ファイル (**sshd_config**) では、既定では使用するアルゴリズムは構成されません。 アルゴリズムが指定されていない場合、SSH サーバーはセキュリティで保護された既定値を使用します。 これらの既定値は、SSH サーバーのバージョンとベンダーによって異なります。  Visual Studio でこれらの既定値がサポートされていない場合、または Visual Studio でサポートされていないアルゴリズムを使用するように SSH サーバーが構成されている場合は、次のようなエラーが発生するおそれがあります。**リモート システムに接続できませんでした。クライアントからサーバーへの共通の HMAC アルゴリズムが見つかりませんでした。**

最新の Linux ディストリビューションで既定の SSH サーバーは、Visual Studio ですぐにご利用になれます。 ただし、セキュリティで保護されていない古いアルゴリズムを使用するように構成されている、古い SSH サーバーを実行している場合は、より安全なバージョンに更新する方法が以下に説明されています。

次の例では、SSH サーバーはセキュリティで保護されていない `hmac-sha1` アルゴリズムを使用しています。これは、Visual Studio 16.9 ではサポートされていません。 SSH サーバーで OpenSSH を使用している場合は、次に示すように `/etc/ssh/sshd_config` ファイルを編集して、より安全なアルゴリズムを有効にすることができます。 その他の SSH サーバーの構成方法については、サーバーのドキュメントを参照してください。

最初に、サーバーで使用されているアルゴリズムのセットに、Visual Studio でサポートされているアルゴリズムが含まれていることを確認します。 リモート マシンで次のコマンドを実行すると、サーバーでサポートされているアルゴリズムが一覧表示されます。

```bash
$ ssh -Q cipher; ssh -Q mac; ssh -Q kex; ssh -Q key
```

次のような出力が生成されます。

```bash
3des-cbc
aes128-cbc
aes192-cbc
aes256-cbc
...
ecdsa-sha2-nistp521-cert-v01@openssh.com
sk-ecdsa-sha2-nistp256-cert-v01@openssh.com
```

この出力には、SSH サーバーでサポートされているすべての暗号化、HMAC、キー交換、ホスト キー アルゴリズムが一覧表示されます。 この一覧に、Visual Studio でサポートされているアルゴリズムが含まれていない場合は、先に進む前に SSH サーバーをアップグレードする必要があります。

リモート マシンで `/etc/ssh/sshd_config` を編集すると、Visual Studio でサポートされているアルゴリズムを有効にすることができます。 次の例は、さまざまな種類のアルゴリズムをその構成ファイルに追加する方法を示しています。

これらの例は、`/etc/ssh/sshd_config` 内の任意の場所に追加できます。 それらが確実に独自の行にあるようにします。

ファイルを編集したら、SSH サーバーを再起動 (Ubuntu の `sudo service ssh restart`) し、Visual Studio からもう一度接続を試みます。

#### <a name="cipher--example"></a>暗号の例

追加: `Ciphers <algorithms to enable>`  
例: `Ciphers aes128-cbc,aes256-cbc`

#### <a name="hmac-example"></a>HMAC の例

追加: `MACs <algorithms to enable>`  
例: `MACs hmac-sha2-256,hmac-sha2-512`

#### <a name="key-exchange-example"></a>キー交換の例

追加: `KexAlgorithms <algorithms to enable>`  
例: `KexAlgorithms ecdh-sha2-nistp256,ecdh-sha2-nistp384`

#### <a name="host-key-example"></a>ホスト キーの例

追加: `HostKeyAlgorithms <algorithms to enable>`  
例: `HostKeyAlgorithms ssh-dss,ssh-rsa`

## <a name="logging-for-remote-connections"></a>リモート接続のログを記録する

   ログを有効にして、接続の問題のトラブルシューティングに役立てることができます。 メニュー バーで、**[ツール] > [オプション]** の順に選択します。 **[オプション]** ダイアログで、**[クロス プラットフォーム] > [ログ]** を選択します。

   ![リモート ログ記録](media/remote-logging-vs2019.png)

   ログには、接続、リモート マシンに送信されたすべてのコマンド (そのテキスト、終了コード、実行時間)、および Visual Studio からシェルへのすべての出力が含まれます。 ログ記録は、Visual Studio でのすべてのクロスプラットフォーム CMake プロジェクトまたは MSBuild ベースの Linux プロジェクトで機能します。

   ファイルまたは出力ウィンドウの **[クロス プラットフォームのログ]** ペインに送られるように、出力を構成できます。 MSBuild ベースの Linux プロジェクトの場合、リモート マシンに送信された MSBuild コマンドは、プロセス外で出力されるため、**[出力ウィンドウ]** にはルーティングされません。 代わりに、"msbuild_" というプレフィックスが付いたファイルに記録されます。

## <a name="command-line-utility-for-the-connection-manager"></a>接続マネージャーのコマンドライン ユーティリティ  

**Visual Studio 2019 バージョン 16.5 以降**:ConnectionManager.exe は、Visual Studio 外でのリモート開発の接続を管理するためのコマンドライン ユーティリティです。 これは、新しい開発マシンをプロビジョニングするなどのタスクに役立ちます。 または、これを利用して Visual Studio で継続的インテグレーションを設定することもできます。 ConnectionManager コマンドの例とすべてのリファレンスについては、「[ConnectionManager リファレンス](connectionmanager-reference.md)」を参照してください。  

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="tcp-port-forwarding"></a>TCP ポート フォワーディング

Visual Studio の Linux サポートは、TCP ポート フォワーディングに依存しています。 リモート システムで TCP ポート フォワーディングが無効になっている場合、**Rsync** と **gdbserver** が影響を受けます。 お客様がこの依存関係の影響を受けている場合は、Developer Community でこちらの[提案チケット](https://developercommunity2.visualstudio.com/t/shDonshshtsh-shrelysh-s/840265?space=62)に賛成票を投じることができます。

rsync は、MSBuild ベースの Linux プロジェクトと CMake プロジェクトの両方で使用され、[IntelliSense で使用するヘッダーをリモート システムから Windows にコピーします](configure-a-linux-project.md#remote_intellisense)。 TCP ポート フォワーディングを有効にできない場合は、リモート ヘッダーの自動ダウンロードを無効にします。 無効にするには、**[ツール] > [オプション]、[クロス プラットフォーム] > [接続マネージャー] > [リモート ヘッダー IntelliSense マネージャー]** の順に移動します。 リモート システムで TCP ポート フォワーディングが有効になっていない場合、IntelliSense のリモート ヘッダーのダウンロードが開始されると、次のエラーが表示されます。

![ヘッダー エラー](media/port-forwarding-headers-error.png)

rsync は、ソース ファイルをリモート システムにコピーするために、Visual Studio の CMake サポートでも使用されます。 TCP ポート フォワーディングを有効にできない場合は、リモート コピー ソース メソッドとして sftp を使用できます。 sftp は rsync よりも低速なことが多いですが、TCP ポート フォワーディングとの依存関係がありません。 [CMake 設定エディター](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects)で、**remoteCopySourcesMethod** プロパティを使用してリモート コピー ソース メソッドを管理できます。 リモート システムで TCP ポート フォワーディングが無効になっている場合は、最初に rsync が呼び出されたときに CMake 出力ウィンドウにエラーが表示されます。

![Rsync エラー](media/port-forwarding-copy-error.png)

gdbserver は、埋め込みデバイスでのデバッグに使用できます。 TCP ポート フォワーディングを有効にできない場合は、すべてのリモート デバッグ シナリオで gdb を使用する必要があります。 リモート システム上のプロジェクトをデバッグする場合、既定で Gdb が使用されます。

## <a name="connect-to-wsl"></a>WSL に接続する

::: moniker-end

::: moniker range="msvc-150"

Visual Studio 2017 では、リモート Linux マシンに使用するのと同じ手順を使用して WSL に接続できます。 **ホスト名** には **localhost** を使います。

::: moniker-end

::: moniker range="msvc-160"

Visual Studio 2019 バージョン 16.1 では、C++ を [Windows Subsystem for Linux (WSL)](/windows/wsl/about) とともに使用するためのネイティブ サポートが追加されています。 これは、ローカルの WSL インストールで直接ビルドおよびデバッグできることを意味します。 リモート接続を追加したり、SSH を構成したりする必要がなくなりました。 詳細については、こちらの [WSL をインストールする方法](/windows/wsl/install-win10)の説明をご覧ください。

WSL インストールを Visual Studio で動作するように構成するには、gcc または clang、gdb、make、ninja-build (Visual Studio 2019 バージョン 16.6 以降を使用する CMake プロジェクトにのみ必要)、rsync、および zip をインストールする必要があります。 次のコマンドを使うことで、apt が使われるディストリビューションにこれらをインストールできます。これによって g++ コンパイラもインストールされます。

```bash
sudo apt install g++ gdb make ninja-build rsync zip
```

詳細については、「[Linux ワークロードのダウンロード、インストール、セットアップ](download-install-and-setup-the-linux-development-workload.md)」をご覧ください。

WSL 用の MSBuild プロジェクトを構成するには、「[Linux プロジェクトを構成する](configure-a-linux-project.md)」を参照してください。 WSL 用の CMake プロジェクトを構成するには、[Linux CMake プロジェクトの構成](cmake-linux-project.md)に関する記事を参照してください。 WSL を使用するシンプルなコンソール アプリケーションを作成するための詳細な手順については、入門のブログ記事「[C++ with Visual Studio 2019 and the Windows Subsystem for Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/)」 (C++ と Visual Studio 2019 および Windows Subsystem for Linux (WSL)) をご覧ください。

::: moniker-end

## <a name="see-also"></a>参照

[Linux プロジェクトを構成する](configure-a-linux-project.md)\
[Linux CMake プロジェクトを構成する](cmake-linux-project.md)\
[Linux プロジェクトの配置、実行、デバッグ](deploy-run-and-debug-your-linux-project.md)\
[CMake デバッグ セッションを構成する](../build/configure-cmake-debugging-sessions.md)
