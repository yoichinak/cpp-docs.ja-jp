---
description: '詳細情報: OpenMP ライブラリリファレンス'
title: OpenMP ライブラリ リファレンス
ms.date: 12/02/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: fa1f654835afef94b0e00f52bebb0b7300d205be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342362"
---
# <a name="openmp-library-reference"></a>OpenMP ライブラリ リファレンス

OpenMP API で使用される構成要素へのリンクを示します。

OpenMP 標準の Visual C++ の実装には、次の構造体が含まれています。

|構成体|説明|
|---------------|-----------------|
|[ディレクティブ](openmp-directives.md)|OpenMP API で使用されるディレクティブへのリンクを提供します。|
|[句](openmp-clauses.md)|OpenMP API で使用される句へのリンクを提供します。|
|[関数](openmp-functions.md)|OpenMP API で使用される関数へのリンクを示します。|
|[環境変数](openmp-environment-variables.md)|OpenMP API で使用される環境変数へのリンクを示します。|

Visual C++ OpenMP ランタイムライブラリ関数は、次のライブラリに含まれています。

|OpenMP ランタイムライブラリ|特性|
|------------------------------|---------------------|
|VCOMP。変数|マルチスレッド、動的リンク (VCOMP140.DLL 用インポートライブラリ)。|
|VCOMPD。変数|マルチスレッド、動的リンク (VCOMP140D.DLL 用インポートライブラリ) (デバッグ)|

コンパイルで _DEBUG が定義されていて、 `#include <omp.h>` がソースコード内にある場合は。LIB が既定の lib になります。それ以外の場合は、VCOMP です。LIB が使用されます。

[/NODEFAULTLIB (ライブラリを無視する)](../../../build/reference/nodefaultlib-ignore-libraries.md)を使用して、既定の lib を削除し、選択した lib と明示的にリンクすることができます。

OpenMP Dll は Visual C++ 再頒布可能なディレクトリにあり、OpenMP を使用するアプリケーションと共に配布する必要があります。

## <a name="see-also"></a>関連項目

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)
