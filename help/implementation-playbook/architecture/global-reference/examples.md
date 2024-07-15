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

このトピックでは、[ グローバル参照アーキテクチャ（GRA） ](overview.md) コードベースを構成する一般的な方法について説明します。 [ 個別パッケージ ](#option-1-separate-packages) オプションをお勧めしますが、状況によっては、以下に説明する他のオプションの 1 つが必要となることがあります。

## 定義

{{$include /help/_includes/gra-definitions.md}}

## オプション 1：パッケージを分離する

このメソッドの設定のベストプラクティスについては、[Composer プロジェクト構造 ](composer/project-structure.md) を参照してください。

![ グローバルリファレンスアーキテクチャの別個のパッケージオプションを示す図 ](../../../assets/playbooks/gra-separate-packages.png)

GRA Composer パッケージを管理する最も柔軟な方法は、メタパッケージを使用することです。 メタパッケージには、他のパッケージの依存関係を定義する `composer.json` ファイルのみが含まれています。 [ プライベートパッケージスト ](https://packagist.com/) リポジトリを使用してメタパッケージを作成します。

### 主なプロジェクト `composer.json`

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

各モジュール、言語パック、テーマおよびライブラリには、独自の Git リポジトリがあります。 各 Git リポジトリは、プライベートパッケージリポジトリに自動的に同期され、Git リポジトリのルートに `composer.json` ファイルがある限り、そこでパッケージを生成します。

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

`composer.json` ファイルは次のようになります。

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
- `GRA`: GRA コードが含まれます。 すべての GRA モジュール、言語パック、ホワイト・ラベル・テーマ、ライブラリ。
- `brand/region`：各ブランドまたは地域には、ブランド固有または地域固有のコードのみを含む独自のリポジトリがあります。
- `release`：上記のすべてが、この Git リポジトリに結合されます。 ここでは結合コミットのみを使用できます。

![ グローバル参照アーキテクチャ用の分割 Git オプションを示す図 ](../../../assets/playbooks/gra-split-git.png)

このオプションを設定するには：

1. Git に 4 つのリポジトリタイプを作成します。 `core` リポジトリと `GRA` リポジトリは 1 回だけ作成します。 ブランドごとに 1 つの `brand/region` と 1 つの `release` リポジトリを作成します。

   リポジトリ名の候補：

   - `m2-core`
   - `m2-gra`
   - `m2-region-x`/`m2-brand-x` （例：`m2-emea`/`m2-adobe`）
   - `m2-release-region-x`/`m2-release-brand-x` （例：`m2-release-emea`/`m2-release-adobe`）

1. `release/` ディレクトリを作成し、次を実行して、すべてのリポジトリの共有 Git 履歴を作成します。

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

1. `core` を除く各リポジトリのクローンを、コンピューター上の別のディレクトリに作成します。

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   git clone git@github.com:example-client/m2-region-x.git
   git clone git@github.com:example-client/m2-gra.git
   ```

1. [Composer を使用したAdobe Commerceのインストール ](../../../installation/composer.md)。 `.gitignore` ファイルを削除し、`core` リモートを追加し、コードを追加してコミットし、プッシュします。

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

1. `GRA` リポジトリで、次のディレクトリを作成します。

   - `app/code/`
   - `app/design/`
   - `app/i18n/`
   - `lib/`

1. コードを追加します。 `.gitignore` ファイルを削除し、コードを追加してコミットし、リモートを追加してプッシュします。

1. `brand/region` リポジトリで以下を行います。 リポジトリと同じことを行い、ファイル `GRA` 一意である必要があることに注意してください。 このリポジトリと `GRA` リポジトリの両方に同じファイルを含めることはできません。

1. `release` リポジトリで、結合を適用します。

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

1. `.gitkeep` ファイルを削除します。

1. `release` リポジトリを実稼動サーバー、テストサーバー、QA サーバーおよび開発サーバーにデプロイします。 `core`、`GRA`、`brand` コードのアップグレードは、次のコマンドを実行するのと同じくらい簡単です。

   ```bash
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

## オプション 4:Monorepo （推奨）

この方法は、Magento Open Source Git リポジトリの動作と非常によく似ています。

すべてのコードは、1 つのリポジトリで開発およびテストされます。 自動処理では、Composer を使用して UAT および実稼動環境にインストールできるこの単一のリポジトリからパッケージを抽出します。

![ グローバルリファレンスアーキテクチャの monorepo オプションを示す図 ](../../../assets/playbooks/gra-monorepo1.png)

monorepo オプションを使用すると、単一のリポジトリーで簡単に操作できるだけでなく、パッケージを使用してインスタンスを柔軟に構成することもできます。

バージョン管理とパッケージの蒸留は、GitHub Actions または GitLab Actions を使用した自動化によって行われます。

![ グローバルリファレンスアーキテクチャの monorepo オプションを示す図 ](../../../assets/playbooks/gra-monorepo2.png)

この自動処理について詳しくは、次のリソースを参照してください。

- [https://github.com/symplify/monorepo-builder](https://github.com/symplify/monorepo-builder)
- [https://github.com/danharrin/monorepo-split-github-action](https://github.com/danharrin/monorepo-split-github-action)

>[!TIP]
>
>モノリポジトリの設定は進んでいますが、最も柔軟性が高く、オーバーヘッドのコストも低くなります。

## 戦略を混在させないでください

GRA パッケージには Composer を、ブランド パッケージまたはリージョン パッケージには `app/` ディレクトリを使用する方法を組み合わせて使用することはお勧めしません。

両方の方法のすべての _利点_ だけでなく、すべての _欠点_ も得られます。 最適に動作させるには、いずれか（Git または Composer）を選択する必要があります。

## 回避するソリューション

- **GRA またはブランドを示すモジュール命名規則**

  GRA またはブランドを示すためにモジュールに名前を付けると、柔軟性の欠如を招きます。 代わりに、Composer メタパッケージを使用して、モジュールが属するグループを判別します。 例えば、顧客 VF の場合、パッケージ `vf/meta-gra` にはすべての GRA パッケージへの参照が含まれており、`composer require vf/meta-gra` コマンドを使用してインストールできます。 パッケージ `vf/meta-kipling` には、すべての Kipling 固有のパッケージへの参照と、`vf/meta-gra` パッケージへの参照が含まれています。 モジュールには `vf/module-sales` という名前を付け、例えば `vf/module-sap` という名前を付けます。 この命名規則を使用すると、パッケージをブランドと GRA のステータスの間で低い影響で移動できます。

- インスタンスあたりの **Adobe Commerce コアアップグレード数**

  様々なブランドや地域ができるだけ近い場所で実行されるように、Adobe Commerce コアアップグレード（パッチアップグレードを含む）をスケジュールします。 共有モジュールで複数のAdobe Commerce バージョンをサポートすると、互換性の制約が原因でモジュールがフォークされ、メンテナンス作業が 2 倍以上になります。 通常の開発を続行する前に、すべてのインスタンスが同じAdobe Commerce バージョンで実行されていることを確認することで、このような手間の増加を防ぐことができます。
