---
description: 詳細については、「コンパイラエラー C2600 ~ C2699」を参照してください。
title: コンパイラ エラー (C2600 - C2699)
ms.date: 04/21/2019
f1_keywords:
- C2604
- C2606
- C2607
- C2608
- C2609
- C2610
- C2615
- C2618
- C2620
- C2621
- C2622
- C2623
- C2625
- C2629
- C2631
- C2639
- C2641
- C2642
- C2643
- C2644
- C2684
- C2685
- C2686
- C2697
helpviewer_keywords:
- C2604
- C2606
- C2607
- C2608
- C2609
- C2610
- C2615
- C2618
- C2620
- C2621
- C2622
- C2623
- C2625
- C2629
- C2631
- C2639
- C2641
- C2642
- C2643
- C2644
- C2684
- C2685
- C2686
- C2697
ms.assetid: 73c6319f-cbea-4a2f-913b-90dc1af61f64
ms.openlocfilehash: 6cdc7f1c4db92a367bc001042e1219c0e2190688
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721460"
---
# <a name="compiler-errors-c2600-through-c2699"></a>コンパイラ エラー (C2600 - C2699)

ドキュメントのこのセクションの記事では、コンパイラによって生成されるエラーメッセージのサブセットについて説明します。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>エラー メッセージ

