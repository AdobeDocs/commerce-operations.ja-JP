---
title: 複数の Vanrish インスタンスを使用したキャッシュのクリア
description: キャッシュの消去が複数の Vanish インスタンスでどのように動作するかを説明します。
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 1%

---

# 複数の Vanish インスタンスをキャッシュクリアする

Adobe CommerceとMagento Open Sourceは、すぐに使用できる複数の Vanrish インスタンスをサポートします。

このトピックでは、コマースを使用して複数の Vanrish インスタンスを設定する際の基本を示します。

## 複数の Varnish インスタンスをパージする設定

Commerce は、Vanish ホストを [`magento setup:config:set`](../../installation/tutorials/deployment.md) コマンドを使用します。

以下を使用する必要があります。 `--http-cache-hosts` Vanish ホストとリッスンポートのコンマ区切りリストを指定するためのパラメータ。 （ホストをスペース文字で区切らないでください）。

パラメーターの形式は次のようにする必要があります。 `<hostname or ip>:<listen port>`を指定します。ここで、 `<listen port>` （ポート 80 の場合）

以下に例を挙げます。

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

その後、コマースキャッシュを更新すると、すべての Vanish ホストをパージできます ( _クリーニング_ キャッシュ ) を管理者またはコマンドラインで使用します。

管理者を使用してキャッシュを更新するには、 **システム** /ツール/ **キャッシュ管理**&#x200B;を選択し、次に **フラッシュMagentoキャッシュ** をクリックします。 （個々のキャッシュタイプを更新することもできます）。

cli から複数の Varnish インスタンスのキャッシュを更新するには、 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) コマンドを [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
