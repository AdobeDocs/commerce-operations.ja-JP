---
title: 開発環境に関する提言
description: Adobe Commerceの開発環境の推奨事項について説明します。 導入に関するガイダンスと最適化戦略。
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%
---
# 開発環境の推奨事項

このページでは、Commerce開発環境に関する推奨事項を提供します。

## キャッシュを無効にするのではなくクリーンにする

多くの開発者は、開発者インスタンスのすべてのキャッシュを無効にする傾向があります。 すべてのキャッシュを無効にせずに、キャッシュのみをクリーニングすることをお勧めします。 キャッシュを完全に無効にするのではなく、[ キャッシュを削除](../configuration/cli/manage-cache.md#clean-and-flush-cache-types)すると、[!DNL Commerce]の実行がより効率的になります。 ほとんどの種類のキャッシュが開発中に無効化されることはほとんどありません。

キャッシュを[無効にする](../configuration/cli/manage-cache.md#enable-or-disable-cache-types)場合は、開発インスタンスでページキャッシュとブロックキャッシュのみを無効にすることをお勧めします。 テスト中にすべてのキャッシュを有効にすることを忘れないでください。

## 開発モードで回避するコマンド

開発モードでは、コンパイル、コード生成、静的コンテンツのデプロイメントのコマンドを実行しないでください。 これらのコマンドは、実稼動モードでのみ使用できるように構築されています。

**開発モードで**&#x200B;実稼動コマンドを実行しないでください：

* `setup:di:compile`は、自動生成されたクラスと最適化された設定キャッシュを生成します。

  ```shell
  bin/magento setup:di:compile
  ```

  開発モードでは、Magentoは生成をオンデマンドで実行します。実行する必要はありません。 クラスの署名を変更し、自動生成された`factories/proxies/interceptors`を再生成する必要がある場合は、これらのクラスまたは&#x200B;_生成_ フォルダーを削除します。

* `setup:static-content:deploy`は、ストアの静的コンテンツをデプロイします。

  ```shell
  bin/magento setup:static-content:deploy
  ```

  開発モードでは、Magentoがオンデマンドで実行します。実行する必要はありません。

## 仮想マシンでの通常のページ読み込み時間

VMで開発し、Magento ページの読み込みに2秒以上かかる場合は、環境設定を確認してください。
