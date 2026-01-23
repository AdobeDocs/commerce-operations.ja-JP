---
title: プロファイルを有効にする
description: 分析ツールで MAGE プロファイラーを使用できるようにする方法の詳細を説明します。
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# プロファイルを有効にする

Commerceのプロファイルを使用すると、次のことができます。

- ビルトインプロファイラーを有効にします。

  Commerceに組み込まれているプロファイラーを使用して、パフォーマンスの分析などのタスクを実行できます。 プロファイルの性質は、使用する分析ツールによって異なります。 HTMLを含む複数の形式をサポートしています。 プロファイラーを有効にすると、プロファイラーが有効で構成されていることを示す `var/profiler.flag` ファイルが生成されます。 無効にすると、このファイルは削除されます。

- Commerceページに依存関係グラフを表示します。

  _依存関係グラフ_ は、オブジェクトの依存関係とそのすべての依存関係、およびその依存関係のすべての依存関係の一覧です。

  _未使用の依存関係_ のリストに特に注目する必要があります。このリストは、コンストラクターから要求を受けたにもかかわらず使用されなかった（つまり、どのメソッドも呼び出されなかった）オブジェクトです。 その結果、これらの依存関係を作成するために費やしたプロセッサー時間とメモリが無駄になります。

Commerceは [`Magento\Framework\Profiler`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/Profiler.php) の基本機能を提供します。

MAGE_PROFILER 変数またはコマンドラインを使用して、プロファイラーを有効にして設定できます。

## MAGE_PROFILER の設定

`MAGE_PROFILER` の値は、[ ブートストラップパラメーターの値の設定 ](../bootstrap/set-parameters.md) で説明しているいずれかの方法で設定できます。

`MAGE_PROFILER` では、次の値をサポートしています。

- 特定のプロファイラーの出力を有効にする `1`。

  次のいずれかの値を使用して、特定のプロファイラーを有効にできます。

   - `csvfile`[`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile` を使用する ](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php)
   - `2`[`Magento\Framework\Profiler\Driver\Standard\Output\Html` を使用する空の値を含む、](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php) を除く他の値

- 依存関係グラフを有効にする `2`。

  依存関係グラフは通常、ページの下部に表示されます。 次の図に、出力の一部を示します。

  ![ 依存関係グラフ ](../../assets/configuration/depend-graphs.png)

## CLI コマンド

CLI コマンドを使用して、プロファイラーを有効または無効にできます。

- `dev:profiler:enable <type>` は、`type` （デフォルト）または `html` の `csvfile` を持つプロファイラーを有効にします。 有効にすると、フラグファイル `var/profiler.flag` が作成されます。
- `dev:profiler:disable` はプロファイラーを無効にします。 無効にすると、フラグ ファイル `var/profiler.flag` は削除されます。

依存関係グラフを有効にするには、変数オプションを使用します。

**プロファイラーを有効または無効にするには**:

1. Commerce サーバーにログインします。
1. Commerce インストールディレクトリに移動します。
1. ファイルシステムの所有者として、プロファイラーを有効にします。

   タイプ `html` を使用してプロファイラーを有効にし、フラグファイルを作成するには、次の手順に従います。

   ```bash
   bin/magento dev:profiler:enable html
   ```

   タイプ `csvfile` を使用してプロファイラーを有効にし、フラグファイルを作成するには、次の手順に従います。

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   出力は `<project-root>/var/log/profiler.csv` に保存されます。 `profiler.csv` は、ページを更新するたびに上書きされます。

   プロファイラーを無効にしてフラグファイルを削除するには、次の手順に従います。

   ```bash
   bin/magento dev:profiler:disable
   ```

