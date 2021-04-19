---
description: 詳細については、「コンパイラエラー C2200 ~ C2299」を参照してください。
title: コンパイラ エラー (C2200 - C2299)
ms.date: 04/21/2019
f1_keywords:
- C2202
- C2209
- C2210
- C2211
- C2214
- C2215
- C2221
- C2225
- C2230
- C2235
- C2237
- C2239
- C2240
- C2257
- C2260
- C2263
- C2265
- C2269
- C2278
- C2281
- C2282
- C2288
- C2291
- C2294
helpviewer_keywords:
- C2202
- C2209
- C2210
- C2211
- C2214
- C2215
- C2221
- C2225
- C2230
- C2235
- C2237
- C2239
- C2240
- C2257
- C2260
- C2263
- C2265
- C2269
- C2278
- C2281
- C2282
- C2288
- C2291
- C2294
ms.assetid: 9b36d11b-9510-4390-96f1-0c9235124d14
ms.openlocfilehash: 2e1ea71c94744342a12b69ca0f5664eedb982d73
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721785"
---
# <a name="compiler-errors-c2200-through-c2299"></a>コンパイラ エラー (C2200 - C2299)

ドキュメントのこのセクションの記事では、コンパイラによって生成されるエラーメッセージのサブセットについて説明します。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>エラー メッセージ

