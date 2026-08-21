---
title: デプロイメント用の設定ファイル
description: Adobe Commerce アプリケーションのデプロイメントにおける設定ファイルの仕組みについて説明します。 共有およびシステム固有の設定管理のベストプラクティスについて説明します。
feature: Configuration, Deploy
exl-id: 772a6814-6b18-4f8f-b31e-72faf790ff37
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# デプロイメント用の設定ファイル

Adobe Commerceには、コンポーネントを簡単にカスタマイズし、デフォルトの機能を拡張するための設定タイプを作成できる設定ファイルが用意されています。 デプロイメント設定のプロセスは、インストール用の共有およびシステム固有の設定で構成されます。 Commerceのデプロイメント設定は[`app/etc/config.php`](../reference/config-reference-configphp.md)と[`app/etc/env.php`](../reference/config-reference-envphp.md)の間で分割されています。

- `app/etc/config.php`は&#x200B;_共有_設定ファイルです。
このファイルには、インストールされているモジュール、テーマ、言語パッケージのリスト、および共有設定が含まれています。

  このファイルをソースコントロールにチェックインし、開発、ステージング、実稼動システムで使用します。

- `app/etc/env.php`には、インストール環境に固有の設定が含まれています。

`config.php`と`env.php`は共に、Commerce _デプロイメント設定_&#x200B;と呼ばれます。これは、ファイルがインストール中に作成され、Commerce アプリケーションを起動するために必要だからです。

>[!INFO]
>
>[!DNL Commerce 2]のデプロイメント設定は、[!DNL Magento 1.x]の`local.xml`に置き換わります。

他の[ モジュール設定ファイル ](../reference/module-files.md)とは異なり、Commerce デプロイメント設定は、初期化中にメモリに読み込まれ、他のファイルと結合されず、拡張できません。 （`config.php`と`env.php`は互いに結合されます）。

## デプロイメント設定の詳細

`config.php`と`env.php`は、[多次元連想配列](https://www.w3schools.com:443/php/php_arrays.asp)を返すPHP ファイルです。これは、基本的に設定パラメーターと値の階層配列です。

この配列の最上位レベルには&#x200B;_設定セグメント_&#x200B;があります。 セグメントには、任意のキーで区別される任意のコンテンツ（スカラー値またはネストされた配列）があります。キーと値のペアの両方は、Commerce フレームワークで定義されます。

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php)は、これらのセクションへのアクセスを提供するだけですが、拡張することはできません。

次の階層レベルでは、各セグメント内の項目は、無効なモジュールを除くすべてのモジュールの設定ファイルを結合して得られるモジュール シーケンス定義に従って順序付けされます。

次の節では、デプロイメント設定の構造と内容について説明します。

- インストール済みモジュールの管理
- システムごとの設定

## インストール済みモジュールの管理

`config.php` ファイルには、インストールされているモジュールのリストが含まれています。 Adobe Commerceには、モジュール（インストール、アンインストール、有効化、無効化、アップグレード）を管理するためのコマンドラインユーティリティとweb ベースのユーティリティの両方が用意されています。

例：

- コンポーネントのアンインストール：[`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- コンポーネントの状態の確認：[`bin/magento module:status`](/help/tools/reference/commerce-on-premises.md#modulestatus)
- コンポーネントを有効または無効にします：[`bin/magento module:disable`](../../installation/tutorials/manage-modules.md)、[`bin/magento module:enable`](../../installation/tutorials/manage-modules.md)。

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

値`1`または`0`は、モジュールが有効か無効かを示します。

無効なモジュールは、Commerce アプリケーションでは認識されません。つまり、マージ設定、依存関係インジェクション、イベント、プラグインなどに関与しません。 無効になっているモジュールは、ストアフロントまたは管理者を変更せず、ルーティングには影響しません。

無効なモジュールとコードベースに存在しないモジュールの唯一の実用的な違いは、無効なモジュールがオートローダによって見つかり、そのクラスと定数が他のコードで再利用できることです。
