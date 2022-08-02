---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# ビルドシステムを更新

**ビルドシステムを更新するには**:

1. ビルドシステムに、ファイルシステムの所有者としてログインします。
1. アプリケーションのルートディレクトリに移動します。

   ```bash
   cd <Magento root dir>
   ```

1. 変更をにプルします。 `app/etc/config.php` ソース管理から。

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

1. ソース管理への変更を確認します。

   ```bash
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
