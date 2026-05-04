---
title: 移行について
description: ' [!DNL Data Migration Tool]を使用してMagento 1からMagento 2へのデータ移行を開始する方法を説明します。'
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
topic: Commerce, Migration
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# 移行について

移行を開始する前に、すべてのMagento 1 cron ジョブを停止します。

移行プロセスでは、移行を成功させるための一般的なルールに従います。

1. **注文管理（発送、請求書の作成、およびクレジットメモ）を除き、Magento 1の管理者に変更を加えない**
1. **コードを変更しないでください**
1. **Magento 2管理者とストアフロントで**&#x200B;の変更を行わない

>[!TIP]
>
>Magento 1のストアフロントでは、すべての操作が許可されます。

## [!DNL Data Migration Tool]を実行

この節では、[!DNL Data Migration Tool]を実行して、設定、データ、または増分変更を移行する方法を示します。

### 最初のステップ

1. ファイルシステムへの書き込み権限を持つユーザーとしてアプリケーションサーバーにログインするか、切り替えます。 「[&#x200B; ファイルシステム所有者に切り替える](../../../installation/prerequisites/file-system/overview.md)」を参照してください。

   bash シェルを使用する場合は、次の構文を使用してファイルシステム所有者に切り替え、同時にコマンドを入力できます。

   ```shell
   su <file system owner> -s /bin/bash -c <command>
   ```

   ファイルシステムの所有者がログインを許可しない場合は、次の操作を実行できます。

   ```shell
   sudo -u <file system owner>  <command>
   ```

1. 任意のディレクトリからMagento コマンドを実行するには、システム `PATH`に`<magento_root>/bin`を追加します。

   シェルの構文は異なるので、[unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables)などの参照を参照してください。

   CentOSのbash シェルの例：

   ```shell
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   オプションで、次の方法でコマンドを実行できます。

   - `cd <magento_root>/bin`として実行`./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>`は、web サーバーのdocrootのサブディレクトリです。

### コマンド構文

次に、典型的なコマンドの例を示します。

```shell
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

どこで：

- `<mode>`は[`settings`](settings.md)、[`data`](data.md)または[`delta`](delta.md)のいずれかです
- `[-r|--reset]`は、最初から移行を開始するオプションの引数です。 この引数は、移行のテストに使用できます。
- `[-a|--auto]`は、整合性チェック エラーが発生した場合に移行が停止するのを防ぐオプションの引数です。
- `{<path to config.xml>}`は`config.xml`への絶対ファイルシステムパスです。この引数は必須です。

>[!NOTE]
>
>ログは`<magento_root>/var/` ディレクトリに書き込まれます。


## 移行指示

[!DNL Data Migration Tool]を作成する際、次のデータ転送シーケンスを想定しました。

1. [設定](settings.md)
1. [データ](data.md)
1. [変更点](delta.md)

同じ順序でデータを移行することを強くお勧めします。
