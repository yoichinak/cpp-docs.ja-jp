---
description: 詳細については、「コンパイラエラー C3100 ~ C3199」を参照してください。
title: コンパイラ エラー (C3100 - C3199)
ms.date: 04/21/2019
f1_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
helpviewer_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
ms.assetid: 7bc40c2f-6a8d-488a-b665-f39375afee77
ms.openlocfilehash: 5e24666ed69acef5a1bced76fe4730c371964b78
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721850"
---
# <a name="compiler-errors-c3100-through-c3199"></a>コンパイラ エラー (C3100 - C3199)

ドキュメントのこのセクションの記事では、コンパイラによって生成されるエラーメッセージのサブセットについて説明します。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>エラー メッセージ

|エラー|Message|
|-----------|-------------|
|[コンパイラ エラー C3100](compiler-error-c3100.md)|'*identifier*': 属性修飾子が不明です。|
|[コンパイラ エラー C3101](compiler-error-c3101.md)|名前付き属性の引数 '*identifier*' に対して無効な式です|
|コンパイラエラー C3102|互換性のために残されています。|
|[コンパイラ エラー C3103](compiler-error-c3103.md)|'*identifier*': 名前付き引数が繰り返される|
|[コンパイラ エラー C3104](compiler-error-c3104.md)|無効な属性引数です|
|コンパイラエラー C3105|'*symbol*': 属性として使用することはできません|
|[コンパイラ エラー C3106](compiler-error-c3106.md)|'*attribute*': 名前のない引数は名前付き引数の前に指定しなければなりません|
|コンパイラエラー C3107|'*attribute*': ネイティブ属性のメンバー関数を定義することはできません|
|コンパイラエラー C3108|初期化子リストが式ではないため、型を推測できません|
|コンパイラエラー C3109|'*identifier*': インターフェイスメソッドは ' __stdcall ' または ' __cdecl ' 呼び出し規約のどちらかを使用する必要があります|
|[コンパイラ エラー C3110](compiler-error-c3110.md)|'*function*': COM インターフェイスメソッドをオーバーロードすることはできません。|
|コンパイラエラー C3111|初期化子リストは、テンプレートパラメーターの既定の引数として使用できません|
|コンパイラエラー C3112|'*interface*': インターフェイスはグローバルまたは名前空間スコープでのみ宣言できます|
|[コンパイラ エラー C3113](compiler-error-c3113.md)|' interface/enum ' をテンプレートまたはジェネリックにすることはできません|
|[コンパイラ エラー C3114](compiler-error-c3114.md)|'*identifier*': 有効な名前付き属性引数ではありません|
|[コンパイラ エラー C3115](compiler-error-c3115.md)|'*attribute*': この属性は '*construct*' では許可されていません|
|[コンパイラ エラー C3116](compiler-error-c3116.md)|'*指定子*': インターフェイスメソッドのストレージクラスが無効です|
|[コンパイラ エラー C3117](compiler-error-c3117.md)|'*interface*': インターフェイスには1つの基底クラスのみを含めることができます|
|[コンパイラ エラー C3118](compiler-error-c3118.md)|'*interface*': インターフェイスでは仮想継承がサポートされていません|
|コンパイラエラー C3119|整列 nas (void) は使用できません|
|[コンパイラ エラー C3120](compiler-error-c3120.md)|'*identifier*': インターフェイスメソッドは可変個引数リストを受け取ることができません|
|[コンパイラ エラー C3121](compiler-error-c3121.md)|クラス '*class*' の GUID を変更できません|
|コンパイラエラー C3122|'*interface*': WinRT ジェネリックインターフェイスは GUID を持つことはできません|
|コンパイラエラー C3123|WinRT ジェネリックインターフェイスは制約を持つことはできません|
|コンパイラエラー C3124|' signed char ' は有効な WinRT データ型ではありません。 代わりに、' unsigned char '、' wchar_t '、または ' signed short ' を使用してください。|
|コンパイラエラー C3125|'*type*': 型は、' Platform:: Exception ' から直接または間接的に派生することはできません|
|[コンパイラ エラー C3126](compiler-error-c3126.md)|共用体型 '*union*' をマネージド/WinRT 型の '*type*' 内に定義することはできません|
|コンパイラエラー C3127|'*type*': '*特徴*' 特徴は WinRT ref クラスでのみ使用できます|
|コンパイラエラー C3128|'*type*' には '*type*' によって導入された vtable がありません|
|コンパイラエラー C3129|'*type*': __default_vptr_for_base は、ローカルで定義されたポリモーフィック型およびベースでのみ使用できます|
|[コンパイラ エラー C3130](compiler-error-c3130.md)|内部コンパイラエラー: 挿入されるコードブロックを PDB に書き込めませんでした|
|[コンパイラ エラー C3131](compiler-error-c3131.md)|プロジェクトには ' name ' プロパティを持つ ' module ' 属性が必要です|
|[コンパイラ エラー C3132](compiler-error-c3132.md)|'*parameter*': パラメーター配列は、型 ' single 次元マネージ/WinRT 配列 ' の仮引数にのみ適用できます|
|[コンパイラ エラー C3133](compiler-error-c3133.md)|C++ varargs に属性を適用することはできません|
|[コンパイラ エラー C3134](compiler-error-c3134.md)|'*value*': 属性引数 '*argument*' の値に有効な型 '*type*' がありません|
|[コンパイラ エラー C3135](compiler-error-c3135.md)|'*identifier*': プロパティに ' const ' または ' volatile ' 型を含めることはできません|
|[コンパイラ エラー C3136](compiler-error-c3136.md)|'*interface*': com インターフェイスは他の com インターフェイスからのみ継承できます。 '*INTERFACE*' は com インターフェイスではありません。|
|[コンパイラ エラー C3137](compiler-error-c3137.md)|'*identifier*': プロパティは初期化できません|
|[コンパイラ エラー C3138](compiler-error-c3138.md)|'*identifier*': '*attribute*' インターフェイスは IDispatch、または idispatch から継承したインターフェイスから継承する必要があります|
|[コンパイラ エラー C3139](compiler-error-c3139.md)|'*type*': メンバーのない UDT をエクスポートできません|
|[コンパイラ エラー C3140](compiler-error-c3140.md)|同じコンパイル単位に複数の ' module ' 属性を含めることはできません|
|[コンパイラ エラー C3141](compiler-error-c3141.md)|'*interface*': インターフェイスはパブリック継承のみをサポートしています|
|[コンパイラ エラー C3142](compiler-error-c3142.md)|'*property*': プロパティのアドレスを取得することはできません。|
|コンパイラエラー C3143|'*argument*': 属性引数に複数の値を指定することはできません|
|コンパイラエラー C3144|'*attribute*': 属性には明示的な引数が必要です。 '*argument*' には名前がありません。|
|[コンパイラ エラー C3145](compiler-error-c3145.md)|'*identifier*': グローバルまたは静的変数に、マネージ/WinRT 型の '*type*' を含めることはできません|
|コンパイラエラー C3146|互換性のために残されています。|
|コンパイラエラー C3147|互換性のために残されています。|
|コンパイラエラー C3148|互換性のために残されています。|
|[コンパイラ エラー C3149](compiler-error-c3149.md)|'*type*': 最上位の '*token*' を指定せずにこの型を使用することはできません|
|[コンパイラ エラー C3150](compiler-error-c3150.md)|'*construct*': '*attribute*' はクラス、構造体、インターフェイス、配列、またはポインターにのみ適用できます|
|コンパイラエラー C3151|互換性のために残されています。|
|[コンパイラ エラー C3152](compiler-error-c3152.md)|'*function*': '*keyword*' はクラス、構造体、または仮想メンバー関数にのみ適用できます|
|[コンパイラ エラー C3153](compiler-error-c3153.md)|'*interface*': インターフェイスのインスタンスを作成することはできません。|
|[コンパイラ エラー C3154](compiler-error-c3154.md)|省略記号の前に ', ' が必要です。 パラメーター配列関数では、非コンマ区切りの省略記号がサポートされていません。|
|[コンパイラ エラー C3155](compiler-error-c3155.md)|属性は、プロパティインデクサーでは使用できません|
|[コンパイラ エラー C3156](compiler-error-c3156.md)|'*class*': マネージド/WinRT 型のローカル定義を持つことはできません|
|[コンパイラ エラー C3157](compiler-error-c3157.md)|ParamArray 属性は最後のパラメーターにのみ適用できます|
|コンパイラエラー C3158|'*function*': '*keyword*' は仮想メンバー関数にのみ適用できます|
|[コンパイラ エラー C3159](compiler-error-c3159.md)|'*identifier*': 値型へのポインターの配列を宣言することはできません|
|[コンパイラ エラー C3160](compiler-error-c3160.md)|'*type*': マネージクラスまたは WinRT クラスのデータメンバーは、この型を持つことはできません|
|[コンパイラ エラー C3161](compiler-error-c3161.md)|'*interface*': インターフェイスでクラス、構造体、またはインターフェイスを入れ子にすることはできません。クラスまたは構造体でインターフェイスを入れ子にすることは無効です|
|[コンパイラ エラー C3162](compiler-error-c3162.md)|'*type*': デストラクターを含む参照型を静的データメンバー '*member*' の型として使用することはできません|
|[コンパイラ エラー C3163](compiler-error-c3163.md)|'*class*': 属性が前の宣言と矛盾しています。|
|コンパイラエラー C3164|互換性のために残されています。|
|コンパイラエラー C3165|'*value*': 整数または浮動小数点値に変換できません。|
|[コンパイラ エラー C3166](compiler-error-c3166.md)|互換性のために残されています。 '*type*': マネージド/WinRT クラスのデータメンバーは、内部 *managed_pointer_type*' に対する型 '*pointer_type* を持つことはできません|
|[コンパイラ エラー C3167](compiler-error-c3167.md)|.NET Framework を初期化できません: インストールされていることを確認してください|
|[コンパイラ エラー C3168](compiler-error-c3168.md)|'*type*': 列挙型の基になる型が正しくありません。|
|コンパイラエラー C3169|'*type*': '*type*' から ' auto ' の型を推測できません|
|[コンパイラ エラー C3170](compiler-error-c3170.md)|プロジェクト内で異なるモジュール識別子を持つことはできません|
|[コンパイラ エラー C3171](compiler-error-c3171.md)|'*module*': プロジェクトで異なるモジュール属性を指定することはできません|
|[コンパイラ エラー C3172](compiler-error-c3172.md)|'*identifier*': プロジェクトで異なる idl_module 属性を指定することはできません|
|[コンパイラ エラー C3173](compiler-error-c3173.md)|idl マージのバージョンが一致しません|
|[コンパイラ エラー C3174](compiler-error-c3174.md)|モジュール属性が指定されませんでした|
|[コンパイラ エラー C3175](compiler-error-c3175.md)|'*function*': アンマネージド関数 '*function*' からマネージド型のメソッドを呼び出すことはできません|
|[コンパイラ エラー C3176](compiler-error-c3176.md)|'*type*': ローカル値の型を宣言することはできません|
|コンパイラエラー C3177|'*type*' を含む型への変換関数は使用できません|
|コンパイラエラー C3178|'*type*': 既定の引数を持つ関数で ParamArray を使用することはできません|
|[コンパイラ エラー C3179](compiler-error-c3179.md)|無名のマネージ/WinRT 型は使用できません|
|[コンパイラ エラー C3180](compiler-error-c3180.md)|'*type*': 名前がメタデータの制限 '*number*' 文字を超えています|
|[コンパイラ エラー C3181](compiler-error-c3181.md)|'*type*':*演算子* に対して無効なオペランドです|
|[コンパイラ エラー C3182](compiler-error-c3182.md)|'*type*': メンバーの using 宣言またはアクセス宣言は、マネージ/WinRT 型内では無効です|
|[コンパイラ エラー C3183](compiler-error-c3183.md)|マネージドまたは WinRT 型の '*class*' の内部に名前のないクラス、構造体、または共用体を定義することはできません|
|コンパイラエラー C3184|互換性のために残されています。|
|[コンパイラ エラー C3185](compiler-error-c3185.md)|' typeid ': マネージドまたは WinRT 型の '*type*' で使用されています。代わりに '*operator*' を使用してください|
|コンパイラエラー C3186|互換性のために残されています。|
|[コンパイラ エラー C3187](compiler-error-c3187.md)|'*identifier*': 関数の本体内でのみ使用できます|
|コンパイラエラー C3188|互換性のために残されています。|
|[コンパイラ エラー C3189](compiler-error-c3189.md)|' typeid<*宣言子*> ': この構文はサポートされなくなりました。代わりに:: typeid を使用してください|
|[コンパイラ エラー C3190](compiler-error-c3190.md)|指定されたテンプレート引数を持つ '*宣言子*' は、'*type*' のメンバー関数の明示的なインスタンス化ではありません|
|コンパイラエラー C3191|互換性のために残されています。|
|[コンパイラ エラー C3192](compiler-error-c3192.md)|構文エラー: ' ^ ' はプレフィックス演算子ではありません (' * ' を意味しましたか?)|
|コンパイラエラー C3193|'*construct*': '/clr ' または '/ZW ' コマンドラインオプションが必要です|
|[コンパイラ エラー C3194](compiler-error-c3194.md)|'*type*': 値型に代入演算子を指定することはできません|
|[コンパイラ エラー C3195](compiler-error-c3195.md)|'*keyword*': は予約されているため、ref クラスまたは値型のメンバーとして使用することはできません。 CLR/WinRT 演算子は、' operator ' キーワードを使用して定義する必要があります|
|[コンパイラ エラー C3196](compiler-error-c3196.md)|'*identifier*': 複数回使用されています|
|[コンパイラ エラー C3197](compiler-error-c3197.md)|'*keyword*': 定義でのみ使用できます|
|[コンパイラ エラー C3198](compiler-error-c3198.md)|浮動小数点プラグマの使い方が正しくありません: fenv_access プラグマは正確なモードでのみ動作します|
|[コンパイラ エラー C3199](compiler-error-c3199.md)|浮動小数点プラグマの使い方が無効です: 例外は、精度の低いモードではサポートされていません|

## <a name="see-also"></a>関連項目

[C/c + + コンパイラおよびビルドツールのエラーと警告](../compiler-errors-1/c-cpp-build-errors.md) \
[コンパイラエラー C2000-C3999、C7000-C7999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
