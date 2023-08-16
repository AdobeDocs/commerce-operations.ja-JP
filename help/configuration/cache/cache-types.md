---
title: キャッシュタイプ
description: キャッシュフロントエンドをキャッシュタイプに関連付けます。
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# キャッシュタイプ

次の手順では、キャッシュフロントエンドとキャッシュタイプの関連付けについて説明します。

## 手順 1：キャッシュフロントエンドの定義

コマースアプリケーションには `default` 任意の [キャッシュタイプ](../cli/manage-cache.md#clean-and-flush-cache-types). この節では、別の名前でキャッシュフロントエンドを任意で定義する方法を説明します。フロントエンドをカスタマイズする場合に適しています。

>[!INFO]
>
>次の手順で `default` キャッシュタイプを変更する必要はありません。 `env.php` 全く、コマースのグローバルを変更します。 `di.xml`. 詳しくは、 [低レベルキャッシュオプション](cache-options.md).

カスタムキャッシュのフロントエンドを指定する必要があります `app/etc/env.php` またはコマースのグローバル `app/etc/di.xml`.

次の例は、 `env.php` ファイル（上書き） `di.xml` ファイル：

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

ここで、 `<unique frontend id>` は、フロントエンドを識別するための一意の名前で、 `<cache options>` は、キャッシュの各タイプ（データベース、Redis など）に固有のトピックで説明するオプションです。

## 手順 2：キャッシュの設定

フロントエンドおよびバックエンドのキャッシュ設定オプションは、 `env.php` または `di.xml`. このタスクはオプションです。

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

場所

- `<frontend_type>` は、低レベルのフロントエンドキャッシュタイプです。 互換性のあるクラスの名前を指定します `Zend\Cache\Core`.
省略した場合 `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) が使用されます。

- `<frontend_option>`, `<frontend_option_value>` は、Commerce フレームワークが作成時にフロントエンドキャッシュに連想配列として渡すオプションの名前と値です。
- `<backend_type>` は、低レベルのバックエンドキャッシュタイプです。 互換性のあるクラスの名前を指定します `Zend_Cache_Backend` そしてこの事件は `Zend_Cache_Backend_Interface`.
- `<backend_option>` および `<backend_option_value>` は、作成時にバックエンドキャッシュに連想配列として渡される Commerce フレームワークのオプションの名前と値です。

詳しくは、 [Laminas のドキュメント](https://docs.laminas.dev/) を参照してください。
