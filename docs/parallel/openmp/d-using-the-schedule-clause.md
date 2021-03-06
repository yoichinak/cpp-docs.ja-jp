---
description: 詳細については、「D」を参照してください。Schedule 句
title: D. schedule 句
ms.date: 01/22/2019
ms.assetid: bf3d8f51-ea05-4803-bf55-657c12e91efe
ms.openlocfilehash: bd1bb4f9a6c661205e2e647fc9e45d81903008c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342492"
---
# <a name="d-the-schedule-clause"></a>D. schedule 句

並列領域には、少なくとも1つのバリアがあり、その中にバリアが追加される場合があります。 各バリアで、チームの他のメンバーは最後のスレッドが到着するまで待機する必要があります。 この待機時間を最小限に抑えるには、すべてのスレッドが同時にバリアに到達するように、共有作業を分散する必要があります。 共有作業の一部がコンストラクトに含まれている場合は、 `for` `schedule` この目的で句を使用できます。

同じオブジェクトへの参照が繰り返し実行されている場合、構成要素のスケジュールの選択は `for` 主にメモリシステムの特性によって決定されます。これには、キャッシュの存在とサイズや、メモリアクセス時間が一様であるかどうかなどが含まれます。 このような考慮事項では、ループの一部のスレッドに比較的少ない処理が割り当てられている場合でも、各スレッドが一連のループで配列の同じ要素セットを一貫して参照することをお勧めします。 この設定は `static` 、すべてのループに対して同じ境界を持つスケジュールを使用して行うことができます。 次の例では、2番目のループの下限として0が使用されて `k` いますが、スケジュールが重要でない場合はより自然であると見なされています。

```cpp
#pragma omp parallel
{
#pragma omp for schedule(static)
  for(i=0; i<n; i++)
    a[i] = work1(i);
#pragma omp for schedule(static)
  for(i=0; i<n; i++)
    if(i>=k) a[i] += work2(i);
}
```

残りの例では、メモリアクセスが主要な考慮事項ではないと想定しています。 特に明記されていない限り、すべてのスレッドは同等の計算リソースを受け取ります。 このような場合、コンストラクトに対してスケジュールを選択するかどうかは、その `for` 前のバリアの間で実行されるすべての共有作業、および句がある場合に、暗黙的な終了バリアまたは最も近い将来のバリアのいずれかに依存し `nowait` ます。 スケジュールの種類ごとに、短い例として、スケジュールの種類が最適な選択であると考えられます。 各例の簡単な説明を次に示します。

`static`スケジュールは、単純なケースにも適しています。1つのコンストラクトを含む並列領域で、 `for` 各イテレーションは同じ量の作業を必要とします。

```cpp
#pragma omp parallel for schedule(static)
for(i=0; i<n; i++) {
  invariant_amount_of_work(i);
}
```

`static`スケジュールは、各スレッドが他のスレッドとほぼ同じ反復回数を取得するプロパティによって特徴付けられます。また、各スレッドは、割り当てられたイテレーションを個別に決定できます。 したがって、作業を分散するために同期は必要ありません。また、各反復処理に同じ作業量が必要な場合は、すべてのスレッドがほぼ同じ時間に完了する必要があります。

*P* スレッドのチームの場合は、*切り上げ (n/p)* を整数 *q* にします。これは、 *0 <= r < p* の *n = p \* q-r* を満たします。 この例のスケジュールの1つの実装 `static` では、最初 *の p-1* スレッドに *q* 反復を割り当て、最後のスレッドに *q&a* を繰り返します。  もう1つの許容される実装では、最初 *の p-r* スレッドに *q* 反復を割り当て、残りの *r* スレッドに対して *q&a* を繰り返します。 この例は、プログラムが特定の実装の詳細に依存しない理由を示しています。

スケジュールは、 `dynamic` `for` さまざまな作業量を必要とするイテレーションがあるコンストラクトの場合に適しています。

