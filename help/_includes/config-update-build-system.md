---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# ビルドシステムの更新

**ビルドシステムを更新するには**:

1. ファイルシステムの所有者としてビルドシステムにログインします。
1. アプリケーションのルートディレクトリに移動します。

   ```bash
   cd <Magento root dir>
   ```

1. ソース管理から変更 `app/etc/config.php` 取り込みます。

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. コードをコンパイルします。

   ```bash
   bin/magento setup:di:compile
   ```

1. コードがコンパイルされたら、静的ビューファイルを生成します。

   ```bash
   bin/magento setup:static-content:deploy -f
   ```

1. ソース管理に対する変更を確認します。

   ```bash
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
