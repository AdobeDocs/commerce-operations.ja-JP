---
title: config.php リファレンス
description: Adobe Commerce設定の config.php ファイルの値と節について説明します。 モジュール、範囲、システム設定、デプロイメントのベストプラクティスについて説明します。
exl-id: 9b355d6d-ea66-480b-ad96-0ea9e7e61844
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 1%

---

# config.php リファレンス

`config.php` ファイルには、次のセクションが含まれます。

| 名前 | 説明 |
| --------- | -------------------|
| `i18n` | すべてのインライン翻訳データ。 このセクションからの読み取りはサポートされていません。 |
| `modules` | 有効なモジュールと無効なモジュールのリスト。 |
| `scopes` | ストア、ストアグループ、web サイトのリストと関連情報。 |
| `system` | 静的なコンテンツのデプロイメントに必要なシステム設定。 |
| `themes` | インストールされたテーマの設定。 |

## モジュール

モジュールとその状態の配列が含まれます。 モジュールが有効の場合、値は 1 です。 それ以外の場合、値は 0 です。

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

詳細情報 [&#x200B; モジュール &#x200B;](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html?lang=ja)。

## スコープ

スコープ設定値の配列が含まれます。 このノードには次のサブノードがあります。

| 名前 | 説明 |
| ---------- | -----------------------------------|
| `websites` | Web サイト設定 |
| `groups` | 設定を保存 |
| `stores` | ビューの保存の設定 |

```conf
'scopes' => [
  'websites' => [
    'admin' => [
      'website_id' => '0',
      'code' => 'admin',
      'name' => 'Admin',
      'sort_order' => '0',
      'default_group_id' => '0',
      'is_default' => '0'
    ]
  ],
  'groups' => [
    0 => [
      'group_id' => '0',
      'website_id' => '0',
      'code' => 'default',
      'name' => 'Default',
      'root_category_id' => '0',
      'default_store_id' => '0'
    ]
  ],
  'stores' => [
    'admin' => [
      'store_id' => '0',
      'code' => 'admin',
      'website_id' => '0',
      'group_id' => '0',
      'name' => 'Admin',
      'sort_order' => '0',
      'is_active' => '1'
    ]
  ]
]
```

[Commerce範囲 &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=ja#scope-settings) の詳細情報。

## system

システムフィールド設定値の配列が含まれます。

```conf
'system'=> [
    'default' =>[
        'checkout' => [
            'cart' => [
                'delete_quote_after' => 31
            ]
        ]
    ]
]
```

[&#x200B; システム固有の設定 &#x200B;](config-reference-sens.md) の詳細情報。

## テーマ

テーマ設定の値の配列が含まれます。

```conf
'themes' => [
  'frontend/Magento/luma' => [
    'parent_id' => 'Magento/blank',
    'theme_path' => 'Magento/luma',
    'theme_title' => 'Magento Luma',
    'is_featured' => '0',
    'area' => 'frontend',
    'type' => '0',
    'code' => 'Magento/luma'
  ]
]
```

[&#x200B; テーマ &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/themes/create-storefront/) の詳細情報。

