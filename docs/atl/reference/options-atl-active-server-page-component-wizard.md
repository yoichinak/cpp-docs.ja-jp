---
description: '詳細情報: オプション、ATL Active Server ページコンポーネントウィザード'
title: オプション、ATL Active Server Page コンポーネント ウィザード
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.options
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
ms.openlocfilehash: 6d41b5cb43aa9f0445e73bbe148a2a753e374a15
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139023"
---
# <a name="options-atl-active-server-page-component-wizard"></a>オプション、ATL Active Server Page コンポーネント ウィザード

ATL Active Server ページコンポーネントウィザードのこのページを使用すると、オブジェクトの効率とエラーのサポートを向上させるための設計を行うことができます。

ATL プロジェクトや ATL COM クラスの詳細については、「[ATL COM デスクトップ コンポーネント](../../atl/atl-com-desktop-components.md)」を参照してください。

- **スレッド モデル**

   スレッドを管理するためのメソッドを示します。 既定では、プロジェクトは **アパートメント** スレッド処理を使用します。

   詳細については、「[プロジェクトのスレッド モデルの指定 (ATL)](../../atl/specifying-the-threading-model-for-a-project-atl.md)」を参照してください。

   |オプション|説明|
   |------------|-----------------|
   |**Single**|オブジェクトが単一のスレッドモデルを使用することを指定します。 単一のスレッドモデルでは、オブジェクトは常にプライマリ COM スレッドで実行されます。 詳細については、「 [シングルスレッドアパートメント](/windows/win32/com/single-threaded-apartments) と [InprocServer32](/windows/win32/com/inprocserver32) 」を参照してください。|
   |**スレッド**|オブジェクトがアパートメントスレッド処理を使用することを指定します。 シングルスレッドアパートメントに相当します。 アパートメントスレッドコンポーネントの各オブジェクトには、オブジェクトの有効期間中、そのスレッドのアパートメントが割り当てられます。ただし、複数のオブジェクトに対して複数のスレッドを使用できます。 各アパートメントは特定のスレッドに関連付けられており、Windows メッセージポンプ (既定値) があります。<br /><br /> 詳細については [、「シングルスレッドアパートメント](/windows/win32/com/single-threaded-apartments) 」を参照してください。|
   |**両方**|オブジェクトが作成されるスレッドの種類に応じて、アパートメントスレッドまたはフリースレッド処理のいずれかを使用できることを指定します。|
   |**Free**|オブジェクトがフリースレッド処理を使用することを指定します。 フリースレッドは、マルチスレッドアパートメントモデルと同じです。 詳細については、「 [マルチスレッドアパートメント](/windows/win32/com/multithreaded-apartments) 」を参照してください。|
   |**Neutral**|オブジェクトがマルチスレッドアパートメントのガイドラインに従うことを指定しますが、任意の種類のスレッドで実行できます。|

- **集計**

   オブジェクトが [集計](/windows/win32/com/aggregation)を使用するかどうかを示します。 集約オブジェクトは、クライアントに公開するインターフェイスを選択し、そのインターフェイスは、集計オブジェクトによって実装されているかのように公開されます。 Aggregate オブジェクトのクライアントは、aggregate オブジェクトとのみ通信します。

   |オプション|説明|
   |------------|-----------------|
   |**あり**|オブジェクトを集計できることを指定します。 これが既定値です。|
   |**いいえ**|オブジェクトが集計されないことを指定します。|
   |**専用**|オブジェクトを集計する必要があることを指定します。|

- **サポート**

   その他のサポートオプション:

   |オプション|説明|
   |------------|-----------------|
   |**ISupportErrorInfo**|オブジェクトがクライアントにエラー情報を返すことができるように、[ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) インターフェイスのサポートを作成します。|
   |**接続ポイント**|オブジェクトのクラスを [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)から派生させることによって、オブジェクトの接続ポイントを有効にします。|
   |**フリースレッドマーシャラー**|同じプロセス内のスレッド間でインターフェイスポインターを効率的にマーシャリングするための、フリースレッドのマーシャラーオブジェクトを作成します。 スレッドモデルとして **、またはいずれか****を指定** するオブジェクトで使用できます。|

## <a name="see-also"></a>関連項目

[ATL Active Server Page コンポーネント ウィザード](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[ATL Active Server Page コンポーネント](../../atl/reference/adding-an-atl-active-server-page-component.md)
