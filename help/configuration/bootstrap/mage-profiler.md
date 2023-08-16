---
title: プロファイルを有効にする
description: MAGE Profiler を解析ツールと共に使用する方法の詳細を説明します。
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# プロファイルを有効にする

コマースプロファイルを使用すると、次のことができます。

- 組み込みプロファイラーを有効にします。

  組み込みプロファイラーを Commerce と共に使用して、パフォーマンスの分析などのタスクを実行できます。 プロファイリングの性質は、使用する解析ツールによって異なります。 複数の形式 (HTMLを含む ) をサポートしています。 プロファイラを有効にすると、 `var/profiler.flag` profiler が有効で構成を示すファイルが生成されます。 無効にすると、このファイルは削除されます。

- コマースページに依存関係グラフを表示します。

  A _依存グラフ_ は、オブジェクトの依存関係とその依存関係のリスト、およびこれらの依存関係のすべての依存関係などです。

  特にのリストに興味を持つべきです _未使用の依存関係_：一部のコンストラクターで要求されたので作成されたオブジェクトですが、使用されませんでした（つまり、メソッドは呼び出されませんでした）。 その結果、これらの依存関係を作成するのに費やされたプロセッサーの時間とメモリは無駄になります。

Commerce は、 [`Magento\Framework\Profiler`][profiler].

MAGE_PROFILER 変数またはコマンドラインを使用して、プロファイラを有効にして構成できます。

## MAGE_PROFILER を設定

次の値を設定できます： `MAGE_PROFILER` ～で論じられたいずれかの方法で [ブートストラップパラメータの値を設定する](../bootstrap/set-parameters.md).

`MAGE_PROFILER` は次の値をサポートしています。

- `1` 特定のプロファイラーの出力を有効にします。

  次のいずれかの値を使用して、特定のプロファイラーを有効にできます。

   - `csvfile` を使用 [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - その他の値 ( `2`) を含み、空の値（を使用） [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]

- `2` 依存関係グラフを有効にする。

  依存関係グラフは通常、ページの下部に表示されます。 次の図は、出力の一部を示しています。

  ![依存関係グラフ](../../assets/configuration/depend-graphs.png)

## CLI コマンド

次の CLI コマンドを使用して、プロファイラーを有効または無効にできます。

- `dev:profiler:enable <type>` 次を使用してプロファイラを有効にします。 `type` / `html` （デフォルト）または `csvfile`. 有効にした場合、flagfile `var/profiler.flag` が作成されました。
- `dev:profiler:disable` プロファイラを無効にします。 無効にした場合、flagfile `var/profiler.flag` が削除されました。

依存関係グラフを有効にするには、変数オプションを使用します。

**プロファイラーを有効または無効にするには**:

1. Commerce サーバーにログインします。
1. Commerce のインストールディレクトリに移動します。
1. ファイル・システムの所有者として、プロファイラを有効にします。

   タイプを使用してプロファイラーを有効にするには `html` フラグファイルを作成します。

   ```bash
   bin/magento dev:profiler:enable html
   ```

   タイプを使用してプロファイラーを有効にするには `csvfile` フラグファイルを作成します。

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   出力はに保存されます。 `<project-root>/var/log/profiler.csv`. The `profiler.csv` は、ページが更新されるたびに上書きされます。

   プロファイラを無効にし、フラグファイルを削除するには、次の手順に従います。

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
