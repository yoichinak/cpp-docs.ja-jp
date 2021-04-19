---
description: 詳細については、「ランダム」を参照してください。 &lt;&gt;
title: '&lt;random&gt;'
ms.date: 08/24/2017
f1_keywords:
- <random>
helpviewer_keywords:
- random header
ms.assetid: 60afc25c-b162-4811-97c1-1b65398d4c57
ms.openlocfilehash: 85c2facebec49c4f15fb4a8705b672e677df926c
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721344"
---
# `<random>`

乱数生成の機能を定義し、一様に分布した乱数を作成できるようにします。

## <a name="requirements"></a>要件

**ヘッダー**: `<random>`

**名前空間:** std

> [!NOTE]
> ライブラリでは `<random>` 、' #include <initializer_list> ' ステートメントが使用されています。

## <a name="summary"></a>まとめ

*乱数ジェネレーター* は、一連の疑似乱数値を生成するオブジェクトです。 *Uniform Random Number Generator* (URNG) は、指定した範囲内で一様に分布した値を生成するジェネレーターです。 URNG として機能するように設計されたクラステンプレートは、このクラスに特定の共通の特徴がある場合は、 *エンジン* と呼ばれます。これについては、この記事の後半で説明します。 URNG を *分布* の `operator()` に対する引数として渡して URNG と分布を組み合わせることで、その分布によって定義された方法で分布値を生成することができます (これが通常の使用方法です)。

次のリンクを使用すると、この記事の主なセクションに移動します。

