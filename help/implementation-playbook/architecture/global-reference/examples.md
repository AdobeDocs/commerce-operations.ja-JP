---
title: グローバルリファレンスアーキテクチャの例
description: 大規模なAdobe Commerceプロジェクトのコード管理の例を参照してください。
role: Developer, Architect
level: Experienced
source-git-commit: 64f330919abab9644de1163c9a6d6501a9c50cc1
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---


# グローバルリファレンスアーキテクチャの例

このトピックでは、 [グローバルリファレンスアーキテクチャ (GRA)](overview.md) コードベース。 ただし、 [別個のパッケージ](#option-1-separate-packages) オプションをお勧めします。状況によっては、以下に示す他のオプションの 1 つが必要になる場合があります。

## 定義

{{$include /help/_includes/gra-definitions.md}}

## オプション 1：パッケージを分割する

詳しくは、 [Composer のプロジェクト構造](composer/project-structure.md) このメソッドの設定に関するベストプラクティスを紹介します。

![グローバルリファレンスアーキテクチャ用の個別のパッケージオプションを示す図](../../../assets/playbooks/gra-separate-packages.png)

GRA Composer パッケージを管理する最も柔軟な方法は、メタパッケージを通じてです。 メタパッケージには `composer.json` ファイルのみ。他のパッケージの依存関係を定義します。 次を使用してメタパッケージを作成 [プライベートパッケージスト](https://packagist.com/) リポジトリー。

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

各モジュール、言語パック、テーマおよびライブラリには、独自の Git リポジトリがあります。 各 Git リポジトリはプライベートパッケージリストリポジトリに自動的に同期され、 `composer.json` ファイルを Git リポジトリのルートに配置します。

## オプション 2：一括パッケージ

以下に、1 つの Composer パッケージ内の複数のモジュールの例を示します。

バルクパッケージには、同じタイプのパッケージのみを含めることができます。 例えば、Adobe Commerceのモジュール、テーマ、言語パック、ライブラリのパッケージが複数ある場合は、タイプごとに個別のバルクパッケージを作成する必要があります。

ベンダーディレクトリ内のファイル構造は、次の例のようになります。 ただし、プロジェクトを確認して、Git リポジトリに何を含めるかを確認してください )。

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

The `composer.json` ファイルは次のようになります。

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

- `core`:Adobe Commerceのコアインストールが含まれます。 Adobe Commerceのバージョンをアップグレードするために使用されます。
- `GRA`:GRA コードが含まれます。 すべての GRA モジュール、言語パック、ホワイトラベルテーマ、およびライブラリ。
- `brand/region`：各ブランドまたは地域には、ブランド固有または地域固有のコードのみを含む独自のリポジトリがあります。
- `release`：上記のすべてがこの Git リポジトリに結合されます。 ここでは結合コミットのみを使用できます。

![グローバルリファレンスアーキテクチャの分割 Git オプションを示す図](../../../assets/playbooks/gra-split-git.png)

このオプションを設定するには：

1. Git で 4 つのリポジトリタイプを作成します。 を作成します。 `core` および `GRA` を 1 回だけリポジトリします。 1 つ作成 `brand/region` 一つ `release` 各ブランドのリポジトリ。

   推奨リポジトリ名：

   - `m2-core`
   - `m2-gra`
   - `m2-region-x`/`m2-brand-x` ( 例： `m2-emea`/`m2-adobe`)
   - `m2-release-region-x`/`m2-release-brand-x` ( 例： `m2-release-emea`/`m2-release-adobe`)

1. の作成 `release/` ディレクトリに移動し、以下を実行して、すべてのリポジトリの共有 Git 履歴を作成します。

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

1. 各リポジトリを複製（例外） `core`（コンピューター上の別のディレクトリにある）

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   git clone git@github.com:example-client/m2-region-x.git
   git clone git@github.com:example-client/m2-gra.git
   ```

1. [Composer でのAdobe Commerceのインストール](../../../installation/composer.md). を削除します。 `.gitignore` ファイルを開き、 `core` リモート、コードの追加とコミット、およびプッシュ。

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

1. Adobe Analytics の `GRA` リポジトリの場合は、次のディレクトリを作成します。

   - `app/code/`
   - `app/design/`
   - `app/i18n/`
   - `lib/`

1. コードを追加します。 を削除します。 `.gitignore` ファイル、コードの追加とコミット、リモートの追加、プッシュを行います。

1. Adobe Analytics の `brand/region` リポジトリ。 の場合と同様にします。 `GRA` リポジトリを作成し、ファイルは一意である必要があります。 このリポジトリと `GRA` リポジトリ。

1. Adobe Analytics の `release` リポジトリー、結合を適用します。

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

1. を削除します。 `.gitkeep` ファイル。

1. をデプロイします。 `release` リポジトリを実稼動、テスト、QA および開発サーバーに追加します。 アップグレード `core`, `GRA`、および `brand` 次のコマンドを簡単に実行できます。

   ```bash
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

## オプション 4：モノレポ（推奨）

この方法は、Magento Open SourceGit リポジトリの動作方法を密接に模倣します。

すべてのコードは、1 つのリポジトリで開発およびテストされます。 自動処理では、この単一のリポジトリからパッケージを表示します。このパッケージは、Composer を使用して UAT および実稼動環境にインストールできます。

![グローバルリファレンスアーキテクチャの単数参照オプションを示す図](../../../assets/playbooks/gra-monorepo1.png)

Monorepo オプションを使用すると、1 つのリポジトリでの作業が簡単になると同時に、パッケージを使用してインスタンスを柔軟に作成できます。

バージョン管理とパッケージの蒸留は、GitHub アクションまたは GitLab アクションを使用して自動化されます。

![グローバルリファレンスアーキテクチャの単数参照オプションを示す図](../../../assets/playbooks/gra-monorepo2.png)

この自動化の詳細については、次のリソースを参照してください。

- [https://github.com/symplify/monorepo-builder](https://github.com/symplify/monorepo-builder)
- [https://github.com/danharrin/monorepo-split-github-action](https://github.com/danharrin/monorepo-split-github-action)

>[!TIP]
>
>モノレポの設定は高度ですが、最も柔軟性が高く、最も低いオーバーヘッドコストで実現します。

## 戦略を混在させない

GRA パッケージと `app/` ブランドまたは地域パッケージのディレクトリ。

全てを手に入れるだけではありません _メリット_ しかも、 _デメリット_ 両方のメソッドの 最適に動作させるには、どちらか一方（Git または Composer）を選択する必要があります。

## 回避するソリューション

- **GRA またはブランドを示すモジュール命名規則**

  GRA またはブランドを示す命名モジュールは、柔軟性の欠如を引き起こします。 代わりに、Composer のメタパッケージを使用して、モジュールが属するグループを特定します。 例えば、顧客 VF の場合、パッケージ `vf/meta-gra` には、すべての GRA パッケージへの参照が含まれ、 `composer require vf/meta-gra` コマンドを使用します。 パッケージ `vf/meta-kipling` には、すべての Kipling 固有のパッケージおよび `vf/meta-gra` パッケージ。 モジュール名は `vf/module-sales` および `vf/module-sap` 例： この命名規則を使用すると、ブランドと GRA のステータスの間でパッケージを移動でき、影響は低くなります。

- **Adobe Commerce core upgrades per instance**

  様々なブランドや地域で可能な限り近いタイミングで実行するために、Adobe Commerceのコアアップグレード（パッチアップグレードを含む）をスケジュールします。 共有モジュールで複数のAdobe Commerceバージョンをサポートすると、互換性の制約が原因でモジュールが分岐し、メンテナンス作業が 2 倍以上になります。 通常の開発を続行する前に、すべてのインスタンスが同じAdobe Commerceバージョンで実行されていることを確認することで、この増加した作業を防ぎます。
