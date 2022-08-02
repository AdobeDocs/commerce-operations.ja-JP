---
title: データベースアクティビティをログに記録
description: Commerce を設定し、ロガーインターフェイスを使用してデータベースアクティビティを記録します。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# データベースアクティビティをログに記録

次の例は、 [`Magento\Framework\DB\LoggerInterface`][interface]:2 つの実装を持つ

- 何も記録しない（デフォルト）: [`Magento\Framework\DB\Logger\Quiet`][quiet]
- にログを記録します。 `var/log` ディレクトリ： [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>Commerce CLI を使用して、 [データベース・ログの有効化と無効化](../cli/enable-logging.md#database-logging).

のデフォルト設定を変更するには `\Magento\Framework\DB\Logger\LoggerProxy`、 `app/etc/di.xml`.

まず、 `loggerAlias` および `logCallStack` 引数：

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

その後、 `Magento\Framework\DB\Logger\File`:

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

最後に、次を使用してコードをコンパイルします。

```bash
bin/magento setup:di:compile
```

次の情報を使用してキャッシュをクリーンアップします。

```bash
bin/magento cache:clean
```

<!-- link definitions -->

[file]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/File.php
[interface]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/LoggerInterface.php
[quiet]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/Quiet.php
