---
title: Git ベースのインストールのアップグレード
description: Git リポジトリからクローンを作成したAdobe Commerce インストールをアップグレードします。
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Git ベースのインストールのアップグレード

このトピックでは、コントリビューションを行う開発者が、Adobe Commerceを再インストールせずに更新する方法について説明します。 コントリビューションを行う開発者でない場合は、[&#x200B; アップグレードの実行 &#x200B;](../implementation/perform-upgrade.md) を参照してください。

貢献している開発者の場合にアップグレードするには：

{{$include /help/_includes/server-login.md}}

1. `composer.json` ファイルに加えた変更は、次の手順で上書きされるので、すべて保存します。

1. `composer.json` ファイルのバックアップを作成します。

   ```bash
   cp composer.json composer.json.old
   ```

1. ローカルリポジトリを更新して、最新のコードを取得します。

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >`git pull origin develop` が失敗した場合は、[&#x200B; トラブルシューティング &#x200B;](https://support.magento.com/hc/en-us/articles/360034229872) を参照してください。

1. `composer.json.old` ファイルを `composer.json` ファイルと差分してマージします。

1. 依存関係を解決し、正確なバージョンを `composer.lock` ファイルに書き込みます。

   ```bash
   composer update
   ```

1. データベースを更新します。

   ```bash
   bin/magento setup:upgrade
   ```

1. キャッシュのクリーンアップ：

   ```bash
   bin/magento cache:clean
   ```

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
