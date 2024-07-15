---
title: キャッシュタイプ
description: キャッシュフロントエンドをキャッシュタイプに関連付けます。
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# キャッシュタイプ

次の手順では、キャッシュフロントエンドとキャッシュタイプの関連付けを順を追って説明します。

## 手順 1：キャッシュフロントエンドの定義

Commerce アプリケーションには、任意の [ キャッシュタイプ ](../cli/manage-cache.md#clean-and-flush-cache-types) に使用できる `default` キャッシュフロントエンドがあります。 この節では、オプションで別の名前でキャッシュフロントエンドを定義する方法について説明します。この方法は、フロントエンドをカスタマイズしたい場合に適しています。

>[!INFO]
>
>`default` のキャッシュタイプを使用する場合、`env.php` を変更する必要はありません。Commerceのグローバル `di.xml` を変更する必要があります。 [ 低レベルキャッシュオプション ](cache-options.md) を参照してください。

`app/etc/env.php` またはCommerceのグローバル `app/etc/di.xml` のカスタム キャッシュ フロントエンドを指定する必要があります。

次の例は、`di.xml` ファイルを上書きする `env.php` ファイルで定義する方法を示しています。

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
    ],
    'type' => [
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

ここで、`<unique frontend id>` はフロントエンドを識別するための一意の名前で、`<cache options>` れは各タイプのキャッシュ（データベース、Redis など）に固有のトピックで説明されているオプションです。

## 手順 2：キャッシュの設定

`env.php` または `di.xml` で、フロントエンドおよびバックエンドのキャッシュ設定オプションを指定できます。 このタスクはオプションです。

`env.php`:

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

ここで、

- `<frontend_type>` は低レベルのフロントエンドキャッシュのタイプです。 `Zend\Cache\Core` と互換性のあるクラスの名前を指定します。
`<frontend_type>` を省略すると、[Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) が使用されます。

- `<frontend_option>`、Commerce フレームワーク `<frontend_option_value>` 作成時にフロントエンドキャッシュに連想配列として渡すオプションの名前と値です。
- `<backend_type>` は、低レベルのバックエンドキャッシュタイプです。 `Zend_Cache_Backend` と互換性があり、`Zend_Cache_Backend_Interface` を実装するクラスの名前を指定します。
- `<backend_option>` と `<backend_option_value>` は、Commerce フレームワークが作成時にバックエンドキャッシュに連想配列として渡すオプションの名前と値です。

最新の Zend 情報については、[Laminas のドキュメント ](https://docs.laminas.dev/) を参照してください。
