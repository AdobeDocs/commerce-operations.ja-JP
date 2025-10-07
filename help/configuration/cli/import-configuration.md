---
title: 設定ファイルからのデータの読み込み
description: 設定ファイルからAdobe Commerce設定を読み込む方法を説明します。 パイプラインのデプロイメントおよびデータベースのインポートプロセスについて説明します。
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# 設定を読み込み

{{file-system-owner}}

Commerce 2.2 [ パイプラインデプロイメントモデル ](../deployment/technical-details.md) を使用して実稼動システムを設定する場合、_および_ からデータベースに設定を `config.php` インポート `env.php` する必要があります。
これらの設定には、設定パスと値、web サイト、ストア、ストアビュー、テーマが含まれます。

Web サイト、ストア、ストアビュー、テーマを読み込んだ後、製品属性を作成して、実稼動システムの web サイト、ストア、ストアビューに適用できます。

>[!INFO]
>
>`bin/magento app:config:import` コマンドは、環境変数に保存された設定を処理しません。

## 読み込みコマンド

実稼動システムで、次のコマンドを実行して、設定ファイル（`config.php` および `env.php`）からデータベースにデータを読み込みます。

```bash
bin/magento app:config:import [-n, --no-interaction]
```

オプションの `[-n, --no-interaction]` フラグを使用して、インタラクションを行わずにデータをインポートします。

オプションフラグを指定せずに `bin/magento app:config:import` と入力した場合は、変更を確定する必要があります。

例えば、設定ファイルに 1 つの新しい web サイトと 1 つの新しいストアが含まれている場合、次のメッセージが表示されます。

```
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

読み込みを続行するには、`yes` と入力します。

読み込むデータが配置設定ファイルに含まれている場合は、次のようなメッセージが表示されます。

```
Start import:
Some information about importing
```

読み込むデータが配置設定ファイルに含まれていない場合は、次のようなメッセージが表示されます。

```
Start import:
Nothing to import
```

## 読み込む内容

以下の節では、読み込むデータについて詳しく説明します。

### システム設定

Commerceでは、データベースに読み込む代わりに、`system` ファイルまたは `config.php` ファイル内の `env.php` 配列の値を直接使用します。これらの値には前処理および後処理のアクションが必要なためです。

例えば、設定パス `web/secure/base_url` の値は、バックエンドモデルで検証する必要があります。

#### バックエンドモデル

バックエンドモデルは、システム設定の変更を処理するメカニズムです。
`<module_name>/adminhtml/system.xml` でバックエンドモジュールを定義します。

すべてのバックエンドモデルは、[`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) クラスを拡張する必要があります。

バックエンドモデルを読み込む場合、設定値は保存されません。

### Web サイト、ストア、ストアグループの設定

次のタイプの設定を読み込みます。
（これらの設定は、`scopes` の `config.php` 配列の下にあります）。

- `websites`:web サイト関連の設定
- `groups`：関連する設定を格納します
- `stores`：表示に関連する設定の保存

前述の設定は、次のモードで読み込むことができます。

- `create`: `config.php` には、実稼動環境にない新しいエンティティ（`websites`、`groups`、`stores`）が含まれています
- `update`: `config.php` に、実稼動環境とは異なるエンティティ（`websites`、`groups`、`stores`）が含まれています
- `delete`: `config.php` には、実稼動環境に存在するエンティティ __、`websites`、`groups`）が含まれていま `stores` ん

>[!INFO]
>
>ストアに関連付けられたルートカテゴリは読み込みません。 Commerce Admin を使用して、ルートカテゴリをストアに関連付ける必要があります。

### テーマの設定

テーマ設定には、Commerce システムに登録されているすべてのテーマが含まれます。データは、`theme` データベーステーブルから直接取得されます。 （テーマの設定は、`themes` の `config.php` 配列にあります）。

#### テーマデータの構造

配列のキーは、完全なテーマパス `area` + `theme path` です。

例：`frontend/Magento/luma`。
`frontend` は領域、`Magento/luma` はテーマのパスです。

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
>- _テーマの登録_. テーマデータが `config.php` で定義されていても、テーマのソースコードがファイルシステムに存在しない場合、テーマは無視されます（つまり、登録されません）。
>- _テーマの削除_. テーマが `config.php` に存在せず、ソースコードがファイルシステムに存在する場合、テーマは削除されません。
