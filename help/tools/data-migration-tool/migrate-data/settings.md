---
title: データ移行設定
description: を使用して、Magento 1 からMagento 2 へ設定の移行を開始する方法を説明します。 [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# データ移行設定

この `Settings` モードでは、ストア、web サイト、およびシステム設定（送料、支払い、税金設定など）が移行されます。 データ移行に応じて [順序](overview.md#migration-order)最初に設定を移行してください。

開始する前に、次の手順に従って準備を行います。

1. アプリケーションサーバーにとしてログインします [ファイルシステム所有者](../../../installation/prerequisites/file-system/overview.md).

1. をに変更します。 `/bin` ディレクトリを指定するか、システムに追加されていることを確認してください `PATH`.

>[!NOTE]
>
>Magento 2 がでデプロイされていることを確認します。 `default` モード。 開発者モードは、移行ツールで検証エラーを引き起こす可能性があります。


を参照してください。 [最初の手順](overview.md#first-steps) の節を参照してください。

## 設定移行コマンドを実行します。

設定の移行を開始するには、次を実行します。

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

ここで、

* `[-r|--reset]` は、最初から移行を開始するオプションの引数です。 この引数を使用して、移行をテストできます

* `[-a|--auto]` は、整合性チェックエラーが発生した場合に移行が停止するのを防ぐオプション引数です。

* `{<path to config.xml>}` は、移行ツールへの絶対ファイルシステムパスです。 [`config.xml`](../configure.md#configure-migration-in-vendor-folder) file；この引数は必須です。

>[!NOTE]
>
>このコマンドでは、すべての構成設定が移行されるわけではありません。 続行する前に、Magento2 管理者のすべての設定を確認してください。


この `Migration completed` 設定が正常に転送されるとメッセージが表示されます。

## カスタム移行ルールの設定

設定の移行時に、システム設定を無視、名前変更、変更することができます。 それには、 `settings.xml` ファイル。

1. アプリケーションサーバーにとしてログインするか、 [ファイルシステム所有者](../../../installation/prerequisites/file-system/overview.md).

1. 次のディレクトリに変更します。

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   例えば、アプリケーションがにインストールされている場合 `/var/www/html`, `settings.xml.dist` ファイルは、次のいずれかのディレクトリにあります。

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. を作成するには `settings.xml` 提供されたサンプルのファイルで、次を実行します：

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. で変更します。 `settings.xml`.

1. マッピング用の設定ファイルの新しい名前を指定するには、 `<settings_map_file>` 内のタグ `path/to/config.xml` ファイル。

詳しくは、 [設定の移行モード](../technical-specification.md#settings-migration-mode) ツールのセクション [仕様](../technical-specification.md).

## 次の移行手順

* [データを移行](data.md)
