---
title: config.php リファレンス
description: Adobe Commerce設定のconfig.php ファイルの値とセクションについて説明します。 モジュール、スコープ、システム設定、デプロイメントのベストプラクティスについて説明します。
exl-id: 9b355d6d-ea66-480b-ad96-0ea9e7e61844
source-git-commit: f9a135fc63574ccbecd3f564a87fc5c4ac03f009
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 1%

---

# config.php リファレンス

`config.php` ファイルには、次のセクションが含まれています。

| 名前 | 説明 |
| --------- | -------------------|
| `i18n` | すべてのインライン翻訳データ。 このセクションからの読み取りはサポートされていません。 |
| `modules` | 有効なモジュールと無効なモジュールのリスト。 |
| `scopes` | 関連情報を含むストア、ストアグループ、およびweb サイトのリスト。 |
| `system` | 静的コンテンツのデプロイメントに必要なシステム設定。 |
| `themes` | インストールされたテーマの設定。 |

## モジュール

モジュールとその状態の配列が含まれます。 モジュールが有効な場合、値は1です。 それ以外の場合、値は0です。

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

[&#x200B; モジュール &#x200B;](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html)の詳細をご覧ください。

## 範囲

スコープ設定値の配列が含まれます。 次のサブノードがあります。

| 名前 | 説明 |
| ---------- | -----------------------------------|
| `websites` | web サイト設定 |
| `groups` | ストア設定 |
| `stores` | ストアビュー設定 |

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

[Commerce スコープ &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings)の詳細をご覧ください。

## システム

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

[&#x200B; システム固有の設定](config-reference-sens.md)について詳しく説明します。

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

[&#x200B; テーマ &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/themes/create-storefront)の詳細

