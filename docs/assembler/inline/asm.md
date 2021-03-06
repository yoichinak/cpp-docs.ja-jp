---
description: '詳細情報: `__asm`'
title: __asm
ms.date: 10/09/2018
f1_keywords:
- __asm
- _asm
- __asm_cpp
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
ms.openlocfilehash: 5fa4e64bdb9ae4fc01e6e379de3e8a6771959e80
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118057"
---
# `__asm`

**Microsoft 固有の仕様**

キーワードは、 **`__asm`** インラインアセンブラーを呼び出し、C または C++ のステートメントが有効であればどこにでも表示できます。 これは、単独では使用できません。 アセンブリ命令、中かっこで囲まれた命令グループ、または少なくとも空の中かっこの後で指定する必要があります。 " **`__asm`** ブロック" という用語は、ここでは、中かっこに囲まれているかどうかを問わず、命令または命令のグループを示します。

> [!NOTE]
> 標準 C++ キーワードの Visual C++ サポート **`asm`** は、コンパイラがキーワードでエラーを生成しないという事実に限定されています。 ただし、 **`asm`** ブロックは意味のあるコードを生成しません。 **`__asm`** の代わりにを使用 **`asm`** します。

## <a name="grammar"></a>文法

*asm-ブロック*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm`***アセンブリ-命令* **`;`**<sub>選択</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm {`***アセンブリ命令リスト* **`}`****`;`**<sub>選択</sub>

*アセンブリ命令リスト*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*アセンブリ-命令* **`;`**<sub>選択</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*アセンブリ-命令* **`;`***アセンブリ命令リスト* **`;`**<sub>選択</sub>

## <a name="remarks"></a>解説

中かっこなしで使用する場合、キーワードは、 **`__asm`** 行の残りの部分がアセンブリ言語のステートメントであることを意味します。 中かっこを付けて使用する場合、中かっこの間の各行がアセンブリ言語のステートメントであることを意味します。 以前のバージョンとの互換性のため、 **`_asm`** はのシノニムです **`__asm`** 。

**`__asm`** キーワードはステートメント区切り文字であるため、同じ行にアセンブリ命令を配置できます。

Visual Studio 2005 より前の手順

```cpp
__asm int 3
```

**/clr** を指定してコンパイルした場合、ネイティブコードが生成されませんでした。コンパイラは命令を CLR break 命令に変換しました。

`__asm int 3` により現在は、関数のネイティブ コードが生成されるようになりました。 関数によってコード内のブレークポイントが発生するようにし、その関数を MSIL にコンパイルする場合は、 [__debugbreak](../../intrinsics/debugbreak.md)を使用します。

以前のバージョンとの互換性を維持するために、 **`_asm`** **`__asm`** コンパイラオプションの [ [ \( 言語拡張を無効にする](../../build/reference/za-ze-disable-language-extensions.md) ] が指定されていない限り、はのシノニムになります。

## <a name="example"></a>例

次のコードフラグメントは、 **`__asm`** 中かっこで囲まれた単純なブロックです。

```cpp
__asm {
   mov al, 2
   mov dx, 0xD007
   out dx, al
}
```

または、各アセンブリ命令の前に **`__asm`** を置くことができます。

```cpp
__asm mov al, 2
__asm mov dx, 0xD007
__asm out dx, al
```

**`__asm`** キーワードはステートメント区切り文字であるため、同じ行にアセンブリ命令を配置することもできます。

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

3つのすべての例で同じコードが生成されますが、最初のスタイル ( **`__asm`** かっこ内のブロックを囲む) にはいくつかの利点があります。 中かっこでは、C または C++ コードからアセンブリコードが明確に分離され、キーワードの繰り返しが不要に **`__asm`** なります。 中かっこにより、あいまいさを防ぐこともできます。 C または C++ のステートメントをブロックと同じ行に配置する場合は、 **`__asm`** ブロックを中かっこで囲む必要があります。 中かっこで囲まないと、コンパイラはどこでアセンブリ コードが終わって C または C++ ステートメントが始まるかがわかりません。 最後に、中かっこ内のテキストは、通常の MASM テキストと同じ形式であるため、既存の MASM ソース ファイルからテキストを簡単に切り取って貼り付けることができます。

C と C++ の中かっことは異なり、ブロックを囲む中かっこは **`__asm`** 変数スコープに影響しません。 ブロックを入れ子にすることもできます。 **`__asm`** 入れ子は、変数のスコープには影響しません。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[キーワード](../../cpp/keywords-cpp.md)<br/>
[インラインアセンブラー](../../assembler/inline/inline-assembler.md)<br/>
