---
description: '詳細情報: 既定でオフになっているコンパイラの警告'
title: 既定で無効になっているコンパイラ警告
ms.date: 08/29/2019
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
ms.openlocfilehash: 2178d62318cfc70fd7ec9805999bafb9a61c18cf
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107576912"
---
# <a name="compiler-warnings-that-are-off-by-default"></a>既定で無効になっているコンパイラ警告

コンパイラは、既定では無効になっている警告をサポートしています。これは、ほとんどの開発者がそれを見つけることができないためです。 場合によっては、スタイルが選択されたこと、または古いコードの共通表現について警告することがあります。 その他の警告は、言語に対する Microsoft 拡張機能の使用に関するものです。 一部の警告は、プログラマが誤った想定を行う可能性がある領域を示しています。これは、予期しない動作や未定義の動作につながる可能性があります。 これらの警告がすべて有効になっている場合は、ライブラリヘッダーに何度も表示されることがあります。 C ランタイムライブラリと C++ 標準ライブラリは、警告レベルの [/W4](../build/reference/compiler-option-warning-level.md)でのみ警告を出力することを目的としています。

## <a name="enable-warnings-that-are-off-by-default"></a>既定でオフになっている警告を有効にする

次のいずれかのオプションを使用して、通常は既定でオフになっている警告を有効にすることができます。

- **#pragma warning (既定値:** *warning_number* **)**

   指定された警告 (*warning_number*) は、既定のレベルで有効になっています。 警告に関するドキュメントには、既定のレベルの警告が記載されています。

- **#pragma の警告 (** *warning_level* **:** *warning_number* **)**

   指定された警告 (*warning_number*) は、指定されたレベル (*warning_level*) で有効になっています。

- [/Wall](../build/reference/compiler-option-warning-level.md)

   `/Wall` は既定では無効のすべての警告を有効にします。 このオプションを使用する場合は、 [/wd](../build/reference/compiler-option-warning-level.md) オプションを使用して個々の警告をオフにすることができます。

- [/w *Lnnnn*](../build/reference/compiler-option-warning-level.md)

   このオプションを選択すると、レベル *L* で警告 *nnnn* が有効になります。

## <a name="warnings-that-are-off-by-default"></a>既定でオフになっている警告

Visual Studio 2015 以降のバージョンでは、次の警告が既定で無効になっています。

