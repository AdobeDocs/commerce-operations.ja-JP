---
title: 複数のVarnish インスタンスによるキャッシュのクリア
description: Adobe Commerceの複数のVarnish インスタンスでのキャッシュのクリアの仕組みを説明します。 設定と管理のベストプラクティス。
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# 複数のVarnish インスタンスのキャッシュのクリア

Adobe Commerceでは、標準搭載の複数のVarnish インスタンスをサポートしています。

このトピックでは、Commerceを使用して複数のVarnish インスタンスを設定する基本的な方法について説明します。

## 複数のVarnish インスタンスをパージするための設定

Commerceは、[`magento setup:config:set`](../../installation/tutorials/deployment.md) コマンドを使用してVarnish ホストを設定した後、Varnish ホストをパージします。

`--http-cache-hosts` パラメーターを使用して、Varnish ホストとリッスン ポートのコンマ区切りリストを指定する必要があります。 （ホストをスペース文字で区切らないでください）。

パラメーターの形式は`<hostname or ip>:<listen port>`である必要があります。ポート 80の場合は`<listen port>`を省略できます。

以下に例を挙げます。

```shell
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

その後、管理者またはコマンドラインを使用してCommerce キャッシュを更新（キャッシュの&#x200B;_クリーニング_&#x200B;とも呼ばれます）すると、すべてのVarnish ホストをパージできます。

管理者を使用してキャッシュを更新するには、**SYSTEM**/ツール/**Cache Management**&#x200B;をクリックし、ページ上部の&#x200B;**Magento キャッシュのフラッシュ**&#x200B;をクリックします。 （個々のキャッシュタイプを更新することもできます）。

cliから複数のVarnish インスタンスのキャッシュを更新するには、[`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) コマンドを[ ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md)として使用します。
