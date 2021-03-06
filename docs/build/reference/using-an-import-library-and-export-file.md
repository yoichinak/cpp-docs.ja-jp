---
description: 詳細については、インポートライブラリとエクスポートファイルの使用に関するページを参照してください。
title: インポート ライブラリとエクスポート ファイルの使用
ms.date: 11/04/2016
helpviewer_keywords:
- circular exports
- import libraries, using
- export files
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
ms.openlocfilehash: f42a98ebe19cb32fb77964f26c37928776b5b30c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247021"
---
# <a name="using-an-import-library-and-export-file"></a>インポート ライブラリとエクスポート ファイルの使用

プログラム (実行可能ファイルまたは DLL) が、インポート元の別のプログラムにエクスポートされる場合、または2つ以上のプログラムが相互にエクスポートおよびインポートを行う場合は、これらのプログラムをリンクするコマンドが循環エクスポートに対応している必要があります。

循環エクスポートがない状況で、別のプログラムからエクスポートを使用するプログラムをリンクする場合は、エクスポートするプログラムのインポートライブラリを指定する必要があります。 エクスポートプログラムのインポートライブラリは、そのエクスポートプログラムをリンクしたときに作成されます。 そのため、インポートプログラムの前に、エクスポートするプログラムをリンクする必要があります。 たとえば、ONE.dll からインポート TWO.dll 場合は、まず ONE.dll をリンクし、インポートライブラリを1つ .lib として取得する必要があります。 次に、TWO.dll をリンクするときに1つの .lib を指定します。 リンカーによって TWO.dll が作成されると、そのインポートライブラリである2つの .lib も作成されます。 TWO.dll からインポートするプログラムをリンクする場合は、2つの .lib を使用します。

ただし、循環エクスポートの場合は、他のプログラムからのインポートライブラリを使用して、相互に依存するすべてのプログラムをリンクすることはできません。 前に説明した例では、TWO.dll も ONE.dll にエクスポートした場合、ONE.dll がリンクされているときに TWO.dll のインポートライブラリはまだ存在しません。 循環エクスポートが存在する場合は、LIB を使用して、いずれかのプログラムのインポートライブラリとエクスポートファイルを作成する必要があります。

開始するには、LIB を実行するいずれかのプログラムを選択します。 LIB コマンドで、プログラムのすべてのオブジェクトとライブラリを一覧表示し、/defを指定します。 プログラムで .def ファイルまたは/EXPORT 指定を使用する場合は、これらも指定します。

プログラムのインポートライブラリ (.lib) とエクスポートファイル (.exp) を作成したら、他のプログラムをリンクするときにインポートライブラリを使用します。 LINK は、ビルドするエクスポートプログラムごとにインポートライブラリを作成します。 たとえば、ONE.dll のオブジェクトとエクスポートで LIB を実行する場合、1つの .lib と1つの .exp を作成します。TWO.dll をリンクするときに、1つの .lib を使用できるようになりました。この手順では、インポートライブラリとして2つの .lib も作成されます。

最後に、で開始したプログラムをリンクします。 [リンク] コマンドで、プログラムのオブジェクトとライブラリ、LIB でプログラム用に作成された .exp ファイル、およびプログラムによって使用されるエクスポートのインポートライブラリまたはライブラリを指定します。 この例を続行するために、ONE.dll の LINK コマンドには、ONE.dll に含まれるオブジェクトとライブラリに加えて、1つの .exp と2つの .lib が含まれています。 LINK コマンドで .def ファイルまたは/EXPORT の指定を指定しないでください。エクスポート定義が .exp ファイルに含まれているため、これらは必要ありません。 .Exp ファイルを使用してリンクする場合、リンクは、.exp ファイルの作成時に作成されたものであると想定しているため、インポートライブラリを作成しません。

## <a name="see-also"></a>関連項目

[インポート ライブラリとエクスポート ファイル](working-with-import-libraries-and-export-files.md)