|警告|メッセージ|
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) (レベル 4)|列挙型 '*enumeration*' のスイッチ内の列挙子 '*identifier*' は、case ラベルによって明示的に処理されていません|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) (レベル 4)|列挙型 '*enumeration*' のスイッチ内の列挙子 '*identifier*' は処理されません|
| [C4165](../error-messages/compiler-warnings/compiler-warning-level-1-c4165.md) (レベル 1) | ' HRESULT ' は ' bool ' に変換されています。これは必要なものですか? |
| [C4191](../error-messages/compiler-warnings/compiler-warning-level-3-c4191.md) (レベル 3)|'*operator*': '*type_of_expression*' から '*type_required*' への安全でない変換です|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) (レベル 4)|'*identifier*': ' type1 *' から '**type1*' への変換です。データが失われる可能性があります。|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) (レベル 4)|'*operator*': ' type1 *' から '**type1*' への変換です。データが失われる可能性があります。|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) (レベル 4)|'*function*': 関数プロトタイプが指定されていません: ' () ' を ' (void) ' に変換しています|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) (レベル 4)|'*function*': メンバー関数は、基底クラスの仮想メンバー関数をオーバーライドしません|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) (レベル 1)|'*virtual_function*': 基底 *クラス ' class*' からの仮想メンバー関数に使用できるオーバーライドはありません。関数は非表示です|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) (レベル 3)|'*class*': クラスは仮想関数を含んでいますが、デストラクターは仮想ではありません|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) (レベル 4)|'*function*': ベース '*type*' から仮想メンバー関数に使用できるオーバーライドはありません。関数は非表示です|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) (レベル 3)|'*operator*': 符号なしまたは負の定数が一致しません。|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) (レベル 4)|非標準の拡張が使用されています: '*var*': for ループで宣言されたループコントロール変数が for ループスコープの外側で使用されています|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) (レベル 4)|'*operator*': 式は常に false です|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) (レベル 4)|'*type*': CLR メタデータで検出された未定義の型が使用されています。この型を使用すると、ランタイム例外が発生する可能性があります|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) (レベル 1)|動作変更: '*function*' が呼び出されましたが、メンバー演算子が前のバージョンで呼び出されました|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) (レベル 1)|動作変更: '*member2*' の代わりに '*member1*' が呼び出されました|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this' : ベース メンバー初期化リストで使用されました。|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) (レベル 4)|'*action*': '*type_1*' から '*type_2*' への変換、符号付き/符号なしの不一致|
|C4370 (レベル 3)|パッキングの改善のために、前バージョンのコンパイラからクラスのレイアウトが変更されました。|
|[C4371](../error-messages/compiler-warnings/c4371.md) (レベル 3)|'*classname*': メンバー '*member*' のパッキングが適切であるため、クラスのレイアウトが以前のバージョンのコンパイラから変更された可能性があります|
|C4388 (レベル 4)|signed と unsigned の数値を比較しようとしました。|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) (レベル 2)|'*function*': 関数シグネチャに型 '*type*' が含まれています。C++ オブジェクトは、純粋なコードと混合またはネイティブの間で渡すことは安全ではありません|
|C4426 (レベル 1)|ヘッダーを含めた後に最適化フラグが変更されました。 #pragma optimize () <sup>14.1</sup>が原因である可能性があります|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) (レベル 4)|'*class1*': 仮想ベース '*class2*' により、/vd2 下のオブジェクトレイアウトが変更されます|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) (レベル 4)|仮想ベース '*class1*' から '*class2*' への dynamic_cast は、一部のコンテキストでは失敗する可能性があります|
|C4444 (レベル 3)|トップ レベルの '__unaligned' がこのコンテキストで実装されていません。|
|[C4464](../error-messages/compiler-warnings/c4464.md) (レベル 4)|相対インクルードパスに '.. ' が含まれています|
|[C4471](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md) (レベル 4)|対象範囲外の列挙の事前宣言には、基になる型 (int と仮定) の<sup>Perm</sup>が必要です|
|C4472 (レベル 1)|'*identifier*' はネイティブ列挙型です。マネージ列挙型を宣言するには、アクセス指定子 (private/public) を追加してください|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) (レベル 4)|'*function*': 参照されていないインライン関数は削除されました|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) (レベル 4)|' type name ': 型名がメタデータの上限である '*limit*' 文字を超えています|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) (レベル 1)|コンマ前の式は、引数リストのない関数として評価します。|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) (レベル 1)|コンマの前の関数呼び出しに引数一覧がありません。|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) (レベル 1)|'*operator*': コンマの前の演算子は無効です。副作用のある演算子が必要です|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) (レベル 1)|コンマ前の式は無効です。有効な式を指定してください。|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) (レベル 1)|'*operator1*': コンマの前の演算子は無効です。'*operator2*' を意図しましたか?|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) (レベル 1)|式の影響はありません; 式の副作用が必要です。|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) (レベル 3)|' __assume ' には '*effect*' 効果が含まれています|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) (レベル 4)|情報: catch (...) の意味が Visual C++ 7.1; 以降に変更されました。構造化例外 (SEH) はキャッチされなくなりました。|
|C4574 (レベル 4)|'*identifier*' は ' 0 ' に定義されています: ' #if *identifier*' を使用しますか?|
|C4577 (レベル 1)|例外処理モードが指定されていない ' noexcept ' が使用されています。例外での終了は保証されていません。 /EHsc を指定する|
|C4582 (レベル 4)|'*type*': コンストラクターは暗黙的に呼び出されません。|
|C4583 (レベル 4)|'*type*': デストラクターは暗黙的に呼び出されません|
|C4587 (レベル 1)|'*anonymous_structure*': 動作変更: コンストラクターは暗黙的に呼び出されなくなりました|
|C4588 (レベル 1)|'*anonymous_structure*': 動作変更: デストラクターは暗黙的に呼び出されなくなりました|
|[C4596](../error-messages/compiler-warnings/c4596.md) (レベル 4)|'*identifier*': メンバー宣言 <sup>14.3</sup> <sup>Perm</sup>内の修飾名が無効です|
|C4598 (レベル1およびレベル 3)|' #include "*header*" ': プリコンパイル済みヘッダーのヘッダー番号 *ヘッダー番号* が、その位置 <sup>14.3</sup>の現在のコンパイルと一致しません|
|C4599 (レベル 3)|'*option* *path*': コマンドライン引数の数値 *がプリコン* パイル済みヘッダー <sup>14.3</sup>と一致しません|
|C4605 (レベル 1)|現在のコマンドラインで '/d *macro*' が指定されましたが、プリコンパイル済みヘッダーがビルドされたときに指定されませんでした|
|[C4608](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md) (レベル 3)|'*union_member*' は、初期化子リスト '*union_member* <sup>' の</sup>別の共用体メンバーによって既に初期化されています。|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) (レベル 3)|#pragma 警告: 警告番号 '*number*' がありません|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) (レベル 4)|'derived class': 基底クラスの既定コンストラクターにアクセスできないため、既定のコンストラクターは生成できませんでした。|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) (レベル 4)|'derived class': 基底クラスのコピー コンストラクターにアクセスできないため、コピー コンストラクターは生成できませんでした。|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) (レベル 4)|'derived class': 基底クラスの代入演算子にアクセスできないため、代入演算子は生成できませんでした。|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) (レベル 1)|digraphs は -Ze でサポートされていません。 文字シーケンス '*digraph*' は '*char*' の代替トークンとして解釈されません|
|[(C4640)](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) (レベル 3)|'*instance*': ローカルの静的オブジェクトの構築はスレッドセーフではありません|
| C4643 (レベル 4) | 名前空間 std の '*identifier*' を事前宣言することは、C++ 標準では許可されていません。 <sup>15.8</sup> |
|C4647 (レベル 3)|動作の変更: __is_pod (*型*) の値が以前のバージョンで異なります。|
|C4654 (レベル 4)|プリコンパイル済みヘッダー行の前に配置されたコードは無視されます。 プリコンパイル済みヘッダーにコードを追加します。 <sup>14.1</sup>|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) (レベル 4)|'*symbol*' はプリプロセッサマクロとして定義されていません。 '*ディレクティブ*' の ' 0 ' に置き換えてください。|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md) (レベル 4)|'*symbol*': 方向性のあるパラメーター属性が指定されていません。 [in] を既定にします|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) (レベル 3)|'*ユーザー定義型*': 動作が変更される可能性があります。 UDT の戻り値の呼び出し規約が変更されています。|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) (レベル 1)|'*function*': プライベートでないメンバーのシグネチャには、アセンブリプライベートネイティブ型 '*native_type*' が含まれています|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) (レベル 4)|'*function*': 関数がインライン化されていません。|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) (レベル 3)|メモリに 32 ビットの浮動結果を格納します。パフォーマンスが低下する可能性があります|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|'*expression*' の volatile アクセスには/volatile: setting が適用されます \<iso&#124;ms> 。 __iso_volatile_load/ストア組み込み関数を使用することを検討してください。|
|C4749 (レベル 4)|条件付きでサポート: offsetof が非標準レイアウト型 '*type*' に適用されました|
|C4767 (レベル 4)|セクション名 '*symbol*' が8文字を超えているため、リンカーによって切り捨てられます|
|C4768 (レベル 3)|リンケージ指定の前の __declspec 属性は無視されます|
|C4774 (レベル 4)|'*string*': 引数 *番号* に必要な書式文字列が文字列リテラルではありません|
|C4777 (レベル 4)|'*function*': 書式文字列 '*string*' には型 ' type1 ' の引数が必要ですが、可変個引数引数の *数値* には *型 '**type1*' が含まれています|
|C4786 (レベル 3)|'*symbol*': オブジェクト名がデバッグ情報の '*number*' 文字に切り詰められました|
| [C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md) (レベル 4) | '*Type*' から bool への暗黙的な変換です。 考えられる情報損失 <sup>16.0</sup> |
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) (レベル 4)|コンストラクト '*member_name*' の後に '*bytes*' バイトのパディングが追加されました|
| [C4822](../error-messages/compiler-warnings/compiler-warning-level-1-c4822.md) (レベル 1) | '*member*': ローカルクラスのメンバー関数に本体がありません。 |
|C4826 (レベル 2)|' Type1 *' から '**type1*' への変換は、符号拡張されています。 これにより、予期しないランタイム動作が発生する可能性があります。|
|C4837 (レベル 4)|検出されたトライグラフ: '??*文字*' は '*character*' に置き換えられました|
|C4841 (レベル 4)|非標準の拡張機能が使用されています: 複合メンバー指定子が offsetof で使用されています|
|C4842 (レベル 4)|複数の継承を使用して型に適用された ' offsetof ' の結果は、コンパイラリリース間で一貫性が保証されていません|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) (レベル 4)|'_file_(*line_number*) ' コンパイラは、かっこ付き初期化リストで左から右への評価順序を強制することはできません|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) (レベル 1)|'LPSTR' にキャストされた幅の広いリテラル文字列|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) (レベル 1)|'LPWSTR' にキャストされたリテラル文字列|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) (レベル 1)|'*宣言子*': GUID は、クラス、インターフェイス、または名前空間にのみ関連付けることができます|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) (レベル 1)|コピー初期化が正しくありません。複数のユーザー定義の変換が暗黙的に適用されています。|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) (レベル 4)|number ビット ポインター用にタイプ ライブラリがビルドされていることを想定します。|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) (レベル 1)|関連するクラス間で使用されている reinterpret_cast: '*class1*' と '*class2*'|
|C4962|'*function*': 最適化によってプロファイルデータに矛盾が生じたため、ガイド付き最適化のプロファイルを無効にします|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) (レベル 4)|'*symbol*': 例外指定が前の宣言と一致しません|
|C4987 (レベル 4)|非標準の拡張機能が使用されています: 'throw (...)' です。|
|C4988 (レベル 4)|'*symbol*': 変数がクラス/関数スコープの外部で宣言されています。|
|C5022|'*type*': 複数の移動コンストラクターが指定されました|
|C5023|'*type*': 複数の移動代入演算子が指定されています。|
|C5024 (レベル 4)|'*type*': 移動コンストラクターが暗黙的に削除済みとして定義されました|
|C5025 (レベル 4)|'*type*': 移動代入演算子は暗黙的に削除済みとして定義されました|
|C5026 (レベル1およびレベル 4)|'*type*': 移動コンストラクターが暗黙的に削除済みとして定義されました|
|C5027 (レベル1およびレベル 4)|'*type*': 移動代入演算子は暗黙的に削除済みとして定義されました|
|C5029 (レベル 4)|非標準の拡張機能が使用されています: C++ のアラインメント属性は変数、データメンバー、タグの種類にのみ適用されます|
|C5031 (レベル 4)|#pragma 警告 (pop): 不一致の可能性があります。ポップアップの警告状態が別のファイル<sup>14.1</sup>にプッシュされました|
|C5032 (レベル 4)|検出された #pragma 警告 (プッシュ) に対応する #pragma 警告 (pop) <sup>14.1</sup>がありません|
|C5034|組み込みの '*組み込み*' を使用すると、関数の *名前* がゲストコード <sup>15.3</sup>としてコンパイルされます。|
|C5035|機能 '*feature*' を使用すると *、* 関数の名前がゲストコード <sup>15.3</sup>としてコンパイルされます|
|C5036 (レベル 1)|/hybrid: x86arm64 ' type1 *' から '**type1*' <sup>15.3</sup>を使用してコンパイルするときの varargs 関数ポインター変換|
|[C5038](../error-messages/compiler-warnings/c5038.md) (レベル 4)|データメンバー '*member1*' はデータメンバー '*member2*' <sup>15.3</sup>の後に初期化されます|
|C5039 (レベル 4)|'*function*':-ehc で extern c 関数に渡される可能性のあるスロー関数へのポインターまたは参照です。 この関数が例外をスローした場合、未定義の動作が発生する可能性があります。 <sup>15.5</sup>|
| C5041 "(レベル 4) | '*メンバー名*': constexpr 静的データメンバーのアウトオブライン定義は必要ありません。 c++ 17 では非推奨とされます。 <sup>15.2</sup>|
|C5042 (レベル 3)|'*function*': 標準 C++ では、ブロックスコープの関数宣言を ' inline ' として指定することはできません。' inline ' 指定子 <sup>15.5</sup>の削除|
|[C5045](../error-messages/compiler-warnings/c5045.md)|/Qspectre スイッチが指定されている場合、コンパイラはメモリ負荷の Spectre 軽減策を挿入します。 <sup>15.7</sup>|
| C5204 (レベル 3) | 仮想関数を持つクラスには、非仮想の自明なデストラクターがあります。 <sup>16.5</sup> |
| C5214 (レベル 4) | volatile 修飾型のオペランドに '*keyword*' を適用することは、c++ 20 <sup>16.7</sup>では非推奨とされます |
| C5215 (レベル 4) | '*関数* パラメーター ' volatile で修飾された型の関数パラメーターは、c++ 20 <sup>16.7</sup>では非推奨とされます |
| C5216 (レベル 4) | '*戻り* 値の型 ' volatile で修飾された戻り値の型は c++ 20 <sup>16.7</sup>で非推奨とされます |
| C5217 (レベル 4) | volatile を含む構造化バインド宣言は、C++ 20 <sup>16.7</sup>では非推奨とされます。 |
| C5219 (レベル 2) | '*type-1*' から '*type-2*' への暗黙的な変換です。データが失われる可能性があります。 <sup>16.7</sup> |
| C5220 (レベル 4) | '*member*': volatile で修飾された型を持つ非静的データメンバーは、<br/> コンパイラで生成されたコピー/移動コンストラクターとコピー/移動代入演算子が自明ではない <sup>16.7</sup> |

