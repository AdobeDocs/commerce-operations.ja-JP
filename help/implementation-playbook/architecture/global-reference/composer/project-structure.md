---
title: Composer のプロジェクト構造
description: グローバルリファレンスアーキテクチャの例で説明されている個別のパッケージオプションを設定および維持する方法について説明します。
feature: Best Practices
role: Developer
source-git-commit: b4213c40fdf903fd962a15fc99b143f31aedbcde
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---


# Composer のプロジェクト構造

このガイドでは、 [個別のパッケージオプション](../examples.md#option-1-separate-packages) グローバルリファレンスアーキテクチャ (GRA) の例で説明しています。

## 前提条件

開始する前に、次の点を確認します。

- Git リポジトリがある
- Composer リポジトリがあります（このトピックでは、プライベートパッケージリストについて説明します）。
- Composer リポジトリを `repo.magento.com` および `packagist.org` リポジトリ

## メインの Git プロジェクトリポジトリ

メインの Git プロジェクトリポジトリには、Composer プロジェクトのみを含める必要があります。 Composer パッケージを使用すると、その他すべてを管理できます。 Composer は依存関係を介して他のすべてのパッケージをインストールするので、メインプロジェクトには次のファイル構造以外のものを含めないでください。

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

次のコンテンツを `.gitignore` ファイル：

```tree
/*
!/composer.json
!/composer.lock
```

## メインプロジェクトを初期化

1. という名前の Git リポジトリを作成します。 `project-<region/country/brand>`.

1. 作成 `composer.json` および `composer.lock` ファイル：

   ```bash
   composer create-project --no-install --repository-url=https://repo.magento.com/ magento/project-enterprise-edition project-<region/country/brand>
   cd <install-directory-name>
   printf '/*\n!/composer.json\n!/composer.lock\n!/.gitignore' > .gitignore
   composer config --unset version
   composer config name '<client>/project-<region/country/brand>'
   composer config description '<client> <region/country/brand> main composer project'
   composer config repositories.private-packagist composer https://repo.packagist.com/<client>/
   composer config repositories.packagist.org false
   composer config --unset repositories.0
   composer install
   git init
   git add --all
   git commit -m 'initialize project'
   git remote add origin git@bitbucket.org:<client>/project-<region/country/brand>.git
   git push -u origin master
   ```

## モジュール以外のファイルを保存

1. 次を追加： `app/etc/config.xml` ファイルを Git リポジトリに保存します。

   作成するモジュールを使用して、他の地域やブランド固有のファイル ( 例： `.htaccess`、Googleまたは Bing 認証テキストファイル、実行可能ファイル、またはAdobe Commerceモジュールで管理されないその他の静的ファイル。

   用途 `magento2-component` パッケージを入力してファイルマッピングを作成し、次の時点でファイルをメイン Git リポジトリにコピーします。 `composer install` および `composer update` 操作。

1. 命名規則に従って Git リポジトリを作成します。 `component-environment-<region/country/brand>`:

   ```bash
   bin/magento module:enable --all
   cd ../
   mkdir component-environment-<region/country/brand>
   cd component-environment-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/component-environment-<region/country/brand>' \
    --description='<client> <region/country/brand> environment files' \
    --type=magento2-component \
    --require="magento/magento-composer-installer:*"
   mkdir -p app/etc
   cp ../project-<region/country/brand>/app/etc/config.php app/etc/
   composer config -e
   ```

1. 次を追加： `app/etc/config.php` ファイルを `extra.map` 属性 `composer.json` ファイル：

   ```json
   {
       "name": "example-client/component-environment-emea",
       "description": "Example client EMEA environment files",
       "type": "magento2-component",
       "require": {
           "magento/magento-composer-installer": "*"
       },
       "extra": {
           "map": [
               [
                   "app/etc/config.php",
                   "app/etc/config.php"
               ]
           ]
       }
   }
   ```

1. を検証します。 `composer.json` ファイルを作成し、Git リポジトリにコミットします。

   ```bash
   composer validate
   git init
   git add --all
   git commit -m 'initialize component'
   git remote add origin git@bitbucket.org:<client>/component-environment-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

## メタパッケージの設定

1. 次の Git リポジトリを作成します。

   - `meta-gra`
   - `meta-<region/country/brand>`

1. 次の依存関係ツリーを設定します。

   ```tree
   client/project-<region/country/brand>
   └─ requires -> client/meta-<region/country/brand>
                  ├─ requires -> client/component-environment-<region/country/brand>
                  └─ requires -> client/meta-gra
                                 └─ requires -> magento/product-enterprise-edition
   ```

1. GRA メタパッケージを作成します。

   ```bash
   cd ..
   mkdir meta-gra
   cd meta-gra
   composer init --no-interaction \
    --name='<client>/meta-gra' \
    --description='<client> GRA meta package' \
    --type=metapackage \
    --require="magento/product-enterprise-edition:<exact.required.version>"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-gra.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. ブランドメタパッケージの作成：

   ```bash
   cd ..
   mkdir meta-<region/country/brand>
   cd meta-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/meta-<region/country/brand>' \
    --description='<client> <region/country/brand> meta package' \
    --type=metapackage \
    --require="<client>/component-environment-<region/country/brand>:~0.1" \
    --require="<client>/meta-gra:~0.1"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. メインプロジェクトで依存関係管理を通じてコレクションを必要とする：

   ```bash
   cd ../project-<region/country/brand>
   rm app/etc/config.php
   composer remove --no-update magento/product-enterprise-edition
   composer require --no-update "<client>/meta-<region/country/brand>:~0.1"
   composer config minimum-stability alpha
   composer config prefer-stable true
   composer update
   git add --all
   git commit -m 'set up GRA dependency tree'
   git push origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Composer が `app/etc/config.php` ファイルから `<client>/component-environment-<region/country/brand>`.

## コードのデプロイ

Web サーバー上では、Composer を使用してコードをデプロイできますが、メインプロジェクトを更新することはできません。 新たにデプロイするたびに Composer を使用してプロジェクトを再インストールすると、実稼動サーバーとテストサーバーが Git にアクセスできる必要がなくなります。

## 他のインスタンスとパッケージの追加

各インスタンス ( 地域、ブランドまたはその他の一意のAdobe Commerceインストール ) には、独自のインストールが必要です **主プロジェクト** 例 **特定のメタパッケージ**、および **環境コンポーネントパッケージ**. The **GRA メタパッケージ** は、 **共有** すべてのインスタンス間で

機能パッケージ (Adobe Commerceのモジュール、テーマ、言語パック、ライブラリなど ) およびサードパーティのパッケージは、次のいずれかの方法で必要になります。

- **GRA メタパッケージ** — インストール先： _すべて_ インスタンス
- **インスタンス固有のメタパッケージ** — 単一のブランドまたは地域にインストールする場合

>[!IMPORTANT]
>
>メインプロジェクトの `composer.json` ファイルを `main` または `release` 分岐。

## 開発の準備

開発の場合は、をインストールします。 `develop` メンテナンスしているすべてのモジュールのバージョン。

分岐戦略によっては、次のことが考えられます。 `develop`, `qa`, `uat`、および `main` 分岐。 各ブランチは、 `dev-` プレフィックス。 この場合、 `develop` ブランチは、Composer を通じてバージョンとして必要になります。 `dev-develop`.

1. 作成 `develop` は、すべてのモジュールおよびプロジェクトリポジトリのブランチです。

   ```bash
   cd ../component-environment-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../meta-<region/country/brand>
   git checkout master
   git checkout -b develop
   
   git push -u origin develop
   
   
   cd ../meta-gra
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../project-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   composer require \
   "magento-services/meta-fantasy-corp:dev-develop as 0.999" \
   "magento-services/meta-gra:dev-develop as 0.999" \
   "magento-services/component-environment-fantasy-corp:dev-develop as 0.999"
   ```

   前の手順では、 `composer.json` ファイル：

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**結合しない** これら `composer.json` ファイルが実稼動ブランチに変更されます。 に安定したバージョンのパッケージのみをインストールする `release` および `main` 分岐。 これらの依存関係は、 `qa` ブランチおよび他のメイン以外のブランチ。
