---
title: コンポーザーの開発
description: 「vendor/」ディレクトリでの Composer モジュールのインプレース開発について説明します。
feature: Best Practices
role: Developer
source-git-commit: b4213c40fdf903fd962a15fc99b143f31aedbcde
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---


# コンポーザーの開発

ここでは、Composer モジュールをインプレースで開発する際に推奨されるアプローチについて説明します ( `vendor/` ディレクトリ ) を参照し、それらのモジュールをメインの Git プロジェクトに追加します。

>[!NOTE]
>
>以下のガイドラインは主に次のものに適用されます。 [グローバルリファレンスアーキテクチャ (GRA)](../overview.md) プロジェクト。

## 開発ブランチの準備

1. メイン Git リポジトリの開発ブランチを作成するか、チェックアウトします。
1. メンテナンスする各モジュールに対して開発バージョンが必要です。

   この例では、メイン Git リポジトリ内のすべてのブランチが Composer パッケージバージョンを表しています。 このシナリオでは、Composer バージョンで推奨される命名規則を次に示します。 `dev-` 支店名が続きます。 例：

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. 別の Composer パッケージに特定のバージョンのモジュールが必要な場合 ( 例： `client/module-example 1.0.12`)、エイリアスを使用してインストールします。

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   の `qa` ブランチ、置換 `dev-develop` 次を使用 `dev-qa`.

## パッケージの Git リポジトリーへの変換

デフォルトでは、パッケージには `.git/` ディレクトリ。 Composer では、事前にビルドされた Composer パッケージを使用する代わりに、Git からパッケージをチェックアウトできます。 このアプローチの利点は、開発中にパッケージを簡単に変更できる点です。

1. からモジュールを削除します。 `vendor/` ディレクトリ。

   ```bash
   rm -rf vendor/client/module-example
   ```

1. を使用してモジュールを再インストールします。 [指定された Git ソース](#prepare-a-development-branch).

   ```bash
   composer install --prefer-source
   ```

1. Composer パッケージが Git リポジトリになったことを確認します。

   ```bash
   cd vendor/client/module-example
   git remote -v
   ```

1. 複数のモジュールを Git リポジトリ（例えば、「クライアント」モジュール）にバッチ変換するには：

   ```bash
   rm -rf vendor/client
   composer install --prefer-source
   ```

## 開発を開始

1. フィーチャ/作業ブランチを作成またはチェックアウトします。 次の例は、Jira チケットと同じ名前のブランチを示しています。

   ```bash
   cd vendor/client/module-example
   git checkout master
   git checkout -b JIRA-1200
   ```

1. モジュール内のブランチを変更した後で、Adobe Commerceのキャッシュと静的コンテンツをフラッシュして変更を確認します。

   ```bash
   bin/magento cache:flush
   bin/magento module:enable --all --clear-static-content
   ```

## 開発環境でメインプロジェクトを更新する

メインの Git リポジトリを更新するには、 `composer.lock` ファイル。 モジュールが新しい場合は、有効にします。

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
