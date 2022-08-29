---
title: 移行の概要
description: を使用してMagento1 からMagento2 へのデータ移行を開始する方法を説明します。 [!DNL Data Migration Tool].
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# 移行の概要

移行を開始する前に、すべてのMagento1 cron ジョブを停止します。

移行プロセス中に、移行を成功させるには、次の一般的なルールに従います。

1. **禁止** Magento1 管理 ( 受注管理（出荷、請求書の作成、クレジット・メモ）を除く ) で変更を行う
1. **禁止** コードを変更する
1. **禁止** Magento2 管理者で変更を加え、 [店頭](https://glossary.magento.com/storefront)

>[!TIP]
>
>Magento1 ストアフロント内のすべての操作が許可されます。

## を実行します。 [!DNL Data Migration Tool]

この節では、 [!DNL Data Migration Tool] 設定、データ、または増分変更を移行する場合。

### 最初の手順

1. ファイル・システムへの書き込み権限を持つユーザーとしてアプリケーション・サーバにログインするか、切り替えます。 詳しくは、 [ファイルシステムの所有者に切り替え](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

   bash シェルを使用する場合は、次の構文を使用して、ファイルシステムの所有者に切り替え、同時にコマンドを入力できます。

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   ファイルシステムの所有者がログインを許可していない場合は、次の操作を実行できます。

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 任意のディレクトリからMagentoコマンドを実行するには、 `<magento_root>/bin` システムに `PATH`.

   シェルの構文は異なるので、次のような参照を参照してください。 [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   CentOS 用の bash シェルの例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   必要に応じて、次の方法でコマンドを実行できます。

   - `cd <magento_root>/bin` を実行します。 `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` は、Web サーバーの docroot のサブディレクトリです。

ここで説明するコマンド引数に加えて、 [一般的な引数](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands.html#instgde-cli-subcommands-common)

### コマンド構文

一般的なコマンドの例を次に示します。

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

ここで、

- `<mode>` は次のいずれかに該当します。 [`settings`](settings.md), [`data`](data.md)または [`delta`](delta.md)
- `[-r|--reset]` は、最初から移行を開始するオプションの引数です。 この引数は、移行のテストに使用できます。
- `[-a|--auto]` は、整合性チェックエラーが発生した場合に移行を停止しないようにする、オプションの引数です。
- `{<path to config.xml>}` は、 `config.xml`;この引数は必須です。

>[!NOTE]
>
>ログは `<magento_root>/var/` ディレクトリ。


## 移行順序

作成時に [!DNL Data Migration Tool]を使用する場合、次のようなデータ転送シーケンスが想定されます。

1. [設定](settings.md)
1. [データ](data.md)
1. [変更点](delta.md)

同じ順序でデータを移行することを強くお勧めします。
