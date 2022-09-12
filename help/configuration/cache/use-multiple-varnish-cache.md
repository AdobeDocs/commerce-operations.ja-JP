---
title: 複数の Vanrish インスタンスを使用したキャッシュのクリア
description: キャッシュの消去が複数の Vanish インスタンスでどのように動作するかを説明します。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 1%

---


# 複数の Vanrish インスタンスをキャッシュクリアする

Adobe CommerceとMagento Open Sourceは、すぐに使用できる複数の Vanrish インスタンスをサポートします。

このトピックでは、コマースを使用して複数の Vanrish インスタンスを設定する際の基本を示します。

## 複数の Varnish インスタンスをパージする設定

Commerce は、Vanish ホストを [`magento setup:config:set`](../../installation/tutorials/deployment.md) コマンドを使用します。

以下を使用する必要があります。 `--http-cache-hosts` Vanish ホストとリッスンポートのコンマ区切りリストを指定するためのパラメータ。 （ホストをスペース文字で区切らないでください）。

パラメーターの形式は、 `<hostname or ip>:<listen port>`を指定し、 `<listen port>` ポート 80 の場合。

以下に例を挙げます。

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

その後、コマースキャッシュを更新すると、すべての Vanish ホストをパージできます ( _クリーニング_ キャッシュ ) を管理者またはコマンドラインで使用します。

管理者を使用してキャッシュを更新するには、 **システム** /ツール/ **キャッシュ管理**&#x200B;を選択し、「 **フラッシュMagentoキャッシュ** をクリックします。 （個々のキャッシュタイプを更新することもできます）。

cli から複数の Varnish インスタンスのキャッシュを更新するには、 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) コマンドを [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
