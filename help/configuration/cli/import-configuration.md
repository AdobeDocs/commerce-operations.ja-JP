---
title: 設定ファイルからのデータの読み込み
description: 設定ファイルからAdobe Commerce設定を読み込みます。
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# 設定を読み込み

{{file-system-owner}}

Commerce 2.2 を使用して実稼動システムをセットアップする場合 [パイプラインデプロイメントモデル](../deployment/technical-details.md)は、次の操作が必要です _import_ からの設定 `config.php` および `env.php` をデータベースに追加します。
これらの設定には、設定パスと値、web サイト、ストア、ストアビュー、テーマが含まれます。

Web サイト、ストア、ストアビュー、テーマを読み込んだ後、製品属性を作成して、実稼動システムの web サイト、ストア、ストアビューに適用できます。

>[!INFO]
>
>この `bin/magento app:config:import` コマンドは、環境変数に保存された設定を処理しません。

## 読み込みコマンド

実稼動システムで、次のコマンドを実行して設定ファイルからデータを読み込みます（`config.php` および `env.php`）を選択します。

```bash
bin/magento app:config:import [-n, --no-interaction]
```

オプションのを使用 `[-n, --no-interaction]` インタラクションなしでデータをインポートするためのフラグ。

次のように入力します `bin/magento app:config:import` オプションフラグを使用しない場合は、変更を確認する必要があります。

例えば、設定ファイルに 1 つの新しい web サイトと 1 つの新しいストアが含まれている場合、次のメッセージが表示されます。

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

読み込みを続行するには、を入力します。 `yes`.

読み込むデータが配置設定ファイルに含まれている場合は、次のようなメッセージが表示されます。

```terminal
Start import:
Some information about importing
```

読み込むデータが配置設定ファイルに含まれていない場合は、次のようなメッセージが表示されます。

```terminal
Start import:
Nothing to import
```

## 読み込む内容

以下の節では、読み込むデータについて詳しく説明します。

### システム設定

Commerceがの値を直接使用する `system` 配列 `config.php` または `env.php` ファイルをデータベースにインポートする代わりに、前処理および後処理のアクションを実行する必要があります。

例えば、設定パスの値 `web/secure/base_url` バックエンドモデルを使用して検証する必要があります。

#### バックエンドモデル

バックエンドモデルは、システム設定の変更を処理するメカニズムです。
バックエンドモジュールは、次の場所で定義します。 `<module_name>/adminhtml/system.xml`.

すべてのバックエンドモデルで、 [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) クラス。

バックエンドモデルを読み込む場合、設定値は保存されません。

### Web サイト、ストア、ストアグループの設定

次のタイプの設定を読み込みます。
（これらの設定は、 `scopes` 配列複写 `config.php`.）

- `websites`:web サイト関連の設定
- `groups`：関連する設定を格納します
- `stores`：ビュー関連の設定の保存

前述の設定は、次のモードで読み込むことができます。

- `create`: `config.php` 新しいエンティティを含む（`websites`, `groups`, `stores`）が実稼動環境に存在しない
- `update`: `config.php` 含まれるエンティティ（`websites`, `groups`, `stores`）が実稼動環境とは異なります
- `delete`: `config.php` 実行 _ではない_ エンティティを含む（`websites`, `groups`, `stores`）が存在する

>[!INFO]
>
>ストアに関連付けられたルートカテゴリは読み込みません。 Commerce Admin を使用して、ルートカテゴリをストアに関連付ける必要があります。

### テーマの設定

テーマ設定には、Commerce システムに登録されているすべてのテーマが含まれます。データはから直接取得されます。 `theme` データベーステーブル。 （テーマの設定はにあります `themes` 配列複写 `config.php`.）

#### テーマデータの構造

配列のキーは、完全なテーマパスです。 `area` + `theme path`

例： `frontend/Magento/luma`.
`frontend` 面積で `Magento/luma` はテーマのパスです。

配列の値は、テーマに関するデータ（コード、タイトル、パス、親 ID）です。

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
>- _テーマの登録_. テーマデータがで定義されている場合 `config.php` ただし、テーマのソースコードがファイルシステムに存在しない場合、テーマは無視されます（つまり、登録されません）。
>- _テーマの削除_. にテーマがない場合 `config.php` ただし、ソースコードはファイルシステムに存在するので、テーマは削除されません。
