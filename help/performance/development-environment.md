---
title: 開発環境の推奨事項
description: ローカルのAdobe Commerce開発環境を設定するためのパフォーマンスの推奨事項について説明します。
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# 開発環境の推奨事項

ここでは、Commerce開発環境の推奨事項を示します。

## 無効にする代わりに、キャッシュをクリーンアップします

多くの開発者は、開発者インスタンスのすべてのキャッシュを無効にする傾向があります。 すべてのキャッシュを無効にせずに、キャッシュのクリーニングのみを行うことをお勧めします。 キャッシュ [!DNL Commerce] 完全に無効にするのではなく [ キャッシュをクリーンアップ ](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) すると、より効率的に実行されます。 ほとんどのタイプのキャッシュは、開発中に無効になることはめったにありません。

[ キャッシュを無効にする ](../configuration/cli/manage-cache.md#enable-or-disable-cache-types) 場合は、開発インスタンスでページキャッシュとブロックキャッシュのみを無効にすることをお勧めします。 テスト中はすべてのキャッシュを必ず有効にしてください。

## 開発モードで回避するコマンド

開発モードでは、コンパイル、コード生成、静的コンテンツのデプロイメントのためのコマンドを実行しないでください。 これらのコマンドは、実稼動モードでのみ使用するために作成されています。

開発モードの実稼動コマンド **実行しない**

* `setup:di:compile` は、自動生成されたクラスと最適化された設定キャッシュを生成します。

  ```bash
  bin/magento setup:di:compile
  ```

  開発モードでは、Magentoはオンデマンドで生成を実行するので、ユーザーが実行する必要はありません。 クラスの署名を変更し、自動生成された `factories/proxies/interceptors` を再生成する必要がある場合は、それらのクラスまたは _generated_ フォルダーを削除します。

* `setup:static-content:deploy` はストアの静的コンテンツをデプロイします。

  ```bash
  bin/magento setup:static-content:deploy
  ```

  開発モードでは、Magentoがオンデマンドで実行するので、ユーザーが実行する必要はありません。

## 仮想マシンの通常のページ読み込み時間

VM 上で開発を行い、Magento ページの読み込みに 2 秒以上かかる場合は、環境設定を確認してください。
