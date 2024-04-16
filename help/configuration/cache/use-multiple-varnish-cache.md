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

Commerceでは、を使用して Varnish ホストを設定した後、Varnish ホストをパージします。 [`magento setup:config:set`](../../installation/tutorials/deployment.md) コマンド。

を使用する必要があります `--http-cache-hosts` パラメーター：Varnish ホストとリッスンポートのコンマ区切りリストを指定します。 （ホストをスペース文字で区切らないでください）。

パラメーターの形式は、 `<hostname or ip>:<listen port>`。を省略できます `<listen port>` ポート 80 の場合。

以下に例を挙げます。

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

その後、Commerceのキャッシュ（ _クリーニング_ キャッシュ）を使用するか、コマンドラインを使用します。

管理者を使用してキャッシュを更新するには、 **システム** > ツール > **キャッシュ管理**&#x200B;を選択し、 **Magentoキャッシュのフラッシュ** ページの上部 （個々のキャッシュタイプを更新することもできます）。

複数の Varnish インスタンスのキャッシュを cli から更新するには、次を使用します。 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) としてコマンド [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
