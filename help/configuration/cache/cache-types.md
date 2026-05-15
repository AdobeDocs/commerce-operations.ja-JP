---
title: キャッシュフロントエンドの設定
description: キャッシュフロントエンドを定義し、Adobe Commerceのキャッシュタイプに関連付ける方法について説明します。 env.phpおよびdi.xmlの設定構文を確認します。
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: de613310ad701dd594a6ee8fcd973aa2c3769870
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# キャッシュフロントエンドの設定

キャッシュフロントエンドとは、Commerceとキャッシュストレージバックエンド間のインターフェイスのことです。 複数のフロントエンドを定義し、それぞれ異なるバックエンド設定を使用して、特定の[&#x200B; キャッシュタイプ &#x200B;](../cli/manage-cache.md#clean-and-flush-cache-types)を各フロントエンドに割り当てることができます。

これは、キャッシュされたデータの種類ごとに異なるキャッシュバックエンドまたは設定を使用する場合に便利です。 例えば、`default`のキャッシュに別のデータベースを使用する場合、専用のRedis データベースで`full_page`のキャッシュを行う必要があります。

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
>**最新のSymfony Cache実装（2.4.9以降）:** Commerce 2.4.9以降では、最新のSymfony Cache実装で`redis`、`valkey`、`file`などの簡素化されたバックエンドタイプを使用できます。 詳しくは、[&#x200B; デフォルトのキャッシュにRedisを使用](redis-pg-cache.md)および[&#x200B; デフォルトのキャッシュにValkeyを使用](valkey-pg-cache.md)を参照してください。

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

- `<frontend_type>` – 低レベルのフロントエンド キャッシュ タイプ。 `Zend\Cache\Core`と互換性のあるクラス名を指定してください。
省略した場合は、[Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php)が使用されます。

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
>- **最新（Symfony Cache）**: `'backend' => 'redis'` （Commerce 2.4.9以降をお勧めします）
>
>最新のSymfony Cache実装は、PSR-6 コンプライアンス、Igbinary シリアル化、gzip圧縮、Lua スクリプト、および永続的な接続を通じて、より優れたパフォーマンスを提供します。

Zend ベースのオプションについては、[Laminasのドキュメント &#x200B;](https://docs.laminas.dev/)を参照してください。また、[Redis](redis-pg-cache.md)および[Valkey](valkey-pg-cache.md)の最新のSymfony キャッシュガイドも参照してください。
