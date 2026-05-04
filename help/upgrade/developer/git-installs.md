---
title: Git ベースのインストールのアップグレード
description: Git リポジトリからクローンしたAdobe Commerce インストールをアップグレードします。
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# Git ベースのインストールのアップグレード

このトピックでは、コントリビューターがAdobe Commerceを再インストールせずに更新できる方法について説明します。 提供元の開発者でない場合は、[ アップグレードを実行する](../implementation/perform-upgrade.md)を参照してください。

開発者向けにアップグレードするには：

{{$include /help/_includes/server-login.md}}

1. 次の手順で上書きされるため、`composer.json` ファイルに加えた変更を保存します。

1. `composer.json` ファイルのバックアップを作成します。

   ```shell
   cp composer.json composer.json.old
   ```

1. ローカルリポジトリを更新して、最新のコードを取得します。

   ```shell
   git pull origin develop
   ```

   >[!NOTE]
   >
   >`git pull origin develop`が失敗した場合は、[ トラブルシューティング ](https://support.magento.com/hc/en-us/articles/360034229872)を参照してください。

1. `composer.json.old` ファイルを`composer.json` ファイルと差分して結合します。

1. 依存関係を解決し、正確なバージョンを`composer.lock` ファイルに書き込みます。

   ```shell
   composer update
   ```

1. データベースを更新します。

   ```shell
   bin/magento setup:upgrade
   ```

1. キャッシュをクリーニングします。

   ```shell
   bin/magento cache:clean
   ```

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
