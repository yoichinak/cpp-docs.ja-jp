---
description: 詳細については、WRL とメディアファンデーションを使用した UWP アプリの作成に関するページを参照してください。
title: 'チュートリアル: WRL および Media Foundation を使用した UWP アプリの作成'
ms.date: 04/15/2021
ms.topic: reference
ms.openlocfilehash: 823d5d53da5d67f79cb4f79e24560d6d581772c3
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539276"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>チュートリアル: WRL および Media Foundation を使用した UWP アプリの作成

> [!NOTE]
> 新しい UWP アプリとコンポーネントの場合は、Windows ランタイム Api 向けの新しい標準 C++ 17 言語プロジェクションである [c++/WinRT](/windows/uwp/cpp-and-winrt-apis/)を使用することをお勧めします。 C++/WinRT は、Windows 10 SDK のバージョン 1803 以降で使用できます。 C++/WinRT は、全体がヘッダー ファイル内に実装され、最新の Windows API に対する最高級のアクセスを提供するように設計されています。

このチュートリアルでは、Windows ランタイム C++ テンプレートライブラリ (WRL) を使用して、 [Microsoft メディアファンデーション](/windows/win32/medfound/microsoft-media-foundation-sdk)を使用するユニバーサル WINDOWS プラットフォーム (UWP) アプリを作成する方法について説明します。

この例では、カスタムメディアファンデーション変換を作成します。 Web カメラからキャプチャされたイメージにグレースケール効果を適用します。 アプリでは、カスタム変換の定義のために C++ を使用し、キャプチャしたイメージを変換するコンポーネントを使用するために C# を使用しています。

> [!NOTE]
> C# の代わりに、JavaScript、Visual Basic、または C++ でカスタム変換コンポーネントを使用することもできます。

通常、C++/CX を使用して Windows ランタイムコンポーネントを作成できます。 ただし、場合によっては、WRL を使用する必要があります。 たとえば、Microsoft メディアファンデーション用のメディア拡張機能を作成する場合は、COM インターフェイスと Windows ランタイムインターフェイスの両方を実装するコンポーネントを作成する必要があります。 C++/CX では Windows ランタイムオブジェクトの作成のみが可能なため、メディア拡張機能を作成するには、WRL を使用する必要があります。 これは、COM インターフェイスと Windows ランタイムインターフェイスの両方の実装を可能にするためです。

> [!NOTE]
> このコード例は長いですが、役に立つメディア ファンデーション変換を作成するために必要な最低限のコードを示しています。 独自のカスタム変換を作成するための出発点として、このコード例を使用することができます。 この例は、メディア拡張機能の [サンプル](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples)で、メディア拡張機能を使用してビデオに効果を適用し、ビデオをデコードし、メディアストリームを生成するスキームハンドラーを作成しています。

## <a name="prerequisites"></a>前提条件

- Visual Studio 2017 以降では、UWP サポートはオプションのコンポーネントです。 インストールするには、Windows の [スタート] メニューから Visual Studio インストーラーを開き、使用している Visual Studio のバージョンを確認します。 [ **変更** ] を選択し、[ **ユニバーサル Windows プラットフォームの開発** ] タイルがオンになっていることを確認します。 [ **オプションのコンポーネント** ] で、visual studio 2017 の場合は「 **C++ tools for uwp (v141)** 」、visual studio 2019 の場合は「 **c++ tools for uwp (v142)** 」を確認します。 次に、使用する Windows SDK のバージョンを確認します。

- [Windows ランタイム](/uwp/api/)の使用経験があります。

- COM の使用経験。

- Web カメラ。

## <a name="key-points"></a>重要なポイント

- カスタム メディア ファンデーション コンポーネントを作成するには、Microsoft インターフェイス定義言語 (MIDL) の定義ファイルを使用してインターフェイスを定義し、そのインターフェイスを実装して、他のコンポーネントからアクティブ化できるようにします。

- 属性と属性、および `namespace` `runtimeclass` `NTDDI_WIN8` [バージョン](/windows/win32/Midl/version) 属性値は、wrl を使用するメディアファンデーションコンポーネントの MIDL 定義の重要な部分です。

