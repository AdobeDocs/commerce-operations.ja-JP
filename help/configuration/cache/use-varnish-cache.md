---
title: Varnishによるキャッシュのクリア
description: Adobe CommerceのVarnish web キャッシングアクセラレータでのキャッシュのクリアの仕組みをご紹介します。 キャッシュ管理と最適化の手法をご紹介します。
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
badgePaas: label="オンプレミス" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce オンプレミス プロジェクトにのみ適用されます。"
autotag-review: '2026-06-22T22:18:33.462Z'
TQID: 'https://experienceleague.adobe.com/ePhbVWjx-hX99p8OKiKqzT-w2KZu-XjS1XieuStKqc4'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 405
ht-degree: 0%

---

# Varnishによるキャッシュのクリア

このトピックでは、Adobe Commerceのweb キャッシングアクセラレータとしてVarnishを使用する基本的な方法について説明します。

{{varnish-config-cloud}}

## ニスのパージ

[Varnish ドキュメント ](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html)によると、「キャッシュからオブジェクトを選択し、そのバリエーションとともに破棄すると、*パージ*&#x200B;が発生します。」 Varnish パージは、キャッシュクリーンコマンドに似ています（または管理画面で&#x200B;**Magento キャッシュをフラッシュ**&#x200B;をクリックします）。

実際、Commerce キャッシュのクリーニング、フラッシュ、更新を行うと、Varnishもパージされます。

VarnishをインストールしてCommerceで動作するように設定した後、次の操作を行うと、Varnishのパージが発生する可能性があります。

- web サイトの維持。

  例えば、管理画面で行う操作はすべて次のようになります。

   - **STORES** > **Settings** > **Configuration** > GENERAL > **General**
   - **STORES** > **Settings** > **Configuration** >GENERAL > **Currency Setup**
   - **STORES** > **Settings** > **Configuration** >GENERAL > **メールアドレスの保存**

  Commerceでこのような変更が検出されると、キャッシュを更新するように通知するメッセージが表示されます。

- ストアの管理（例：カテゴリ、価格、商品、プロモーション価格ルールの追加または編集）

  Varnishは、これらのタスクのいずれかを実行すると自動的にパージされます。

- ソースコードの維持。

  キャッシュを更新し、`generated/code`および`generated/metadata` ディレクトリ内のすべてを定期的に削除する必要があります。 キャッシュの更新について詳しくは、次の節を参照してください。

## VarnishをパージするためのCommerceの設定

Commerceは、[`magento setup:config:set`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset) コマンドを使用してVarnish ホストを設定した後、Varnish ホストをパージします。

オプションのパラメーター`--http-cache-hosts` パラメーターを使用して、Varnish ホストとリッスン ポートのコンマ区切りリストを指定できます。 1台または複数のVarnish ホストを設定します。 （ホストをスペース文字で区切らないでください）。

パラメーターの形式は`<hostname or ip>:<listen port>`である必要があります。ポート 80の場合は`<listen port>`を省略できます。

以下に例を挙げます。

```shell
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

その後、管理者またはコマンドラインを使用してCommerce キャッシュを更新する場合（*キャッシュのクリーニング*&#x200B;とも呼ばれます）、Varnish ホストをパージできます。

管理者を使用してキャッシュを更新するには、**[!UICONTROL SYSTEM]**/ツール/**Cache Management**&#x200B;をクリックし、ページ上部の&#x200B;**Magento キャッシュのフラッシュ**&#x200B;をクリックします。 （個々のキャッシュタイプを更新することもできます）。

コマンドラインを使用してキャッシュを更新するには、通常、[`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) コマンドを[ ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)として使用します。
