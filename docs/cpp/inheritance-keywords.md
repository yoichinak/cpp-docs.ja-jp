---
description: 詳細については、「継承キーワード」を参照してください。
title: 継承キーワード
ms.date: 04/12/2021
f1_keywords:
- __multiple_inheritance
- __single_inheritance_cpp
- __virtual_inheritance_cpp
- __virtual_inheritance
- __multiple_inheritance_cpp
- __single_inheritance
helpviewer_keywords:
- __single_inheritance keyword [C++]
- declaring derived classes [C++]
- keywords [C++], inheritance keywords
- __multiple_inheritance keyword [C++]
- __virtual_inheritance keyword [C++]
- inheritance, declaring derived classes
- derived classes [C++], declaring
- inheritance, keywords
ms.openlocfilehash: 4daf2899b7b0a556d41779974539aef253b2b4d2
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "107576938"
---
# <a name="inheritance-keywords"></a>継承キーワード

**Microsoft 固有の仕様**

> **`class`** *`class-name`*\
> **`class __single_inheritance`** *`class-name`*\
> **`class __multiple_inheritance`** *`class-name`*\
> **`class __virtual_inheritance`** *`class-name`*

各値の説明:

*`class-name`*<br/>
宣言するクラスの名前。

C++ では、クラスの定義の前に、クラスメンバーへのポインターを宣言できます。 次に例を示します。

```cpp
class S;
int S::*p;
```

上記のコードで `p` は、は、クラス S の整数メンバーへのポインターとして宣言されています。ただし、 `class S` このコードではまだ定義されていません。宣言されているだけです。 コンパイラがこのようなポインターを検出した場合、そのポインターの汎化表現を作成する必要があります。 この表現のサイズは、指定した継承モデルによって異なります。 コンパイラに継承モデルを指定するには、次の3つの方法があります。

- スイッチを使用してコマンドラインで実行する [`/vmg`](../build/reference/vmb-vmg-representation-method.md)

- プラグマを使用する [`pointers_to_members`](../preprocessor/pointers-to-members.md)

- 継承キーワード、、およびを使用し **`__single_inheritance`** **`__multiple_inheritance`** **`__virtual_inheritance`** ます。 この手法により、クラス単位で継承モデルを制御します。

    > [!NOTE]
    >  常にクラスを定義した後で、そのクラスのメンバーへのポインターを宣言する場合は、これらのオプションを使用する必要がありません。

クラスが定義される前にクラスメンバーへのポインターを宣言すると、結果の実行可能ファイルのサイズと速度に悪影響を及ぼす可能性があります。 クラスによって使用される継承が複雑になるほど、クラスのメンバーへのポインターを表すために必要なバイト数が大きくなります。 また、ポインターを解釈するために必要なコードが大きくなります。 単一 (またはまったく) の継承は最も複雑ではなく、仮想継承は最も複雑です。 クラスが定義される前に宣言したメンバーへのポインターは、常に最も大きな、最も複雑な表現を使用します。

上記の例を次のように変更します。

```cpp
class __single_inheritance S;
int S::*p;
```

指定したコマンドラインオプションやプラグマに関係なく、のメンバーへのポインターで `class S` は、可能な限り小さい表現が使用されます。

> [!NOTE]
> メンバーへのクラス ポインター表現の同じ前方宣言は、そのクラスのメンバーへのポインターを宣言する各翻訳単位で発生する必要があり、その宣言はメンバーへのポインターを宣言する前に発生する必要があります。

以前のバージョンとの互換性のため、、 **`_single_inheritance`** **`_multiple_inheritance`** 、および **`_virtual_inheritance`** は、、、およびのシノニムです **`__single_inheritance`** **`__multiple_inheritance`** **`__virtual_inheritance`** 。ただし、コンパイラオプションの [ [ `/Za` \( 言語拡張を無効にする](../build/reference/za-ze-disable-language-extensions.md)] が指定されている場合を除きます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)