- [使用例](#code)

- [分類済みリスト](#listing)

- [エンジンと分布](#engdist)

- [解説](#comments)

### <a name="quick-tips"></a>簡単なヒント

次に、`<random>` を使用する場合に留意すべきヒントを示します。

- ほとんどの場合、URNG は分布で成形される必要がある生のビットを生成します (これに関する注目すべき例外は、 [`std::shuffle()`](../standard-library/algorithm-functions.md#shuffle) URNG を直接使用するためです)。

- URNG や分布の実行は変更操作を意味するため、URNG または分布の単一のインスタンス化を同時に、安全に呼び出すことはできません。 詳細については、「[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)」をご覧ください。

- 複数のエンジンの[定義済み typedef](#typedefs) が提供されています。エンジンを使用している場合、これは URNG を作成するお薦めの方法です。

- 大部分のアプリケーションに対して最も役立つ組み合わせは、`mt19937` エンジンと `uniform_int_distribution` の組み合わせです (この記事の後の方にある[コード例](#code)に示されています)。

`<random>` ヘッダーには選択できるオプションが多数あり、これらはいずれも以前の C ランタイム関数 `rand()` より適しています。 `rand()` の不具合やこれらの不具合に対する `<random>` の対応の詳細については、[このビデオ](https://go.microsoft.com/fwlink/p/?linkid=397615)をご覧ください。

## <a name="examples"></a><a name="code"></a> 使用例

次のコード例では、非確定的なシードを使用して作成されたジェネレーターを使用して 5 つの乱数を生成する方法を示します。

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
                        // replace the call to rd() with a
                        // constant value to get repeatable
                        // results.

    for (int i = 0; i < 5; ++i) {
        cout << gen() << " "; // print the raw output of the generator.
    }
    cout << endl;
}
```

```Output
2430338871 3531691818 2723770500 3252414483 3632920437
```

これらは高品質の乱数であり、このプログラムを実行するたびに変化しますが、有効範囲内である必要はありません。 この範囲を制御するには、次のコードに示すように、一様分布を使用します。

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
    uniform_int_distribution<> dist(1,6); // distribute results between 1 and 6 inclusive.

    for (int i = 0; i < 5; ++i) {
        cout << dist(gen) << " "; // pass the generator to the distribution.
    }
    cout << endl;
}
```

```Output
5 1 6 1 2
```

次のコード例では、一様に分布した乱数のジェネレーターを使用してベクトルと配列の内容をシャッフルする、より実用的な一連のユース ケースを示します。

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <array>
#include <iostream>
#include <random>
#include <string>
#include <vector>
#include <functional> // ref()

using namespace std;

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

template <class URNG>
void test(URNG& urng) {

    // Uniform distribution used with a vector
    // Distribution is [-5, 5] inclusive
    uniform_int_distribution<int> dist(-5, 5);
    vector<int> v;

    for (int i = 0; i < 20; ++i) {
        v.push_back(dist(urng));
    }

    cout << "Randomized vector: ";
    print(v);

    // Shuffle an array
    // (Notice that shuffle() takes a URNG, not a distribution)
    array<string, 26> arr = { { "H", "He", "Li", "Be", "B", "C", "N", "O", "F",
        "Ne", "Na", "Mg", "Al", "Si", "P", "S", "Cl", "Ar", "K", "Ca", "Sc",
        "Ti", "V", "Cr", "Mn", "Fe" } };

    shuffle(arr.begin(), arr.end(), urng);

    cout << "Randomized array: ";
    print(arr);
    cout << "--" << endl;
}

int main()
{
    // First run: non-seedable, non-deterministic URNG random_device
    // Slower but crypto-secure and non-repeatable.
    random_device rd;
    cout << "Using random_device URNG:" << endl;
    test(rd);

    // Second run: simple integer seed, repeatable results
    cout << "Using constant-seed mersenne twister URNG:" << endl;
    mt19937 engine1(12345);
    test(engine1);

    // Third run: random_device as a seed, different each run
    // (Desirable for most purposes)
    cout << "Using non-deterministic-seed mersenne twister URNG:" << endl;
    mt19937 engine2(rd());
    test(engine2);

    // Fourth run: "warm-up" sequence as a seed, different each run
    // (Advanced uses, allows more than 32 bits of randomness)
    cout << "Using non-deterministic-seed \"warm-up\" sequence mersenne twister URNG:" << endl;
    array<unsigned int, mt19937::state_size> seed_data;
    generate_n(seed_data.begin(), seed_data.size(), ref(rd));
    seed_seq seq(begin(seed_data), end(seed_data));
    mt19937 engine3(seq);
    test(engine3);
}
```

```Output
Using random_device URNG:
Randomized vector: 5 -4 2 3 0 5 -2 0 4 2 -1 2 -4 -3 1 4 4 1 2 -2
Randomized array: O Li V K C Ti N Mg Ne Sc Cl B Cr Mn Ca Al F P Na Be Si Ar Fe S He H
--
Using constant-seed mersenne twister URNG:
Randomized vector: 3 -1 -5 0 0 5 3 -4 -3 -4 1 -3 0 -3 -2 -4 5 1 -1 -1
Randomized array: Al O Ne Si Na Be C N Cr Mn H V F Sc Mg Fe K Ca S Ti B P Ar Cl Li He
--
Using non-deterministic-seed mersenne twister URNG:
Randomized vector: 5 -4 0 2 1 -2 4 4 -4 0 0 4 -5 4 -5 -1 -3 0 0 3
Randomized array: Si Fe Al Ar Na P B Sc H F Mg Li C Ti He N Mn Be O Ca Cr V K Ne Cl S
--
Using non-deterministic-seed "warm-up" sequence mersenne twister URNG:
Randomized vector: -1 3 -2 4 1 3 0 -5 5 -5 0 0 5 0 -3 3 -4 2 5 0
Randomized array: Si C Sc H Na O S Cr K Li Al Ti Cl B Mn He Fe Ne Be Ar V P Ca N Mg F
--
```

このコードは、テスト テンプレート関数を使用した 2 つの異なるランダム化 (整数のベクターのランダム化と、インデックス付きデータの配列のシャッフル) を示しています。 最初のテスト関数の呼び出しでは、暗号的に安全で非確定的な、シード設定不可および繰り返し不可の URNG `random_device` を使用しています。 2 回目のテスト実行では、確定的な 32 ビットの定数シードを指定し、`mersenne_twister_engine` を URNG として使用しています。これは、結果が繰り返し可能であることを意味します。 3 回目のテスト実行は、`mersenne_twister_engine` からの 32 ビットの非確定的な結果を使用して `random_device` にシードを設定しています。 4 回目のテスト実行では、`random_device` の結果で埋められた[シード シーケンス](../standard-library/seed-seq-class.md)を使用することで、3 回目のテスト実行を拡張しています。これによって、32 ビット以上の非確定的なランダム性が効果的に得られます (それでもまだ暗号的に安全ではありません)。 詳細については、この続きを参照してください。

## <a name="categorized-listing"></a><a name="listing"></a> 分類別一覧

### <a name="uniform-random-number-generators"></a><a name="urngs"></a> Uniform Random Number ジェネレーター

URNG は、次の特性においてよく説明されます。

1. **周期の長さ**: 生成された数のシーケンスを繰り返すために、どれだけの回数の反復処理を行うか。 長いほど良いです。

2. **パフォーマンス**: どれだけ迅速に数を生成できるか、どれだけメモリを使用するか。 値が小さいほど良いです。

3. **品質**: 生成されたシーケンスがどれほど真の乱数に近いか。 これは通常 "*ランダム性*" と呼ばれます。

次の各セクションでは、 `<random>` ヘッダーで提供されている Uniform Random Number Generator (URNG) を示します。

#### <a name="non-deterministic-generator"></a><a name="rd"></a> 非確定的なジェネレーター

[`random_device` 講義](../standard-library/random-device-class.md)\
外部デバイスを使用して、非確定的で暗号的に安全なランダム シーケンスを生成します。 通常、エンジンにシードを設定するために使用されます。 パフォーマンスは低いですが、品質は非常に高いです。 詳細については、「 [解説](#comments)」を参照してください。

#### <a name="engine-typedefs-with-predefined-parameters"></a><a name="typedefs"></a> 定義済みのパラメーターを持つエンジンの Typedef

エンジンとエンジン アダプターのインスタンス化用。 詳細については、「[エンジンと分布](#engdist)」をご覧ください。

- `default_random_engine` 既定のエンジン。

    ```cpp
    typedef mt19937 default_random_engine;
    ```

- `knuth_b` クヌース エンジン。

    ```cpp
    typedef shuffle_order_engine<minstd_rand0, 256> knuth_b;
    ```

- `minstd_rand0` 1988 年の最小標準エンジン (ルイス、グッドマン、ミラー、1969 年)。

    ```cpp
    typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
    ```

- `minstd_rand` 改良版の `minstd_rand0`最小標準エンジン (パーク、ミラー、ストックマイヤー、1993 年)。

    ```cpp
    typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
    ```

- `mt19937` 32 ビット メルセンヌ ツイスタ エンジン (松本、西村、1998年)。

    ```cpp
    typedef mersenne_twister_engine<
        unsigned int, 32, 624, 397,
        31, 0x9908b0df,
        11, 0xffffffff,
        7, 0x9d2c5680,
        15, 0xefc60000,
        18, 1812433253> mt19937;
    ```

- `mt19937_64` 64 ビット メルセンヌ ツイスタ エンジン (松本、西村、2000年)。

    ```cpp
    typedef mersenne_twister_engine<
        unsigned long long, 64, 312, 156,
        31, 0xb5026f5aa96619e9ULL,
        29, 0x5555555555555555ULL,
        17, 0x71d67fffeda60000ULL,
        37, 0xfff7eee000000000ULL,
        43, 6364136223846793005ULL> mt19937_64;
    ```

- `ranlux24` 24 ビット RANLUX 法エンジン (マーティン・ルッシャー、フレッド・ジェームズ、1994年)。

    ```cpp
    typedef discard_block_engine<ranlux24_base, 223, 23> ranlux24;
    ```

- `ranlux24_base``ranlux24` のベースとして使用されます。

    ```cpp
    typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;
    ```

- `ranlux48` 48 ビット RANLUX 法エンジン (マーティン・ルッシャー、フレッド・ジェームズ、1994年)。

    ```cpp
    typedef discard_block_engine<ranlux48_base, 389, 11> ranlux48;
    ```

- `ranlux48_base``ranlux48` のベースとして使用されます。

    ```cpp
    typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;
    ```

#### <a name="engine-templates"></a><a name="eng"></a> エンジン テンプレート

エンジン テンプレートは、スタンドアロンの URNG または[エンジン アダプター](#engadapt)に渡されるベース エンジンとして使用されます。 通常、これらは[定義済みのエンジンの typedef](#typedefs) でインスタンス化され、[分布](#distributions)に渡されます。 詳細については、「[エンジンと分布](#engdist)」をご覧ください。

|名前|Description|
|-|-|
|[`linear_congruential_engine` 講義](../standard-library/linear-congruential-engine-class.md)|線形合同法アルゴリズムでランダム シーケンスを生成します。 最も単純で、最も低品質です。|
|[`mersenne_twister_engine` 講義](../standard-library/mersenne-twister-engine-class.md)|メルセンヌ ツイスタ アルゴリズムでランダム シーケンスを生成します。 最も複雑で、random_device クラスを除いて最も高品質です。 パフォーマンスは非常に高速です。|
|[`subtract_with_carry_engine` 講義](../standard-library/subtract-with-carry-engine-class.md)|キャリー付き減算アルゴリズムでランダム シーケンスを生成します。 `linear_congruential_engine` の改善版ですが、`mersenne_twister_engine` より品質もパフォーマンスもかなり低いです。|

#### <a name="engine-adaptor-templates"></a><a name="engadapt"></a> エンジン アダプター テンプレート

エンジン アダプターは他の (ベース) エンジンを適応させるテンプレートです。 通常、これらは[定義済みのエンジンの typedef](#typedefs) でインスタンス化され、[分布](#distributions)に渡されます。 詳細については、「[エンジンと分布](#engdist)」をご覧ください。

|名前|Description|
|-|-|
|[`discard_block_engine` 講義](../standard-library/discard-block-engine-class.md)|ベースとなるエンジンから返された値を破棄することによってランダム シーケンスを生成します。|
|[`independent_bits_engine` 講義](../standard-library/independent-bits-engine-class.md)|ベースのエンジンから返された値のビットを再パックすることで、指定したビット数でランダム シーケンスを生成します。|
|[`shuffle_order_engine` 講義](../standard-library/shuffle-order-engine-class.md)|ベースのエンジンから返された値を並べ替えることで、ランダム シーケンスを生成します。|

[[エンジンテンプレート](#eng)]

### <a name="random-number-distributions"></a><a name="distributions"></a> 乱数分布

次の各セクションに、`<random>` ヘッダーで提供されている分布を示します。 分布は後処理メカニズムであり、通常は入力として URNG 出力を使用し、定義された統計的確率密度関数によって出力を分布させます。 詳細については、「[エンジンと分布](#engdist)」をご覧ください。

#### <a name="uniform-distributions"></a>一様分布

|名前|Description|
|-|-|
|[`uniform_int_distribution` 講義](../standard-library/uniform-int-distribution-class.md)|閉区間 \[a, b] (包含的-包含的) 内の範囲にわたる一様の整数値分布を作成します。|
|[`uniform_real_distribution` 講義](../standard-library/uniform-real-distribution-class.md)|半開区間 [a, b) (包含的-排他的) 内の範囲にわたる一様の実数 (浮動小数点) 値分布を作成します。|
|[`generate_canonical`](../standard-library/random-functions.md#generate_canonical)|[0, 1) (包含的-排他的) にわたる特定の精度の実数 (浮動小数点) 値の均等分布を作成します。|

[[乱数分布](#distributions)]

#### <a name="bernoulli-distributions"></a>ベルヌイ分布

|名前|Description|
|-|-|
|[`bernoulli_distribution` 講義](../standard-library/bernoulli-distribution-class.md)|値のベルヌーイ分布を生成 **`bool`** します。|
|[`binomial_distribution` 講義](../standard-library/binomial-distribution-class.md)|整数値の二項分布を作成します。|
|[`geometric_distribution` 講義](../standard-library/geometric-distribution-class.md)|整数値の幾何分布を作成します。|
|[`negative_binomial_distribution` 講義](../standard-library/negative-binomial-distribution-class.md)|整数値の負の二項分布を作成します。|

[[乱数分布](#distributions)]

#### <a name="normal-distributions"></a>正規分布

|名前|Description|
|-|-|
|[`cauchy_distribution` 講義](../standard-library/cauchy-distribution-class.md)|実数 (浮動小数点) 値のコーシー分布を作成します。|
|[`chi_squared_distribution` 講義](../standard-library/chi-squared-distribution-class.md)|実数 (浮動小数点) 値のカイ 2 乗分布を作成します。|
|[`fisher_f_distribution` 講義](../standard-library/fisher-f-distribution-class.md)|実数 (浮動小数点) 値の F 分布 (スネデカー分布の F 分布または Fisher-Snedecor 分布とも呼ばれます) を生成します。|
|[`lognormal_distribution` 講義](../standard-library/lognormal-distribution-class.md)|実数 (浮動小数点) 値の対数正規分布を作成します。|
|[`normal_distribution` 講義](../standard-library/normal-distribution-class.md)|実数 (浮動小数点) 値の正規 (ガウス) 分布を作成します。|
|[`student_t_distribution` 講義](../standard-library/student-t-distribution-class.md)|実数 (浮動小数点) 値のスチューデントの *t* 分布を作成します。|

[[乱数分布](#distributions)]

#### <a name="poisson-distributions"></a>ポワソン分布

|名前|Description|
|-|-|
|[`exponential_distribution` 講義](../standard-library/exponential-distribution-class.md)|実数 (浮動小数点) 値の指数分布を作成します。|
|[`extreme_value_distribution` 講義](../standard-library/extreme-value-distribution-class.md)|実数 (浮動小数点) 値の極値分布を作成します。|
|[`gamma_distribution` 講義](../standard-library/gamma-distribution-class.md)|実数 (浮動小数点) 値のガンマ分布を作成します。|
|[`poisson_distribution` 講義](../standard-library/poisson-distribution-class.md)|整数値のポワソン分布を作成します。|
|[`weibull_distribution` 講義](../standard-library/weibull-distribution-class.md)|実数 (浮動小数点) 値のワイブル分布を作成します。|

[[乱数分布](#distributions)]

#### <a name="sampling-distributions"></a>標本分布

|名前|Description|
|-|-|
|[`discrete_distribution` 講義](../standard-library/discrete-distribution-class.md)|整数の離散分布を作成します。|
|[`piecewise_constant_distribution` 講義](../standard-library/piecewise-constant-distribution-class.md)|実数 (浮動小数点) 値の区分定数分布を作成します。|
|[`piecewise_linear_distribution` 講義](../standard-library/piecewise-linear-distribution-class.md)|実数 (浮動小数点) 値の区分線形分布を作成します。|

[[乱数分布](#distributions)]

### <a name="utility-functions"></a>ユーティリティ関数

このセクションでは、`<random>` ヘッダーで提供される一般的なユーティリティ関数を示します。

|名前|Description|
|-|-|
|[`seed_seq` 講義](../standard-library/seed-seq-class.md)|バイアスのかかっていないスクランブルされたシード シーケンスを生成します。 ランダムな変量ストリームのレプリケーションを避けるために使用されます。 エンジンから多数の URNG がインスタンス化される場合に役立ちます。|

### <a name="operators"></a>演算子

このセクションでは、`<random>` ヘッダーで提供される演算子を示します。

|名前|Description|
|-|-|
|`operator==`|演算子の左側の URNG が右側のエンジンと等しいかどうかを調べます。|
|`operator!=`|演算子の左側の URNG が右側のエンジンと等しくないかどうかを調べます。|
|`operator<<`|ステータス情報をストリームに書き込みます。|
|`operator>>`|ステータス情報をストリームから抽出します。|

## <a name="engines-and-distributions"></a><a name="engdist"></a> エンジンとディストリビューション

で定義されているこれらのクラステンプレートカテゴリの詳細については、次のセクションを参照してください `<random>` 。 これらのクラステンプレートカテゴリはいずれも引数として型を受け取り、共有テンプレートパラメーター名を使用して、実際の引数の型として許可されている型のプロパティを次のように記述します。

- `IntType` 、、、、、、 **`short`** **`int`** **`long`** **`long long`** **`unsigned short`** **`unsigned int`** **`unsigned long`** 、または **`unsigned long long`** があることを示します。

- `UIntType`**`unsigned short`**、、 **`unsigned int`** **`unsigned long`** 、またはを示し **`unsigned long long`** ます。

- `RealType` 、、 **`float`** **`double`** またはを示し **`long double`** ます。

### <a name="engines"></a>エンジン

[エンジン テンプレート](#eng)と[エンジン アダプター テンプレート](#engadapt)は、作成されるジェネレーターをそのパラメーターでカスタマイズするテンプレートです。

*エンジン* は、最小値と最大値の間に一様に分布した乱数のソースとして機能するインスタンス (ジェネレーター) を持つクラスまたはクラステンプレートです。 *エンジン アダプター* は、他の乱数エンジンが作成した値を受け取って、何らかのアルゴリズムをこれらの値に適用することで、さまざまなランダム性プロパティを持つ値のシーケンスを提供します。

すべてのエンジンとエンジン アダプターには、次のメンバーが存在します。

- **`typedef`**`numeric-type` `result_type` は、ジェネレーターのによって返される型です `operator()` 。 `numeric-type`は、インスタンス化時にテンプレート パラメーターとして渡されます。

- `result_type operator()` : `min()` と `max()` の範囲内で一様に分布した値を返します。

- `result_type min()`: ジェネレーターの `operator()` から返される最小値を返します。 エンジン アダプターは、ベース エンジンの `min()` の結果を使用します。

- `result_type max()`: ジェネレーターの `operator()` から返される最大値を返します。 `result_type` が整数 (整数値) 型である場合、`max()` は実際に返される可能性のある最大の値 (包含的) になります。`result_type` が浮動小数点 (実数値) 型である場合、`max()` は返される可能性のあるすべての値より大きい最小の値 (非包含的) になります。 エンジン アダプターは、ベース エンジンの `max()` の結果を使用します。

- `void seed(result_type s)`: シード値 `s` を使用してジェネレーターにシードを設定します。 エンジンの場合、シグネチャは `void seed(result_type s = default_seed)` で、既定のパラメーターがサポートされます (エンジン アダプターでは、別個の `void seed()` が定義されています。次のサブセクションを参照してください)。

- `template <class Seq> void seed(Seq& q)`を使用してジェネレーターをシードし [`seed_seq`](../standard-library/seed-seq-class.md) `Seq` ます。

- 引数 `result_type x` を持つ明示的なコンストラクター。作成されるジェネレーターには、`seed(x)` を呼び出した場合と同じようにシード値が設定されます。

- 引数 `seed_seq& seq` を持つ明示的なコンストラクター。作成されるジェネレーターには、`seed(seq)` を呼び出した場合と同じようにシード値が設定されます。

- `void discard(unsigned long long count)` は、実際には `operator()` `count` 時間を呼び出し、各値を破棄します。

**エンジン アダプター** では、さらに次のメンバーがサポートされます (`Engine` はエンジン アダプターの最初のテンプレート パラメーターで、ベース エンジンの型を指定します)。

- ベース エンジンの既定のコンストラクターからの場合と同様にジェネレーターを初期化する既定のコンストラクター。

- 引数 `const Engine& eng` を持つ明示的なコンストラクター。 これは、ベース エンジンを使用したコピーの構築をサポートするためのものです。

- 引数 `Engine&& eng` を持つ明示的なコンストラクター。 これは、ベース エンジンを使用した移動の構築をサポートするためのものです。

- ベース エンジンの既定のシード値でジェネレーターを初期化する `void seed()`。

- ジェネレーターの構築に使用されたベース エンジンを返す `const Engine& base()` プロパティ関数。

すべてのエンジンで、後続の `operator()` への呼び出しで生成される値のシーケンスを決定する *状態* が保守されます。 同じ型のエンジンからインスタンス化された 2 つのジェネレーターの状態は、`operator==` および `operator!=` を使って比較できます。 2 つの状態を比較した結果、等しければ、それらからは同じ値のシーケンスが生成されます。 オブジェクトの状態は、そのジェネレーターの `operator<<` を使用することにより、符号なし 32 ビット値のシーケンスとしてストリームに保存できます。 保存することによって状態が変化することはありません。 保存された状態は、`operator>>` を使用すれば、同じ型のエンジンからインスタンス化されたジェネレーターに読み込むことができます。

### <a name="distributions"></a>ディストリビューション

[乱数分布](#distributions)は、エンジンから取得された一様分布の乱数ストリームを、特定の分布を持つ乱数ストリームに変換するインスタンスを持つクラステンプレートまたはクラステンプレートです。 すべての分布には、次のメンバーが存在します。

- **`typedef`**`numeric-type` `result_type` は、分布のによって返される型です `operator()` 。 `numeric-type`は、インスタンス化時にテンプレート パラメーターとして渡されます。

- `template <class URNG> result_type operator()(URNG& gen)`: 一様に分布する乱数値のソースとして `gen` を使い、格納されている *分布のパラメーター* を使用して、分布の定義に従って分布された値を返します。

- `template <class URNG> result_type operator()(URNG& gen, param_type p)`: 一様に分布する乱数値のソースとして `gen` を使い、パラメーター構造体 `p` を使用して、分布の定義に従って分布した値を返します。

- **`typedef`**`unspecified-type` `param_type` オプションでに渡すパラメーターのパッケージであり、 `operator()` 戻り値を生成するために、格納されているパラメーターの代わりに使用されます。

- `const param&` コンストラクター: 格納されているパラメーターを、その引数から初期化します。

- `param_type param() const`: 格納されているパラメーターを取得します。

- `void param(const param_type&)`: 格納されているパラメーターを、その引数から設定します。

- `result_type min()`: 分布の `operator()` から返される最小値を返します。

- `result_type max()`: 分布の `operator()` から返される最大値を返します。 `result_type` が整数 (整数値) 型である場合、`max()` は実際に返される可能性のある最大の値 (包含的) になります。`result_type` が浮動小数点 (実数値) 型である場合、`max()` は返される可能性のあるすべての値より大きい最小の値 (非包含的) になります。

- `void reset()`: 次回 `operator()` を呼び出したときに、その結果が、その前にエンジンから取得された値に左右されないようにするため、キャッシュされている値をすべて破棄します。

パラメーター構造体は、分布に必要なすべてのパラメーターを格納するオブジェクトです。 その構成要素を次に示します。

- **`typedef`**`distribution-type` `distribution_type` 。分布の型です。

- 分布のコンストラクターと同じパラメーター リストを受け取る 1 つ以上のコンストラクター。

- 分布と同じパラメーター アクセス関数。

- 等値比較演算子と非等値比較演算子。

詳細については、この下にある参照サブトピックを参照してください (この記事で既にリンクされています)。

## <a name="remarks"></a><a name="comments"></a> 解説

次の比較表に示すように、Visual Studio には 2 つの非常に有用な URNG (`mt19937` と `random_device`) があります。

|URNG|Fast|暗号的に安全|シード設定可能|決定的|
|----------|-----------|---------------------|---------------|--------------------|
|`mt19937`|はい|いいえ|はい|はい<sup>*</sup>|
|`random_device`|いいえ|はい|いいえ|いいえ|

<sup>* 既知のシードが提供される場合。</sup>

ISO C++ 標準では `random_device` が暗号的に安全であることは要求されていませんが、Visual Studio では暗号的に安全であるように実装されています ("暗号的に安全" という用語は保証を示すものではありません。特定のランダム化アルゴリズムが提供する最小限のレベルのエントロピ (それによる予測可能性レベル) を意味しています。 詳細については、Wikipedia の記事「 [暗号安全な擬似乱数ジェネレーター](https://go.microsoft.com/fwlink/p/?linkid=398017)」を参照してください。)ISO C++ 標準ではこれを必要としないため、他のプラットフォームは `random_device` (暗号的に安全ではなく) 単純な擬似乱数ジェネレーターとして実装され、別のジェネレーターのシードソースとしてのみ適している可能性があります。 クロスプラットフォーム コードで `random_device` を使用する場合は、これらのプラットフォームのドキュメントを参照してください。

定義上、`random_device` の結果は再現可能でなく、また、副作用として、他の URNG よりも実行がかなり遅い場合があります。 暗号的に安全であることが要求されない大部分のアプリケーションでは `mt19937` または類似のエンジンを使用しますが、[コード例](#code)に示すように、`random_device` の呼び出しでシードを設定することもできます。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)