|エラー|Message|
|-----------|-------------|
|[コンパイラ エラー C2600](compiler-error-c2600.md)|'*function*': コンパイラで生成された特殊なメンバー関数を定義することはできません (クラスで最初に宣言する必要があります)|
|[コンパイラ エラー C2601](compiler-error-c2601.md)|'*function*': ローカル関数の定義が正しくありません。|
|[コンパイラ エラー C2602](compiler-error-c2602.md)|'*class*::*identifier*' は '*class*' の基底クラスのメンバーではありません|
|[コンパイラ エラー C2603](compiler-error-c2603.md)|'*function*': 関数内のコンストラクターまたはデストラクターを含むブロックスコープの静的オブジェクトが多すぎます。|
|コンパイラエラー C2604|'*identifier*': 複数のインターフェイスメソッドを実装することはできません|
|[コンパイラ エラー C2605](compiler-error-c2605.md)|'*identifier*': このメソッドはマネージド/WinRT クラス内で予約されています|
|コンパイラエラー C2606|'*class1*': ランタイムベース '*class2*' から継承されているため、'*member*' を再実装することはできません|
|コンパイラエラー C2607|静的アサーションに失敗しました|
|コンパイラエラー C2608|互換性のために残されています。|
|コンパイラエラー C2609|互換性のために残されています。|
|コンパイラエラー C2610|'*class*::*member*': は、既定値にできる特殊なメンバー関数ではありません|
|[コンパイラ エラー C2611](compiler-error-c2611.md)|'*token*': ' ~ ' は正しくありません (識別子が必要です)|
|[コンパイラ エラー C2612](compiler-error-c2612.md)|基底クラスまたはメンバー初期化子リストで、末尾の '*character*' は無効です。|
|[コンパイラ エラー C2613](compiler-error-c2613.md)|基底クラスリストの末尾の '*character*' は無効です。|
|[コンパイラ エラー C2614](compiler-error-c2614.md)|'*class*': 無効なメンバー初期化です: '*identifier*' は基底クラスでもメンバーでもありません|
|コンパイラエラー C2615|互換性のために残されています。|
|[コンパイラ エラー C2616](compiler-error-c2616.md)|'*conversion*': 非左辺値 '*type1*' を const ではない ' type1 *' に* 暗黙的に変換することはできません|
|[コンパイラ エラー C2617](compiler-error-c2617.md)|'*function*': 一致する return ステートメントがありません。|
|コンパイラエラー C2618|互換性のために残されています。|
|[コンパイラ エラー C2619](compiler-error-c2619.md)|'*identifier*': 静的データメンバーは、匿名構造体または共用体では使用できません|
|コンパイラエラー C2620|互換性のために残されています。|
|コンパイラエラー C2621|互換性のために残されています。|
|コンパイラエラー C2622|互換性のために残されています。|
|コンパイラエラー C2623|互換性のために残されています。|
|[コンパイラ エラー C2624](compiler-error-c2624.md)|'*scope*::*type*': ローカルクラスを使用して ' extern ' 変数を宣言することはできません|
|コンパイラエラー C2625|'*identifier*': 無効な共用体メンバーです。型 '*type*' は参照型です|
|[コンパイラ エラー C2626](compiler-error-c2626.md)|'*identifier*': プライベート/保護されたデータメンバーは、匿名構造体または共用体では使用できません|
|[コンパイラ エラー C2627](compiler-error-c2627.md)|'*function*': メンバー関数は無名共用体では使用できません|
|[コンパイラ エラー C2628](compiler-error-c2628.md)|'*type1**' の* 後に続く ' type1 ' は無効です ('; ' を忘れたことがあります)。|
|コンパイラエラー C2629|'*identifier*': 無名の構造体または共用体で入れ子にされた型を宣言することはできません|
|[コンパイラ エラー C2630](compiler-error-c2630.md)|'*symbol*' は、コンマ区切りのリストで指定する必要があります|
|コンパイラエラー C2631|'*identifier*': クラスまたは列挙型をエイリアステンプレート内で定義することはできません|
|[コンパイラ エラー C2632](compiler-error-c2632.md)|'*type1**' の* 後に続く ' type1 ' は無効です|
|[コンパイラ エラー C2633](compiler-error-c2633.md)|'*identifier*': ' inline ' は、コンストラクターの唯一の有効なストレージクラスです|
|[コンパイラ エラー C2634](compiler-error-c2634.md)|'*class*::*member*': 参照メンバーへのポインターが無効です。|
|[コンパイラ エラー C2635](compiler-error-c2635.md)|' type1 ' を '*type1*' に変換できません \*  \* 。仮想基底クラスからの変換は暗黙的です。|
|[コンパイラ エラー C2636](compiler-error-c2636.md)|'*identifier*': 参照メンバーへのポインターは無効です|
|[コンパイラ エラー C2637](compiler-error-c2637.md)|'*identifier*': データメンバーへのポインターを変更できません|
|[コンパイラ エラー C2638](compiler-error-c2638.md)|'*identifier*': __based 修飾子は、メンバーへのポインターでは無効です|
|コンパイラエラー C2639|互換性のために残されています。|
|[コンパイラ エラー C2640](compiler-error-c2640.md)|'*identifier*': __based 修飾子は参照では無効です|
|コンパイラエラー C2641|互換性のために残されています。|
|コンパイラエラー C2642|互換性のために残されています。|
|コンパイラエラー C2643|互換性のために残されています。|
|コンパイラエラー C2644|互換性のために残されています。|
|[コンパイラ エラー C2645](compiler-error-c2645.md)|メンバーへのポインターの修飾名がありません (':: * ' が見つかりました)|
|[コンパイラ エラー C2646](compiler-error-c2646.md)|グローバルまたは名前空間スコープの匿名構造体/共用体は static として宣言されなければなりません|
|[コンパイラ エラー C2647](compiler-error-c2647.md)|'*operator*': ' type1 *' の*'*type1*' を逆参照することはできません|
|[コンパイラ エラー C2648](compiler-error-c2648.md)|'*identifier*': メンバーを既定のパラメーターとして使用するには、静的メンバーが必要です|
|[コンパイラ エラー C2649](compiler-error-c2649.md)|'*identifier*': ' class/struct/union ' ではありません|
|[コンパイラ エラー C2650](compiler-error-c2650.md)|'*operator*': 仮想関数にすることはできません。|
|[コンパイラ エラー C2651](compiler-error-c2651.md)|'*type*': ':: ' の左側は、クラス、構造体、または共用体でなければなりません|
|[コンパイラ エラー C2652](compiler-error-c2652.md)|'*identifier*': コピーコンストラクターが無効です: 最初のパラメーターを '*type*' にすることはできません|
|[コンパイラ エラー C2653](compiler-error-c2653.md)|'*identifier*': クラスまたは名前空間の名前ではありません|
|[コンパイラ エラー C2654](compiler-error-c2654.md)|'*identifier*': メンバー関数の外にあるメンバーにアクセスしようとしました|
|[コンパイラ エラー C2655](compiler-error-c2655.md)|'*identifier*': 現在のスコープでは定義または再宣言が無効です|
|[コンパイラ エラー C2656](compiler-error-c2656.md)|'*function*': 関数はビットフィールドとして使用できません|
|[コンパイラ エラー C2657](compiler-error-c2657.md)|ステートメントの先頭に '*class*::* ' が見つかりました (型を指定してください)。|
|[コンパイラ エラー C2658](compiler-error-c2658.md)|'*identifier*': 匿名構造体または共用体で再定義される|
|[コンパイラ エラー C2659](compiler-error-c2659.md)|'*operator*': 関数は左辺オペランドとして機能します|
|[コンパイラ エラー C2660](compiler-error-c2660.md)|'*function*': 関数は *数値* 引数を受け取りません|
|[コンパイラ エラー C2661](compiler-error-c2661.md)|'*function*': *数値* 引数を受け取るオーバーロードされた関数はありません。|
|[コンパイラ エラー C2662](compiler-error-c2662.md)|'*function*': ' type1 ' から '*type1**' に*' this ' ポインターを変換することはできません|
|[コンパイラ エラー C2663](compiler-error-c2663.md)|'*function*': *数値* オーバーロードに ' this ' ポインターの有効な変換がありません|
|[コンパイラ エラー C2664](compiler-error-c2664.md)|'*function*': 引数の *数* を ' type1 *' から '**type1*' に変換できません。|
|[コンパイラ エラー C2665](compiler-error-c2665.md)|'*function*': すべての引数の型を変換できません *でした。*|
|[コンパイラ エラー C2666](compiler-error-c2666.md)|'*function*': *数値* のオーバーロードに似た変換があります。|
|[コンパイラ エラー C2667](compiler-error-c2667.md)|'*function*': *数値* オーバーロードの中に最適な変換がありません。|
|[コンパイラ エラー C2668](compiler-error-c2668.md)|'*function*': オーバーロードされた関数の呼び出しがあいまいです|
|[コンパイラ エラー C2669](compiler-error-c2669.md)|メンバー関数は無名共用体では使用できません|
|[コンパイラ エラー C2670](compiler-error-c2670.md)|'*function*': 関数テンプレートは、パラメーター *番号* を型 '*type*' から変換できません|
|[コンパイラ エラー C2671](compiler-error-c2671.md)|'*function*': 静的メンバー関数には ' this ' ポインターがありません。|
|[コンパイラ エラー C2672](compiler-error-c2672.md)|'*function*': 一致するオーバーロードされた関数が見つかりませんでした|
|[コンパイラ エラー C2673](compiler-error-c2673.md)|'*function*': グローバル関数に ' this ' ポインターがありません。|
|[コンパイラ エラー C2674](compiler-error-c2674.md)|ジェネリック宣言はこのコンテキストでは許可されていません|
|[コンパイラ エラー C2675](compiler-error-c2675.md)|単項 *演算子 ' operator*': '*type*' は、この演算子または定義済みの演算子に使用できる型への変換を定義していません|
|[コンパイラ エラー C2676](compiler-error-c2676.md)|二項演算子 '*operator*': '*type*' は、この演算子または定義済みの演算子に使用できる型への変換を定義していません|
|[コンパイラ エラー C2677](compiler-error-c2677.md)|二項演算子 '*operator*': 型 '*type*' を受け取るグローバル演算子が見つかりません (または変換できません)|
|[コンパイラ エラー C2678](compiler-error-c2678.md)|二項演算子 '*operator*': 型 '*type*' の左辺オペランドを受け取る演算子が見つかりません (または変換できません)|
|[コンパイラ エラー C2679](compiler-error-c2679.md)|二項演算子 '*operator*': 型 '*type*' の右側のオペランドを受け取る演算子が見つかりません (または変換できません)|
|[コンパイラ エラー C2680](compiler-error-c2680.md)|'*type*':*キャスト* のターゲット型が無効です。|
|[コンパイラ エラー C2681](compiler-error-c2681.md)|'*type*':*キャスト* の式の型が無効です。|
|[コンパイラ エラー C2682](compiler-error-c2682.md)|' type1 ' から '*type1**' へ* の変換に '*cast*' を使用することはできません|
|[コンパイラ エラー C2683](compiler-error-c2683.md)|'*cast*': '*type*' はポリモーフィックな型ではありません|
|コンパイラエラー C2684|'*宣言子*': 削除された関数と既定化された関数は、マネージド/WinRT クラスではサポートされていません|
|コンパイラエラー C2685|'*宣言子*': 削除された関数と既定値の関数は、明示的な制限指定子ではサポートされていません|
|コンパイラエラー C2686|同じパラメーター型の静的および非静的メンバー関数をオーバーロードすることはできません|
|[コンパイラ エラー C2687](compiler-error-c2687.md)|'*type*': 例外宣言を ' void ' にしたり、不完全な型、ポインター、または不完全な型への参照を意味したりすることはできません|
|[コンパイラ エラー C2688](compiler-error-c2688.md)|'*type*::*member*': 複数のまたは仮想継承を伴う共変の戻り値が varargs 関数でサポートされていません|
|[コンパイラ エラー C2689](compiler-error-c2689.md)|'*function*': フレンド関数はローカルクラス内では定義できません|
|[コンパイラ エラー C2690](compiler-error-c2690.md)|'*operator*': マネージド/WinRT 配列に対してポインター演算を実行できません|
|[コンパイラ エラー C2691](compiler-error-c2691.md)|'*type*': マネージド/WinRT 配列は、この要素型を持つことはできません|
|[コンパイラ エラー C2692](compiler-error-c2692.md)|'*function*': '/clr ' オプションを指定した C コンパイラでは完全なプロトタイプ関数が必要です|
|[コンパイラ エラー C2693](compiler-error-c2693.md)|'*operator*': マネージド/WinRT 配列への参照の比較が正しくありません。|
|[コンパイラ エラー C2694](compiler-error-c2694.md)|'*override_function*': オーバーライドする仮想関数は、基底クラスの仮想メンバー関数 '*base_function*' よりも制限が少ない例外指定を含んでいます|
|[コンパイラ エラー C2695](compiler-error-c2695.md)|'*override_function*': オーバーライドする仮想関数は、呼び出し規約によってのみ '*base_function*' と異なります|
|[コンパイラ エラー C2696](compiler-error-c2696.md)|マネージドまたは WinRT 型の '*type*' の一時オブジェクトを作成することはできません|
|コンパイラエラー C2697|互換性のために残されています。|
|[コンパイラ エラー C2698](compiler-error-c2698.md)|'*declaration1*' の using 宣言は、'*declaration2*' の既存の using 宣言と共存させることはできません|

## <a name="see-also"></a>関連項目

[C/c + + コンパイラおよびビルドツールのエラーと警告](../compiler-errors-1/c-cpp-build-errors.md) \
[コンパイラエラー C2000-C3999、C7000-C7999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
