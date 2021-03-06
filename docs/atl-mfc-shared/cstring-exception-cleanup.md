---
description: 詳細については、「CString 例外のクリーンアップ」を参照してください。
title: '文字列: CString の例外の後処理'
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
ms.openlocfilehash: 9c77c9bf5d3f123315c126ce2361be63230c173b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167150"
---
# <a name="cstring-exception-cleanup"></a>文字列: CString の例外の後処理

以前のバージョンの MFC では、使用後に [CString](../atl-mfc-shared/reference/cstringt-class.md) オブジェクトをクリーンアップすることが重要でした。 MFC バージョン3.0 以降では、明示的なクリーンアップは不要になりました。

MFC が現在使用している C++ 例外処理機構の下では、例外発生後のクリーンアップについて心配する必要はありません。 例外がキャッチされた後に C++ がスタックを "アンワインド" する方法の詳細については、「 [try、catch、および throw ステートメント](../cpp/try-throw-and-catch-statements-cpp.md)」を参照してください。 C++ のキーワードではなく mfc の **try** CATCH マクロを使用する場合でも、mfc では c++ の例外機構を使用するので、 /  **`try`** **`catch`** 明示的にクリーンアップする必要はありません。

## <a name="see-also"></a>関連項目

[文字列 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[例外処理](../mfc/exception-handling-in-mfc.md)
