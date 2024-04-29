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

このガイドでは、 [別個のパッケージオプション](../examples.md#option-1-separate-packages) グローバルリファレンスアーキテクチャ（GRA）の例で説明します。

## 前提条件

開始する前に、次の点を確認してください。

- Git リポジトリがある
- Composer リポジトリがある（このトピックではプライベート・パッケージ・リストをハイライト表示）
- Composer リポジトリをミラーするように設定しました。 `repo.magento.com` および `packagist.org` リポジトリ

## メイン Git プロジェクトリポジトリ

メイン Git プロジェクトリポジトリには、Composer プロジェクトのみを含める必要があります。 Composer パッケージを使用すると、その他すべてを管理できます。 Composer は依存関係によって他のすべてのパッケージをインストールするため、メイン プロジェクトには次のファイル構造以外のファイルを含めないでください。

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

次の内容をに追加します `.gitignore` ファイル：

```tree
/*
!/composer.json
!/composer.lock
```

## 主プロジェクトの初期化

1. という Git リポジトリを作成します。 `project-<region/country/brand>`.

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

1. を追加 `app/etc/config.xml` ファイルを Git リポジトリに追加します。

   作成するモジュールを使用して、他の地域やブランド固有のファイル（など）をインストールできます `.htaccess`、Googleまたは Bing 認証テキストファイル、実行可能ファイル、またはAdobe Commerce モジュールで管理されないその他の静的ファイル。

   使用方法 `magento2-component` パッケージを入力して、ファイルのマッピングを作成し、 `composer install` および `composer update` の操作。

1. 命名規則に従った Git リポジトリを作成します `component-environment-<region/country/brand>`:

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

1. を追加 `app/etc/config.php` ファイルをマッピングとして： `extra.map` 属性 `composer.json` ファイル：

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

1. の検証 `composer.json` ファイルを作成して Git リポジトリにコミットします。

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

1. Composer がをコピーしたことを確認します `app/etc/config.php` ファイルの送信元 `<client>/component-environment-<region/country/brand>`.

## コードのデプロイ

Web サーバーでは、Composer を使用してコードをデプロイできますが、メイン プロジェクトを更新することはできません。 新しいデプロイメントのたびに、Composer を使用してプロジェクトを再インストールします。これにより、実稼動サーバーとテストサーバーが Git にアクセスする必要がなくなります。

## 他のインスタンスおよびパッケージの追加

インスタンス（地域、ブランド、その他の一意のAdobe Commerceのインストール）ごとに独自の情報を取得する必要があります **メイン プロジェクト** インスタンス， **特異的メタパッケージ**、および **環境コンポーネントパッケージ**. この **GRA メタパッケージ** は、 **共有** すべてのインスタンスで。

次のいずれかの方法で、機能パッケージ（Adobe Commerce モジュール、テーマ、言語パック、ライブラリなど）およびサードパーティパッケージを要求する必要があります。

- **GRA メタパッケージ** – にインストールする場合 _all_ instances
- **インスタンス固有のメタパッケージ** – 単一のブランドまたは地域にインストールする場合

>[!IMPORTANT]
>
>メインプロジェクトのにパッケージを必要としない `composer.json` に関するファイル `main` または `release` ブランチ。

## 開発の準備

開発のために、をインストール `develop` 管理するすべてのモジュールのバージョン。

分岐戦略に応じて、次のいずれかになります `develop`, `qa`, `uat`、および `main` ブランチ。 各ブランチは、 `dev-` プレフィックス。 したがって、 `develop` ブランチは、バージョンとして Composer を通じて必要になる場合があります `dev-develop`.

1. 作成 `develop` すべてのモジュールとプロジェクトリポジトリに分岐します。

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

   前の手順では、に次の行が生成されます `composer.json` ファイル：

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**結合しない** これらの `composer.json` 実稼動ブランチへのファイルの変更。 安定したバージョンのパッケージのみを次の場所にインストールします： `release` および `main` ブランチ。 これらの依存関係は、 `qa` ブランチと、その他の非メインブランチ。
