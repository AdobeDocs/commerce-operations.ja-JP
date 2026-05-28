---
title: 設定ファイルからのデータのインポート
description: Adobe Commerceの設定を設定ファイルから読み込む方法について説明します。 パイプラインのデプロイメントとデータベースのインポートプロセスを確認します。
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# 構成設定のインポート

{{file-system-owner}}

Commerce 2.2 [ パイプライン デプロイメントモデル ](../deployment/technical-details.md)を使用して実稼動システムを設定する場合、`config.php`および`env.php`から&#x200B;_import_設定をデータベースに取り込む必要があります。
これらの設定には、設定パスと値、web サイト、ストア、ストアビューおよびテーマが含まれます。

web サイト、ストア、ストアビュー、およびテーマを読み込んだ後、製品属性を作成し、実稼動システム上のweb サイト、ストア、ストアビューに適用できます。

>[!INFO]
>
>`bin/magento app:config:import` コマンドは、環境変数に保存されている構成を処理しません。

## 読み込みコマンド

実稼動システムで、次のコマンドを実行して、設定ファイル（`config.php`および`env.php`）からデータベースにデータをインポートします。

```shell
bin/magento app:config:import [-n, --no-interaction]
```

オプションの`[-n, --no-interaction]` フラグを使用して、操作なしでデータを読み込みます。

オプションのフラグなしで`bin/magento app:config:import`を入力した場合は、変更を確認する必要があります。

例えば、設定ファイルに1つの新しいweb サイトと1つの新しいストアが含まれている場合、次のメッセージが表示されます。

```text
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

インポートを続行するには、`yes`と入力します。

デプロイメント設定ファイルにインポートするデータが含まれている場合は、次のようなメッセージが表示されます。

```text
Start import:
Some information about importing
```

デプロイメント設定ファイルに読み込むデータが含まれていない場合は、次のようなメッセージが表示されます。

```text
Start import:
Nothing to import
```

## インポートするもの

次の節では、インポートするデータについて詳しく説明します。

### システム設定

Commerceでは、一部の前処理および後処理アクションが必要なため、データベースに読み込む代わりに、`config.php`または`env.php` ファイルの`system`配列内の値を直接使用します。

例えば、設定パス `web/secure/base_url`の値は、バックエンドモデルで検証する必要があります。

#### バックエンドモデル

バックエンドモデルは、システム構成の変更を処理する仕組みです。
バックエンドモジュールは`<module_name>/adminhtml/system.xml`で定義します。

すべてのバックエンドモデルは、[`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) クラスを拡張する必要があります。

バックエンドモデルを読み込む場合、設定値は保存されません。

### web サイト、ストア、ストアグループの設定

次のタイプの設定をインポートします。
（これらの設定は`config.php`の`scopes`配列下にあります）。

- `websites`: web サイト関連の設定
- `groups`：関連する設定を保存します
- `stores`: ストアビュー関連の設定

上記の設定は、次のモードで読み込むことができます。

- `create`: `config.php`には、実稼動環境に存在しない新しいエンティティ （`websites`、`groups`、`stores`）が含まれています
- `update`: `config.php`には、実稼動環境とは異なるエンティティ （`websites`、`groups`、`stores`）が含まれています
- `delete`: `config.php`には、_not_&#x200B;に、実稼動環境に存在するエンティティ （`websites`、`groups`、`stores`）が含まれています

>[!INFO]
>
>ストアに関連付けられているルートカテゴリは読み込みません。 Commerce Adminを使用して、ルートカテゴリをストアに関連付ける必要があります。

### テーマ設定

テーマの設定には、Commerce システムに登録されているすべてのテーマが含まれます。データは、`theme` データベース テーブルから直接取得されます。 （テーマ設定は`config.php`の`themes`配列にあります）。

#### テーマデータの構造

配列のキーは完全なテーマパスです：`area` + `theme path`

例：`frontend/Magento/luma`。
`frontend`はエリアで、`Magento/luma`はテーマパスです。

配列の値はテーマに関するデータです：コード、タイトル、パス、親ID

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
>- _テーマ登録_。 テーマデータが`config.php`で定義されていても、テーマのソースコードがファイルシステムに存在しない場合、テーマは無視されます（つまり、登録されません）。
>- _テーマ削除_。 テーマが`config.php`に存在しないが、ソースコードがファイルシステムに存在する場合、テーマは削除されません。
