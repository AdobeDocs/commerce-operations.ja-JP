---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# 共有設定を更新します

**設定を更新するには**:

1. ファイルシステムの所有者として開発システムにログインするか、所有者に切り替えます。

1. アプリケーションルートに移動し、dump コマンドを実行します。

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   例えば、Commerceが以下にインストールされている場合： `/var/www/html/magento2`を入力します。

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. を確認します。 `app/etc/config.php` が更新されました。

   ```bash
   git status
   ```

   応答の例：

   ```terminal
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >実行 _ではない_ に対する変更の送信 `generated`, `pub/media`、または `pub/static` ソース管理するディレクトリ。 これらのファイルは、ビルドシステム上で生成します。 開発システムに、実稼動システムで使用する準備ができていないコードやテーマなどが含まれている可能性があります。

1. 変更内容をにチェックインします。 `app/etc/config.php` ソース管理にのみ適用されます。

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
