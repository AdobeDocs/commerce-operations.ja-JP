---
title: データベースアクティビティを記録
description: Logger インターフェイスを使用して、データベースアクティビティをログに記録するようにCommerceを設定します。
feature: Configuration, Logs, Storage
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# データベースアクティビティを記録

次の例は、2 つの実装を持つ `[Magento\Framework\DB\LoggerInterface](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/LoggerInterface.php)` を使用してデータベースアクティビティをログに記録する方法を示しています。

- ログなし（デフォルト）:[`Magento\Framework\DB\Logger\Quiet`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/Logger/Quiet.php)
- `var/log` ディレクトリへのログ：[`Magento\Framework\DB\Logger\File`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/Logger/File.php)

>[!TIP]
>
>Commerce CLI を使用して、[&#x200B; データベースのログ記録を有効または無効にする &#x200B;](../cli/enable-logging.md#database-logging) ことができます。

`\Magento\Framework\DB\Logger\LoggerProxy` のデフォルト設定を変更するには、`app/etc/di.xml` を編集します。

まず、引数 `loggerAlias` および `logCallStack` のデフォルト値を次のように変更します。

```xml
<type name="Magento\Framework\DB\Logger\LoggerProxy">
    <arguments>
        <argument name="loggerAlias" xsi:type="const">Magento\Framework\DB\Logger\LoggerProxy::LOGGER_ALIAS_FILE</argument>
        <argument name="logAllQueries" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_LOG_EVERYTHING</argument>
        <argument name="logQueryTime" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_QUERY_TIME_THRESHOLD</argument>
        <argument name="logCallStack" xsi:type="boolean">false</argument>
    </arguments>
</type>
```

その後、`Magento\Framework\DB\Logger\File` のファイルパスを指定します。

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

最後に、以下を使用してコードをコンパイルします。

```bash
bin/magento setup:di:compile
```

次のようにキャッシュをクリーンアップします。

```bash
bin/magento cache:clean
```

