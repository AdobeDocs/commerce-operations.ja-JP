---
title: Composer プロジェクト構造
description: グローバルリファレンスアーキテクチャの例で説明されている個別のパッケージオプションを設定および保守する方法について説明します。
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 8757d5b8-8309-452f-bfb3-1188a816d14f
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Composer プロジェクト構造

このガイドでは、グローバルリファレンスアーキテクチャ（GRA）の例で説明している [separate packages option](../examples.md#option-1-separate-packages) を設定および保守する方法について説明します。

## 前提条件

開始する前に、次の点を確認してください。

- Git リポジトリがある
- Composer リポジトリがある（このトピックではプライベート・パッケージ・リストをハイライト表示）
- `repo.magento.com` リポジトリと `packagist.org` リポジトリをミラーリングするように Composer リポジトリを設定しました。

## メイン Git プロジェクトリポジトリ

メイン Git プロジェクトリポジトリには、Composer プロジェクトのみを含める必要があります。 Composer パッケージを使用すると、その他すべてを管理できます。 Composer は依存関係によって他のすべてのパッケージをインストールするため、メイン プロジェクトには次のファイル構造以外のファイルを含めないでください。

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

次の内容を `.gitignore` ファイルに追加します。

```tree
/*
!/composer.json
!/composer.lock
```

## 主プロジェクトの初期化

1. `project-<region/country/brand>` という Git リポジトリを作成します。

1. `composer.json` ファイルと `composer.lock` ファイルを作成します。

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

1. `app/etc/config.xml` ファイルを Git リポジトリに追加します。

   作成するモジュールを使用して、`.htaccess`、Google、Bing 認証テキストファイル、実行可能ファイル、Adobe Commerce モジュールで管理されないその他の静的ファイルなど、他のリージョンまたはブランド固有のファイルをインストールできます。

   `magento2-component` タイプのパッケージを使用して、`composer install` および `composer update` の操作中にファイルをメイン Git リポジトリにコピーするためのファイルマッピングを作成します。

1. 命名規則 `component-environment-<region/country/brand>` に従って、Git リポジトリを作成します。

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

1. `app/etc/config.php` ファイルをマッピングとして、`composer.json` ファイルの `extra.map` 属性に追加します。

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

1. `composer.json` ファイルを検証し、Git リポジトリにコミットします。

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

1. ブランドメタパッケージを作成します。

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

1. メイン プロジェクトの依存関係管理を通じてコレクションを必要とする：

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

1. Composer が `<client>/component-environment-<region/country/brand>` から `app/etc/config.php` ファイルをコピーしたことを確認します。

## コードのデプロイ

Web サーバーでは、Composer を使用してコードをデプロイできますが、メイン プロジェクトを更新することはできません。 新しいデプロイメントのたびに、Composer を使用してプロジェクトを再インストールします。これにより、実稼動サーバーとテストサーバーが Git にアクセスする必要がなくなります。

## 他のインスタンスおよびパッケージの追加

各インスタンス（地域、ブランド、その他の一意のAdobe Commerceのインストール）は、独自の **メインプロジェクト** インスタンス、**固有のメタパッケージ** および **環境コンポーネントパッケージ** を取得する必要があります。 **GRA メタパッケージ** はすべてのインスタンスで **共有** する必要があります。

次のいずれかの方法で、機能パッケージ（Adobe Commerce モジュール、テーマ、言語パック、ライブラリなど）およびサードパーティパッケージを要求する必要があります。

- **GRA メタパッケージ** - _all_ インスタンスへのインストール用
- **インスタンス固有のメタパッケージ** - 1 つのブランドまたは地域へのインストール用

>[!IMPORTANT]
>
>`main` または `release` のブランチにあるメインプロジェクトの `composer.json` ファイルにパッケージを必要としません。

## 開発の準備

開発の場合は、保守するすべてのモジュールの `develop` バージョンをインストールします。

ブランチ戦略に応じて、`develop`、`qa`、`uat`、`main` のブランチが存在する場合があります。 各ブランチは、`dev-` というプレフィックスとともに Composer に存在します。 そのため、`develop` ブランチは、バージョン `dev-develop` として Composer を通じて必要になる場合があります。

1. すべてのモジュールとプロジェクトリポジトリに `develop` ブランチを作成します。

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

   前の手順では、`composer.json` ファイルに次の行を生成します。

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**結合しないでください** これらの `composer.json` ファイルの変更は、実稼動ブランチに対して行われます。 `release` および `main` のブランチには、安定したバージョンのパッケージのみをインストールしてください。 これらの依存関係は、`qa` のブランチと、その他の非メインブランチに対して定義できます。
