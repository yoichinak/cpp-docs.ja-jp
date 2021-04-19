---
description: 詳細については、「コンパイラの警告 C4400 から C4599 まで」を参照してください。
title: コンパイラ警告 (C4400 - C4599)
ms.date: 04/21/2019
f1_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4452
- C4453
- C4454
- C4455
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
helpviewer_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4451
- C4452
- C4453
- C4454
- C4455
- C4456
- C4457
- C4459
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
ms.assetid: b07850a5-ae89-48ea-bf9a-f0e30939f9b9
ms.openlocfilehash: c27f73174c98b40efe7ef0d932ea4b2f8f371988
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721187"
---
# <a name="compiler-warnings-c4400-through-c4599"></a>コンパイラ警告 (C4400 - C4599)

ドキュメントのこのセクションの記事では、コンパイラによって生成される警告メッセージのサブセットについて説明します。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>警告メッセージ

|警告|メッセージ|
|-------------|-------------|
|[コンパイラ警告 (レベル 1) C4600](compiler-warning-level-1-c4600.md)|#pragma '*macro name*': 有効な空でない文字列が必要です。|
|[コンパイラ警告 (レベル 4) C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|'*type*': この型の const/volatile 修飾子はサポートされていません|
|[コンパイラ警告 (レベル 1) C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|'*ビットフィールド*': メンバーはビットフィールドです|
|[コンパイラ警告 (レベル 1) C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|PTR 演算子を使用する必要があります|
|[コンパイラ警告 (レベル 1) C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|無効な PTR 演算子|
|[コンパイラ警告 (レベル 3) C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|ディレクティブの期間が無視されました|
|[コンパイラ警告 (レベル 1) C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|'*identifier*': 識別子は予約語です|
|[コンパイラ警告 (レベル 1) C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|ディレクティブのオペランドが無視されました|
|[コンパイラ警告 (レベル 1) C4407](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|異なるポインター間でメンバー表現がキャストされると、コンパイラが正しくないコードを生成する可能性があります|
|[コンパイラ警告 (レベル 4) C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|匿名の ' struct&#124;union ' はデータメンバーを宣言しませんでした|
|[コンパイラ警告 (レベル 1) C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|命令サイズが無効です|
|[コンパイラ警告 (レベル 1) C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|オペランドのサイズが正しくありません|
|[コンパイラ警告 (レベル 1) C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|'*identifier*': シンボルはディスプレイスメントレジスタに解決されます|
|[コンパイラ警告 (レベル 2) C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|'*function*': 関数シグネチャに型 '*type*' が含まれています。C++ オブジェクトは、純粋なコードと混合またはネイティブの間で渡すことは安全ではありません。|
|コンパイラの警告 C4413|' classname:: member ': 参照メンバーは、コンストラクターが終了した後に保持されない一時的なに初期化されています|
|[コンパイラ警告 (レベル 3) C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|'*function*': near に変換された関数への short ジャンプ|
|コンパイラの警告 (レベル 1) C4415|__declspec が重複しています (code_seg ('*name*'))|
|コンパイラの警告 (レベル 1) C4416|__declspec (code_seg (...)) に空の文字列が含まれています。無視されます|
|コンパイラの警告 (レベル 1) C4417|明示的なテンプレートのインスタンス化には、__declspec (code_seg (...)) を含めることはできません。無視されます|
|コンパイラの警告 (レベル 1) C4418|__declspec (code_seg (...)) は列挙型で無視されます|
|コンパイラの警告 (レベル 3) C4419|プライベート ref クラス '*class*' に適用した場合、'*symbol*' は無効です。|
|[コンパイラ警告 (レベル 1) C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|'*checked_operator*': 演算子は使用できません。代わりに '*operator*' を使用します。実行時チェックが危害を受ける可能性があります|
|コンパイラの警告 (レベル 3) C4421|'*parameter*': 再開可能な関数の参照パラメーターが安全でない可能性があります|
|コンパイラの警告 (レベル 3) C4423|' std:: bad_alloc ': 行 *番号* のクラス ('*type*') によってキャッチされます|
|コンパイラの警告 (レベル 3) C4424|行 *番号* で ' type1 ' の前 *に '**type1*' があることをキャッチします。' std:: bad_alloc ' がスローされた場合、予期しない動作が発生する可能性があります|
|コンパイラの警告 (レベル 1) C4425|SAL 注釈を '... ' に適用することはできません|
|コンパイラの警告 (レベル 1) C4426|ヘッダーを含めた後に最適化フラグが変更されました。 #pragma optimize () が原因である可能性があります。|
|コンパイラの警告 (レベル 1) C4427|'*operator*': 定数除算でオーバーフローが発生しています。未定義の動作です。|
|[コンパイラ警告 (レベル 4) C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|不完全または不適切な形式のユニバーサル文字名です。|
|[コンパイラの警告 (エラー) C4430](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|型指定子がありません - int と仮定しました。 注: C++ では既定の-int はサポートされていません|
|[コンパイラ警告 (レベル 4) C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|型指定子がありません - int と仮定しました。 メモ: C は、現在 int を既定値としてサポートしていません|
|[コンパイラ警告 (レベル 4) C4434](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|静的コンストラクターにはプライベートアクセシビリティが必要です。プライベートアクセスへの変更|
|[コンパイラ警告 (レベル 4) C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|'*derived_class*': 仮想ベース '*base_class*' により、/vd2 下のオブジェクトレイアウトが変更されます|
|[コンパイラ警告 (レベル 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|\_コンストラクターまたはデストラクター内の仮想ベース '*base_class*' から '*derived_class*' への動的キャストが、部分的に構築されたオブジェクトで失敗する可能性があります|
|[コンパイラ警告 (レベル 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|\_仮想ベース '*base_class*' から '*derived_class*' への動的キャストは、一部のコンテキストでは失敗する可能性があります|
|コンパイラの警告 C4438|'*function*': clrcompat モードで安全に呼び出すことはできません。 '*Function*' が clr に対して呼び出した場合、clr ヘッドの破損が発生する可能性があります|
|[コンパイラの警告 (エラー) C4439](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|'*function*': シグネチャのマネージ型を持つ関数定義には __clrcall の呼び出し規約が必要です|
|[コンパイラ警告 (レベル 1) C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|'*calling_convention1*' から '*calling_convenction2*' への呼び出し規約の再定義は無視されます|
|[コンパイラ警告 (レベル 1) C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|'*calling_convention1*' の呼び出し規約が無視されました。'*calling_convention2*' が代わりに使用されています|
|コンパイラの警告 (レベル 1) C4442|__annotation 引数に埋め込まれた null ターミネータです。  値は切り捨てられます。|
|コンパイラの警告 (レベル 1) C4443|プラグマパラメーターは ' 0 '、' 1 '、または ' 2 ' である必要があります|
|コンパイラの警告 (レベル 3) C4444|'*identifier*': 最上位レベルの ' __unaligned ' はこのコンテキストでは実装されていません|
|[コンパイラ警告 (レベル 1) C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|'*function*': ' WinRT&#124;マネージ ' 型では、仮想メソッドをプライベートにすることはできません|
|コンパイラの警告 (レベル 1) C4446|'*type*': 型名と競合するため、メンバー '*name1*' をこの型にマップできません。 メソッドの名前が '*name2*' に変更されました|
|コンパイラの警告 (レベル 1) C4447|スレッドモデルのない ' main ' シグネチャが見つかりました。 ' Int main (Platform:: Array \<Platform::String^> ^ args) ' の使用を検討してください。|
|コンパイラの警告 C4448|'*type* 1 ' には、メタデータで指定された既定のインターフェイスがありません。 *' ': ' は* 実行時に失敗する可能性があるため、選択しています。|
|コンパイラの警告 C4449|'*type*' は、封印されていない型を ' [WebHostHidden] ' としてマークする必要があります|
|コンパイラの警告 C4450|'*type1*'*は ' type1 ' から* 派生しているため、' type1 ' を ' [WebHostHidden] ' としてマークする必要があります|
|コンパイラの警告 (レベル 4) C4451|' classname1:: member ': このコンテキスト内で ref クラス ' classname2:: member ' を使用すると、コンテキストをまたがるオブジェクトのマーシャリングが無効になる可能性があります|
|コンパイラの警告 (レベル 1) C4452|'*identifier*': パブリック型をグローバルスコープで指定することはできません。 これは、出力 winmd ファイルの名前の子である名前空間に存在する必要があります。|
|コンパイラの警告 (レベル 1) C4453|'*type*': ' [WebHostHidden] ' 型は、' [WebHostHidden] ' ではないパブリック型の発行されたサーフェイスでは使用できません|
|コンパイラの警告 (レベル 1) C4454|'*function*' は、[DefaultOverload] が指定されていない入力パラメーターの数を超えてオーバーロードされています。 '*宣言*' を既定のオーバーロードとして選択しています|
|コンパイラの警告 (レベル 1) C4455|' operator *operator*': アンダースコアで始まらないリテラルサフィックス識別子は予約されています|
|[コンパイラ警告 (レベル 4) C4456](compiler-warning-level-4-c4456.md)|'*identifier*' を宣言すると、以前のローカル宣言が非表示になります|
|[コンパイラ警告 (レベル 4) C4457](compiler-warning-level-4-c4457.md)|'*identifier*' を宣言すると、関数パラメーターが非表示になります|
|[コンパイラ警告 (レベル 4) C4458](compiler-warning-level-4-c4458.md)|'*identifier*' の宣言はクラスメンバーを非表示にします|
|[コンパイラ警告 (レベル 4) C4459](compiler-warning-level-4-c4459.md)|'*identifier*' を宣言すると、グローバル宣言が非表示になります|
|[コンパイラ警告 (レベル 4) C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|' WinRT&#124;マネージ ' 演算子 '*operator*' には、参照によって渡されたパラメーターがあります。 ' WinRT&#124;マネージ ' 演算子 '*operator '* は C++ 演算子 '*cpp_operator*' とは異なるセマンティクスを持っています。値渡しで渡すつもりでしたか?|
|[コンパイラ警告 (レベル 1) C4461](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|'*classname*': このクラスにはファイナライザー '! があります。*ファイナライザー*' ですが、デストラクター ' ~*dtor*' はありません。|
|[コンパイラの警告 (レベル1、エラー) C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|'*type*': 型の GUID を特定できません。 プログラムは、実行時に失敗する可能性があります。|
|[コンパイラ警告 (レベル 4) C4463](compiler-warning-level-4-c4463.md)|超え'*min_value*' から '*max_value*' までの値のみを保持できるビットフィールドに '*value*' を代入しています|
|[コンパイラ警告 (レベル 4) C4464](../../error-messages/compiler-warnings/compiler-warning-level-4-c4464.md)|相対インクルードパスに '.. ' が含まれています|
|[コンパイラ警告 (レベル 1) C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|浮動小数点制御プラグマは/clr で無視されます|
|[コンパイラ警告 (レベル 4) C4471](compiler-warning-level-4-c4471.md)|'*enumeration*': 対象範囲外の列挙の事前宣言には基になる型 (int と仮定) を指定する必要があります|
|コンパイラの警告 (レベル 1) C4472|'*identifier*' はネイティブ列挙型です: アクセス指定子 (private/public) を追加して ' WinRT&#124;managed ' 列挙型を宣言してください|
|[コンパイラ警告 (レベル 1) C4473](c4473.md)|'*function*': 書式文字列に渡された引数が不足しています|
|コンパイラの警告 (レベル 3) C4474|'*function*': 書式文字列に渡された引数が多すぎます|
|コンパイラの警告 (レベル 3) C4475|'*function*': 長さの修飾子 '*modifier*' は、書式指定子の型フィールド文字 '*character*' と共に使用することはできません|
|コンパイラの警告 (レベル 3) C4476|'*function*': 書式指定子に不明な型フィールド文字 '*character*' があります。|
|[コンパイラ警告 (レベル 1) C4477](c4477.md)|'*function*': 書式文字列 '*string*' には型 '*type*' の引数が必要ですが、可変個引数引数の数値には型 '*type*' が *指定* されています|
|コンパイラの警告 (レベル 1) C4478|'*function*': 位置指定プレースホルダーと位置指定されていないプレースホルダーを同じ書式指定文字列に混在させることはできません|
|コンパイラの警告 (エラー) C4480|非標準の拡張機能が使用されています: 列挙型 '*enumeration*' の基になる型を指定します|
|[コンパイラ警告 (レベル 4) C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|非標準の拡張が使用されています: オーバーライド指定子 '*keyword*'|
|コンパイラの警告 C4482|非標準の拡張機能が使用されています: 修飾名で使用される列挙型 '*enumeration*'|
|コンパイラの警告 (レベル1、エラー) C4483|構文エラー: C++ のキーワードが必要です|
|[コンパイラの警告 (エラー) C4484](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|'*override_function*': 基本 ref クラスメソッド '*base_class_function*' と一致しますが、' virtual '、' new '、' override ' に設定されていません。' new ' (' virtual ' ではなく) が想定されています|
|[コンパイラの警告 (エラー) C4485](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|'*override_function*': 基本 ref クラスメソッド '*base_class_function*' と一致しますが、' new ' または ' override ' に設定されていません。' new ' (および ' virtual ') が想定されています|
|[コンパイラ警告 (レベル 1) C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|'*function*': ref クラスまたは値クラスのプライベート仮想メソッドは ' sealed ' に設定されなければなりません|
|[コンパイラ警告 (レベル 4) C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|'*derived_class_function*': 継承された仮想でないメソッド '*base_class_function*' と一致しますが、' new ' として明示的に設定されていません|
|[コンパイラ警告 (レベル 1) C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|'*function*': インターフェイスメソッド '*interface_method*' を実装するには、'*keyword*' キーワードが必要です|
|[コンパイラ警告 (レベル 1) C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|'*指定子*': インターフェイスメソッド '*method*' では許可されていません。オーバーライド指定子は、ref クラスおよび値クラスメソッドでのみ使用できます|
|[コンパイラ警告 (レベル 1) C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|' override ': オーバーライド指定子の使い方が正しくありません。'*function*' が基本 ref クラスメソッドと一致しません|
|コンパイラの警告 (レベル 1) C4491|'*name*': 無効な IDL バージョン形式が指定されています。|
|コンパイラの警告 (レベル1、エラー) C4492|'*function1*': 基本 ref クラスメソッド '*function2*' と一致しますが、' override ' に設定されていません|
|コンパイラの警告 (レベル3、エラー) C4493|'*type*' のデストラクターには ' public ' アクセシビリティが設定されていないため、delete 式は無効です。|
|コンパイラの警告 (レベル 1) C4494|'*function*': 関数の戻り値の型がポインターまたは参照ではないため、__declspec (アロケーター) を無視します|
|コンパイラの警告 C4495|非標準の拡張機能 ' __super ' が使用されています: 明示的な基底クラス名に置き換えてください|
|コンパイラの警告 C4496|非標準の拡張機能 ' for each ' が使用されています: replace-for ステートメントで置き換えてください|
|コンパイラの警告 C4497|非標準の拡張機能 ' sealed ' が使用されています: ' final ' に置き換えてください|
|コンパイラの警告 C4498|非標準の拡張機能が使用されています: '*extension*'|
|コンパイラの警告 (レベル 4) C4499|'*function*': 明示的な特殊化にストレージクラスを含めることはできません (無視) "|
|[コンパイラ警告 (レベル 1) C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|'*リンケージ指定*' にはキーワード ' extern ' を使用する必要があります。他のすべての指定子の前に指定しなければなりません。|
|[コンパイラ警告 (レベル 1) C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|'*identifier*': 装飾名の長さが制限を超えています。名前が切り詰められました|
|[コンパイラ警告 (レベル 4) C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|'*function*': 参照されていないローカル関数は削除されました|
|[コンパイラ警告 (レベル 1) C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|インライン関数 '*function*' の定義がありません。|
|[コンパイラ警告 (レベル 1) C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|'*function*': 関数は値を返す必要があります。戻り値の型として ' void ' が想定されます|
|コンパイラの警告 C4509|非標準の拡張機能が使用されています: '*function*' は SEH を使用し、'*object*' はデストラクターを含んでいます|
|[コンパイラ警告 (レベル 4) C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|'*class*': 既定のコンストラクターは暗黙的に削除済みとして定義されました|
|[コンパイラ警告 (レベル 3) C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|'*class*': コピーコンストラクターは暗黙的に削除済みとして定義されました|
|[コンパイラ警告 (レベル 4) C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|'*class*': 代入演算子は暗黙的に削除済みとして定義されました|
|[コンパイラ警告 (レベル 4) C4513](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|'*class*': デストラクターは暗黙的に削除済みとして定義されました|
|[コンパイラ警告 (レベル 4) C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|'*function*': 参照されていないインライン関数は削除されました|
|[コンパイラ警告 (レベル 4) C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|'*namespace*': 名前空間はそれ自体を使用します|
|[コンパイラ警告 (レベル 4) C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|' class:: symbol ': アクセス宣言は推奨されていません。メンバー using 宣言は、より優れた代替手段を提供します。|
|[コンパイラ警告 (レベル 4) C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|アクセス宣言は非推奨とされます。メンバー using 宣言は、より優れた代替手段を提供します。|
|[コンパイラ警告 (レベル 1) C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|'*指定子*': ストレージクラスまたは型指定子が予期せずになりました。無効|
|コンパイラの警告 (エラー) C4519|既定のテンプレート引数はクラステンプレートでのみ使用できます|
|[コンパイラ警告 (レベル 3) C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|'*class*': 複数のコピーコンストラクターが指定されました|
|[コンパイラ警告 (レベル 3) C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|'*class*': 複数の代入演算子が指定されています。|
|[コンパイラ警告 (レベル 3) C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|'*class*': 複数のデストラクターが指定されています。|
|[コンパイラ警告 (レベル 1) C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|'*function*': 静的メンバー関数は、仮想関数 '*virtual* function ' のオーバーライドを無視できません。仮想関数は非表示になります|
|[コンパイラ警告 (レベル 1) C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|C++ 例外ハンドラーが使用されましたが、アンワインドセマンティクスが有効になっていません。 /EHsc を指定する|
|コンパイラの警告 (レベル 1) C4531|C++ 例外処理は Windows CE では使用できません。 構造化例外処理の使用|
|[コンパイラ警告 (レベル 1) C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|' continue ': ' __finally/finally ' ブロックからジャンプすると、終了処理中に未定義の動作が発生します|
|[コンパイラ警告 (レベル 1) C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|'*variable*' の初期化が '*goto label*' によってスキップされました|
|[コンパイラ警告 (レベル 3) C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|'*constructor*' は、既定の引数のため、' class/struct ' '*identifier*' の既定のコンストラクターにはなりません|
|[コンパイラ警告 (レベル 3) C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|_set_se_translator () の呼び出しには/EHa が必要です|
|[コンパイラ警告 (レベル 4) C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|'*typename*': 型名がメタデータの制限 '*character_limit*' 文字を超えています。|
|[コンパイラ警告 (レベル 1) C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|'*object*': '. ' は UDT 型以外に適用されています|
|[コンパイラ警告 (レベル 3) C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|'*type*': この型の const/volatile 修飾子はサポートされていません|
|[コンパイラ警告 (レベル 1) C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|アクセスできない、またはあいまいなベースへの変換に使用 dynamic_castランタイムテストが失敗します ('*type1**' から '* type1 ')|
|[コンパイラ警告 (レベル 1) C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|'*identifier*' は、ポリモーフィックな型 '*type*' で/gr-; で使用されています予期しない動作が発生する可能性があります|
|コンパイラの警告 (レベル 1) C4542|マージされた挿入されたテキストファイルの生成をスキップします。 *filetype* ファイルを書き込めません: '*issue*': *message*|
|[コンパイラ警告 (レベル 3) C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|属性 ' no injected_text ' によって抑制された挿入テキスト \_|
|[コンパイラ警告 (レベル 1) C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|'*宣言*': このテンプレート宣言では、既定のテンプレート引数が無視されます|
|[コンパイラ警告 (レベル 1) C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|コンマ前の式は、引数リストのない関数として評価します。|
|[コンパイラ警告 (レベル 1) C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|コンマの前の関数呼び出しに引数一覧がありません。|
|[コンパイラ警告 (レベル 1) C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|'*operator*': コンマの前の演算子は無効です。副作用のある演算子が必要です|
|[コンパイラ警告 (レベル 1) C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|コンマ前の式は無効です。有効な式を指定してください。|
|[コンパイラ警告 (レベル 1) C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|'*operator*': コンマの前の演算子は無効です。'*operator*' を意図しましたか?|
|[コンパイラ警告 (レベル 1) C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|式は引数リストのない関数に評価されます|
|[コンパイラ警告 (レベル 1) C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|関数呼び出しに引数リストがありません|
|[コンパイラ警告 (レベル 1) C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|'*operator*': 演算子は無効です。副作用のある演算子が必要です|
|[コンパイラ警告 (レベル 1) C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|'*operator*': 演算子は無効です。' 演算子を使用しましたか?|
|[コンパイラの警告 (レベル 3) C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md) C4554|'*operator*': 演算子の優先順位に誤りがあることを確認してください。かっこを使用して優先順位を明確にする|
|[コンパイラ警告 (レベル 1) C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|式の影響はありません; 式の副作用が必要です。|
|[コンパイラ警告 (レベル 1) C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|組み込み直接引数 '*value*' の値が範囲 '*lower_bound*  -  *upper_bound*' を超えています|
|[コンパイラ警告 (レベル 3) C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|' __assume ' には '*effect*' 効果が含まれています|
|[コンパイラ警告 (レベル 1) C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|オペランド '*value*' の値が '*lower_bound*  -  *upper_bound*' の範囲を超えています|
|[コンパイラ警告 (レベル 4) C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|'*function*': 再定義します。関数は __declspec (修飾子) を取得します。|
|[コンパイラ警告 (レベル 1) C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|' __fastcall ' は '/clr ' オプションと互換性がありません: ' __stdcall ' に変換しています|
|コンパイラの警告 (レベル 4) C4562|'/clr ' オプションでは完全なプロトタイプ関数が必要です: ' () ' を ' (void) ' に変換します。|
|[コンパイラ警告 (レベル 4) C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|' class ' '*classname*' のメソッド '*method*' で、サポートされていない既定のパラメーター '*parameter*' が定義されています|
|[コンパイラ警告 (レベル 4) C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|'*function*': 再定義します。シンボルは、以前に __declspec (修飾子) を使用して宣言されていました。|
|[コンパイラ警告 (レベル 1) C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|ユニバーサル文字名 '*char*' で表される文字は、現在のコードページ (*number*) では表現できません|
|コンパイラの警告 (レベル 1) C4568|'*function*': 明示的なオーバーライドのシグネチャと一致するメンバーはありません|
|コンパイラの警告 (レベル 3) C4569|'*function*': 明示的なオーバーライドのシグネチャと一致するメンバーはありません|
|[コンパイラ警告 (レベル 3) C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|'*type*': は抽象として明示的に宣言されていませんが、抽象関数を含んでいます|
|[コンパイラ警告 (レベル 4) C4571](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|情報: catch (...) の意味が Visual C++ 7.1; 以降に変更されました。構造化例外 (SEH) はキャッチされなくなりました。|
|[コンパイラ警告 (レベル 1) C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|[ParamArray] 属性は/clr で非推奨とされます。 '... ' を使用してください。その代わりに|
|コンパイラの警告 (レベル 1) C4573|'*ラムダ関数*' を使用するには、コンパイラが ' this ' をキャプチャする必要がありますが、現在の既定のキャプチャモードでは許可されていません|
|コンパイラの警告 (レベル 4) C4574|'*Identifier*' は ' 0 ' に定義されています: ' #if Identifier ' を使用しますか?|
|コンパイラの警告 (レベル 1) C4575|' __vectorcall ' は '/clr ' オプションと互換性がありません: ' __stdcall ' に変換しています|
|コンパイラの警告 (レベル1、エラー) C4576|初期化子リストが続くかっこで囲まれた型は、標準でない明示的な型変換構文です|
|[コンパイラの警告 (レベル1、Off) C4577](../../error-messages/compiler-warnings/compiler-warning-level-1-c4577.md)|例外処理モードが指定されていない ' noexcept ' が使用されています。例外での終了は保証されていません。 /EHsc を指定する|
|コンパイラの警告 (レベル1、エラー) C4578|' abs ': ' type1 *' から '**type1*' への変換です。データが失われる可能性があります ('*function*' を呼び出すか、#include し \<cmath> ますか?)|
|[コンパイラ警告 (レベル 3) C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[attribute] は非推奨とされます。System::Attribute または Platform::Metadata を基底クラスとして指定してください|
|[コンパイラ警告 (レベル 1) C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|非推奨の動作: 属性を処理するために ' "*string*" ' が '*string*' に置き換えられました|
|コンパイラの警告 (レベル 4) C4582|'*type*': コンストラクターは暗黙的に呼び出されません。|
|コンパイラの警告 (レベル 4) C4583|'*type*': デストラクターは暗黙的に呼び出されません|
|[コンパイラ警告 (レベル 1) C4584](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|'*class1*': 基底クラス '*class2*' は既に '*class3*' の基底クラスです|
|コンパイラの警告 (レベル1、エラー) C4585|'*class*': WinRT ' public ref class ' は、シールドするか、既存の封印されていないクラスから派生しなければなりません|
|コンパイラの警告 (レベル1、エラー) C4586|'*type*': パブリック型を ' Windows ' という名前の最上位レベルの名前空間で宣言することはできません|
|コンパイラの警告 (レベル 1) C4587|'*anonymous_structure*': 動作変更: コンストラクターは暗黙的に呼び出されなくなりました|
|コンパイラの警告 (レベル 1) C4588|'*anonymous_structure*': 動作変更: デストラクターは暗黙的に呼び出されなくなりました|
|コンパイラの警告 (レベル 1) C4591|' constexpr ' 呼び出しの *深さの上限* を超えています (/constexpr: depth \<NUMBER> )|
|コンパイラの警告 (レベル 3) C4592|'*function*': ' constexpr ' 呼び出し評価に失敗しました。関数は実行時に呼び出されます|
|コンパイラの警告 (レベル 1) C4593|'*function*': ' constexpr ' 呼び出しの評価ステップの制限 '*limit*' を超えています。制限を増やすには、/constexpr: ステップを使用します \<NUMBER>|
|コンパイラの警告 (レベル 3) C4594|'*type*': 例外がスローされた場合、デストラクターは暗黙的に呼び出されません|
|コンパイラの警告 (レベル 1) C4595|'*type*': 動作の変更: 例外がスローされた場合、デストラクターは暗黙的に呼び出されなくなりました|
|[コンパイラ警告 (レベル 4) C4596](../../error-messages/compiler-warnings/c4596.md)|'*identifier*': メンバー宣言内の修飾名が無効です|
|コンパイラの警告 (エラー) C4597|未定義の動作: offsetof が仮想ベースのメンバーに適用されています|
|コンパイラの警告 (レベル1およびレベル 3) C4598|' #include "*ヘッダー*" ': プリコンパイル済みヘッダーのヘッダー番号 *番号* が、その位置の現在のコンパイルと一致しません|
|コンパイラの警告 (レベル 3) C4599|'*flag* *path*': コマンドライン引数の番号 *番号* がプリコンパイル済みヘッダーと一致しません|

## <a name="see-also"></a>関連項目

[C/c + + コンパイラおよびビルドツールのエラーと警告](../compiler-errors-1/c-cpp-build-errors.md) \
[コンパイラ警告 (C4000 - C5999)](compiler-warnings-c4000-c5999.md)
