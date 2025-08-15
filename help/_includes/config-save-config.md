---
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
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

   例えば、Commerceが `/var/www/html/magento2` にインストールされている場合は、次のように入力します。

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. `app/etc/config.php` が更新されたことを確認します。

   ```bash
   git status
   ```

   応答の例：

   ```
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >変更をソース管理に対して _、_、または `generated` ディレクトリに送信 `pub/media` ない `pub/static` でください。 これらのファイルは、ビルドシステム上で生成します。 開発システムに、実稼動システムで使用する準備ができていないコードやテーマなどが含まれている可能性があります。

1. 変更内容を「`app/etc/config.php` only to source control」にチェックインします。

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