```cpp
#pragma omp parallel for schedule(dynamic)
  for(i=0; i<n; i++) {
    unpredictable_amount_of_work(i);
}
```

`dynamic`スケジュールの特性は、スレッドが、他のスレッドが最後の反復処理を実行するよりも長い間、バリアで待機していないことを示します。 この要件は、使用可能になったスレッドに対して一度に1つずつイテレーションを割り当てる必要があることを意味します。割り当てごとに同期を行います。 1 *を超える最小チャンクサイズを* 指定することで、同期のオーバーヘッドを減らすことができます。これにより、スレッドには *k 未満* の値が保持 *されます*。 これにより、他のスレッドが (最大で) *k* 回の反復を実行するのではなく、バリアで待機する時間が長くなることが保証されます。

スケジュールは、 `dynamic` スレッドがさまざまなコンピューティングリソースを受け取る場合に便利です。これは、各イテレーションの作業量が変化するのとほとんど同じ効果があります。 同様に、動的スケジュールは、スレッドがさまざまなタイミングで構成要素に到達した場合にも役立ち `for` ます。ただし、このような場合は、スケジュールを使用 `guided` することをお勧めします。

`guided`スケジュールは、 `for` 各反復処理で同じ作業量が必要になるような構成要素で、スレッドが異なるタイミングで到着する可能性がある場合に適しています。 このような状況は、たとえば、コンストラクトの `for` 前に1つ以上のセクション、または句を使用して構成されている場合に発生する可能性が `for` `nowait` あります。

```cpp
#pragma omp parallel
{
  #pragma omp sections nowait
  {
    // ...
  }
  #pragma omp for schedule(guided)
  for(i=0; i<n; i++) {
    invariant_amount_of_work(i);
  }
}
```

と同様 `dynamic` に、スケジュールでは、 `guided` 他のスレッドが最終的な反復を実行するよりも長いバリアで待機しているスレッドがないこと、または *k* のチャンクサイズが指定されている場合は最終的な *k* 回の反復処理が行われることが保証されます。 このようなスケジュールで `guided` は、最も少ない同期を必要とするプロパティによってスケジュールが設定されます。 チャンクサイズが *k* の場合、一般的な実装では、使用可能な最初のスレッドに *q = シーリング (n/p)* イテレーションが割り当てられ、 *n* を *n ~ q* と *p \* k* の大きな値に設定して、すべての反復が割り当てられるまで繰り返します。

最適なスケジュールの選択がこれらの例のように明確でない場合、スケジュールは、 `runtime` プログラムを変更して再コンパイルしなくても、さまざまなスケジュールとチャンクサイズを試すのに便利です。 また、プログラムが適用される入力データに対して、最適なスケジュールが (予測可能な方法で) 依存する場合にも役立ちます。

異なるスケジュール間のトレードオフの例については、8つのスレッド間で1000回のイテレーションを共有することを検討してください。 各イテレーションに一定量の作業があり、それを時間単位として使用しているとします。

すべてのスレッドが同時に開始すると、スケジュールによって、 `static` コンストラクトは125単位で実行され、同期は行われません。 しかし、1つのスレッドが到着した100単位の遅延であるとします。 その後、残りの7つのスレッドはバリアで100ユニットを待機し、コンストラクト全体の実行時間は225になります。

との両方のスケジュールによっ `dynamic` `guided` て、バリアで1つ以上のユニットを待機しているスレッドがないことが保証されるため、遅延スレッドによって、コンストラクトの実行時間が138単位にのみ増加し、同期による遅延によって増加する可能性があります。 このような遅延が無視されない場合は、同期の数が1000であることが重要になり `dynamic` `guided` ます。ただし、の既定のチャンクサイズを想定する場合は、41のみです。 チャンクサイズが25で、 `dynamic` 両方が `guided` 150 単位で終了し、さらに必要な同期の遅延が発生します。これにより、それぞれ40と20にのみ番号が付けられます。
