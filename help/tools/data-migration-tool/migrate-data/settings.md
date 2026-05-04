---
title: データ移行の設定
description: ' [!DNL Data Migration Tool]を使用してMagento 1からMagento 2への設定の移行を開始する方法について説明します。'
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# データ移行の設定

`Settings` モードでは、ストア、web サイト、および送料、支払い、税金設定などのシステム設定が移行されます。 データ移行[order](overview.md#migration-order)によると、最初に設定を移行する必要があります。

開始する前に、次の手順を実行して準備します。

1. [&#x200B; ファイルシステム所有者](../../../installation/prerequisites/file-system/overview.md)としてアプリケーションサーバーにログインします。

1. `/bin` ディレクトリに変更するか、システム `PATH`に追加してください。

>[!NOTE]
>
>Magento 2が`default` モードでデプロイされていることを確認します。 開発者モードは、移行ツールで検証エラーを引き起こす可能性があります。


詳しくは、[最初の手順](overview.md#first-steps) セクションを参照してください。

## settings migration コマンドを実行します

設定の移行を開始するには、以下を実行します。

```shell
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

どこで：

* `[-r|--reset]`は、最初から移行を開始するオプションの引数です。 この引数は、移行のテストに使用できます

* `[-a|--auto]`は、整合性チェック エラーが発生した場合に移行が停止するのを防ぐオプションの引数です。

* `{<path to config.xml>}`は、移行ツールの[`config.xml`](../configure.md#configure-migration-in-vendor-folder) ファイルへの絶対ファイルシステムパスです。この引数は必須です。

>[!NOTE]
>
>このコマンドは、すべての設定設定を移行するわけではありません。 続行する前に、Magento 2管理者のすべての設定を確認してください。


設定が正常に転送されると、`Migration completed` メッセージが表示されます。

## カスタム移行ルールの設定

設定を移行する際に、システム設定を無視、名前変更、または変更することができます。 これには、`settings.xml` ファイルでカスタムルールを指定します。

1. [&#x200B; ファイルシステム所有者](../../../installation/prerequisites/file-system/overview.md)としてアプリケーションサーバーにログインするか、切り替えます。

1. 次のディレクトリに移動します。

   ```shell
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   例えば、アプリケーションが`/var/www/html`にインストールされている場合、`settings.xml.dist` ファイルは次のいずれかのディレクトリにあります。

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. 指定されたサンプルから`settings.xml` ファイルを作成するには、次を実行します。

   ```shell
   cp settings.xml.dist settings.xml
   ```

1. `settings.xml`で変更を加えます。

1. マッピング用の設定ファイルの新しい名前を指定するには、`path/to/config.xml` ファイルの`<settings_map_file>` タグを変更します。

詳しくは、ツールの[仕様](../technical-specification.md)の[設定の移行モード &#x200B;](../technical-specification.md#settings-migration-mode)の節を参照してください。

## 次の移行手順

* [データの移行](data.md)
