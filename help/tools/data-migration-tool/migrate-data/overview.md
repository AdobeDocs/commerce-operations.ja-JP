---
title: 移行の概要
description: ' [!DNL Data Migration Tool] を使用してMagento 1 からMagento 2 へのデータ移行を開始する方法を説明します。'
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 移行の概要

移行を開始する前に、Magento 1 cron ジョブをすべて停止します。

移行プロセス中は、移行を正しく実行するために次の一般的なルールに従います。

1. **注** 管理（配送、請求書の作成、およびクレジット メモ）を除き、Magento 1 Admin で変更を行わないでください。
1. コードを変更しない **&#x200B;**
1. Magento 2 管理およびストアフロントで変更を加える **しないでください**

>[!TIP]
>
>Magento 1 ストアフロントでのすべての操作が許可されています。

## [!DNL Data Migration Tool] を実行する

このセクションでは、[!DNL Data Migration Tool] を実行して設定、データ、または増分変更を移行する方法を示します。

### 最初の手順

1. ファイルシステムへの書き込み権限を持つユーザーとしてアプリケーションサーバーにログインするか、そのユーザーに切り替えます。 [&#x200B; ファイルシステム所有者への切り替え &#x200B;](../../../installation/prerequisites/file-system/overview.md) を参照してください。

   bash シェルを使用する場合は、次の構文を使用してファイルシステムの所有者に切り替え、同時にコマンドを入力できます。

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   ファイルシステムの所有者がログインを許可しない場合は、次の操作を実行できます。

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 任意のディレクトリからMagento コマンドを実行するには、`<magento_root>/bin` をシステム `PATH` ードに追加します。

   シェルは構文が異なるため、[unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables) などのリファレンスを参照してください。

   CentOS 用の bash シェルの例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   オプションで、次の方法でコマンドを実行できます。

   - `cd <magento_root>/bin` として `./magento <command name>` び出して実行
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` は、web サーバーの docroot のサブディレクトリです。

### コマンド構文

一般的なコマンドの例を次に示します。

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

ここで、

- `<mode>` には、[`settings`](settings.md)、[`data`](data.md)、[`delta`](delta.md) があります。
- `[-r|--reset]` は、最初から移行を開始するオプションの引数です。 この引数を使用して、移行をテストできます。
- `[-a|--auto]` は、整合性チェックエラーが発生した場合に移行が停止するのを防ぐオプション引数です。
- `{<path to config.xml>}` は `config.xml` への絶対ファイルシステムパスです。この引数は必須です。

>[!NOTE]
>
>ログは `<magento_root>/var/` ディレクトリに書き込まれます。


## 移行順序

[!DNL Data Migration Tool] を作成する際には、次のデータ転送シーケンスを想定していました。

1. [設定](settings.md)
1. [データ](data.md)
1. [変更点](delta.md)

データの移行は同じ順序で行うことを強くお勧めします。