|エラー|Message|
|-----------|-------------|
|[コンパイラ エラー C2200](compiler-error-c2200.md)|'*function*': 関数は既に定義されています|
|[コンパイラ エラー C2201](compiler-error-c2201.md)|'*identifier*': エクスポート/インポートするには、外部リンケージが必要です|
|コンパイラエラー C2202|'*function*': すべてのコントロールパスが値を返すわけではありません|
|[コンパイラ エラー C2203](compiler-error-c2203.md)|delete 演算子で配列の境界を指定することはできません|
|[コンパイラ エラー C2204](compiler-error-c2204.md)|'*type*': 型定義がかっこ内に見つかりました。|
|[コンパイラ エラー C2205](compiler-error-c2205.md)|'*identifier*': ブロックスコープで extern 変数を初期化することはできません|
|[コンパイラ エラー C2206](compiler-error-c2206.md)|'*function*': typedef は関数の定義には使用できません|
|[コンパイラ エラー C2207](compiler-error-c2207.md)|'*member*': クラステンプレートのメンバーは関数型を取得できません|
|[コンパイラ エラー C2208](compiler-error-c2208.md)|'*type*': この型を使用して定義されたメンバーはありません|
|コンパイラエラー C2209|'*identifier*': エイリアスをコンストラクター宣言で使用することはできません|
|コンパイラエラー C2210|'*identifier*': パック展開は、エイリアステンプレート内のパックされていないパラメーターの引数として使用できません|
|コンパイラエラー C2211|パブリックデストラクターを持つ ref クラスから派生した非仮想デストラクターは、パブリックである必要もあります|
|[コンパイラ エラー C2212](compiler-error-c2212.md)|'*identifier*': __based 関数へのポインターに対して使用できません|
|[コンパイラ エラー C2213](compiler-error-c2213.md)|'*identifier*': __based の引数が無効です|
|コンパイラエラー C2214|' void ' に基づくポインターでは、を使用する必要があり >|
|コンパイラエラー C2215|'*keyword*' は '/ARCH: SSE ' と共に使用することはできません|
|[コンパイラ エラー C2216](compiler-error-c2216.md)|'*keyword1*' を '*keyword2*' と共に使用することはできません|
|[コンパイラ エラー C2217](compiler-error-c2217.md)|'*attribute1*' には '*attribute2*' が必要です|
|[コンパイラ エラー C2218](compiler-error-c2218.md)|'*calltype*' を '/ARCH: IA32 ' と共に使用することはできません|
|[コンパイラ エラー C2219](compiler-error-c2219.md)|構文エラー: 型修飾子は ' * ' の後になければなりません|
|[コンパイラ エラー C2220](compiler-error-c2220.md)|警告をエラーとして処理しました-'*filetype*' ファイルは生成されませんでした|
|コンパイラエラー C2221|互換性のために残されています。|
|[コンパイラ エラー C2222](compiler-error-c2222.md)|予期しない型 '*type*': 基底クラスまたはメンバーが必要です|
|[コンパイラ エラー C2223](compiler-error-c2223.md)|'->*identifier*' の左側は構造体または共用体を指す必要があります|
|[コンパイラ エラー C2224](compiler-error-c2224.md)|' の左側。*識別子*' は構造体型または共用体型でなければなりません|
|コンパイラエラー C2225|互換性のために残されています。|
|[コンパイラ エラー C2226](compiler-error-c2226.md)|構文エラー: 予期しない型 '*type*' です|
|[コンパイラ エラー C2227](compiler-error-c2227.md)|'->*identifier*' の左側はクラス、構造体、共用体、ジェネリック型を指している必要があります|
|[コンパイラ エラー C2228](compiler-error-c2228.md)|' の左側。*識別子*' はクラス、構造体、共用体でなければなりません|
|[コンパイラ エラー C2229](compiler-error-c2229.md)|クラス/構造体/共用体 '*type*' に、無効な0サイズの配列が含まれています。|
|コンパイラエラー C2230|モジュール '*name*' が見つかりませんでした|
|[コンパイラ エラー C2231](compiler-error-c2231.md)|'.*identifier*': 左のオペランドが ' class/struct/union ' を指しています。 '-> ' を使用してください|
|[コンパイラ エラー C2232](compiler-error-c2232.md)|'->*identifier*': 左オペランドに ' class/struct/union ' 型が含まれています。 '. ' を使用してください。|
|[コンパイラ エラー C2233](compiler-error-c2233.md)|'*identifier*': サイズが0の配列を含むオブジェクトの配列は無効です|
|[コンパイラ エラー C2234](compiler-error-c2234.md)|*identifier*': 参照の配列が正しくありません|
|コンパイラエラー C2235|互換性のために残されています。|
|[コンパイラ エラー C2236](compiler-error-c2236.md)|予期しないトークン '*token*' です。 ';' が入力されていることを確認してください。|
|コンパイラエラー C2237|複数のモジュール宣言|
|[コンパイラ エラー C2238](compiler-error-c2238.md)|'*token*' の前に予期しないトークンがあります。|
|コンパイラエラー C2239|'*function*': __declspec (dllexport) 関数を削除しようとしています|
|コンパイラエラー C2240|互換性のために残されています。|
|[コンパイラ エラー C2241](compiler-error-c2241.md)|'*identifier*': メンバーアクセスは制限されています|
|[コンパイラ エラー C2242](compiler-error-c2242.md)|列挙型、構造体、共用体の後に typedef 名を書くことはできません。|
|[コンパイラ エラー C2243](compiler-error-c2243.md)|'*conversion_type*': ' type1 *' から '**type1*' への変換は存在しますが、アクセスできません|
|[コンパイラ エラー C2244](compiler-error-c2244.md)|'*identifier*': 関数の定義を既存の宣言と一致させることができません|
|[コンパイラ エラー C2245](compiler-error-c2245.md)|friend として指定された存在しないメンバー関数 '*function*' (メンバー関数シグネチャがオーバーロードと一致しません)|
|[コンパイラ エラー C2246](compiler-error-c2246.md)|'*identifier*': ローカルに定義されたクラスの静的データメンバーが正しくありません|
|[コンパイラ エラー C2247](compiler-error-c2247.md)|'*class1*' は '*class2*' を継承するために '*指定子*' を使用するため、'*identifier*' にアクセスできません|
|[コンパイラ エラー C2248](compiler-error-c2248.md)|'*identifier*': クラス '*class*' で宣言された *アクセシビリティ**メンバー* にアクセスできません|
|[コンパイラ エラー C2249](compiler-error-c2249.md)|'*identifier*': 仮想基底 *クラス ' class*' で宣言された *アクセシビリティ**メンバー* へのアクセス可能なパスがありません|
|[コンパイラ エラー C2250](compiler-error-c2250.md)|'*identifier*': *クラス*::*member*' のあいまいな継承です|
|[コンパイラ エラー C2251](compiler-error-c2251.md)|名前空間 '*namespace*' にはメンバー '*identifier*' がありません。 '*member*' という意味ですか?|
|[コンパイラ エラー C2252](compiler-error-c2252.md)|テンプレートの明示的なインスタンス化は名前空間スコープでのみ実行できます|
|[コンパイラ エラー C2253](compiler-error-c2253.md)|'*function*': 純粋指定子または抽象オーバーライド指定子は、仮想関数でのみ使用できます|
|[コンパイラ エラー C2254](compiler-error-c2254.md)|'*function*': フレンド関数では、純粋指定子または抽象オーバーライド指定子は使用できません|
|[コンパイラ エラー C2255](compiler-error-c2255.md)|'*element*': クラス定義外では使用できません|
|[コンパイラ エラー C2256](compiler-error-c2256.md)|'*function*' で friend 指定子が正しく使用されることはありません|
|コンパイラエラー C2257|'*指定子*': 後続の戻り値の型では指定できません。|
|[コンパイラ エラー C2258](compiler-error-c2258.md)|純粋仮想関数の宣言に構文上の誤りがあります、'= 0' でなければなりません。|
|[コンパイラ エラー C2259](compiler-error-c2259.md)|'*class*': 抽象クラスをインスタンス化できません。|
|コンパイラエラー C2260|'*指定子*': InternalsVisibleToAttribute friend アセンブリ指定子が無効です|
|[コンパイラ エラー C2261](compiler-error-c2261.md)|'*string*': アセンブリ参照は無効であるため、解決できません|
|[コンパイラ エラー C2262](compiler-error-c2262.md)|'*指定子*': InternalsVisibleTo 宣言にバージョン、カルチャ、またはプロセッサアーキテクチャを指定することはできません|
|コンパイラエラー C2263|互換性のために残されています。|
|[コンパイラ エラー C2264](compiler-error-c2264.md)|'*function*': 関数の定義または宣言にエラーがあります。関数は呼び出されません。|
|コンパイラエラー C2265|互換性のために残されています。|
|[コンパイラ エラー C2266](compiler-error-c2266.md)|'*identifier*': 非定数の境界配列への参照は無効です|
|[コンパイラ エラー C2267](compiler-error-c2267.md)|'*function*': ブロックスコープを持つ静的関数は無効です|
|[コンパイラ エラー C2268](compiler-error-c2268.md)|'*function*' は、コンパイラの定義済みライブラリヘルパーです。 ライブラリヘルパーは、/GL ではサポートされていません。/GL. を使用せずにオブジェクトファイル '*filename*' をコンパイルします|
|コンパイラエラー C2269|修飾される関数型へのポインターまたは参照を作成することはできません (メンバーへのポインターが必要です)|
|[コンパイラ エラー C2270](compiler-error-c2270.md)|'*function*': 修飾子は、非メンバー関数では使用できません|
|[コンパイラ エラー C2271](compiler-error-c2271.md)|'*function*': new/delete に仮引数リスト修飾子を含めることはできません|
|[コンパイラ エラー C2272](compiler-error-c2272.md)|'*function*': 静的メンバー関数では、修飾子は使用できません|
|[コンパイラ エラー C2273](compiler-error-c2273.md)|'*type*': '-> ' 演算子の右辺が正しくありません。|
|[コンパイラ エラー C2274](compiler-error-c2274.md)|'*type*': '. ' 演算子の右側が正しくありません。|
|[コンパイラ エラー C2275](compiler-error-c2275.md)|'*type*': この型は式として不適切に使用されています|
|[コンパイラ エラー C2276](compiler-error-c2276.md)|'*operator*': バインドされたメンバー関数式に対する無効な操作です。|
|[コンパイラ エラー C2277](compiler-error-c2277.md)|'*function*': このメンバー関数のアドレスを取得することはできません。|
|コンパイラエラー C2278|互換性のために残されています。|
|[コンパイラ エラー C2279](compiler-error-c2279.md)|例外指定は typedef 宣言には記述できません|
|[コンパイラ エラー C2280](compiler-error-c2280.md)|'*class*::*function*': 削除された関数を参照しようとしています|
|コンパイラエラー C2281|'*class*::*function*': 関数は最初の宣言でのみ削除できます|
|コンパイラエラー C2282|'*function1*' は '*function2*' をオーバーライドできません|
|[コンパイラ エラー C2283](compiler-error-c2283.md)|'*識別子*': 名前のないクラスまたは構造体では、純粋指定子または抽象オーバーライド指定子は使用できません|
|コンパイラエラー C2284|'*function*': 組み込み関数に対する引数が無効です。パラメーター *番号*|
|[コンパイラ エラー C2285](compiler-error-c2285.md)|メンバー表現へのポインターは既に決定されています-プラグマは無視されます。|
|[コンパイラ エラー C2286](compiler-error-c2286.md)|'*identifier*' 表現のメンバーへのポインターは、既に *継承* に設定されています-宣言は無視されます|
|[コンパイラ エラー C2287](compiler-error-c2287.md)|'*identifier*': 継承表現: '*inheritiance*' は、必要な '*継承*' よりも一般的ではありません|
|コンパイラエラー C2288|互換性のために残されています。|
|[コンパイラ エラー C2289](compiler-error-c2289.md)|同じ型の修飾子が 2 度以上使われています。|
|[コンパイラ エラー C2290](compiler-error-c2290.md)|C++ ' asm ' 構文は無視されました。 __asm を使用してください。|
|コンパイラエラー C2291|匿名の名前空間はエクスポートできません。|
|[コンパイラ エラー C2292](compiler-error-c2292.md)|'*identifier*': ベストケースの継承表現: *inheritance1*' が宣言されていますが、'*inheritance2*' が必要です|
|[コンパイラ エラー C2293](compiler-error-c2293.md)|'*identifier*': メンバー変数を __based 指定子として指定することはできません|
|コンパイラエラー C2294|内部リンケージがあるため、シンボル '*identifier*' をエクスポートできません|
|[コンパイラ エラー C2295](compiler-error-c2295.md)|エスケープされた '*character*': マクロ定義では無効です|
|[コンパイラ エラー C2296](compiler-error-c2296.md)|'*operator*': 無効です。左オペランドに型 '*type*' が含まれています。|
|[コンパイラ エラー C2297](compiler-error-c2297.md)|'*operator*': 無効です。右オペランドに型 '*type*' が含まれています|
|[コンパイラ エラー C2298](compiler-error-c2298.md)|メンバー関数へのバインドされたポインターへの呼び出しがありません|
|[コンパイラ エラー C2299](compiler-error-c2299.md)|'*function*': 動作の変更: 明示的な特殊化をコピーコンストラクターまたはコピー代入演算子にすることはできません|

## <a name="see-also"></a>関連項目

[C/c + + コンパイラおよびビルドツールのエラーと警告](../compiler-errors-1/c-cpp-build-errors.md) \
[コンパイラエラー C2000-C3999、C7000-C7999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
