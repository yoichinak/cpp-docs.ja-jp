---
description: 詳細については、「コンパイラエラー C2500 ~ C2599」を参照してください。
title: コンパイラ エラー (C2500 - C2599)
ms.date: 04/21/2019
f1_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
helpviewer_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
ms.assetid: a869aaed-e9f6-49e3-b273-00ea7f45bed7
ms.openlocfilehash: 7374d8b0b584759371bc16fc397da1486b2fe65f
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721370"
---
# <a name="compiler-errors-c2500-through-c2599"></a>コンパイラ エラー (C2500 - C2599)

ドキュメントのこのセクションの記事では、コンパイラによって生成されるエラーメッセージのサブセットについて説明します。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>エラー メッセージ

|エラー|Message|
|-----------|-------------|
|[コンパイラ エラー C2500](compiler-error-C2500.md)|'*identifier1*': '*identifier2*' は既に直接基底クラスです|
|コンパイラエラー C2501|'*identifier*': ' __declspec (*指定子*) ' は、構造体、共用体、クラス、または符号なしビットフィールドメンバーにのみ適用できます|
|[コンパイラ エラー C2502](compiler-error-C2502.md)|'*identifier*': 基底クラスのアクセス修飾子が多すぎます|
|[コンパイラ エラー C2503](compiler-error-C2503.md)|'*class*': 基底クラスにサイズが0の配列を含めることはできません|
|[コンパイラ エラー C2504](compiler-error-C2504.md)|'*class*': 基底クラスが定義されていません。|
|[コンパイラ エラー C2505](compiler-error-C2505.md)|'*symbol*': ' __declspec (*指定子*) ' は、グローバルオブジェクトまたは静的データメンバーの宣言または定義にのみ適用できます|
|[コンパイラ エラー C2506](compiler-error-C2506.md)|'*member*': ' __declspec (*指定子*) ' はこのシンボルに適用できません|
|[コンパイラ エラー C2507](compiler-error-C2507.md)|'*identifier*': 基底クラスの仮想修飾子が多すぎます|
|コンパイラエラー C2508|'*identifier*': ' __declspec (*specifier1*) ' を ' __declspec (*specifier2*) ' と組み合わせることはできません|
|[コンパイラ エラー C2509](compiler-error-C2509.md)|'*identifier*': メンバー関数が '*class*' で宣言されていません|
|[コンパイラ エラー C2510](compiler-error-C2510.md)|'*identifier*': ':: ' の左側はクラス、構造体、共用体でなければなりません|
|[コンパイラ エラー C2511](compiler-error-C2511.md)|'*identifier*': オーバーロードされたメンバー関数が '*class*' に見つかりませんでした|
|[コンパイラ エラー C2512](compiler-error-C2512.md)|'*identifier*': 適切な既定のコンストラクターを使用できません|
|[コンパイラ エラー C2513](compiler-error-C2513.md)|' * type ': ' = ' の前に変数が宣言されていません|
|[コンパイラ エラー C2514](compiler-error-C2514.md)|'*class*': クラスにコンストラクターがありません。|
|コンパイラエラー C2515|'*identifier*': ' vtguard ' は、クラス宣言または定義にのみ適用できます|
|[コンパイラ エラー C2516](compiler-error-C2516.md)|'*class*': は有効な基底クラスではありません。|
|[コンパイラ エラー C2517](compiler-error-C2517.md)|'*identifier*': ':: ' の右側が定義されていません|
|[コンパイラ エラー C2518](compiler-error-C2518.md)|キーワード '*keyword*' は基底クラスリストでは無効です。無効|
|コンパイラエラー C2519|'*identifier*': WinRT 属性にはパブリックフィールドのみを含めることができます|
|コンパイラエラー C2520|'*class*': 暗黙的な変換に使用できる非明示的なコンストラクターがありません。|
|[コンパイラ エラー C2521](compiler-error-C2521.md)|デストラクターまたはファイナライザーは引数を受け取りません。|
|コンパイラエラー C2522|'*identifier*': オーバーロード識別子は '*identifier2*' で既に指定されているため、'*identifier1*' で使用することはできません|
|[コンパイラ エラー C2523](compiler-error-C2523.md)|'*class*:: ~*identifier*': デストラクターまたはファイナライザーのタグが一致しません。|
|[コンパイラ エラー C2524](compiler-error-C2524.md)|'*identifier*': デストラクターまたはファイナライザーには ' void ' パラメーターリストが必要です|
|コンパイラエラー C2525|'*identifier*': パラメーター '*identifier1*' は基本関数の '*identifier2*' という名前になっており、公開された実装で一致する必要があります|
|[コンパイラ エラー C2526](compiler-error-C2526.md)|'*identifier1*': c リンケージ関数は、C++ クラス '*identifier2*' を返すことはできません|
|コンパイラエラー C2527|'*identifier*': DefaultOverload を '*function1*' と '*function2*' の両方で指定することはできません。 実装時に1つの仕様を削除するか、関数の名前を変更します。|
|[コンパイラ エラー C2528](compiler-error-C2528.md)|'*identifier*': 参照へのポインターは無効です|
|[コンパイラ エラー C2529](compiler-error-C2529.md)|'*identifier*': 参照への参照が無効です|
|[コンパイラ エラー C2530](compiler-error-C2530.md)|'*identifier*': 参照を初期化する必要があります|
|[コンパイラ エラー C2531](compiler-error-C2531.md)|'*identifier*': ビットフィールドへの参照が無効です|
|[コンパイラ エラー C2532](compiler-error-C2532.md)|'*identifier*': 参照の修飾子が正しくありません|
|[コンパイラ エラー C2533](compiler-error-C2533.md)|'*identifier*': コンストラクターは戻り値の型を使用できません|
|[コンパイラ エラー C2534](compiler-error-C2534.md)|'*identifier*': コンストラクターは値を返せません。|
|[コンパイラ エラー C2535](compiler-error-C2535.md)|'*identifier*': メンバー関数は既に定義または宣言されています|
|コンパイラエラー C2536|互換性のために残されています。|
|[コンパイラ エラー C2537](compiler-error-C2537.md)|'*指定子*': リンケージ指定が正しくありません。|
|コンパイラエラー C2538|互換性のために残されています。|
|コンパイラエラー C2539|互換性のために残されています。|
|[コンパイラ エラー C2540](compiler-error-C2540.md)|配列バインドとしての非定数式|
|[コンパイラ エラー C2541](compiler-error-C2541.md)|'*identifier*': ポインターではないオブジェクトは削除できません|
|[コンパイラ エラー C2542](compiler-error-C2542.md)|'*identifier*': クラスオブジェクトに初期化用のコンストラクターがありません|
|[コンパイラ エラー C2543](compiler-error-C2543.md)|演算子 ' [] ' には '] ' が必要です|
|[コンパイラ エラー C2544](compiler-error-C2544.md)|演算子 ' () ' には ') ' が必要です|
|[コンパイラ エラー C2545](compiler-error-C2545.md)|'*operator*': オーバーロードされた演算子が見つかりません|
|コンパイラエラー C2546|'*identifier*': pia と pia なしの両方で型が定義されている場合、pia を最初に参照する必要があります|
|コンパイラエラー C2547|'*identifier*': パブリッシュされたメソッドのすべてのパラメーターは、宣言で明示的に指定する必要があります|
|[コンパイラ エラー C2548](compiler-error-C2548.md)|'*function*': パラメーター *パラメーター* の既定のパラメーターがありません|
|[コンパイラ エラー C2549](compiler-error-C2549.md)|ユーザー定義の変換では、戻り値の型を指定できません|
|[コンパイラ エラー C2550](compiler-error-C2550.md)|'*identifier*': コンストラクターの初期化子リストは、コンストラクターの定義でのみ使用できます|
|[コンパイラ エラー C2551](compiler-error-C2551.md)|'void *' 型には明示的なキャストが必要です|
|[コンパイラ エラー C2552](compiler-error-C2552.md)|'*identifier*': 非集計は初期化子リストでは初期化できません|
|[コンパイラ エラー C2553](compiler-error-C2553.md)|'*type* *derived_class*::*function*': オーバーライドする仮想関数の戻り値の型が '*type* *base_class*::*function*' と異なります|
|[コンパイラ エラー C2555](compiler-error-C2555.md)|'*derived_class*::*function*': オーバーライドする仮想関数の戻り値の型が異なり、'*base_class*::*function*' からの共変ではありません|
|[コンパイラ エラー C2556](compiler-error-C2556.md)|'*type1* *class*::*function*': オーバーロードされた関数は、' type1 *class*::*function*' からの戻り値の型によってのみ異なります。|
|[コンパイラ エラー C2557](compiler-error-C2557.md)|'*identifier*': プライベートメンバーとプロテクトメンバーをコンストラクターなしで初期化することはできません|
|[コンパイラ エラー C2558](compiler-error-C2558.md)|クラス '*class*': コピーコンストラクターが使用できないか、またはコピーコンストラクターが ' explicit ' と宣言されています|
|コンパイラエラー C2559|'*identifier*': ref 修飾子を持つメンバー関数で、ref 修飾子のないメンバー関数をオーバーロードすることはできません|
|コンパイラエラー C2560|'*identifier*': ref 修飾子のないメンバー関数で ref 修飾子を使用してメンバー関数をオーバーロードすることはできません|
|[コンパイラ エラー C2561](compiler-error-C2561.md)|'*function*': 関数は値を返す必要があります|
|[コンパイラ エラー C2562](compiler-error-C2562.md)|'*function*': ' void ' 関数は値を返します|
|[コンパイラ エラー C2563](compiler-error-C2563.md)|仮パラメーターリストが一致しません|
|コンパイラエラー C2564|互換性のために残されています。|
|コンパイラエラー C2565|'*identifier*': ref 修飾子はコンストラクターまたはデストラクターでは無効です|
|[コンパイラ エラー C2566](compiler-error-C2566.md)|条件式のオーバーロードされた関数|
|[コンパイラ エラー C2567](compiler-error-C2567.md)|'*filename*' のメタデータを開けません。 *possible_reason*|
|[コンパイラ エラー C2568](compiler-error-C2568.md)|'*identifier*': 関数のオーバーロードを解決できません|
|[コンパイラ エラー C2569](compiler-error-C2569.md)|'*identifier*': 列挙型/共用体を基底クラスとして使用することはできません|
|[コンパイラ エラー C2570](compiler-error-C2570.md)|'*identifier*': 共用体に基底クラスを含めることはできません|
|[コンパイラ エラー C2571](compiler-error-C2571.md)|'*identifier*': 仮想関数を共用体 '*union*' に指定することはできません|
|[コンパイラ エラー C2572](compiler-error-C2572.md)|'*function*': 既定の引数の再定義: パラメーター *番号*|
|[コンパイラ エラー C2573](compiler-error-C2573.md)|'*class*': この型のオブジェクトへのポインターを削除することはできません。クラスに ' operator delete ' の非配置オーバーロードがありません。 :D e) を使用するか、クラスに ' operator delete (void *) ' を追加します。|
|[コンパイラ エラー C2574](compiler-error-C2574.md)|'*デストラクター*': static として宣言することはできません。|
|[コンパイラ エラー C2575](compiler-error-C2575.md)|'*identifier*': 仮想にできるのは、メンバー関数と基底クラスのみです|
|コンパイラエラー C2576|'*identifier*': 新しい仮想メソッドを ' public ' として導入することはできません。 メソッドを非仮想にするか、アクセシビリティを ' internal ' または ' protected private ' に変更することを検討してください。|
|[コンパイラ エラー C2577](compiler-error-C2577.md)|'*identifier*': デストラクターまたはファイナライザーに戻り値の型を含めることはできません|
|コンパイラエラー C2578|'*class*': 型に ' protected ' または ' protected public ' コンストラクターを含めることはできません|
|[コンパイラ エラー C2579](compiler-error-C2579.md)|型の *型* (*オフセット*) を解決できません。 *ファイル名* にする必要があります|
|コンパイラエラー C2580|'*identifier*': 既定化された特殊なメンバー関数の複数のバージョンは使用できません|
|[コンパイラ エラー C2581](compiler-error-C2581.md)|'*type*': 静的 ' operator = ' 関数は無効です|
|[コンパイラ エラー C2582](compiler-error-C2582.md)|' operator *operator*' 関数は '*type*' で使用できません|
|[コンパイラ エラー C2583](compiler-error-C2583.md)|'*identifier*': ' const/volatile ' ' this ' ポインターはコンストラクターまたはデストラクターでは無効です|
|[コンパイラ エラー C2584](compiler-error-C2584.md)|'*class*': direct base '*base_class2*' にアクセスできません。'*base_class1*' のベースが既にあります。|
|[コンパイラ エラー C2585](compiler-error-C2585.md)|'*type*' への明示的な変換があいまいです|
|[コンパイラ エラー C2586](compiler-error-C2586.md)|不適切なユーザー定義の変換構文です: 間接指定が無効です。|
|[コンパイラ エラー C2587](compiler-error-C2587.md)|'*identifier*': ローカル変数が既定のパラメーターとして不適切に使用される|
|[コンパイラ エラー C2588](compiler-error-C2588.md)|':: ~*identifier*': 無効なグローバルデストラクターまたはファイナライザーです。|
|[コンパイラ エラー C2589](compiler-error-C2589.md)|'*identifier*': ':: ' の右側に無効なトークンがあります|
|コンパイラエラー C2590|'*identifier*': 基底クラスまたはメンバー初期化子リストを持つことができるのはコンストラクターだけです。|
|コンパイラエラー C2591|ExclusiveTo は、引数として '*type*' を使用することはできません。 ' Ref class ' のみが有効な引数です|
|[コンパイラ エラー C2592](compiler-error-C2592.md)|'*class*': '*base_class2*' は '*base_class1*' から継承されているため、再指定することはできません|
|[コンパイラ エラー C2593](compiler-error-C2593.md)|' operator *identifier*' があいまいです|
|[コンパイラ エラー C2594](compiler-error-C2594.md)|'*operator*': '*type1**' から '* type1 ' へのあいまいな変換です|
|コンパイラエラー C2595|'*identifier*' WinRT 属性の型はシールされなければなりません|
|コンパイラエラー C2596|'*identifier*' WinRT 属性フィールドには、' public enum class '、' int '、' unsigned int '、' bool '、' platform:: Type '、' platform:: String '、または ' Windows:: Foundation:: HResult ' のみを指定できます|
|[コンパイラ エラー C2597](compiler-error-C2597.md)|静的でないメンバー '*identifier*' への参照が無効です|
|[コンパイラ エラー C2598](compiler-error-C2598.md)|リンケージ指定はグローバルスコープである必要があります|
|[コンパイラ エラー C2599](compiler-error-C2599.md)|'*identifier*': マネージ/WinRT 列挙型の事前宣言は使用できません|

## <a name="see-also"></a>関連項目

[C/c + + コンパイラおよびビルドツールのエラーと警告](../compiler-errors-1/c-cpp-build-errors.md) \
[コンパイラエラー C2000-C3999、C7000-C7999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
