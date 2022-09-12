---
title: 開発環境Recommendations
description: ローカルのAdobe CommerceまたはMagento Open Source開発環境を設定する際の推奨パフォーマンスについて説明します。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# 開発環境に関する推奨事項

このページでは、コマース開発環境に関する推奨事項を示します。

## 無効にする代わりにキャッシュを消去する

多くの開発者は、開発者インスタンス上のすべてのキャッシュを無効にする傾向があります。 すべてのキャッシュを無効にせずに、キャッシュのみをクリーニングすることをお勧めします。 [!DNL Commerce] 次の場合により効率的に実行 [キャッシュをクリーンアップする] 完全に無効にする代わりに、を使用します。 ほとんどのタイプのキャッシュは、開発時に無効化されることはほとんどありません。

次の場合、 [キャッシュを無効にする]を無効にする場合は、開発インスタンスでページキャッシュとブロックキャッシュのみを無効にすることをお勧めします。 テスト中にすべてのキャッシュを必ず有効にしてください。

## 開発モードで回避するコマンド

開発モードでは、コンパイル、コード生成、静的コンテンツのデプロイメントに対してコマンドを実行しないでください。 これらのコマンドは、実稼働モードでのみ使用するように構築されました。

**実行しない** 開発モードの実稼働コマンド：

* `setup:di:compile` 自動生成されたクラスと最適化された構成キャッシュを生成します。

   ```bash
   bin/magento setup:di:compile
   ```

   開発モードでは、Magentoはオンデマンドで生成を実行します。実行する必要はありません。 クラスの署名を変更し、自動生成されたクラスを再生成する必要がある場合 `factories/proxies/interceptors`、これらのクラスを削除するか、 _生成済み_ フォルダー。

* `setup:static-content:deploy` ：ストアの静的コンテンツをデプロイします。

   ```bash
   bin/magento setup:static-content:deploy
   ```

   開発モードでは、Magentoはオンデマンドで実行します。実行する必要はありません。

## 仮想マシンでの通常のページ読み込み時間

VM で開発し、Magentoページの読み込みに 2 秒以上かかる場合は、環境設定を確認します。

<!-- Link definitions -->

[キャッシュをクリーンアップする]: ../configuration/cli/manage-cache.md#clean-and-flush-cache-types
[キャッシュを無効にする]: ../configuration/cli/manage-cache.md#enable-or-disable-cache-types
