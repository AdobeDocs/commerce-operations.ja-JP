---
title: グローバルリファレンスアーキテクチャの例
description: 大規模なAdobe Commerce プロジェクトのコード管理の例を参照してください。
role: Developer, Architect
level: Experienced
hide: true
hidefromtoc: true
exl-id: 2a85b9bf-e547-4a2a-9234-210865f55609
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# グローバルリファレンスアーキテクチャの例

このトピックでは、を整理する一般的な方法について説明します [グローバルリファレンスアーキテクチャ（GRA）](overview.md) コードベース。 ただし、 [別個のパッケージ](#option-1-separate-packages) オプションをお勧めします。状況によっては、次に説明する他のオプションのいずれかが必要な場合があります。

## 定義

{{$include /help/_includes/gra-definitions.md}}

## オプション 1：パッケージを分離する

参照： [Composer プロジェクト構造](composer/project-structure.md) このメソッドの設定のベストプラクティス。

![グローバルリファレンスアーキテクチャの別個のパッケージオプションを示す図](../../../assets/playbooks/gra-separate-packages.png)

GRA Composer パッケージを管理する最も柔軟な方法は、メタパッケージを使用することです。 メタパッケージには `composer.json` ファイルのみ。他のパッケージ依存関係を定義します。 を使用したメタパッケージの作成 [プライベート パッケージ担当者](https://packagist.com/) リポジトリ。

### 主プロジェクト `composer.json`

```json
{
    "name": "example-client/region-1",
    "description": "Example Client Region 1",
    "type": "project",
    "require": {
        "magento/product-enterprise-edition": "2.3.5",
        "example-client/meta-region-1": "~1.0"
    },
    "minimum-stability": "dev",
    "prefer-stable": true,
    "repositories": [
        {"type": "composer", "url": "https://repo.packagist.com/example-client/"},
        {"packagist.org": false}
    ]
}
```

### `example-client/meta-region-1 composer.json`

```json
{
    "name": "example-client/meta-region-1",
    "description": "Region 1 meta package",
    "type": "metapackage",
    "require": {
        "example-client/meta-gra": "~1.0",
        "example-client/theme-frontend-region1",
        "example-client/language-es-es",
        "ingenico/ogone-client"
    }
}
```

### `example-client/meta-gra composer.json`

```json
{
    "name": "example-client/meta-gra",
    "description": "GRA meta package",
    "type": "metapackage",
    "require": {
        "geoip2/geoip2": "~2.0",
        "magento-services/module-stackify-logger": "~1.1",
        "example-client/sap-connector",
        "example-client/service-chat",
        "example-client/store-locator"
    }
}
```

各モジュール、言語パック、テーマおよびライブラリには、独自の Git リポジトリがあります。 各 Git リポジトリは、プライベートパッケージリポジトリーに対して自動的に同期し、 `composer.json` git リポジトリーのルートにあるファイルです。

## オプション 2：バルクパッケージ

以下は、1 つの Composer パッケージ内の複数モジュールの例です。

バルクパッケージには、同じタイプのパッケージのみを含めることができます。 例えば、Adobe Commerceのモジュール、テーマ、言語パックおよびライブラリ用のパッケージが複数ある場合、種類ごとに個別のバルクパッケージを作成する必要があります。

ベンダーディレクトリ内のファイル構造は、次の例のようになります。 ただし、プロジェクトを調べて、Git リポジトリーに含める必要があるものを確認してください。

```tree
.
└── example-client/
    └── gra/
        └── src/
            ├── SapConnector/
            │   ├── etc/
            │   └── registration.php
            ├── ServiceChat/
            │   ├── etc/
            │   └── registration.php
            ├── StoreLocator/
            │   ├── etc/
            │   └── registration.php
            └── composer.json
```

この `composer.json` ファイルは次のようになります。

```json
{
    "name": "example-client/gra",
    "description": "GRA Modules",
    "require": {
        "magento/magento-composer-installer": "*"
    },
    "type": "magento2-module",
    "autoload": {
        "files": [
            "src/SapConnector/registration.php",
            "src/ServiceChat/registration.php",
            "src/StoreLocator/registration.php"
        ],
        "psr-4": {
            "ExampleClient\\SapConnector\\": "src/SapConnector",
            "ExampleClient\\ServiceChat\\": "src/ServiceChat",
            "ExampleClient\\StoreLocator\\": "src/StoreLocator"
        }
    }
}
```

## オプション 3:Git の分割

このアーキテクチャでは、次の 4 つの Git リポジトリを使用してコードを保存します。

- `core`:Adobe Commerce コアインストールが含まれます。 Adobe Commerceのバージョンをアップグレードするために使用されます。
- `GRA`:GRA コードが含まれます。 すべての GRA モジュール、言語パック、ホワイト・ラベル・テーマ、ライブラリ。
- `brand/region`：各ブランドまたは地域には、ブランド固有または地域固有のコードのみを含む独自のリポジトリがあります。
- `release`：上記のすべてが、この Git リポジトリに結合されます。 ここでは結合コミットのみを使用できます。

![グローバル参照アーキテクチャ用の分割 Git オプションを示す図](../../../assets/playbooks/gra-split-git.png)

このオプションを設定するには：

1. Git に 4 つのリポジトリタイプを作成します。 を作成 `core` および `GRA` リポジトリーは 1 回のみ。 1 つ作成 `brand/region` と 1 `release` 各ブランドのリポジトリ。

   リポジトリ名の候補：

   - `m2-core`
   - `m2-gra`
   - `m2-region-x`/`m2-brand-x` （例： `m2-emea`/`m2-adobe`）
   - `m2-release-region-x`/`m2-release-brand-x` （例： `m2-release-emea`/`m2-release-adobe`）

1. を作成 `release/` ディレクトリに移動し、以下を実行して、すべてのリポジトリの共有 Git 履歴を作成します。

   ```bash
   git init
   git remote add origin git@github.com:example-client/m2-release-brand-x.git
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   touch .gitkeep
   git add .gitkeep
   git commit -m 'initialize repository'
   git push -u origin master
   git push core master
   git push gra master
   git push region-x master
   ```

1. 次を除き、各リポジトリをクローンします `core`：コンピューターの別のディレクトリにあります。

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   git clone git@github.com:example-client/m2-region-x.git
   git clone git@github.com:example-client/m2-gra.git
   ```

1. [Composer によるAdobe Commerceのインストール](../../../installation/composer.md). を削除 `.gitignore` ファイル、を追加 `core` コードをリモートから追加してコミットし、プッシュします。

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition m2-core
   cd m2-core
   git init
   rm .gitignore
   git remote add origin git@github.com:example-client/m2-core.git
   git fetch
   git checkout .gitkeep
   git add --all
   git commit -m 'install Adobe Commerce'
   git push
   ```

1. が含まれる `GRA` リポジトリで、次のディレクトリを作成します。

   - `app/code/`
   - `app/design/`
   - `app/i18n/`
   - `lib/`

1. コードを追加します。 を削除 `.gitignore` コードをファイルに追加してコミットし、リモートを追加してプッシュします。

1. が含まれる `brand/region` リポジトリ。 と同じようにします。 `GRA` リポジトリを使用します。ファイルは一意である必要があります。 このリポジトリーとフォルダーの両方に同じファイルを含めることはできません `GRA` リポジトリ。

1. が含まれる `release` リポジトリで、結合を適用します。

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   cd m2-release-brand-x
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

1. を削除 `.gitkeep` ファイル。

1. のデプロイ `release` 実稼動サーバー、テストサーバー、QA サーバー、開発サーバーへのリポジトリ。 アップグレード `core`, `GRA`、および `brand` 次のコマンドを実行すると、コードを簡単に実行できます。

   ```bash
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

## オプション 4:Monorepo （推奨）

この方法は、Magento Open Source Git リポジトリの動作と非常によく似ています。

すべてのコードは、1 つのリポジトリで開発およびテストされます。 自動処理では、Composer を使用して UAT および実稼動環境にインストールできるこの単一のリポジトリからパッケージを抽出します。

![グローバルリファレンスアーキテクチャの monorepo オプションを示す図](../../../assets/playbooks/gra-monorepo1.png)

monorepo オプションを使用すると、単一のリポジトリーで簡単に操作できるだけでなく、パッケージを使用してインスタンスを柔軟に構成することもできます。

バージョン管理とパッケージの蒸留は、GitHub Actions または GitLab Actions を使用した自動化によって行われます。

![グローバルリファレンスアーキテクチャの monorepo オプションを示す図](../../../assets/playbooks/gra-monorepo2.png)

この自動処理について詳しくは、次のリソースを参照してください。

- [https://github.com/symplify/monorepo-builder](https://github.com/symplify/monorepo-builder)
- [https://github.com/danharrin/monorepo-split-github-action](https://github.com/danharrin/monorepo-split-github-action)

>[!TIP]
>
>モノリポジトリの設定は進んでいますが、最も柔軟性が高く、オーバーヘッドのコストも低くなります。

## 戦略を混在させないでください

Composer を使用して GRA パッケージと `app/` ブランドまたは地域パッケージのディレクトリ。

あなただけのすべてを得るわけではない _メリット_ しかしまた、すべて _デメリット_ 両方のメソッド。 最適に動作させるには、いずれか（Git または Composer）を選択する必要があります。

## 回避するソリューション

- **GRA またはブランドを示すモジュール命名規則**

  GRA またはブランドを示すためにモジュールに名前を付けると、柔軟性の欠如を招きます。 代わりに、Composer メタパッケージを使用して、モジュールが属するグループを判別します。 例えば、顧客 VF の場合、パッケージ `vf/meta-gra` すべての GRA パッケージへの参照が含まれており、 `composer require vf/meta-gra` コマンド。 パッケージ `vf/meta-kipling` すべての Kipling 固有のパッケージへの参照と `vf/meta-gra` パッケージ。 モジュールには名前が付けられています `vf/module-sales` および `vf/module-sap` 例： この命名規則を使用すると、パッケージをブランドと GRA のステータスの間で低い影響で移動できます。

- **インスタンスごとのAdobe Commerce コアアップグレード**

  様々なブランドや地域ができるだけ近い場所で実行されるように、Adobe Commerce コアアップグレード（パッチアップグレードを含む）をスケジュールします。 共有モジュールで複数のAdobe Commerce バージョンをサポートすると、互換性の制約が原因でモジュールがフォークされ、メンテナンス作業が 2 倍以上になります。 通常の開発を続行する前に、すべてのインスタンスが同じAdobe Commerce バージョンで実行されていることを確認することで、このような手間の増加を防ぐことができます。
