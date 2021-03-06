---
description: 詳細については、プロバイダーのテストに関するページを参照してください。
title: プロバイダーのテスト
ms.date: 10/29/2018
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
ms.openlocfilehash: de9ba1b6cb66df8041cc6a94f357d52fc2194553
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272657"
---
# <a name="testing-your-provider"></a>プロバイダーのテスト

プロバイダーをリリースする前に、次のテストを示された順序で実行する必要があります。 これらのテストは、プロバイダーがほとんどのユーザーに対して適切に機能していることを示しています。

1. OLE DB コンシューマーテンプレートで記述された [コンシューマー](../../data/oledb/creating-an-ole-db-consumer.md) アプリケーションを使用して、プロバイダーをテストします。 テストコンシューマーは、プロバイダーのすべての機能領域 (追加または変更したすべてのコード) をカバーする必要があります。

1. ADO で記述されたコンシューマーアプリケーションを使用して、プロバイダーをテストします。 ほとんどの開発者 (特に Microsoft Visual Basic および Microsoft C# 開発者) は、コンシューマーアプリケーションに ADO または ADO.NET を使用します。 テストコンシューマーは、プロバイダーのすべての機能領域をカバーする必要があります。 ADO コンシューマーアプリケーションの例については、「 [Microsoft Visual Basic の Ado コード例](/previous-versions/ms807514(v=msdn.10))」を参照してください。

1. OLE DB 準拠テスト (ADO 準拠テストを含む) を実行して、プロバイダーが OLE DB プロバイダーのレベル0の標準を満たしていることを示します。 (レベル0の説明については、 [OLE DB プログラマーガイド](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)で **OLE DB レベル0の準拠テスト** を検索してください。 これらのテストと関連ドキュメントは、データアクセス SDK の Visual C++ に含まれています。 また、これらのテストは、他の [サービスプロバイダー](../../data/oledb/ole-db-resource-pooling-and-services.md) によって集計された場合にプロバイダーが良好に動作することを示すのにも役立ちます。また、プロパティを変更または追加する場合に特に便利です。 準拠テストの詳細については、Visual Studio のいずれかの Cd にある Data Access SDK の Readme ファイルを参照してください。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダーテンプレートの操作](../../data/oledb/working-with-ole-db-provider-templates.md)
