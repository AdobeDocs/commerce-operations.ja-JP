---
title: 管理者URIの表示または変更
description: Adobe Commerce Admin アプリケーションのURIを表示および変更するには、次の手順に従います。
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---

# 管理者URIの表示または変更

このコマンドを実行する前に、[ デプロイメント設定を作成または更新する必要があります](deployment.md)。

## 管理者URIの表示

この節では、コマンドラインを使用して管理者用の統一リソース ID （[URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)）を表示する方法について説明します。

コマンドオプション：

```shell
bin/magento info:adminuri
```

サンプル結果は次のとおりです。

```text
Admin Panel URI: /admin_1wgrah
```

`<magento_root>/app/etc/env.php`で管理者URIを表示することもできます。 スニペットは次のようになります。

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## 管理者URLの変更

管理者URIを変更するには、[`magento setup:config:set`](deployment.md) コマンドを使用します。
