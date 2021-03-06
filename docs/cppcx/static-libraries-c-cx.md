---
description: '詳細情報: スタティックライブラリ (C++/CX)'
title: スタティック ライブラリ (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 0e8a0100e2822719e4105ed4e9b1029a4ff488da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341933"
---
# <a name="static-libraries-ccx"></a>スタティック ライブラリ (C++/CX)

ユニバーサル Windows プラットフォーム (UWP) アプリで使用されるスタティックライブラリには、STL 型を含む ISO 標準の C++ コードと、Windows ランタイム app プラットフォームから除外されていない Win32 Api の呼び出しを含めることができます。 スタティックライブラリは Windows ランタイムコンポーネントを使用し、特定の制限がある Windows ランタイムコンポーネントを作成する場合があります。

## <a name="creating-static-libraries"></a>スタティック ライブラリの作成

新しいプロジェクトを作成する手順は、インストールされている Visual Studio のバージョンによって異なります。 優先するバージョンの Visual Studio のドキュメントを表示するには、 **[バージョン]** セレクター コントロールを使用します。 このページの目次の一番上にあります。

::: moniker range="msvc-160"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>Visual Studio 2019 で UWP スタティックライブラリを作成するには

1. メニュー バーで、 **[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択して、 **[新しいプロジェクトの作成]** ダイアログ ボックスを開きます。

1. ダイアログの上部で、[  **言語** ] を [ **C++**] に設定し、[ **プラットフォーム** ] を [ **Windows**] に設定し、[ **プロジェクトの種類** ] を [ **UWP**] に設定します。

1. フィルター処理されたプロジェクトの種類の一覧から [ **スタティックライブラリ (ユニバーサル Windows-C++/cx)** ] を選択し、[ **次へ**] を選択します。 次のページで、プロジェクトに名前を付け、必要に応じてプロジェクトの場所を指定します。

1. **[作成]** ボタンをクリックしてプロジェクトを作成します。

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>Visual Studio 2017 または Visual Studio 2015 で UWP スタティックライブラリを作成するには

1. メニュー バーで、 **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。 [   >  **Windows universal** Visual C++ [**スタティックライブラリ (ユニバーサル Windows)**] を選択します。

1. **ソリューション エクスプローラー** で、プロジェクトのショートカット メニューを開き、 **[プロパティ]** をクリックします。 [**プロパティ**] ダイアログボックスの [**構成プロパティ**] [  >  **C/c + +** ] ページで、[**使用 Windows ランタイム拡張** **] を [はい] (/ZW)** に設定します。

::: moniker-end

新しいスタティックライブラリをコンパイルするときに、UWP アプリに対して除外されている Win32 API を呼び出すと、コンパイラによってエラー C3861 "識別子が見つかりません" が発生します。 Windows ランタイムでサポートされている別の方法を探すには、「 [UWP アプリの Windows api に代わる](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)方法」を参照してください。

UWP アプリソリューションに C++ スタティックライブラリプロジェクトを追加する場合、UWP サポートプロパティが **[はい]** に設定されるように、ライブラリプロジェクトのプロパティ設定を更新することが必要になる場合があります。 この設定がないと、コードはビルドおよびリンクされますが、Microsoft Store のアプリを検証しようとするとエラーが発生します。 スタティック ライブラリは、そのライブラリを利用するプロジェクトと同じコンパイラ設定でコンパイルする必要があります。

`ref` パブリック クラス、パブリック インターフェイス クラス、またはパブリック値クラスを作成するスタティック ライブラリを使用すると、リンクは次の警告を出します。

> **警告 LNK4264:** /ZW でコンパイルされたオブジェクトファイルをスタティックライブラリにアーカイブしています。Windows ランタイム型を作成する場合は、Windows ランタイムメタデータを含むスタティックライブラリとリンクすることは推奨されません。

スタティックライブラリがライブラリ自体の外部で使用される Windows ランタイムコンポーネントを生成していない場合にのみ、警告を無視しても問題ありません。 ライブラリが、自らが定義したコンポーネントを利用していない場合、パブリック メタデータに型情報が含まれている状況でも、リンカーは実装を最適化できます。 このことは、スタティック ライブラリ内のパブリック コンポーネントはコンパイルされるが、実行時にアクティブにならないことを意味します。 このため、他のコンポーネントまたはアプリによる使用を目的とした Windows ランタイムコンポーネントは、ダイナミックリンクライブラリ (DLL) に実装する必要があります。

## <a name="see-also"></a>関連項目

[スレッド処理とマーシャリング](../cppcx/threading-and-marshaling-c-cx.md)
