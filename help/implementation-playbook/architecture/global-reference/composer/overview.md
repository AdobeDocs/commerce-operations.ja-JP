---
title: Composer の開発
description: '''vendor/'' ディレクトリに Composer モジュールをインプレースで開発する方法について説明します。'
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 7664ffb5-2e46-49c3-b2e6-c133c35d2f6b
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Composer の開発

このトピックでは、Composer モジュールを（内の Git リポジトリとして）インプレースで開発するための推奨アプローチについて説明します。 `vendor/` ディレクトリ）に追加し、それらのモジュールをメイン Git プロジェクトに追加します。

>[!NOTE]
>
>これらのガイドラインは主に次のものに適用されます。 [グローバルリファレンスアーキテクチャ（GRA）](../overview.md) プロジェクト。

## 開発ブランチの準備

1. メイン Git リポジトリに開発ブランチを作成またはチェックアウトします。
1. 保守するモジュールごとに開発バージョンが必要です。

   この例では、メイン Git リポジトリ内のすべてのブランチが Composer パッケージ バージョンを表します。 このシナリオの Composer バージョンの推奨命名規則は次のとおりです `dev-` + ブランチ名。 例：

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. 別の Composer パッケージで特定のバージョンのモジュールが必要な場合（例： `client/module-example 1.0.12`）、エイリアスを使用してインストールします。

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   の場合 `qa` 分岐、置換 `dev-develop` （を使用） `dev-qa`.

## パッケージの Git リポジトリへの変換

デフォルトでは、パッケージにはが含まれていません。 `.git/` ディレクトリ。 Composer は、事前にビルドされた Composer パッケージを使用する代わりに、Git からパッケージをチェックアウトできます。 このアプローチの利点は、開発時にパッケージを簡単に変更できることです。

1. からモジュールを削除 `vendor/` ディレクトリ。

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

1. 複数のモジュールを Git リポジトリ（「クライアント」モジュールなど）にバッチ変換するには：

   ```bash
   rm -rf vendor/client
   composer install --prefer-source
   ```

## 開発の開始

1. フィーチャー/作業ブランチを作成またはチェックアウトします。 次の例は、Jira チケットと同じ名前のブランチを示しています。

   ```bash
   cd vendor/client/module-example
   git checkout master
   git checkout -b JIRA-1200
   ```

1. モジュールでブランチを変更した後、Adobe Commerceのキャッシュと静的コンテンツをフラッシュして、変更を確認します。

   ```bash
   bin/magento cache:flush
   bin/magento module:enable --all --clear-static-content
   ```

## 開発した主プロジェクトの更新

を変更して、メイン Git リポジトリを更新します。 `composer.lock` ファイル。 新しいモジュールの場合は、有効にします。

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
