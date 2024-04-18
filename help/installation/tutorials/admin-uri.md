---
title: 管理 URI の表示または変更
description: Adobe Commerce管理アプリケーションの URI を表示および変更するには、次の手順に従います。
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# 管理 URI の表示または変更

このコマンドを実行する前に、次の操作が必要です [デプロイメント設定の作成または更新](deployment.md).

## 管理 URI の表示

ここでは、コマンドラインを使用して Admin Uniform Resource Identifier （[URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)）に設定します。

コマンドオプション：

```bash
bin/magento info:adminuri
```

次に結果の例を示します。

```terminal
Admin Panel URI: /admin_1wgrah
```

また、管理者 URI は次の場所でも確認できます `<magento_root>/app/etc/env.php`. スニペットは次のとおりです。

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## 管理者 URL の変更

管理 URI を変更するには、 [`magento setup:config:set`](deployment.md) コマンド。
