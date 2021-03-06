---
description: '詳細情報: 方法:Visual Studio C++ プロジェクトを 64 ビット、x64 プラットフォーム用に設定する'
title: '方法: Visual Studio C++ プロジェクトを 64 ビット、x64 プラットフォーム用に設定する'
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: 717f9db302f4a7bfef12d30830336b22f9fc5169
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156373"
---
# <a name="how-to-configure-visual-studio-c-projects-to-target-64-bit-x64-platforms"></a>方法: Visual Studio C++ プロジェクトを 64 ビット、x64 プラットフォーム用に設定する

Visual Studio IDE でプロジェクト構成を使用して、64 ビット、x64 プラットフォームを対象とするように C++ アプリケーションを設定できます。 Win32 プロジェクトの設定を 64 ビットのプロジェクト構成に移行することもできます。

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>64 ビットのプラットフォームを対象とするように C++ アプリケーションを設定するには

1. 構成する C++ プロジェクトを開きます。

1. そのプロジェクトのプロパティ ページが開きます。 詳しくは、「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](working-with-project-properties.md)」をご覧ください。

   > [!NOTE]
   > .NET プロジェクトの場合、 **[構成プロパティ]** ノードまたはその子ノードのいずれかが **[\<Projectname> プロパティ ページ]** ダイアログ ボックスで選択されていることを確認してください。選択されていない場合、 **[構成マネージャー]** ボタンは使用不可のままになります。

1. **[構成マネージャー]** ボタンを選択して **[構成マネージャー]** ダイアログ ボックスを開きます。

1. **[アクティブ ソリューション プラットフォーム]** ドロップダウン リストで、 **[\<New...>]** オプションを選択して **[新しいソリューション プラットフォーム]** ダイアログ ボックスを開きます。

1. **[新しいプラットフォームを入力または選択してください]** ドロップダウン リストで、64 ビット ターゲット プラットフォームを選択します。

   > [!NOTE]
   > **[新しいソリューション プラットフォーム]** ダイアログ ボックスで、 **[設定のコピー元]** オプションを使用して、既存のプロジェクト設定を新しい 64 ビットのプロジェクト構成にコピーします。

1. **[OK]** を選択します。 前の手順で選択したプラットフォームが **[構成マネージャー]** ダイアログ ボックスの **[アクティブ ソリューション プラットフォーム]** の下に表示されます。

1. **[構成マネージャー]** ダイアログ ボックスの **[閉じる]** ボタンを選択し、 **[\<Projectname> プロパティ ページ]** ダイアログ ボックスの **[OK]** ボタンを選択します。

### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>Win32 プロジェクトの設定を 64 ビットのプロジェクト構成に移行するには

- 64 ビットのプラットフォームを対象とするプロジェクトの設定中に **[新しいソリューション プラットフォーム]** ダイアログ ボックスが開いたら、 **[設定のコピー元]** ドロップダウン リストで **[Win32]** を選択します。 これらのプロジェクト設定は、プロジェクト レベルで自動的に更新されます。

  - [/MACHINE](reference/machine-specify-target-platform.md) リンカー オプションは **/MACHINE:X64** に設定されます。

  - **[出力の登録]** はオフにされます。 詳細については、「 [Linker Property Pages](reference/linker-property-pages.md)」を参照してください。

  - **[ターゲット環境]** は **/env x64** に設定されます。 詳細については、「[[MIDL] プロパティ ページ](reference/midl-property-pages.md)」を参照してください。

  - **[パラメーターの確認]** はクリアされ、既定値にリセットされます。 詳細については、「[[MIDL] プロパティ ページ](reference/midl-property-pages.md)」を参照してください。

  - **[デバッグ情報の形式]** が Win32 プロジェクト構成で **/ZI** に設定された場合、64 ビットのプロジェクト構成では **/Zi** に設定されます。 詳細については、「[/Z7、/Zi、/ZI (デバッグ情報の形式)](reference/z7-zi-zi-debug-information-format.md)」を参照してください。

  > [!NOTE]
  > プロジェクトのプロパティは、ファイル レベルでオーバーライドされる場合、いずれも変更されません。

## <a name="see-also"></a>関連項目

[64 ビットの x64 ターゲット用に C++ プロジェクトを構成する](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[64 ビット アプリケーションをデバッグする](/visualstudio/debugger/debug-64-bit-applications)
