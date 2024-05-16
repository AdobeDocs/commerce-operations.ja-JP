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

Commerce アプリケーションには、 `default` すべてに使用できるキャッシュフロントエンド [キャッシュタイプ](../cli/manage-cache.md#clean-and-flush-cache-types). この節では、オプションで別の名前でキャッシュフロントエンドを定義する方法について説明します。この方法は、フロントエンドをカスタマイズしたい場合に適しています。

>[!INFO]
>
>を使用するには `default` キャッシュタイプ。変更する必要はありません `env.php` Commerceをグローバルに変更する `di.xml`. 参照： [低レベルのキャッシュオプション](cache-options.md).

次のどちらかの場合は、カスタム キャッシュ フロントエンドを指定する必要があります `app/etc/env.php` またはCommerce グローバル `app/etc/di.xml`.

次の例は、 `env.php` ファイル。この設定は `di.xml` ファイル：

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

ここで、 `<unique frontend id>` は、フロントエンドを識別するための一意の名前で、 `<cache options>` は、各タイプのキャッシュ（データベース、Redis など）に固有のトピックで説明されているオプションです。

## 手順 2：キャッシュの設定

フロントエンドおよびバックエンドのキャッシュ設定オプションは、で指定できます。 `env.php` または `di.xml`. このタスクはオプションです。

`env.php` 例：

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

- `<frontend_type>` は低レベルのフロントエンドキャッシュタイプです。 互換性のあるクラスの名前を指定します `Zend\Cache\Core`.
を省略した場合 `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) が使用されます。

- `<frontend_option>`, `<frontend_option_value>` は、Commerce フレームワークが作成時にフロントエンドキャッシュに連想配列として渡すオプションの名前と値です。
- `<backend_type>` は低レベルのバックエンドキャッシュタイプです。 互換性のあるクラスの名前を指定します `Zend_Cache_Backend` およびその実装内容 `Zend_Cache_Backend_Interface`.
- `<backend_option>` および `<backend_option_value>` は、Commerce フレームワークが作成時に連想配列としてバックエンドキャッシュに渡すオプションの名前と値です。

を参照してください。 [Laminas ドキュメント](https://docs.laminas.dev/) 最新の Zend の情報です。
