---
description: 詳細情報:/genprofile、/FASTGENPROFILE (プロファイリングインストルメントビルドの生成)
title: /GENPROFILE、/FASTGENPROFILE (プロファイル インストルメント ビルドの生成)
ms.date: 04/14/2021
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.openlocfilehash: 3b966148525fc470d53e2af9052a666aa39d7d99
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539487"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>`/GENPROFILE`、 `/FASTGENPROFILE` (プロファイリングインストルメントビルドの生成)

*`.pgd`* ガイド付き最適化のプロファイル (PGO) をサポートするための、リンカーによるファイルの生成を指定します。 **`/GENPROFILE`** とには、 **`/FASTGENPROFILE`** 異なる既定のパラメーターを使用します。 **`/GENPROFILE`** プロファイリング中の速度とメモリ使用量の精度を優先するために使用します。 **`/FASTGENPROFILE`** メモリ使用量を減らし、精度を上げるために使用します。

## <a name="syntax"></a>Syntax

> **`/GENPROFILE`**\[**`:`**_`profile-argument`_\[**`,`**_`profile-argument`_ ...]]\
> **`/FASTGENPROFILE`**\[**`:`**_`profile-argument`_\[**`,`**_`profile-argument`_ ...]]\

> *`profile-argument`*\
> &emsp;{ **`COUNTER32`** &vert; **`COUNTER64`** }\
> &emsp;{ **`EXACT`** &vert; **`NOEXACT`** }\
> &emsp;**`MEMMAX=`**_数値_\
> &emsp;**`MEMMIN=`**_数値_\
> &emsp;{ **`PATH`** &vert; **`NOPATH`** }\
> &emsp;{ **`TRACKEH`** &vert; **`NOTRACKEH`** }\
> &emsp;**`PGD=`**_/db_

### <a name="arguments"></a>引数

任意の *`profile-argument`* 引数をまたはに指定 **`/GENPROFILE`** でき **`/FASTGENPROFILE`** ます。 ここでパイプ文字 () で区切られた引数 **`|`** は、相互に排他的です。 引数を区切るには、コンマ文字 ( **`,`** ) を使用します。 引数、コンマ、またはコロン () の後にスペースを入れないで **`:`** ください。

**`COUNTER32`** &vert; **`COUNTER64`**\
**`COUNTER32`** 32 ビットプローブカウンターの使用を指定し、64ビットプローブカウンターを指定するには、を使用し **`COUNTER64`** ます。 を指定すると **`/GENPROFILE`** 、既定値はに **`COUNTER64`** なります。 を指定すると **`/FASTGENPROFILE`** 、既定値はに **`COUNTER32`** なります。

**`EXACT`** &vert; **`NOEXACT`**\
**`EXACT`** プローブにスレッドセーフなインタロックインクリメントを指定するには、を使用します。 **`NOEXACT`** プローブに対して保護されていないインクリメント操作を指定します。 既定値は **`NOEXACT`** です。

**`MEMMAX`**=*value*、 **`MEMMIN`** = *value*\
およびを使用して **`MEMMAX`** **`MEMMIN`** 、メモリ内のトレーニングデータの予約サイズの最大値と最小値を指定します。 値は、予約するメモリ量 (バイト単位) です。 既定では、これらの値は内部ヒューリスティックによって決定されます。

**`PATH`**  &vert; **`NOPATH`**\
**`PATH`** 関数への一意のパスごとに個別の PGO カウンターのセットを指定するには、を使用します。 **`NOPATH`** 各関数に対して1つのカウンターセットだけを指定するには、を使用します。 を指定すると **`/GENPROFILE`** 、既定値はに **`PATH`** なります。 を指定すると **`/FASTGENPROFILE`** 、既定値はに **`NOPATH`** なります。

**`TRACKEH`**  &vert; **`NOTRACKEH`**\
トレーニング中に例外がスローされた場合に、追加のカウンターを使用して正確なカウントを保持するかどうかを指定します。 **`TRACKEH`** 正確なカウントに追加のカウンターを指定するには、を使用します。 **`NOTRACKEH`** を使用すると、例外処理を使用しないコード、またはトレーニングシナリオで例外として実行されないコードに1つのカウンターを指定できます。  を指定すると **`/GENPROFILE`** 、既定値はに **`TRACKEH`** なります。 を指定すると **`/FASTGENPROFILE`** 、既定値はに **`NOTRACKEH`** なります。

**`PGD`**=*/db*\
ファイルの基本ファイル名を指定し *`.pgd`* ます。 既定では、リンカーは、基本の実行可能イメージのファイル名と拡張子を使用し *`.pgd`* ます。

## <a name="remarks"></a>注釈

**`/GENPROFILE`** およびオプションは、 **`/FASTGENPROFILE`** ガイド付き最適化のプロファイル (PGO) のためのアプリケーショントレーニングをサポートするために必要なプロファイルインストルメンテーションファイルを生成するようにリンカーに指示します。 これらのオプションは、Visual Studio 2015 で新しく追加されたものです。 これらのオプションは、非推奨の、 **`/LTCG:PGINSTRUMENT`** **`/PGD`** 、およびオプション、、、 **`/POGOSAFEMODE`** **`PogoSafeMode`** **`VCPROFILE_ALLOC_SCALE`** および **`VCPROFILE_PATH`** 環境変数に優先します。 アプリケーショントレーニングによって生成されるプロファイル情報は、ビルド中のプログラム全体の最適化のための入力として使用されます。 また、アプリのトレーニングとビルド中にパフォーマンスを向上させるために、さまざまなプロファイリング機能を制御するためのオプションを設定することもできます。 によって指定される既定のオプションでは、 **`/GENPROFILE`** 特に大規模で複雑なマルチスレッドアプリの場合に、最も正確な結果が得られます。 このオプションは、精度を犠牲にして、 **`/FASTGENPROFILE`** トレーニング中のメモリフットプリントが小さく、パフォーマンスが速くなるように、異なる既定値を使用します。

のを使用してビルドした後、インストルメント化されたアプリを実行すると、プロファイル情報がキャプチャされ **`/GENPROFILE`** **`/FASTGENPROFILE`** ます。 この情報は、 [`/USEPROFILE`](useprofile.md) プロファイル手順を実行するためにリンカーオプションを指定し、最適化されたビルドステップのガイドとして使用するときにキャプチャされます。 アプリをトレーニングする方法と収集されたデータの詳細については、「 [ガイド付き最適化のプロファイル](../profile-guided-optimizations.md)」を参照してください。

**`/LTCG`** またはを指定する場合は、常にを指定し **`/GENPROFILE`** **`/FASTGENPROFILE`** ます。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[構成プロパティ]**  >  **[リンカー]**  >  **[コマンド ライン]** プロパティ ページを選択します。

1. [ **`/GENPROFILE`** **`/FASTGENPROFILE`** **追加のオプション** ] ボックスに、オプションまたはオプションと引数を入力します。 **`OK`** 変更を保存することを選択します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーリファレンス](linking.md)\
[MSVC リンカーオプション](linker-options.md)\
[`/LTCG` (リンク時のコード生成)](ltcg-link-time-code-generation.md)
