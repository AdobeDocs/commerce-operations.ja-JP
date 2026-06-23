---
title: 複数のVarnish インスタンスによるキャッシュのクリア
description: Adobe Commerceの複数のVarnish インスタンスでのキャッシュのクリアの仕組みを説明します。 設定と管理のベストプラクティス。
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
badgePaas: label="オンプレミス" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce オンプレミス プロジェクトにのみ適用されます。"
autotag-review: '2026-06-22T22:16:50.500Z'
TQID: 'https://experienceleague.adobe.com/GeX8wkpM1rLLWM7jMhP2r-SJ8uV-x7fLXC8WEazZQDo'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 206
ht-degree: 0%

---

# 複数のVarnish インスタンスによるキャッシュのクリア

Adobe Commerceでは、標準搭載の複数のVarnish インスタンスをサポートしています。

このトピックでは、Commerceを使用して複数のVarnish インスタンスを設定する基本的な方法について説明します。

{{varnish-config-cloud}}

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
