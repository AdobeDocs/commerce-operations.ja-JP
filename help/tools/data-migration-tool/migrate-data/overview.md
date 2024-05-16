---
title: 移行の概要
description: を使用して、Magento 1 からMagento 2 へのデータ移行を開始する方法を説明します [!DNL Data Migration Tool].
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

1. **実行しない** 受注管理（出荷、請求書の作成およびクレジット・メモ）を除き、Magento1 管理者に変更を加えます。
1. **実行しない** 任意のコードの変更
1. **実行しない** Magento 2 管理およびストアフロントでの変更

>[!TIP]
>
>Magento 1 のストアフロントでのすべての操作が許可されます。

## を実行 [!DNL Data Migration Tool]

ここでは、を実行する方法について説明します。 [!DNL Data Migration Tool] 設定、データまたは増分変更を移行します。

### 最初の手順

1. ファイルシステムへの書き込み権限を持つユーザーとしてアプリケーションサーバーにログインするか、そのユーザーに切り替えます。 参照： [ファイルシステムの所有者に切り替える](../../../installation/prerequisites/file-system/overview.md).

   bash シェルを使用する場合は、次の構文を使用してファイルシステムの所有者に切り替え、同時にコマンドを入力できます。

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   ファイルシステムの所有者がログインを許可しない場合は、次の操作を実行できます。

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 任意のディレクトリからMagentoコマンドを実行するには、 `<magento_root>/bin` お使いのシステム `PATH`.

   シェルは構文が異なるので、のようなリファレンスを参照してください。 [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   CentOS 用の bash シェルの例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   オプションで、次の方法でコマンドを実行できます。

   - `cd <magento_root>/bin` そしてそれらを `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` は、web サーバーの docroot のサブディレクトリです。

### コマンド構文

一般的なコマンドの例を次に示します。

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

ここで、

- `<mode>` 次となる場合があります。 [`settings`](settings.md), [`data`](data.md)、または [`delta`](delta.md)
- `[-r|--reset]` は、最初から移行を開始するオプションの引数です。 この引数を使用して、移行をテストできます。
- `[-a|--auto]` は、整合性チェックエラーが発生した場合に移行が停止するのを防ぐオプション引数です。
- `{<path to config.xml>}` は、への絶対ファイルシステムパスです。 `config.xml`。この引数は必須です。

>[!NOTE]
>
>ログはに書き込まれます `<magento_root>/var/` ディレクトリ。


## 移行順序

の作成時 [!DNL Data Migration Tool]では、次のデータ転送シーケンスを想定しました。

1. [設定](settings.md)
1. [データ](data.md)
1. [変更点](delta.md)

データの移行は同じ順序で行うことを強くお勧めします。
