---
description: 詳細については、「コンパイラの警告 C4600 から C4799 まで」を参照してください。
title: コンパイラ警告 (C4600 - C4799)
ms.date: 04/21/2019
f1_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
helpviewer_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
ms.openlocfilehash: 4533838f099fbbc3fc4e46ec523ac928ba531e46
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721200"
---
# <a name="compiler-warnings-c4600-through-c4799"></a>コンパイラ警告 (C4600 - C4799)

ドキュメントのこのセクションの記事では、コンパイラによって生成される警告メッセージのサブセットについて説明します。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>警告メッセージ

|警告|メッセージ|
|-------------|-------------|
|[コンパイラ警告 (レベル 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma ' macro name ': 有効な空でない文字列が必要です。|
|[コンパイラ警告 (レベル 1) C4602](compiler-warning-level-1-c4602.md)|#pragma pop_macro: ' macro name ' は、この識別子に対して以前の #pragma push_macro がありません|
|[コンパイラ警告 (レベル 1) C4603](compiler-warning-level-1-c4603.md)|'*identifier*': マクロが定義されていないか、プリコンパイル済みヘッダーの使用後に定義が異なります|
|コンパイラの警告 (レベル 1) C4604|'*type*': ネイティブとマネージの境界を越えて値渡しで引数を渡すには、有効なコピーコンストラクターが必要です。 それ以外の場合、ランタイムの動作は定義されません。|
|コンパイラの警告 (レベル 1) C4605|現在のコマンドラインで '/d *macro*' が指定されましたが、プリコンパイル済みヘッダーがビルドされたときに指定されませんでした|
|[コンパイラ警告 (レベル 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma 警告: ' warning number ' が無視されました。コード分析の警告は警告レベルに関連付けられていません|
|[コンパイラ警告 (レベル 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|'union_member' は既に初期化子リスト 'union_member' 内の他の共用体メンバーにより初期化されています。|
|コンパイラの警告 (レベル3、エラー) C4609|'*type1**' は、型 '* type1 ' の既定のインターフェイス '*interface*' から派生しています。 '*Type1*' に対して別の既定のインターフェイスを使用するか、基本/派生リレーションシップを解除してください。|
|[コンパイラ警告 (レベル 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|オブジェクト ' class ' をインスタンス化することはできません。ユーザー定義のコンストラクターが必要です|
|[コンパイラ警告 (レベル 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|' function ' と C++ オブジェクトの破棄の間の相互作用は、移植不可です|
|[コンパイラ警告 (レベル 1) C4612](compiler-warning-level-1-c4612.md)|インクルード ファイル名にエラーがあります|
|[コンパイラ警告 (レベル 1) C4613](compiler-warning-level-1-c4613.md)|'*symbol*': セグメントのクラスは変更できません|
|[コンパイラ警告 (レベル 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|#pragma 警告: 不明なユーザー警告の種類|
|[コンパイラ警告 (レベル 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma 警告: 警告番号 ' number ' は有効なコンパイラ警告ではありません|
|[コンパイラ警告 (レベル 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|プラグマパラメーターに空の文字列が含まれています。プラグマは無視されました|
|[コンパイラ警告 (レベル 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning: 警告番号 'number' がありません。|
|[コンパイラ警告 (レベル 1) C4620](compiler-warning-level-1-c4620.md)|型 'type' に対して後置形式の 'operator ++' は見つかりません。前置形式を使用します|
|[コンパイラ警告 (レベル 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|型 ' type ' に対して後置形式でない ' operator--' が見つかりました。プレフィックス形式を使用します|
|[コンパイラ警告 (レベル 3) C4622](compiler-warning-level-3-c4622.md)|オブジェクトファイルでプリコンパイル済みヘッダーの作成中に生成されたデバッグ情報を上書きしています: ' file '|
|[コンパイラ警告 (レベル 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|' derived class ': 基底クラスの既定のコンストラクターにアクセスできないか、または削除されたため、既定のコンストラクターは暗黙的に削除済みとして定義されました|
|[コンパイラ警告 (レベル 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|' derived class ': 基底クラスのデストラクターにアクセスできないか、または削除されたため、デストラクターは暗黙的に削除済みとして定義されました|
|[コンパイラ警告 (レベル 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|' derived class ': 基底クラスのコピーコンストラクターにアクセスできないか、または削除されたため、コピーコンストラクターは暗黙的に削除済みとして定義されました|
|[コンパイラ警告 (レベル 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|' derived class ': 基底クラスの代入演算子にアクセスできないか、または削除されたため、代入演算子は暗黙的に削除済みとして定義されました|
|[コンパイラ警告 (レベル 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|' \<identifier> ': プリコンパイル済みヘッダーの使用を検索しているときにスキップされました|
|[コンパイラ警告 (レベル 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|digraphs は -Ze でサポートされていません。 文字シーケンス ' digraph ' は '% s ' の代替トークンとして解釈されません|
|[コンパイラ警告 (レベル 4) C4629](compiler-warning-level-4-c4629.md)|digraph が使用されました。文字のシーケンス 'digraph' はトークン 'char' として解釈されます。(これが意図でない場合は、2 文字の間にスペースを挿入してください)|
|[コンパイラ警告 (レベル 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|' symbol ': ' extern ' ストレージクラスの指定子がメンバー定義で無効です。|
|コンパイラの警告 (レベル 2) C4631|MSXML または XPath は使用できません。XML ドキュメント コメントは処理されません。 reason|
|[コンパイラ警告 (レベル 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|XML ドキュメントコメント: ファイルアクセスが拒否されました: 理由|
|[コンパイラ警告 (レベル 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|XML ドキュメントコメントの対象: エラー: 理由|
|[コンパイラ警告 (レベル 4) C4634](compiler-warning-level-4-c4634.md)|XML ドキュメントコメントの対象: 適用できません: 理由|
|[コンパイラ警告 (レベル 3) C4635](compiler-warning-level-3-c4635.md)|XML ドキュメント コメント対象: XML の形式が正しくありません: 理由|
|[コンパイラ警告 (レベル 3) C4636](compiler-warning-level-3-c4636.md)|XML ドキュメントコメントがコンストラクトに適用されました: タグには空でない ' attribute ' 属性が必要です。|
|[コンパイラの警告 (レベル3およびレベル 4) C4637](compiler-warning-level-3-c4637.md)|XML ドキュメントコメントのターゲット: タグが破棄されました \<include> 。 理由|
|[コンパイラ警告 (レベル 3) C4638](compiler-warning-level-3-c4638.md)|XML ドキュメントコメントの対象: 不明なシンボル ' symbol ' への参照です。|
|[コンパイラ警告 (レベル 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|MSXML エラーです。 XML ドキュメントコメントは処理されません。 理由|
|[コンパイラ警告 (レベル 3) C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instance': ローカル スタティック オブジェクトの構築がスレッド セーフではありません。|
|[コンパイラ警告 (レベル 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|XML ドキュメントコメントはあいまいな相互参照を含んでいます:|
|[コンパイラ警告 (レベル 3) C4645](compiler-warning-level-3-c4645.md)|__declspec(noreturn) で宣言された関数に return ステートメントがあります。|
|[コンパイラ警告 (レベル 3) C4646](compiler-warning-level-3-c4646.md)|__declspec(noreturn) で宣言された関数に、non-void 戻り値の型があります。|
|コンパイラの警告 (レベル 3) C4647|動作の変更: __is_pod (*型*) の値が以前のバージョンで異なります。|
|コンパイラの警告 (レベル 3) C4648|標準属性 ' carries_dependency ' は無視されます|
|コンパイラの警告 (レベル 3) C4649|このコンテキストでは属性は無視されます|
|[コンパイラ警告 (レベル 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|デバッグ情報がプリコンパイル済みヘッダーにありません。ヘッダーからのグローバルシンボルのみを使用できます|
|[コンパイラ警告 (レベル 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|プリコンパイル済みヘッダーに対して ' definition ' が指定されましたが、現在のコンパイル用ではありません|
|[コンパイラ警告 (レベル 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|コンパイラオプション ' option ' はプリコンパイル済みヘッダーと矛盾しています。現在のコマンドラインオプションは、プリコンパイル済みヘッダーに定義されているものよりも優先されます|
|[コンパイラ警告 (レベル 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|コンパイラオプション ' option ' はプリコンパイル済みヘッダーと矛盾しています。現在のコマンドラインオプションは無視されます|
|コンパイラの警告 (レベル 4) C4654|プリコンパイル済みヘッダー行の前に配置されたコードは無視されます。 プリコンパイル済みヘッダーにコードを追加します。|
|[コンパイラ警告 (レベル 1) C4655](compiler-warning-level-1-c4655.md)|' symbol ': 変数の型が最新のビルド以降に新しくなったか、別の場所で定義されています|
|[コンパイラ警告 (レベル 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|' symbol ': データ型が新規であるか、最新のビルド以降に変更されているか、別の場所で定義されています|
|[コンパイラ警告 (レベル 1) C4657](compiler-warning-level-1-c4657.md)|式には、最新のビルド以降の新しいデータ型が含まれています|
|コンパイラの警告 (レベル 1) C4658|' function ': 関数プロトタイプは、最新のビルド以降、または他の場所で異なる方法で宣言されています。|
|[コンパイラ警告 (レベル 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma ' pragma ': 予約セグメント ' segment ' の使用には定義されていない動作があります。 #pragma コメントを使用してください (リンカー,...)|
|[コンパイラ警告 (レベル 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|' identifier ': 明示的なテンプレートのインスタンス化要求に対して適切な定義が指定されていません|
|[コンパイラ警告 (レベル 1) C4662](compiler-warning-level-1-c4662.md)|明示的なインスタンス化。テンプレート クラス 'identifier1' に 'identifier2' を特定する定義がありません|
|[コンパイラ警告 (レベル 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|' function ': 強制インスタンス化に一致する関数テンプレートが定義されていません|
|[コンパイラ警告 (レベル 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|' symbol ' はプリプロセッサマクロとして定義されていません。 ' ディレクティブ ' の ' 0 ' に置き換えてください。|
|[コンパイラ警告 (レベル 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|' cast ': 安全でない変換です: ' class ' はマネージ型オブジェクトです|
|[コンパイラ警告 (レベル 4) C4670](compiler-warning-level-4-c4670.md)|' identifier ': この基底クラスにアクセスできません|
|コンパイラの警告 (レベル 4) C4671|' identifier ': コピーコンストラクターにアクセスできません|
|[コンパイラ警告 (レベル 4) C4672](compiler-warning-level-4-c4672.md)|' identifier1 ': あいまいです。 1 つ目を 'identifier2' とします。|
|[コンパイラ警告 (レベル 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|' identifier ' をスローすると、次の型はキャッチサイトでは考慮されません|
|[コンパイラ警告 (レベル 1) C4674](compiler-warning-level-1-c4674.md)|'method' は宣言された 'static' であり、パラメーターを 1 つだけ持たなければなりません。|
|コンパイラの警告 (レベル 4) C4676|'% s ': デストラクターにアクセスできません。|
|[コンパイラ警告 (レベル 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|' function ': プライベートでないメンバーのシグネチャには、アセンブリプライベート型 ' private_type ' が含まれています|
|[コンパイラ警告 (レベル 1) C4678](compiler-warning-level-1-c4678.md)|基底クラス 'base_type' のアクセス可能性が 'derived_type' よりも小さいです。|
|[コンパイラ警告 (レベル 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|' member ': メンバーをインポートできませんでした|
|[コンパイラ警告 (レベル 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|' class ': コクラスは既定のインターフェイスを指定していません|
|[コンパイラ警告 (レベル 4) C4681](compiler-warning-level-4-c4681.md)|' class ': コクラスは、イベントソースである既定のインターフェイスを指定していません|
|[コンパイラ警告 (レベル 4) C4682](compiler-warning-level-4-c4682.md)|' parameter ': 方向性のあるパラメーター属性が指定されていません。 [in] を既定にします|
|[コンパイラ警告 (レベル 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|' function ': イベントソースに ' out' パラメーターが指定されています。複数のイベントハンドラーをフックする場合は注意が必要です|
|[コンパイラ警告 (レベル 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|' attribute ': WARNING!! 属性により、無効なコード生成が発生する可能性があります: 使用に注意してください|
|[コンパイラ警告 (レベル 1) C4685](compiler-warning-level-1-c4685.md)|テンプレート パラメーターの解析中に '> >' が必要ですが、'>>' が見つかりました。|
|[コンパイラ警告 (レベル 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'user-defined type': 動作と UDT の戻り値の呼び出し規則に変更がある可能性があります。|
|[コンパイラの警告 (エラー) C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|' class ': シールドされた抽象クラスはインターフェイス ' interface ' を実装できません|
|[コンパイラ警告 (レベル 1) C4688](../../error-messages/compiler-warnings/compiler-warning-level-1-c4688.md)|'constraint': 制約リストはアセンブリ プライベート型 'type' を含んでいます|
|コンパイラの警告 (レベル 1) C4689|'% c ': #pragma detect_mismatch; でサポートされていない文字です。無視される #pragma|
|[コンパイラ警告 (レベル 4) C4690](../../error-messages/compiler-warnings/compiler-warning-level-4-c4690.md)|\[ emitidl (pop)]: ポップの数がプッシュよりも多くなっています|
|[コンパイラ警告 (レベル 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|' type ': 参照されている型が参照されていないアセンブリ ' file ' で必要です。現在の翻訳単位で定義されている型が代わりに使用されます|
|[コンパイラ警告 (レベル 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'関数': 公開されたメンバーのシグネチャはアセンブリ プライベート ネイティブ型 'native_type' を含んでいます|
|[コンパイラの警告 (レベル1、エラー) C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|' class ': シールドされた抽象クラスにインスタンスメンバー ' instance member ' を含めることはできません|
|[コンパイラの警告 (レベル1、エラー) C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|' class ': シールドされた抽象クラスは、基底クラス ' base_class ' を持つことはできません|
|コンパイラの警告 (レベル 1) C4695|#pragma execution_character_set: ' character set ' はサポートされている引数ではありません: 現在は ' UTF-8 ' のみがサポートされています|
|コンパイラの警告 (レベル 1) C4696|/ZBvalue1 オプションが範囲を超えています。' value2 ' と想定しています|
| [コンパイラの警告 (レベル 3) C4698](../../error-messages/compiler-warnings/c4698.md) | '*feature*' は評価のみを目的としており、今後の更新で変更または削除される可能性があります。 |
|[コンパイラ警告 (レベル 1 およびレベル 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|初期化されていないローカル変数 ' name ' が使用されています|
|[コンパイラ警告 (レベル 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|初期化されていない可能性があるローカル変数 ' name ' を使用します|
|[コンパイラ警告 (レベル 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|到達できないコード|
|[コンパイラ警告 (レベル 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|初期化されていない可能性のあるローカルポインター変数 '% s ' が使用されました|
|[コンパイラ警告 (レベル 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|条件式内の代入|
|[コンパイラ警告 (レベル 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|配列インデックス式内のコンマ演算子|
|[コンパイラ警告 (レベル 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'function': インライン関数ではありません。|
|[コンパイラ警告 (レベル 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|関数 ' function ' が自動インライン展開に対して選択されました|
|[コンパイラ警告 (レベル 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|関数 ' function ' はインライン __forceinline としてマークされていません|
|[コンパイラ警告 (レベル 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|' function ': すべてのコントロールパスが値を返すわけではありません|
|[コンパイラの警告 (レベル1、エラー) C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|' function ': 値を返す必要があります|
|[コンパイラ警告 (レベル 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|' function ': すべてのコントロールパスで再帰的に行われます。関数は、ランタイムスタックオーバーフローを発生させます|
|[コンパイラ警告 (レベル 4) C4718](compiler-warning-level-4-c4718.md)|' function call ': 再帰呼び出しには副作用がありません。削除します。|
|コンパイラの警告 (レベル 1) C4719|Qfast が指定されているときに Double 定数が見つかりました-単一の有効桁数を示すサフィックスとして ' f ' を使用します|
|コンパイラの警告 (レベル 2) C4720|インラインアセンブラーレポート: ' message '|
|コンパイラの警告 (レベル 1) C4721|' function ': 組み込み関数として使用できません。|
|[コンパイラ警告 (レベル 1) C4722](compiler-warning-level-1-c4722.md)|' function ': デストラクターが戻りません。メモリリークの可能性があります。|
|[コンパイラ警告 (レベル 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|0による除算の可能性|
|[コンパイラ警告 (レベル 3) C4724](compiler-warning-level-3-c4724.md)|剰余の 2 番目のオペランドは、コンパイル時に 0 と評価され、不定の結果を返します。|
|コンパイラの警告 (レベル 3) C4725|Pentium のモデルによっては、命令が不正確になります。|
|[コンパイラ警告 (レベル 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|Obj_file_1 と obj_file_2 で同じタイムスタンプを持つ pch_file という名前の PCH が見つかりました。  最初の PCH を使用します。|
|コンパイラの警告 (レベル 1) C4728|PCH 参照が必要なため、/Yl-オプションは無視されます|
|コンパイラの警告 (レベル 4) C4729|フロー グラフ ベースの警告の関数が大きすぎます。|
|[コンパイラの警告 (レベル 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)コンパイラの警告 (レベル 1) C4730|' main ': _m64 と浮動小数点式の混合により、正しくないコードが生成される可能性があります|
|[コンパイラ警告 (レベル 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|' pointer ': インラインアセンブリコードによって変更されたフレームポインターレジスタ ' register '|
|コンパイラの警告 (レベル 1) C4732|組み込み '% s ' は、このアーキテクチャではサポートされていません|
|[コンパイラ警告 (レベル 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|インライン asm が ' FS: 0 ' に割り当てられています: ハンドラーがセーフハンドラーとして登録されていません|
|[コンパイラ警告 (レベル 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|メモリに 32 ビットの浮動結果を格納します。パフォーマンスが低下する可能性があります|
|[コンパイラの警告 (レベル 1) C4739](compiler-warning-level-1-c4739.md)|変数 'var' への参照はそのストレージ領域を超えています|
|[コンパイラ警告 (レベル 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|インライン asm コードの内外のフローにより、グローバルな最適化が抑制される|
|[コンパイラ警告 (レベル 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|' file1 ' と ' file2 ' では、' var ' の配置が異なります。数値と数値|
|[コンパイラ警告 (レベル 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|' type ' のサイズが ' file1 ' と ' file2 ' で異なっています: number と number bytes|
|[コンパイラ警告 (レベル 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|' var ' は、' file1 ' および ' file2 ' で異なる型を含んでいます: ' type1 ' と ' type1 '|
|[コンパイラ警告 C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|'*expression*' の volatile アクセスには/volatile: setting が適用されます \<iso&#124;ms> 。 __iso_volatile_load/ストア組み込み関数を使用することを検討してください。|
|[コンパイラ警告 (レベル 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|マネージド ' entrypoint ' を呼び出しています: マネージドコードは、DLL エントリポイントおよび DLL エントリポイントから到達した呼び出しを含むローダーロック下では実行できません|
|コンパイラの警告 (レベル 4) C4749|条件付きでサポート: offsetof が非標準レイアウト型 '*type*' に適用されました|
|[コンパイラ警告 (レベル 1) C4750](compiler-warning-level-1-c4750.md)|'identifier': ループにインライン展開されている _alloca() を含む関数です|
|コンパイラの警告 (レベル 4) C4751|/arch: AVX は、インライン ASM 内の Intel (R) Streaming SIMD 拡張機能には適用されません。|
|コンパイラの警告 (レベル 4) C4752|Intel (R) Advanced Vector Extension が見つかりました。/arch: AVX の使用を検討してください。|
|[コンパイラ警告 (レベル 4) C4754](compiler-warning-level-4-c4754.md)|% S (% d) の比較における算術演算の変換規則により、1つの分岐を実行できません。 '% S ' を '% s ' (または% d バイトの類似する型) にキャストします。|
|コンパイラの警告 C4755|% S (% d) の比較における算術演算の変換規則により、1つの分岐をインライン関数で実行できません。 '% S ' を '% s ' (または% d バイトの類似する型) にキャストします。|
|[コンパイラ警告 (レベル 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|定数演算でオーバーフローが発生しています|
|コンパイラの警告 (レベル 4) C4757|添字は大きな符号なしの値です。負の定数を意図しましたか?|
|[コンパイラ警告 (レベル 4) C4764](compiler-warning-level-4-c4764.md)|キャッチオブジェクトを16バイトより大きい値に揃えることはできません|
|コンパイラの警告 (レベル 4) C4767|セクション名 '% s ' は8文字を超えているため、リンカーによって切り捨てられます。|
|コンパイラの警告 (レベル 3) C4768|リンケージ指定の前の __declspec 属性は無視されます|
|コンパイラの警告 C4770|インデックスとして使用される部分的に検証された列挙型 '*name*'|
|コンパイラの警告 C4771|境界は、単純なポインターを使用して作成する必要があります。MPX 組み込み関数は無視されました|
|[コンパイラの警告 (レベル1、エラー) C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import 参照されていないタイプライブラリの型が参照されています。' missing_type ' がプレースホルダーとして使用されています|
|コンパイラの警告 (レベル 4) C4774|'*string*': 引数 *番号* に必要な書式文字列が文字列リテラルではありません|
|コンパイラの警告 (レベル 3) C4775|関数 '*function*' の書式文字列 '*string*' で非標準の拡張機能が使用されています|
|コンパイラの警告 (レベル 1) C4776|'%*character*' は、関数 '*function*' の書式文字列では許可されていません|
|コンパイラの警告 (レベル 4) C4777|'*function*': 書式文字列 '*string*' には型 ' type1 ' の引数が必要ですが、可変個引数引数の *数値* には *型 '**type1*' が含まれています|
|コンパイラの警告 (レベル 3) C4778|'*function*': 書式文字列 '*string*' が未終了です。|
|[コンパイラ警告 (レベル 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|' identifier ': 識別子が ' number ' 文字に切り詰められました|
|[コンパイラ警告 (レベル 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|バッファー 'identifier' (サイズが N バイト) でオーバーランが発生します。M バイトがオフセット L から書き込まれます|
|コンパイラの警告 (レベル 2) C4792|関数 '% s ' は sysimport を使用して宣言され、ネイティブコードから参照されています。リンクにはインポートライブラリが必要です|
|[コンパイラ警告 (レベル 1 および 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|' function ': 関数はネイティブとしてコンパイルされています: ' reason '|
|[コンパイラ警告 (レベル 1) C4794](compiler-warning-level-1-c4794.md)|スレッドローカルストレージ変数 '% s ' のセグメントが '% s ' から '% s ' に変更されました|
|[コンパイラ警告 (レベル 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|関数 ' function ' には、EMM 命令がありません。|

## <a name="see-also"></a>関連項目

[C/c + + コンパイラおよびビルドツールのエラーと警告](../compiler-errors-1/c-cpp-build-errors.md) \
[コンパイラ警告 (C4000 - C5999)](compiler-warnings-c4000-c5999.md)