- [`Microsoft::WRL::RuntimeClass`](runtimeclass-class.md) は、カスタムメディアファンデーションコンポーネントの基本クラスです。 テンプレート引数として指定されている [ `Microsoft::WRL::RuntimeClassType::WinRtClassicComMix]` (runtimeclasstype-enumeration.md) 列挙値は、クラスを Windows ランタイムクラスとして、また従来の COM ランタイムクラスとして使用するようにマークします。

- マクロは、 [`InspectableClass`](inspectableclass-macro.md) 参照カウントやメソッドなどの基本的な COM 機能を実装 `QueryInterface` し、ランタイムクラス名と信頼レベルを設定します。

- クラスを使用し [`Microsoft::WRL::Module`](module-class.md) て、、、などの DLL エントリポイント関数を実装し [`DllGetActivationFactory`](/windows/win32/winrt/functions) [`DllCanUnloadNow`](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow) [`DllGetClassObject`](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject) ます。

- コンポーネント DLL をにリンク *`runtimeobject.lib`* します。 また [`/WINMD`](../../cppcx/compiler-and-linker-options-c-cx.md) 、リンカーラインでを指定して、Windows メタデータを生成します。

- プロジェクト参照を使用して、WRL コンポーネントに UWP アプリからアクセスできるようにします。

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>WRL を使用してメディアファンデーショングレースケール変換コンポーネントを作成するには

1. Visual Studio で、空の **ソリューション** プロジェクトを作成します。 プロジェクトに *MediaCapture* のように名前を指定します。

1. **DLL (ユニバーサル Windows)** プロジェクトをソリューションに追加します。 プロジェクトに「 *グレースケール変換*」などの名前を指定します。

1. **MIDL ファイル (.idl)** ファイルをプロジェクトに追加します。 ファイルにという名前を指定します。たとえば、のように指定 *`GrayscaleTransform.idl`* します。

1. 次のコードを、「グレースケール変換」に追加します。

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. 次のコードを使用して、の内容を置き換え *`pch.h`* ます。

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. 新しいヘッダーファイルをプロジェクトに追加し、という名前 *`BufferLock.h`* を付けて、内容を次のコードに置き換えます。

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. *`GrayscaleTransform.h`* この例では、は使用されません。 このファイルは必要に応じてプロジェクトから削除できます。

1. 次のコードを使用して、の内容を置き換え *`GrayscaleTransform.cpp`* ます。

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. 新しいモジュール定義ファイルをプロジェクトに追加し、という名前 *`GrayscaleTransform.def`* を指定して、次のコードを追加します。

   ```idl
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. 次のコードを使用して、の内容を置き換え `dllmain.cpp` ます。

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. プロジェクトの [ **プロパティページ** ] ダイアログボックスで、次の **リンカー** プロパティを設定します。

   1. [ **入力**] の [ **モジュール定義ファイル**] で、を指定し `GrayScaleTransform.def` ます。

   1. また、[ **入力**] で、、、およびを [ `runtimeobject.lib` 追加の `mfuuid.lib` `mfplat.lib` **依存関係** ] プロパティに追加します。

   1. [ **Windows メタデータ**] で、[ **windows メタデータの生成** **] を [はい] (/WINMD)** に設定します。

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>カスタムメディアファンデーションコンポーネントの WRL を C# アプリから使用するには

1. 新しい C# の [ **空のアプリ (ユニバーサル Windows)** ] プロジェクトをソリューションに追加し `MediaCapture` ます。 プロジェクトに *MediaCapture* のように名前を指定します。

1. **MediaCapture** プロジェクトで、プロジェクトへの参照を追加し `GrayscaleTransform` ます。 詳細については、「 [方法: 参照マネージャーを使用して参照を追加または削除](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)する」を参照してください。

1. の [ *`Package.appxmanifest`* **機能** ] タブで、[ **マイク** と **web カメラ**] を選択します。 Web カメラから写真をキャプチャするために、両方の機能が必要です。

1. で *`MainPage.xaml`* 、次のコードをルート要素に追加し [`Grid`](/uwp/api/windows.ui.xaml.controls.grid) ます。

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. 次のコードを使用して、の内容を置き換え `MainPage.xaml.cs` ます。

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

を次の図に示し `MediaCapture app` ます。

![写真をキャプチャする MediaCapture アプリのスクリーンショット。](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>次の手順

例では、既定の Web カメラから写真を 1 枚ずつキャプチャする方法を示します。 [メディア拡張機能のサンプル](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples)ではさらに多くのことができます。 ここでは、web カメラデバイスを列挙し、ローカルスキームハンドラーを使用する方法について説明します。 このサンプルでは、個々の写真とビデオのストリームで動作する他のメディア効果も示しています。

## <a name="see-also"></a>関連項目

[Windows ランタイム C++ テンプレートライブラリ (WRL)](windows-runtime-cpp-template-library-wrl.md)\
[Microsoft メディア ファンデーション](/windows/win32/medfound/microsoft-media-foundation-sdk)
