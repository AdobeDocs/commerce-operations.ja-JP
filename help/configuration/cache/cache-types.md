---
title: キャッシュフロントエンドとタイプの設定
description: キャッシュフロントエンドを定義し、Adobe Commerceのキャッシュタイプに関連付ける方法について説明します。 env.phpおよびdi.xmlの設定構文を確認します。
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2:
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 7171e5abfad69ad0f2d3f4c4b5eb57c13d07feb4
workflow-type: tm+mt
source-wordcount: 507
ht-degree: 1%

---

# キャッシュフロントエンドとタイプの設定

キャッシュフロントエンドとは、Commerceのキャッシュタイプとキャッシュストレージバックエンドの間のインターフェイスのことです。 複数のフロントエンドを定義し、それぞれ異なるバックエンド設定を使用して、特定の[&#x200B; キャッシュタイプ &#x200B;](../cli/manage-cache.md#clean-and-flush-cache-types)を各フロントエンドに割り当てることができます。

この関係を使用して、各キャッシュタイプがデータを保存する場所を決定します。

`cache type` -> `cache frontend` -> `cache backend`

これは、キャッシュされたデータの種類ごとに異なるキャッシュバックエンドまたは設定を使用する場合に便利です。 例えば、専用のValkey データベースを使用する`page_cache` フロントエンドに`full_page` キャッシュ タイプを割り当てる場合や、他のキャッシュ タイプが`default` フロントエンドを使用する場合があります。

{{cloud-cache-config}}

## デフォルトのフロントエンドを使用する

Commerceには、すべてのキャッシュタイプに対応する`default` キャッシュフロントエンドが用意されています。 [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) フロントエンドキャッシュを実装することで、[Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html)を拡張します。

ほとんどの場合、フロントエンドをカスタマイズする必要はありません。 バックエンドを設定するだけです。 [&#x200B; キャッシュバックエンドオプション &#x200B;](cache-options.md)を参照してください。

## カスタムキャッシュフロントエンドの定義

次の手順では、キャッシュフロントエンドをキャッシュタイプに関連付ける方法を説明します。

### 手順1：キャッシュフロントエンドの定義とキャッシュタイプの割り当て

カスタムキャッシュフロントエンドを定義するには、設定を`app/etc/env.php`に追加します（設定は`di.xml`を上書きします）。

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<unique frontend id>' => [
             <cache options>
        ],
    ],
    'type' => [
         <cache type 1> => [
             'frontend' => '<unique frontend id>'
        ],
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

どこで：

- `<unique frontend id>` — フロントエンドを識別するための一意の名前（例：`default`、`page_cache`、`stale_cache_enabled`）
- `<cache options>` – このフロントエンドのバックエンドタイプとオプション（[&#x200B; キャッシュオプション &#x200B;](cache-options.md)を参照）
- `<cache type>` – このフロントエンドに割り当てるCommerce キャッシュの種類（例：`config`、`layout`、`block_html`、`full_page`）

>[!TIP]
>
>Adobe Commerce 2.4.9以降では、Symfony Cache実装で`valkey`や`file`などの簡略化されたバックエンドタイプ名を使用します。 バックエンドの例とバージョン固有のガイダンスについては、[&#x200B; キャッシュバックエンドオプション &#x200B;](cache-options.md)を参照してください。


### 手順2：フロントエンドとバックエンドオプションの設定

フロントエンドとバックエンドのキャッシュ設定オプションは、`env.php`または`di.xml`で指定できます。 このタスクはオプションです。 オプションを指定しない場合、Commerceではデフォルトのフロントエンドとバックエンドの設定が使用されます。

`env.php`例：

```php?start_inline=1
'frontend' => <frontend_type>,
'frontend_options' => [
    <frontend_option> => <frontend_option_value>,
    ...
],
'backend' => <backend_type>,
'backend_options' => [
    <backend_option> => <backend_option_value>,
    ...
],
```

どこで：

- `<frontend_type>` – 低レベルのフロントエンド キャッシュ タイプ。 `Zend\Cache\Core`と互換性のあるクラス名を指定してください。省略した場合は、[Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)が使用されます。

- `<frontend_option>`、`<frontend_option_value>` — Commerce フレームワークが作成時に自動化配列としてフロントエンドキャッシュに渡すオプションの名前と値。

- `<backend_type>` – 下位レベルのバックエンド キャッシュの種類。 次を指定できます。
   - **最新のSymfony キャッシュ （2.4.9以降、推奨）**: `redis`、`valkey`、`file`などの簡略化された名前
   - **レガシー（Zend ベース）**: `Zend_Cache_Backend_Interface`を実装する`Zend_Cache_Backend`と互換性のあるフルクラス名

- `<backend_option>`、`<backend_option_value>` — Commerce フレームワークが作成時にバックエンドキャッシュに連想配列として渡すオプションの名前と値。

>[!NOTE]
>
>**従来の実装と最新の実装の比較：**
>
>- **レガシー（Zend ベース）**: `'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis'`
>- **最新（Symfony Cache）**: Commerce バージョン 2.4.9以降およびValkeyがサポートされているキャッシュバックエンドである2.4.5 ～ 2.4.8のリリースラインの現在のパッチリリースの`'backend' => 'valkey'`。
>
>最新のSymfony Cache実装は、PSR-6 コンプライアンス、Igbinary シリアル化、gzip圧縮、Lua スクリプト、および永続的な接続を通じて、より優れたパフォーマンスを提供します。

Zend ベースのオプションについては、[Laminas ドキュメント &#x200B;](https://docs.laminas.dev/)を参照してください。 Symfony Cacheの設定については、このドキュメントの[Redis](redis-pg-cache.md)および[Valkey](valkey-pg-cache.md)の記事を参照してください。
