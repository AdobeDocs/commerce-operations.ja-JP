---
title: Git ベースのインストールのアップグレード
description: Git リポジトリから複製したAdobe CommerceまたはMagento Open Sourceのインストールをアップグレードします。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# Git ベースのインストールのアップグレード

このトピックでは、投稿した開発者が、Adobe CommerceまたはMagento Open Sourceを再インストールせずに更新する方法について説明します。 貢献している開発者でない場合は、 [アップグレードの実行](../implementation/perform-upgrade.md).

貢献している開発者の場合は、アップグレードするには：

1. サーバーにログインします。

1. 次に切り替え： [ファイルシステム所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. アプリケーションを複製したディレクトリに移動します。 例：

   ```bash
   cd /var/www/magento2
   ```

1. 変更を `composer.json` ファイルを上書きする理由は、次の手順で上書きされるからです。

1. のバックアップを作成します `composer.json` ファイル。

   ```bash
   cp composer.json composer.json.old
   ```

1. ローカルリポジトリを更新して最新のコードを取得します。

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >If `git pull origin develop` 失敗： [トラブルシューティング](https://support.magento.com/hc/en-us/articles/360034229872).

1. の差分とマージ `composer.json.old` ファイルに `composer.json` ファイル。

1. 依存関係を解決し、正確なバージョンを `composer.lock` ファイル。

   ```bash
   composer update
   ```

1. データベースを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. キャッシュをクリーンアップします。

   ```bash
   bin/magento cache:clean
   ```
