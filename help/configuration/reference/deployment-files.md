---
title: デプロイメント用の設定ファイル
description: Commerce アプリケーションをインストールするための設定ファイルの動作を理解します。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---


# デプロイメント用の設定ファイル

Adobe Commerceには、コンポーネントを簡単にカスタマイズし、デフォルト機能を拡張するための設定タイプを作成できる設定ファイルが用意されています。 デプロイメント設定のプロセスは、インストール用の共有設定とシステム固有の設定で構成されます。 コマースのデプロイメント設定は、 [`app/etc/config.php`](../reference/config-reference-configphp.md) および [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` が _共有_ 設定ファイル。
このファイルには、インストールされたモジュール、テーマ、言語パッケージの一覧が含まれています。および共有設定

   このファイルをチェックインしてソース管理を行い、開発、ステージング、実稼動の各システムで使用します。

   2.2 リリース以降、 `app/etc/config.php` ファイルが `.gitignore` ファイル。
これは容易にするために行われた [パイプラインのデプロイメント](../deployment/technical-details.md).

- `app/etc/env.php` には、インストール環境に固有の設定が含まれます。

一緒に `config.php` および `env.php` コマースと呼ばれます。 _デプロイメント設定_ ファイルはインストール中に作成され、Commerce アプリケーションを起動するために必要なためです。

>[!INFO]
>
>この [!DNL Commerce 2] デプロイメント設定の置き換え `local.xml` in [!DNL Magento 1.x].

他と異なる [モジュール設定ファイル](../reference/module-files.md)の場合、コマースデプロイメント設定は初期化中にメモリに読み込まれ、他のファイルと結合されず、拡張できません。 (`config.php` および `env.php` ただし、相互に統合されている場合は除きます )。

## デプロイメント設定の詳細

`config.php` および `env.php` は、 [多次元連想配列](https://www.w3schools.com:443/php/php_arrays.asp)：基本的に、設定パラメーターと値の階層構造です。

この配列の最上位レベルは次のとおりです。 _設定セグメント_. セグメントには、任意のキーで区別される任意のコンテンツ（スカラー値またはネストされた配列）があります。キーと値のペアの両方は、コマースフレームワークによって定義されます。

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) は、これらのセクションへのアクセスを提供するだけですが、拡張はできません。

次の階層レベルでは、各セグメントの項目は [モジュール](https://glossary.magento.com/module) 無効なモジュールを除くすべてのモジュールの設定ファイルをマージして取得するシーケンス定義。

次の節では、デプロイメント設定の構造と内容について説明します。

- インストール済みモジュールの管理
- システム固有の設定

## インストール済みモジュールの管理

この `config.php` ファイルには、インストールされたモジュールのリストが含まれています。 Adobe Commerceは、モジュールの管理（インストール、アンインストール、有効化、無効化、アップグレード）を行うコマンドラインユーティリティと Web ベースのユーティリティの両方を提供します。

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

無効なモジュールは、Commerce アプリケーションで認識されません。つまり、マージ設定、依存関係インジェクション、イベント、プラグインなどには参加しません。 無効なモジュールでは [店頭](https://glossary.magento.com/storefront) または [管理者](https://glossary.magento.com/admin) ルーティングに影響を及ぼさない。

無効モジュールとコードベース内の無効モジュールの唯一の実用的な違いは、無効モジュールがオートローダによって見つかり、そのクラスと定数が他のコードで再利用できる点です。
