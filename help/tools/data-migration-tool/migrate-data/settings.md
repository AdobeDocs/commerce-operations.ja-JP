---
title: データ移行設定
description: を使用して、Magento1 からMagento2 への設定の移行を開始する方法を説明します。 [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# データ移行設定

The `Settings` モードは、店舗、Web サイト、および配送、支払い、税の設定などのシステム設定を移行します。 アドビのデータ移行に従って [注文](overview.md#migration-order)を使用する場合は、最初に設定を移行する必要があります。

開始する前に、次の手順に従って準備を行います。

1. としてアプリケーションサーバーにログインします。 [ファイルシステム所有者](../../../installation/prerequisites/file-system/overview.md).

1. 次に変更： `/bin` ディレクトリに追加するか、システムに追加されていることを確認します。 `PATH`.

>[!NOTE]
>
>にMagento2 がデプロイされていることを確認します。 `default` モード。 開発者モードでは、移行ツールで検証エラーが発生する可能性があります。


詳しくは、 [最初の手順](overview.md#first-steps) の節を参照してください。

## 設定移行コマンドを実行します。

設定の移行を開始するには、次のコマンドを実行します。

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

次の場合：

* `[-r|--reset]` は、最初から移行を開始するオプションの引数です。 この引数を使用して移行をテストできます。

* `[-a|--auto]` は、整合性チェックエラーが発生した場合に移行を停止しないようにする、オプションの引数です。

* `{<path to config.xml>}` は、移行ツールの [`config.xml`](../configure.md#configure-migration-in-vendor-folder) ファイル。この引数は必須です。

>[!NOTE]
>
>このコマンドでは、すべての設定が移行されるわけではありません。 先に進む前に、Magento2 管理ですべての設定を確認します。


The `Migration completed` 設定が正常に転送された後に、メッセージが表示されます。

## カスタム移行ルールの設定

設定の移行時に、システム設定を無視、名前変更、または変更できます。 この場合は、 `settings.xml` ファイル。

1. アプリケーションサーバーに、 [ファイルシステム所有者](../../../installation/prerequisites/file-system/overview.md).

1. 次のディレクトリに移動します。

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   例えば、アプリケーションが `/var/www/html`、 `settings.xml.dist` ファイルは、次のいずれかのディレクトリにあります。

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. を作成するには、以下を実行します。 `settings.xml` 提供されたサンプルのファイルで、次のコマンドを実行します。

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. で変更を加えます。 `settings.xml`.

1. マッピングの設定ファイルの新しい名前を指定するには、 `<settings_map_file>` タグを `path/to/config.xml` ファイル。

詳しくは、 [移行モードの設定](../technical-specification.md#settings-migration-mode) ツールのセクション [仕様](../technical-specification.md).

## 次の移行手順

* [データの移行](data.md)
