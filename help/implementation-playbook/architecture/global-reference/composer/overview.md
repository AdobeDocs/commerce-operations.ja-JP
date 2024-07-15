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

このトピックでは、Composer モジュールを（`vendor/` ディレクトリ内の Git リポジトリとして）インプレースで開発し、それらのモジュールをメイン Git プロジェクトに追加するための推奨されるアプローチについて説明します。

>[!NOTE]
>
>これらのガイドラインは、主に [GRA （グローバル・リファレンス・アーキテクチャ） ](../overview.md) プロジェクトに適用されます。

## 開発ブランチの準備

1. メイン Git リポジトリに開発ブランチを作成またはチェックアウトします。
1. 保守するモジュールごとに開発バージョンが必要です。

   この例では、メイン Git リポジトリ内のすべてのブランチが Composer パッケージ バージョンを表します。 このシナリオで Composer バージョンに推奨される命名規則は、`dev-` に続いてブランチ名です。 例：

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. 別の Composer パッケージで特定のバージョンのモジュール（`client/module-example 1.0.12` など）が必要な場合は、エイリアスを付けてインストールします。

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   `qa` ブランチの場合は、`dev-develop` を `dev-qa` に置き換えます。

## パッケージの Git リポジトリへの変換

デフォルトでは、パッケージには `.git/` ディレクトリは含まれていません。 Composer は、事前にビルドされた Composer パッケージを使用する代わりに、Git からパッケージをチェックアウトできます。 このアプローチの利点は、開発時にパッケージを簡単に変更できることです。

1. `vendor/` ディレクトリからモジュールを削除します。

   ```bash
   rm -rf vendor/client/module-example
   ```

1. [ 指定された Git ソース ](#prepare-a-development-branch) を使用してモジュールを再インストールします。

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

`composer.lock` ファイルを変更して、メイン Git リポジトリを更新します。 新しいモジュールの場合は、有効にします。

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
