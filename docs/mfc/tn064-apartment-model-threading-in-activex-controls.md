---
description: '詳細については、ActiveX コントロールでのテクニカルノート 64: Apartment-Model スレッド処理に関するページを参照してください。'
title: 'テクニカル ノート 64: ActiveX コントロールにおけるアパートメント モデルのスレッド処理'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
ms.openlocfilehash: 977f429dfc7be6583f7021d1837caae15fca1495
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214690"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>テクニカル ノート 64: ActiveX コントロールにおけるアパートメント モデルのスレッド処理

> [!NOTE]
> 次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

このテクニカルノートでは、ActiveX コントロールでアパートメントモデルのスレッド処理を有効にする方法について説明します。 アパートメントモデルのスレッド処理は、Visual C++ バージョン4.2 以降でのみサポートされていることに注意してください。

## <a name="what-is-apartment-model-threading"></a>Apartment-Model スレッド処理とは

アパートメントモデルは、マルチスレッドのコンテナーアプリケーション内で、ActiveX コントロールなどの埋め込みオブジェクトをサポートするためのアプローチです。 アプリケーションには複数のスレッドが存在する場合がありますが、埋め込みオブジェクトの各インスタンスは1つの "アパートメント" に割り当てられ、1つのスレッドでのみ実行されます。 つまり、コントロールのインスタンスへのすべての呼び出しは、同じスレッド上で行われます。

ただし、同じ種類のコントロールの異なるインスタンスを異なるアパートメントに割り当てることができます。 したがって、コントロールの複数のインスタンスが共通のデータ (たとえば、静的データまたはグローバルデータ) を共有している場合、この共有データへのアクセスは、クリティカルセクションなどの同期オブジェクトによって保護される必要があります。

アパートメントスレッドモデルの詳細については、「 *OLE プログラマーリファレンス*」の「[プロセスとスレッド](/windows/win32/ProcThread/processes-and-threads)」を参照してください。

## <a name="why-support-apartment-model-threading"></a>Apartment-Model スレッド処理をサポートする理由

アパートメントモデルのスレッド処理をサポートするコントロールは、アパートメントモデルもサポートするマルチスレッドのコンテナーアプリケーションで使用できます。 アパートメントモデルのスレッド処理を有効にしない場合は、コントロールを使用できるコンテナーの可能性のあるセットを制限します。

ほとんどのコントロールでは、特に共有データがほとんどまたはまったくない場合は、アパートメントモデルのスレッド処理を簡単に有効にすることができます。

## <a name="protecting-shared-data"></a>共有データの保護

コントロールで静的メンバー変数などの共有データを使用する場合、複数のスレッドが同時にデータを変更できないようにするには、そのデータへのアクセスがクリティカルセクションで保護されている必要があります。 この目的のためにクリティカルセクションを設定するには、コントロールのクラスでクラスの静的メンバー変数を宣言し `CCriticalSection` ます。 コードが `Lock` `Unlock` 共有データにアクセスするすべての場所で、このクリティカルセクションオブジェクトのおよびメンバー関数を使用します。

たとえば、すべてのインスタンスで共有される文字列を保持する必要があるコントロールクラスを考えてみます。 この文字列は、静的メンバー変数に保持し、クリティカルセクションによって保護することができます。 コントロールのクラス宣言には、次のものが含まれます。

```cpp
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

クラスの実装には、次の変数の定義が含まれます。

```cpp
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

静的メンバーへのアクセスは `_strShared` 、クリティカルセクションで保護できます。

```cpp
void CSampleCtrl::SomeMethod()
{
    _critSect.Lock();
if (_strShared.Empty())
    _strShared = "<text>";
    _critSect.Unlock();

...
}
```

## <a name="registering-an-apartment-model-aware-control"></a>アパートメントモデルに対応したコントロールの登録

アパートメントモデルのスレッド処理をサポートするコントロールは *、クラス id* InprocServer32 キーの下にあるクラス id レジストリエントリに "アパートメント" という値を持つ名前付きの値 "ThreadingModel" を追加することによって、この機能をレジストリで示す必要があり \\ ます。 このキーがコントロールに自動的に登録されるようにするには、6番目のパラメーターの *afxRegApartmentThreading* フラグをに渡し `AfxOleRegisterControlClass` ます。

```cpp
BOOL CSampleCtrl::CSampleCtrlFactory::UpdateRegistry(BOOL bRegister)
{
    if (bRegister)
    return AfxOleRegisterControlClass(
    AfxGetInstanceHandle(),
    m_clsid,
    m_lpszProgID,
    IDS_SAMPLE,
    IDB_SAMPLE,
    afxRegApartmentThreading,
    _dwSampleOleMisc,
    _tlid,
    _wVerMajor,
    _wVerMinor);

else
    return AfxOleUnregisterClass(m_clsid,
    m_lpszProgID);

}
```

コントロールプロジェクトが Visual C++ バージョン4.1 以降の ControlWizard で生成された場合、このフラグは既にコード内に存在しています。 スレッドモデルを登録するために変更は必要ありません。

以前のバージョンのコントロールウィザードによってプロジェクトが生成された場合、既存のコードには6番目のパラメーターとしてブール値が設定されます。 既存のパラメーターが TRUE の場合は、 *afxRegInsertable | afxRegApartmentThreading* に変更します。 既存のパラメーターが FALSE の場合は、 *afxRegApartmentThreading* に変更します。

コントロールがアパートメントモデルのスレッド処理の規則に従っていない場合は、このパラメーターで *afxRegApartmentThreading* を渡さないようにする必要があります。

## <a name="see-also"></a>関連項目

[番号別テクニカルノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカルノート](../mfc/technical-notes-by-category.md)
