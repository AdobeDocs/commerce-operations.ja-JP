---
title: 複数の Varnish インスタンスでのキャッシュのクリア
description: 複数の Varnish インスタンスでのキャッシュのクリアの仕組みを説明します。
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 1%

---

# 複数の Varnish インスタンスをクリアするキャッシュ

Adobe Commerceでは、すぐに使用できる複数の Varnish インスタンスをサポートしています。

このトピックでは、Commerceで複数の Varnish インスタンスを設定する際の基本について説明します。

## 複数の Varnish インスタンスをパージする設定

Commerceは、[`magento setup:config:set`](../../installation/tutorials/deployment.md) コマンドを使用して Varnish ホストを設定した後に、Varnish ホストをパージします。

`--http-cache-hosts` パラメーターを使用して、Varnish ホストとリッスンポートのコンマ区切りリストを指定する必要があります。 （ホストをスペース文字で区切らないでください）。

パラメーターの形式は `<hostname or ip>:<listen port>` にする必要があります。ポート 80 の場合、`<listen port>` を省略できます。

以下に例を挙げます。

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

その後、Admin またはコマンドラインでCommerceのキャッシュ（「キャッシュのクリーニング _とも呼ばれます）を更新すると_ すべての Varnish ホストをパージできます。

管理者を使用してキャッシュを更新するには、**SYSTEM**/ツール/**Cache Management** をクリックし、ページ上部の **Magentoキャッシュをフラッシュ** をクリックします。 （個々のキャッシュタイプを更新することもできます）。

cli から複数の Varnish インスタンスのキャッシュを更新するには、[`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) コマンドを [ ファイル・システムの所有者 ](../../installation/prerequisites/file-system/overview.md) として使用します。
