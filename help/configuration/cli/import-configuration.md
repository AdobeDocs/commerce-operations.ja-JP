---
title: 設定ファイルからデータを読み込む
description: Adobe Commerceの設定を設定ファイルから読み込みます。
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# 設定を読み込み

{{file-system-owner}}

コマース 2.2 を使用して実稼動システムを設定する場合 [パイプラインデプロイメントモデル](../deployment/technical-details.md)を選択し、 _インポート_ 次の設定から `config.php` および `env.php` をデータベースに追加します。
これらの設定には、設定パスと値、Web サイト、ストア、ストア表示、テーマが含まれます。

Web サイト、ストア、ストアの表示、テーマを読み込んだ後、製品属性を作成し、実稼動システム上の Web サイト、ストア、ストアの表示に適用できます。

>[!INFO]
>
>The `bin/magento app:config:import` コマンドは、環境変数に格納された設定を処理しません。

## インポートコマンド

実稼動システムで、次のコマンドを実行して設定ファイル (`config.php` および `env.php`) をデータベースに追加します。

```bash
bin/magento app:config:import [-n, --no-interaction]
```

オプションの `[-n, --no-interaction]` フラグを設定して、何の操作もおこなわずにデータを読み込みます。

次を入力すると、 `bin/magento app:config:import` オプションのフラグがない場合は、変更を確定する必要があります。

例えば、設定ファイルに新しい Web サイトと新しいストアが 1 つ含まれている場合、次のメッセージが表示されます。

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

インポートを続行するには、 `yes`.

デプロイメント設定ファイルにインポートするデータが含まれている場合は、次のようなメッセージが表示されます。

```terminal
Start import:
Some information about importing
```

デプロイメント設定ファイルにインポートするデータが含まれていない場合は、次のようなメッセージが表示されます。

```terminal
Start import:
Nothing to import
```

## インポートする内容

次の節では、インポートするデータの詳細について説明します。

### システム設定

Commerce は、 `system` 配列を `config.php` または `env.php` ファイルを読み込む代わりに、ファイルを読み込むことをお勧めします。これは、いくつかの前処理アクションと後処理アクションが必要になるからです。

例えば、設定パスの値 `web/secure/base_url` は、バックエンドモデルで検証する必要があります。

#### バックエンドモデル

バックエンドモデルは、システム設定の変更を処理するメカニズムです。
バックエンドモジュールは、 `<module_name>/adminhtml/system.xml`.

すべてのバックエンドモデルは、 [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) クラス。

バックエンドモデルを読み込む際には、設定値は保存しません。

### Web サイト、ストア、およびストアグループの設定

次のタイプの設定を読み込みます。
( これらの設定は、 `scopes` 配列 `config.php`.)

- `websites`: Web サイト関連の設定
- `groups`：関連する設定を格納します
- `stores`：ストアビュー関連の設定

前述の設定は、次のモードで読み込むことができます。

- `create`: `config.php` 新しいエンティティ (`websites`, `groups`, `stores`) が実稼動環境に存在しない
- `update`: `config.php` エンティティ (`websites`, `groups`, `stores`) と呼ばれ、実稼動環境とは異なる
- `delete`: `config.php` は、 _not_ エンティティ (`websites`, `groups`, `stores`) が実稼動環境に存在する

>[!INFO]
>
>ストアに関連付けられたルートカテゴリはインポートされません。 コマース管理を使用して、ルートカテゴリをストアに関連付ける必要があります。

### テーマの設定

テーマの設定には、コマースシステムに登録されているすべてのテーマが含まれます。データは、 `theme` データベーステーブル。 ( テーマの設定は `themes` 配列 `config.php`.)

#### テーマデータの構造

配列のキーは完全なテーマパスです。 `area` + `theme path`

例： `frontend/Magento/luma`.
`frontend` 領域および `Magento/luma` はテーマのパスです。

配列の値は、テーマに関するデータ（コード、タイトル、パス、親 ID）です

完全な例：

```php?start_inline=1
'frontend/Magento/luma' =>
   array (
      'parent_id' => 'Magento/blank',
      'theme_path' => 'Magento/luma',
      'theme_title' => 'Magento Luma',
      'is_featured' => '0',
      'area' => 'frontend',
      'type' => '0',
      'code' => 'Magento/luma',
),
```

>[!INFO]
>
>- _テーマの登録_. テーマデータが `config.php` しかし、テーマのソースコードはファイルシステムに存在しないので、そのテーマは無視されます（つまり、登録されていません）。
>- _テーマの削除_. テーマがに存在しない場合 `config.php` ただし、ソースコードはファイルシステム上に存在し、テーマは削除されません。
