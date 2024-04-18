---
title: Git ベースのインストールのアップグレード
description: Git リポジトリからクローンを作成したAdobe Commerce インストールをアップグレードします。
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Git ベースのインストールのアップグレード

このトピックでは、コントリビューションを行う開発者が、Adobe Commerceを再インストールせずに更新する方法について説明します。 コントリビューション機能を持つ開発者でない場合は、を参照してください。 [アップグレードの実行](../implementation/perform-upgrade.md).

貢献している開発者の場合にアップグレードするには：

{{$include /help/_includes/server-login.md}}

1. に加えた変更を保存します。 `composer.json` ファイルを上書きするには、次の手順に従います。

1. のバックアップを作成 `composer.json` ファイル。

   ```bash
   cp composer.json composer.json.old
   ```

1. ローカルリポジトリを更新して、最新のコードを取得します。

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >次の場合 `git pull origin develop` 失敗。を参照してください。 [トラブルシューティング](https://support.magento.com/hc/en-us/articles/360034229872).

1. の差分と結合 `composer.json.old` を含むファイル `composer.json` ファイル。

1. 依存関係を解決し、正確なバージョンをに書き込む `composer.lock` ファイル。

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
