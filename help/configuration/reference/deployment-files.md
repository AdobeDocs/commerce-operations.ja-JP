---
title: デプロイメント用の設定ファイル
description: Commerce アプリケーションをインストールするための設定ファイルの動作を理解します。
feature: Configuration, Deploy
exl-id: 772a6814-6b18-4f8f-b31e-72faf790ff37
source-git-commit: b40d2bd4d466782ba5bc1b29ee8681756d9e85cc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# デプロイメント用の設定ファイル

Adobe Commerceには、コンポーネントを簡単にカスタマイズし、デフォルト機能を拡張するための設定タイプを作成できる設定ファイルが用意されています。 デプロイメント設定のプロセスは、インストール用の共有設定とシステム固有の設定で構成されます。 コマースのデプロイメント設定は、 [`app/etc/config.php`](../reference/config-reference-configphp.md) および [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` が _共有_ 設定ファイル。
このファイルには、インストールされたモジュール、テーマ、言語パッケージの一覧と、共有構成設定が含まれています。

  このファイルをチェックインしてソース管理を行い、開発、ステージング、実稼動の各システムで使用します。

- `app/etc/env.php` には、インストール環境に固有の設定が含まれます。

一緒に `config.php` および `env.php` コマースと呼ばれます。 _デプロイメント設定_ ファイルはインストール中に作成され、Commerce アプリケーションを起動するために必要なためです。

>[!INFO]
>
>The [!DNL Commerce 2] デプロイメント設定の置き換え `local.xml` in [!DNL Magento 1.x].

他と異なる [モジュール設定ファイル](../reference/module-files.md)の場合、コマースデプロイメント設定は初期化中にメモリに読み込まれ、他のファイルと結合されず、拡張できません。 (`config.php` および `env.php` ただし、相互に統合されている場合は除きます )。

## デプロイメント設定の詳細

`config.php` および `env.php` は PHP ファイルで、 [多次元連想配列](https://www.w3schools.com:443/php/php_arrays.asp)：基本的に、設定パラメーターと値の階層的な配置です。

この配列の最上位レベルは次のとおりです。 _設定セグメント_. セグメントには、任意のキーで区別される任意のコンテンツ（スカラー値またはネストされた配列）があります。キーと値のペアの両方は、コマースフレームワークによって定義されます。

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) は、これらのセクションへのアクセスを提供するだけですが、拡張はできません。

次の階層レベルでは、各セグメントの項目は、無効なモジュールを除き、すべてのモジュールの設定ファイルを結合して取得されるモジュールシーケンス定義に従って並べ替えられます。

次の節では、デプロイメント設定の構造と内容について説明します。

- インストール済みモジュールの管理
- システム固有の設定

## インストール済みモジュールの管理

The `config.php` ファイルには、インストールされたモジュールのリストが含まれています。 Adobe Commerceは、モジュールの管理（インストール、アンインストール、有効化、無効化、アップグレード）を行うコマンドラインユーティリティと Web ベースのユーティリティの両方を提供します。

例：

- コンポーネントをアンインストール： [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- コンポーネントのステータスの確認： [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
- コンポーネントを有効または無効にする： [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md), [`bin/magento module:enable`](../../installation/tutorials/manage-modules.md).

> _config.php_

```php
return array (
  'modules' =>
  array (
    'Magento_Core' => 1,
    'Magento_Store' => 1,
    'Magento_Theme' => 1,
    'Magento_Authorization' => 1,
    'Magento_Directory' => 1,
    'Magento_Backend' => 1,
    'Magento_Backup' => 1,
    'Magento_Eav' => 1,
    'Magento_Customer' => 1,
...
  ),
);
```

値 `1` または `0` モジュールが有効か無効かを示します。

無効なモジュールは、コマースアプリケーションでは認識されません。つまり、設定のマージ、依存関係の挿入、イベント、プラグインなどには関与しません。 無効になったモジュールはストアフロントや管理者を変更せず、ルーティングにも影響しません。

無効モジュールとコードベース内の無効モジュールの唯一の実用的な違いは、無効モジュールがオートローダによって見つかり、そのクラスと定数が他のコードで再利用できる点です。