<sup>14.1</sup> Visual Studio 2015 Update 1 以降では、この警告を利用できます。
<sup>14.3</sup> Visual Studio 2015 Update 3 以降では、この警告を利用できます。
<sup>15.2</sup> Visual Studio 2017 バージョン15.2 以降では、この警告は使用できます。
<sup>15.3</sup> Visual Studio 2017 バージョン15.3 以降では、この警告は使用できます。
<sup>15.5</sup> Visual Studio 2017 バージョン15.5 以降では、この警告は使用できます。
<sup>15.7</sup> Visual Studio 2017 バージョン15.7 以降では、この警告は使用できます。
<sup>15.8</sup> Visual Studio 2017 バージョン15.8 以降では、この警告は使用できます。
<sup>16.0</sup> この警告は、Visual STUDIO 2019 RTM 以降で使用できます。
<sup>16.5</sup> Visual Studio 2019 バージョン16.5 以降では、この警告は使用できます。
<sup>16.7</sup> Visual Studio 2019 バージョン16.7 以降では、この警告は使用できます。
<sup>Perm</sup> この警告は、 [/permissive-](../build/reference/permissive-standards-conformance.md) コンパイラオプションが設定されていない場合にオフになります。

## <a name="warnings-off-by-default-in-earlier-versions"></a>以前のバージョンでは、既定で警告がオフになっています

これらの警告は、Visual Studio 2015 より前のバージョンのコンパイラでは既定でオフになっていました。

|警告|メッセージ|
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) (レベル 2)|'*conversion*': ' type1 *' から '**type1*' への切り捨て|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) (レベル 1)|'*variable*': ポインターが '*type*' から '*type*' に切り捨てられる|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) (レベル 1)|'*operation*': ' type1 ' からより大きいサイズ *の '**type1*' への変換です。|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) (レベル 1)|'*operator*': ' type1 ' をより大きいサイズ *の '**type1*' に拡張することはできません。|

この警告は、Visual Studio 2012 より前のバージョンのコンパイラでは既定で無効になっていました。

|警告|メッセージ|
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) (レベル 4)|型指定子がありません - int と仮定しました。 メモ: C は、現在 int を既定値としてサポートしていません|

## <a name="see-also"></a>関連項目

[warning](../preprocessor/warning.md)
