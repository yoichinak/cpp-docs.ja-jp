---
description: 詳細については、「コンパイラエラー C3000 ~ C3099」を参照してください。
title: コンパイラ エラー (C3000 - C3099)
ms.date: 04/21/2019
f1_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
helpviewer_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
ms.assetid: 01b7b9cb-b351-4b5a-8cb0-1fcddb08d2ab
ms.openlocfilehash: b6471a6c1c92039d1c16512b2121187be96040d0
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721863"
---
# <a name="compiler-errors-c3000-through-c3099"></a>コンパイラ エラー (C3000 - C3099)

ドキュメントのこのセクションの記事では、コンパイラによって生成されるエラーメッセージのサブセットについて説明します。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>エラー メッセージ

|エラー|Message|
|-----------|-------------|
|コンパイラエラー C3000|互換性のために残されています。|
|[コンパイラ エラー C3001](compiler-error-c3001.md)|'*message*': OpenMP ディレクティブ名が必要です|
|[コンパイラ エラー C3002](compiler-error-c3002.md)|'*name1* *name2*': 複数の OpenMP ディレクティブ名があります。|
|[コンパイラ エラー C3003](compiler-error-c3003.md)|'*ディレクティブ*': OpenMP ディレクティブ名は、ディレクティブ句の後には使用できません|
|[コンパイラ エラー C3004](compiler-error-c3004.md)|'*clause*': 句は、OpenMP '*ディレクティブ*' ディレクティブでは無効です|
|[コンパイラ エラー C3005](compiler-error-c3005.md)|'*message*': OpenMP '*ディレクティブ*' ディレクティブで予期しないトークンが検出されました|
|[コンパイラ エラー C3006](compiler-error-c3006.md)|'*clause*': OpenMP '*ディレクティブ*' ディレクティブ上の句には、必要な引数がありません|
|[コンパイラ エラー C3007](compiler-error-c3007.md)|'*clause*': OpenMP '*ディレクティブ*' ディレクティブ上の句は引数を受け取りません|
|[コンパイラ エラー C3008](compiler-error-c3008.md)|'*argument*': OpenMP '*ディレクティブ*' ディレクティブで、引数の終わりに ') ' がありません。|
|[コンパイラ エラー C3009](compiler-error-c3009.md)|'*label*': OpenMP 構造化ブロックへのジャンプは許可されていません|
|[コンパイラ エラー C3010](compiler-error-c3010.md)|'*label*': OpenMP 構造化ブロックからのジャンプは許可されていません|
|[コンパイラ エラー C3011](compiler-error-c3011.md)|インライン アセンブリを、並行領域内で使用することはできません|
|[コンパイラ エラー C3012](compiler-error-c3012.md)|'*function*': 組み込み関数は、並列領域内で直接使用することはできません|
|[コンパイラ エラー C3013](compiler-error-c3013.md)|'*clause*': 句は、OpenMP '*ディレクティブ*' ディレクティブで1回のみ出現できます|
|[コンパイラ エラー C3014](compiler-error-c3014.md)|OpenMP '*ディレクティブ*' ディレクティブの後に for ループが必要です|
|[コンパイラ エラー C3015](compiler-error-c3015.md)|OpenMP 'for' ステートメントの初期化には、正しくない形式が含まれています|
|[コンパイラ エラー C3016](compiler-error-c3016.md)|'*identifier*': OpenMP ' for ' ステートメントのインデックス変数は、符号付き整数型を持つ必要があります|
|[コンパイラ エラー C3017](compiler-error-c3017.md)|OpenMP 'for' ステートメントの終了テストには、正しくない形式が含まれています|
|[コンパイラ エラー C3018](compiler-error-c3018.md)|'*identifier*': OpenMP ' for ' テストまたはインクリメントは、インデックス変数 '*variable*' を使用しなければなりません|
|[コンパイラ エラー C3019](compiler-error-c3019.md)|OpenMP ' for ' ステートメントのインクリメントには、正しくない形式が含まれています|
|[コンパイラ エラー C3020](compiler-error-c3020.md)|'*variable*': OpenMP ' for ' ループのインデックス変数は、ループ本体では変更できません|
|[コンパイラ エラー C3021](compiler-error-c3021.md)|'*argument*': OpenMP '*ディレクティブ*' ディレクティブの引数が空です|
|[コンパイラ エラー C3022](compiler-error-c3022.md)|'*ディレクティブ*': スケジュールの種類 '*ディレクティブ*' (OpenMP '*ディレクティブ*' ディレクティブ) が無効です。|
|[コンパイラ エラー C3023](compiler-error-c3023.md)|'*argument*': OpenMP '*ディレクティブ*' 句への引数で、予期しないトークンが検出されました|
|[コンパイラ エラー C3024](compiler-error-c3024.md)|' schedule (runtime) ': chunk_size 式は使用できません|
|[コンパイラ エラー C3025](compiler-error-c3025.md)|'*clause*': 整数式が必要です。|
|[コンパイラ エラー C3026](compiler-error-c3026.md)|'*clause*': 定数式は正の数値でなければなりません|
|[コンパイラ エラー C3027](compiler-error-c3027.md)|'*clause*': 演算またはポインター式が必要です。|
|[コンパイラ エラー C3028](compiler-error-c3028.md)|'*member*': データ共有句で使用できるのは、変数または静的データメンバーだけです|
|[コンパイラ エラー C3029](compiler-error-c3029.md)|'*symbol*': OpenMP ディレクティブのデータ共有句で1回のみ使用できます|
|[コンパイラ エラー C3030](compiler-error-c3030.md)|'*identifier*': '*ディレクティブ*' 句またはディレクティブ内の変数は参照型を含むことはできません|
|[コンパイラ エラー C3031](compiler-error-c3031.md)|'*identifier*': ' reduction ' 句の変数には、スカラー演算型を指定しなければなりません|
|[コンパイラ エラー C3032](compiler-error-c3032.md)|'*identifier*': '*clause*' 句の変数は、不完全な型 '*type*' を持つことはできません|
|[コンパイラ エラー C3033](compiler-error-c3033.md)|'*identifier*': '*clause*' 句の変数に、const で修飾される型を含めることはできません|
|[コンパイラ エラー C3034](compiler-error-c3034.md)|OpenMP '*ディレクティブ*' ディレクティブを '*ディレクティブ*' ディレクティブの中に直接入れ子にすることはできません|
|[コンパイラ エラー C3035](compiler-error-c3035.md)|OpenMP 'ordered' ディレクティブは、'ordered' 句と共に 'for' または 'parallel for' ディレクティブに直接バインドしなければなりません|
|[コンパイラ エラー C3036](compiler-error-c3036.md)|'*clause*': OpenMP ' reduction ' 句の無効な演算子トークンです|
|[コンパイラ エラー C3037](compiler-error-c3037.md)|'*identifier*': '*clause*' 句の変数は、それを囲むコンテキスト内で共有されなければなりません|
|[コンパイラ エラー C3038](compiler-error-c3038.md)|'*identifier*': ' private ' 句の変数を、それを囲むコンテキスト内のリダクション変数にすることはできません|
|[コンパイラ エラー C3039](compiler-error-c3039.md)|'*identifier*': OpenMP ' for ' ステートメントのインデックス変数を減少変数にすることはできません|
|[コンパイラ エラー C3040](compiler-error-c3040.md)|'*identifier*': ' reduction ' 句の変数の型は、減少演算子 '*operator*' と互換性がありません|
|[コンパイラ エラー C3041](compiler-error-c3041.md)|'*identifier*': ' copyprivate ' 句の変数は、それを囲むコンテキスト内でプライベートである必要があります|
|[コンパイラ エラー C3042](compiler-error-c3042.md)|' copyprivate ' および ' nowait ' 句を OpenMP '*ディレクティブ*' ディレクティブに一緒に記述することはできません|
|[コンパイラ エラー C3043](compiler-error-c3043.md)|OpenMP 'critical' ディレクティブを 'critical' ディレクティブの中で、同じ名前で入れ子にすることはできません|
|[コンパイラ エラー C3044](compiler-error-c3044.md)|' section ': OpenMP ' sections ' ディレクティブの直下でのみ入れ子にすることができます|
|[コンパイラ エラー C3045](compiler-error-c3045.md)|OpenMP 'sections' ディレクティブの後に複合ステートメントが必要です。 '{' が必要です|
|[コンパイラ エラー C3046](compiler-error-c3046.md)|OpenMP '#pragma omp sections' の領域で構造化ブロックがありません|
|[コンパイラ エラー C3047](compiler-error-c3047.md)|OpenMP 'sections' 領域の構造化ブロックの前には '#pragma omp section' が必要です|
|[コンパイラ エラー C3048](compiler-error-c3048.md)|'#pragma omp atomic' の後の式は、正しくない形式を含んでいます|
|[コンパイラ エラー C3049](compiler-error-c3049.md)|'*argument*': OpenMP ' default ' 句の引数が無効です|
|[コンパイラ エラー C3050](compiler-error-c3050.md)|'*class*': ref クラスは '*identifier*' から継承できません|
|コンパイラエラー C3051|互換性のために残されています。|
|[コンパイラ エラー C3052](compiler-error-c3052.md)|'*identifier*': 変数が、default (none) 句の下のデータ共有句に含まれていません|
|[コンパイラ エラー C3053](compiler-error-c3053.md)|'*identifier*': ' threadprivate ' は、グローバルまたは静的データ項目に対してのみ有効です|
|[コンパイラ エラー C3054](compiler-error-c3054.md)|'#pragma omp parallel' は、ジェネリック クラスまたはジェネリック関数では現在サポートされていません|
|[コンパイラ エラー C3055](compiler-error-c3055.md)|'*identifier*': ' threadprivate ' ディレクティブで使用する前にシンボルを参照することはできません|
|[コンパイラ エラー C3056](compiler-error-c3056.md)|'*identifier*': シンボルは、' threadprivate ' ディレクティブと同じスコープ内にありません|
|[コンパイラ エラー C3057](compiler-error-c3057.md)|'*identifier*': ' threadprivate ' シンボルの動的な初期化は現在サポートされていません|
|[コンパイラ エラー C3058](compiler-error-c3058.md)|'*identifier*': シンボルは ' copyin ' 句で使用される前に ' threadprivate ' として宣言されていません|
|[コンパイラ エラー C3059](compiler-error-c3059.md)|'*identifier*': ' threadprivate ' シンボルを '*clause*' 句で使用することはできません|
|[コンパイラ エラー C3060](compiler-error-c3060.md)|'*identifier*': フレンド関数は、修飾名を使用してクラス内で定義することはできません (宣言することしかできません)|
|コンパイラエラー C3061|演算子 '*operator*': 基になる型 '*type*' を持つ列挙型 '*type*' では使用できません|
|[コンパイラ エラー C3062](compiler-error-c3062.md)|'*identifier*': 基になる型が '*type*' であるため、列挙子には値が必要です|
|[コンパイラ エラー C3063](compiler-error-c3063.md)|演算子 '*operator*': すべてのオペランドには、同じ列挙型を指定しなければなりません|
|コンパイラエラー C3064|'*identifier*': 単純型であるか、またはに解決されなければなりません|
|[コンパイラ エラー C3065](compiler-error-c3065.md)|クラスでないスコープでのプロパティ宣言は使用できません|
|[コンパイラ エラー C3066](compiler-error-c3066.md)|これらの引数を使用して、この型のオブジェクトを呼び出すことができる方法は複数あります。|
|コンパイラエラー C3067|初期化子リストは、組み込み演算子 [] では使用できません|
|[コンパイラ エラー C3068](compiler-error-c3068.md)|'*identifier*': C++ 例外が発生した場合、アンワインドを必要とするオブジェクトを ' 生 ' 関数に含めることはできません|
|[コンパイラ エラー C3069](compiler-error-c3069.md)|演算子 '*operator*': 列挙型には使用できません|
|[コンパイラ エラー C3070](compiler-error-c3070.md)|'*identifier*': プロパティに ' set ' メソッドがありません|
|[コンパイラ エラー C3071](compiler-error-c3071.md)|演算子 '*operator*' は、ref クラスまたは値型のインスタンスにのみ適用できます|
|[コンパイラ エラー C3072](compiler-error-c3072.md)|演算子 '*operator*' を ref クラスのインスタンスに適用できません。単項 '% ' 演算子を使用して ref クラスのインスタンスをハンドル型に変換してください|
|[コンパイラ エラー C3073](compiler-error-c3073.md)|'*identifier*': ref クラスにユーザー定義のコピーコンストラクターがありません。|
|コンパイラエラー C3074|配列は、かっこで囲まれた初期化子では初期化できません|
|[コンパイラ エラー C3075](compiler-error-c3075.md)|'*identifier*': 参照型 '*type*' のインスタンスを値型に埋め込むことはできません|
|[コンパイラ エラー C3076](compiler-error-c3076.md)|'*identifier*': 参照型 '*type*' のインスタンスをネイティブ型に埋め込むことはできません|
|[コンパイラ エラー C3077](compiler-error-c3077.md)|'*identifier*': ファイナライザーは参照型のメンバーとしてのみ使用できます|
|コンパイラエラー C3078|新しい式に配列のサイズを指定する必要があります|
|コンパイラエラー C3079|初期化子リストは、この代入演算子の右オペランドとして使用できません|
|[コンパイラ エラー C3080](compiler-error-c3080.md)|'*ファイナライザー*': ファイナライザーは、ストレージクラス指定子を持つことはできません|
|コンパイラエラー C3081|互換性のために残されています。|
|コンパイラエラー C3082|互換性のために残されています。|
|[コンパイラ エラー C3083](compiler-error-c3083.md)|'*identifier*': ':: ' の左側のシンボルは型でなければなりません|
|[コンパイラ エラー C3084](compiler-error-c3084.md)|'*identifier*': デストラクターまたはファイナライザーを '*keyword*' にすることはできません|
|[コンパイラ エラー C3085](compiler-error-c3085.md)|'*identifier*': コンストラクターを '*keyword*' にすることはできません|
|コンパイラエラー C3086|' std:: initializer_list ' が見つかりません: #include する必要があります \<initializer_list>|
|[コンパイラ エラー C3087](compiler-error-c3087.md)|'*identifier*': '*宣言*' の呼び出しは、既にこのメンバーを初期化しています|
|コンパイラエラー C3088|'*class*': 属性コンストラクターには名前付きの仮引数が必要です|
|コンパイラエラー C3089|'*identifier*': パラメーター名がどのデータメンバーの名前とも一致しません|
|コンパイラエラー C3090|'*class*': 属性クラスをテンプレートにすることはできません|
|コンパイラエラー C3091|'*class*': 属性クラスは基底クラスを含むことはできません|
|コンパイラエラー C3092|'*class*': 属性クラスメンバーをビットフィールド、' static ' または ' const ' にすることはできません|
|コンパイラエラー C3093|'*type*': 属性クラスメンバー '*member*' に対して型を使用することはできません|
|[コンパイラ エラー C3094](compiler-error-c3094.md)|'*attribute*': 匿名使用は許可されていません|
|[コンパイラ エラー C3095](compiler-error-c3095.md)|'*attribute*': 属性を繰り返すことはできません|
|[コンパイラ エラー C3096](compiler-error-c3096.md)|'*attribute*': 属性は、属性クラスのデータメンバーに対してのみ使用できます|
|[コンパイラ エラー C3097](compiler-error-c3097.md)|'*attribute*': 属性は ' assembly: ' または ' module: ' でスコープされなければなりません|
|コンパイラエラー C3098|'*identifier*': 属性にはユーザー定義のコンストラクターがありません|
|[コンパイラ エラー C3099](compiler-error-c3099.md)|'*keyword*': マネージ/WinRT 属性に対して [System:: AttributeUsageAttribute]/[Windows:: Foundation:: Metadata:: AttributeUsageAttribute] を使用します|

## <a name="see-also"></a>関連項目

[C/c + + コンパイラおよびビルドツールのエラーと警告](../compiler-errors-1/c-cpp-build-errors.md) \
[コンパイラエラー C2000-C3999、C7000-C7999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
