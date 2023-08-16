---
title: 移行の概要
description: を使用してMagento1 からMagento2 へのデータ移行を開始する方法を説明します。 [!DNL Data Migration Tool].
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# 移行の概要

移行を開始する前に、すべてのMagento1 cron ジョブを停止します。

移行プロセス中に、移行を成功させるには、次の一般的なルールに従います。

1. **禁止** Magento1 管理 ( 受注管理（発送、請求書の作成、クレジット・メモ）を除く ) で変更を行う
1. **禁止** コードを変更する
1. **禁止** Magento2 の Admin と storefront で変更を行う

>[!TIP]
>
>Magento1 ストアフロント内のすべての操作が許可されます。

## を実行します。 [!DNL Data Migration Tool]

この節では、 [!DNL Data Migration Tool] 設定、データ、または増分変更を移行する場合。

### 最初の手順

1. ファイル・システムへの書き込み権限を持つユーザーとしてアプリケーション・サーバにログインするか、切り替えます。 詳しくは、 [ファイルシステムの所有者に切り替え](../../../installation/prerequisites/file-system/overview.md).

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

### コマンドの構文

次に、一般的なコマンドの例を示します。

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

次の場合：

- `<mode>` は次の場合があります。 [`settings`](settings.md), [`data`](data.md)または [`delta`](delta.md)
- `[-r|--reset]` は、最初から移行を開始するオプションの引数です。 この引数は、移行のテストに使用できます。
- `[-a|--auto]` は、整合性チェックエラーが発生した場合に移行を停止しないようにする、オプションの引数です。
- `{<path to config.xml>}` は、に対するファイルシステムの絶対パスです。 `config.xml`；この引数は必須です。

>[!NOTE]
>
>ログは `<magento_root>/var/` ディレクトリ。


## 移行順序

作成時に、 [!DNL Data Migration Tool]を使用する場合、次のようなデータ転送シーケンスが想定されます。

1. [設定](settings.md)
1. [データ](data.md)
1. [変更点](delta.md)

同じ順序でデータを移行することを強くお勧めします。
