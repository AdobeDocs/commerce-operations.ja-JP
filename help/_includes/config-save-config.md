---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# 共有設定の更新

**設定を更新するには**:

1. 開発システムにファイルシステム所有者としてログインするか、ファイルシステム所有者に切り替えます。

1. アプリケーションのルートに移動し、dump コマンドを実行します。

   ```shell
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   例えば、`/var/www/html/magento2`にCommerceがインストールされている場合は、次のように入力します。

   ```shell
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. `app/etc/config.php`が更新されたことを確認してください。

   ```shell
   git status
   ```

   回答サンプル：

   ```text
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >_not_&#x200B;は、`generated`、`pub/media`または`pub/static` ディレクトリに変更を送信して、ソース管理に送信します。 それらのファイルをビルドシステムで生成します。 開発システムには、本番システムで使用する準備ができていないコードやテーマが含まれている可能性があります。

1. ソース管理に対してのみ`app/etc/config.php`への変更をチェックインします。

   ```shell
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
