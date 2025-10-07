---
title: デプロイメントの設定ファイル
description: 設定ファイルがAdobe Commerce アプリケーションのデプロイメントでどのように機能するかを説明します。 共有およびシステム固有の構成管理のベストプラクティスについて説明します。
feature: Configuration, Deploy
exl-id: 772a6814-6b18-4f8f-b31e-72faf790ff37
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# デプロイメントの設定ファイル

Adobe Commerceが提供する設定ファイルを使用すると、コンポーネントを簡単にカスタマイズし、設定タイプを作成してデフォルト機能を拡張できます。 デプロイメント設定のプロセスは、インストール用の共有およびシステム固有の設定で構成されます。 Commerceのデプロイメント設定は、[`app/etc/config.php`](../reference/config-reference-configphp.md) と [`app/etc/env.php`](../reference/config-reference-envphp.md) に分かれています。

- `app/etc/config.php` は _共有_ 設定ファイルです。
このファイルには、インストールされているモジュール、テーマ、言語パッケージ、および共有設定の一覧が含まれています。

  このファイルをソース管理にチェックインし、開発、ステージング、実稼動の各システムで使用します。

- `app/etc/env.php` には、インストール環境に固有の設定が含まれます。

`config.php` と `env.php` のファイルは、インストール時に作成され、Commerce アプリケーションの起動に必要なので、これらのファイルを合わせてCommerce _deployment configuration_ と呼びます。

>[!INFO]
>
>[!DNL Commerce 2] デプロイメント設定は、`local.xml` の [!DNL Magento 1.x] に代わるものです。

他の [ モジュール設定ファイル ](../reference/module-files.md) とは異なり、Commerce デプロイメント設定は、初期化時にメモリに読み込まれ、他のファイルと結合されず、拡張できません。 （ただし、`config.php` と `env.php` はマージされます）。

## デプロイメント設定の詳細

`config.php` と `env.php` は [ 多次元連想配列 ](https://www.w3schools.com:443/php/php_arrays.asp) を返す PHP ファイルで、基本的には設定パラメータと値の階層的な配列です。

この配列の最上位には、_設定セグメント_ があります。 セグメントには、任意のキーで区別される任意のコンテンツ（スカラー値またはネストされた配列）があります。キーと値のペアの両方がCommerce フレームワークによって定義されます。

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) は、これらのセクションへのアクセスを提供するだけで、セクションの拡張はできません。

次の階層レベルでは、無効なモジュールを除くすべてのモジュールの設定ファイルを結合して得られるモジュールシーケンス定義に従って、各セグメントの項目が並べられます。

以降の節では、デプロイメント設定の構造と内容について説明します。

- インストール済みモジュールの管理
- システム固有の設定

## インストール済みモジュールの管理

`config.php` ファイルには、インストール済みモジュールのリストが含まれています。 Adobe Commerceには、モジュールを管理（インストール、アンインストール、有効化、無効化、アップグレード）するためのコマンドラインユーティリティと web ベースのユーティリティの両方が用意されています。

例：

- コンポーネントのアンインストール：[`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- コンポーネントのステータスの確認：[`bin/magento module:status`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#modulestatus)
- コンポーネント（[`bin/magento module:disable`](../../installation/tutorials/manage-modules.md)、[`bin/magento module:enable`](../../installation/tutorials/manage-modules.md)）を有効または無効にします。

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

値 `1` または `0` は、モジュールが有効か無効かを示します。

無効なモジュールはCommerce アプリケーションで認識されません。つまり、設定の結合、依存関係のインジェクション、イベント、プラグインなどには含まれません。 無効にしたモジュールはストアフロントや管理者を変更せず、ルーティングにも影響を与えません。

コードベースで無効なモジュールと存在しないモジュールの実際的な違いは、無効なモジュールがオートローダーによって見つかり、そのクラスと定数が他のコードで再利用できる点です。
