---
title: 管理 URI を表示または変更する
description: Adobe CommerceまたはMagento Open Source管理アプリケーションの URI を表示および変更するには、次の手順に従います。
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# 管理 URI を表示または変更する

このコマンドを実行する前に、次の操作を行う必要があります。 [デプロイメント設定を作成または更新する](deployment.md).

## 管理 URI を表示

このセクションでは、コマンドラインを使用して Admin Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) をクリックします。

コマンドオプション：

```bash
bin/magento info:adminuri
```

結果の例を次に示します。

```terminal
Admin Panel URI: /admin_1wgrah
```

また、 `<magento_root>/app/etc/env.php`. スニペットは次のとおりです。

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## 管理 URL の変更

管理 URI を変更するには、 [`magento setup:config:set`](deployment.md) コマンドを使用します。
