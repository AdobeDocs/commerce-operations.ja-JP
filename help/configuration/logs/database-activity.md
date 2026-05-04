---
title: ログデータベースアクティビティ
description: Logger インターフェイスを使用して、データベースのアクティビティをログに記録するようにCommerceを設定します。
feature: Configuration, Logs, Storage
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# ログデータベースアクティビティ

次の例は、2つの実装を持つ`[Magento\Framework\DB\LoggerInterface](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/LoggerInterface.php)`を使用してデータベースのアクティビティをログに記録する方法を示しています。

- ログなし（デフォルト）: [`Magento\Framework\DB\Logger\Quiet`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/Logger/Quiet.php)
- `var/log` ディレクトリ [`Magento\Framework\DB\Logger\File`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/Logger/File.php)にログします

>[!TIP]
>
>Commerce CLIを使用して、[&#x200B; データベースのログを有効または無効にできます](../cli/enable-logging.md#database-logging)。

`\Magento\Framework\DB\Logger\LoggerProxy`のデフォルト設定を変更するには、`app/etc/di.xml`を編集します。

最初に、`loggerAlias`引数と`logCallStack`引数のデフォルト値を次のように変更します。

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

その後、`Magento\Framework\DB\Logger\File`のファイルパスを指定します。

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

最後に、次のコードをコンパイルします。

```shell
bin/magento setup:di:compile
```

次のコマンドを使用してキャッシュをクリーニングします。

```shell
bin/magento cache:clean
```

