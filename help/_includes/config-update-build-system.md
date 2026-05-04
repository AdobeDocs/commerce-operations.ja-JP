---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# ビルドシステムを更新

**ビルドシステムを更新するには**:

1. ビルドシステムにファイルシステム所有者としてログインします。
1. アプリケーションのルートディレクトリに移動します。

   ```shell
   cd <Magento root dir>
   ```

1. ソース コントロールから`app/etc/config.php`への変更をプルします。

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. コードをコンパイルします。

   ```shell
   bin/magento setup:di:compile
   ```

1. コードをコンパイルしたら、静的ビューファイルを生成します。

   ```shell
   bin/magento setup:static-content:deploy -f
   ```

1. ソースコントロールの変更を確認します。

   ```shell
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
