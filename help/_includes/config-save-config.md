---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# 共有設定を更新

**設定を更新するには**:

1. 開発システムに、ファイルシステムの所有者としてログインするか、ファイルシステムの所有者に切り替えます。

1. アプリケーションのルートに移動し、dump コマンドを実行します。

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   例えば、Commerce が `/var/www/html/magento2`、次を入力します。

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. 確認 `app/etc/config.php` が更新されました。

   ```bash
   git status
   ```

   レスポンスのサンプル：

   ```terminal
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >実行 _not_ 変更を `generated`, `pub/media`または `pub/static` ソース管理へのディレクトリ。 これらのファイルは、ビルドシステム上で生成されます。 開発システムには、実稼動システムで使用する準備ができていないコードやテーマなどが含まれている可能性があります。

1. 変更を `app/etc/config.php` ソース管理にのみ適用されます。

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
