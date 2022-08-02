---
title: config.php リファレンス
description: config.php ファイルの値のリストを参照してください。
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# config.php リファレンス

この `config.php` ファイルには次のセクションが含まれます。

| 名前 | 説明 |
| --------- | -------------------|
| `i18n` | すべてのインライン翻訳データ。 このセクションからの読み取りはサポートされていません。 |
| `modules` | 有効なモジュールと無効なモジュールのリスト。 |
| `scopes` | ストア、ストアグループ、および関連情報を含む Web サイトのリスト。 |
| `system` | 静的コンテンツのデプロイメントに必要なシステム設定です。 |
| `themes` | インストールされたテーマの設定。 |

## モジュール

モジュールとその状態の配列が含まれます。 モジュールが有効な場合、値は 1 です。 それ以外の場合、値は 0 です。

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

詳細情報： [モジュール].

## スコープ

スコープ設定値の配列が含まれます。 このノードには次のサブノードが含まれます。

| 名前 | 説明 |
| ---------- | -----------------------------------|
| `websites` | Web サイトの設定 |
| `groups` | 設定を保存 |
| `stores` | ストア表示設定 |

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

詳細情報： [コマーススコープ][scopes].

## システム

システムフィールドの設定値の配列が含まれます。

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

詳細情報： [システム固有の設定](config-reference-sens.md).

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

詳細情報： [テーマ].

<!-- link definitions -->

[モジュール]: https://devdocs.magento.com/videos/fundamentals/create-a-new-module/
[scopes]: https://docs.magento.com/user-guide/configuration/scope.html
[テーマ]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/theme-create.html
