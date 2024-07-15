---
title: 設定を上書き
description: 環境変数を使用して、設定を上書きする方法を説明します。
exl-id: 788fd3cd-f8c1-4514-8141-547fed36e9ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---

# 設定を上書き

このトピックでは、設定パスを把握しながら環境変数名を取得する方法について説明します。 環境変数を使用して、Adobe Commerce設定を上書きできます。 例えば、実稼動システム上の支払い処理者のライブ URL の値を上書きできます。

環境変数を使用して _any_ 構成設定の値を上書きできます。ただし、Adobeでは、[ デプロイメントの一般概要 ](../deployment/overview.md) で説明されているように、共有構成ファイル `config.php` およびシステム固有の構成ファイル `env.php` を使用して一貫性のある設定を維持することをお勧めします。

>[!TIP]
>
>[2}Cloud Infrastructure 上のCommerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) ガイドの { 環境の設定 _のトピックを確認してください。_

## 環境変数

環境変数名は、スコープと、特定の形式の設定パスで構成されます。 次の節では、変数名を決定する方法について詳しく説明します。

変数は、次のいずれかの場合に使用できます。

- [ 機密性の高い値 ](config-reference-sens.md) は、環境変数または [`magento config:sensitive:set`](../cli/set-configuration-values.md) コマンドを使用して設定する必要があります。
- システム固有の値は、次を使用して設定する必要があります。

   - 環境変数
   - [`magento config:set`](../cli/set-configuration-values.md) コマンド
   - Admin コマンドに続いて [`magento app:config:dump` コマンド ](../cli/export-configuration.md)

設定パスは次の場所にあります。

- [機密およびシステム固有の設定パスのリファレンス](config-reference-sens.md)
- [支払構成パス参照](config-reference-payment.md)
- [Commerce B2B Extension 設定パスのリファレンス](config-reference-b2b.md)
- [その他の設定パスのリファレンス](config-reference-general.md)

### 変数名

システム設定の変数名の一般的な形式は次のとおりです。

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

次のいず `<SCOPE>` かを使用できます。

- グローバル スコープ （つまり _すべての_ スコープのグローバル設定）

  グローバルスコープ変数の形式は次のとおりです。

  `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- 特定の範囲（つまり、設定は指定されたストア表示または web サイトにのみ影響します）

  例えば、ストア表示のスコープ変数の形式は次のようになります。

  `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

  範囲の詳細については、次を参照してください。

   - [手順 1:web サイトまたはストア表示の範囲の値を見つける](#step-1-find-the-website-or-store-view-scope-value)
   - [ 範囲 ](https://docs.magento.com/user-guide/configuration/scope.html) に関するCommerce ユーザーガイドのトピック
   - [ 範囲のクイックリファレンス ](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` は、`/` の代わりに 2 つのアンダースコア文字が使用される設定パスです。 詳しくは、[ 手順 2：システム変数の設定 ](#step-2-set-global-website-or-store-view-variables) を参照してください。

### 変数形式

`<SCOPE>` は `<SYSTEM__VARIABLE__NAME>` から 2 つのアンダースコア文字で区切られます。

`<SYSTEM__VARIABLE__NAME>` は、設定の _設定パス_ から派生します。これは、特定の設定を一意に識別する `/` 区切りの文字列です。 システム変数を作成するには、設定パスの各 `/` 文字を 2 つのアンダースコア文字で置き換えます。

設定パスにアンダースコア文字が含まれている場合、アンダースコア文字は変数に残ります。

設定パスの完全なリストは、次の場所で確認できます。

- [機密およびシステム固有の設定パスのリファレンス](config-reference-sens.md)
- [支払構成パス参照](config-reference-payment.md)
- [Commerce Enterprise B2B Extension 設定パスのリファレンス](config-reference-b2b.md)
- [その他の設定パスのリファレンス](config-reference-general.md)

## 手順 1:web サイトまたはストア表示の範囲の値を見つける

この節では、_範囲_ （ストアビューまたは web サイト）ごとにシステム設定値を見つけて設定する方法について説明します。 グローバルスコープ変数を設定するには、[ 手順 2：グローバル、web サイトまたはストアビューの変数の設定 ](#step-2-set-global-website-or-store-view-variables) を参照してください。

範囲の値は、`store`、`store_group`、`store_website` の各テーブルから取得されます。

- `store` の表は、ストアのビュー名とコードを示しています
- `store_website` の表に、Web サイトの名前とコードを示します

また、Admin を使用してコード値を検索することもできます。

テーブルの読み方：

- `Path in Admin` 列

  コンマの前の値は、管理ナビゲーションのパスです。 コンマの後の値が、右側のペインのオプションです。

- 列 `Variable name`、対応する環境変数の名前です。

  必要に応じて、これらの設定パラメーターのシステム値を環境変数として指定することもできます。

   - 変数名全体は常に ALL CAPS です
   - 変数名を `CONFIG__` で開始します（アンダースコア文字 2 文字に注意）
   - 次の節で示すように、管理データベースまたはCommerce データベースで、変数名の `<STORE_VIEW_CODE>` 部または `<WEBSITE_CODE>` 部を見つけることができます。
   - 「手順 2：グローバル、web サイトまたはストア表示の変数を設定する [」の説明に従って、`<SYSTEM__VARIABLE__NAME>` を確認 ](#step-2-set-global-website-or-store-view-variables) きます。

### 管理画面で web サイトまたはストアの表示範囲を検索する

次の表に、管理者で web サイトまたはストアビューの値を検索する方法を示します。

| 説明 | 管理画面のパス | 変数名 |
|--------------|--------------|----------------------|
| ストアビューの作成、編集、削除 | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Web サイトの作成、編集、削除 | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

例えば、管理画面で web サイトまたはストアの表示範囲の値を検索するには、次のようにします。

1. Web サイトの表示を許可されたユーザーとして管理者にログインします。
1. **[!UICONTROL Stores]**/**[!UICONTROL All Store]s** をクリックします。
1. Web サイトまたはストアビューの名前をクリックします。

   次のような右側のパネルが表示されます。

   ![Web サイトコードの検索 ](../../assets/configuration/website-code.png)

1. 範囲名が「**[!UICONTROL Code]**」フィールドに表示されます。
1. [ 手順 2：グローバル、web サイトまたはストア表示の変数を設定する ](#step-2-set-global-website-or-store-view-variables) をクリックして続行します。

### データベース内で web サイトまたはストアの表示範囲を検索する

データベースからこれらの値を取得するには：

1. まだファイルシステムの所有者として開発システムにログインしない場合は、ログインします。
1. 次のコマンドを入力します。

   ```bash
   mysql -u <database-username> -p
   ```

1. `mysql>` プロンプトで、次のコマンドを表示された順序で入力します。

   ```shell
   use <database-name>;
   ```

1. 次の SQL クエリを使用して、関連する値を検索します。

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   次に例を示します。

   ```shell
   mysql> SELECT * FROM STORE_WEBSITE;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

1. `code` 列の値を `name` の値ではなく、スコープ名として使用します。

   例えば、テスト web サイトの設定変数を設定するには、次の形式を使用します。

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   次の節では、`<SYSTEM__VARIABLE__NAME>` について説明します。

## 手順 2：グローバル、web サイトまたはストア表示の変数を設定する

この節では、システム変数の設定方法について説明します。

- グローバルスコープ（すべての web サイト、ストア、ストアビュー）の値を設定するには、変数名の先頭に `CONFIG__DEFAULT__` を付けます。

- 特定のストアビューまたは web サイトの値を設定するには、[ 手順 1：範囲の値を見つける ](#step-1-find-the-website-or-store-view-scope-value) で説明されているように変数名を開始します。

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- 変数名の最後の部分は設定パスで、設定ごとに一意になります。

[ いくつかの例を参照 ](#examples)。

次の表に、変数の例をいくつか示します。

| 説明 | 管理者のパス（**ストア**/**設定**/**設定** を省略） | 変数名 |
|--------------|--------------|----------------------|
| Elasticsearchサーバーのホスト名 | カタログ > **カタログ**, **Elasticsearchサーバーのホスト名** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearchサーバーポート | カタログ > **カタログ**、**Elasticsearchサーバーポート** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| 配送先国の起源 | 売上 > **出荷設定** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| カスタム管理 URL | 詳細 > **管理者** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| カスタム管理パス | 詳細 > **管理者** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## 例

この節では、いくつかのサンプル変数の値を検索する方法について説明します。

### Elasticsearchサーバーのホスト名

グローバルHTML縮小用の変数名を見つけるには：

1. 範囲を決定します。

   これはグローバルスコープなので、変数名は `CONFIG__DEFAULT__` で始まります。

1. 残りの変数名は `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` です。

   **結果**：変数名は `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` です

### 配送先国の起源

出荷国の出荷元の変数名を検索する手順は、次のとおりです。

1. 範囲を決定します。

   「手順 1:Web サイトまたはストア表示の範囲の値を検索する」の説明に従って ](#find-a-website-or-store-view-scope-in-the-database) データベース [ で範囲を検索します。 （手順 2：グローバル、web サイトまたはストア表示の変数の設定の [ の表に示すように、管理者の値を見つけることもできます ] （#step-2-set-global-website-or-store-view-variables。

   例えば、範囲は `CONFIG__WEBSITES__DEFAULT` のようになります。

1. 残りの変数名は `SHIPPING__ORIGIN__COUNTRY_ID` です。

   **結果**：変数名は `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID` です

## 環境変数の使用方法

PHP の [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) associate 配列を使用して、設定値を変数として設定します。 Commerceの実行時に実行される任意の PHP スクリプトで値を設定できます。

>[!TIP]
>
>`index.php` または `pub/index.php` の変数値の設定は、web サーバーの設定に応じて異なるアプリケーションエントリポイントを使用できるので、常に期待どおりに機能するとは限りません。 `$_ENV` ディレクティブを `app/bootstrap.php` ファイルに配置すると、異なるアプリケーションのエントリポイントに関係なく、`app/bootstrap.php` ファイルがCommerce アーキテクチャの一部として読み込まれるので、`$_ENV` ディレクティブは常に実行されます。

2 つの `$_ENV` 値を設定する例を次に示します。

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

詳しい手順の例は、[ 環境変数を使用して設定値を設定 ](../deployment/example-environment-variables.md) を参照してください。

>[!WARNING]
>
>- `$_ENV` 配列に設定した値を使用するには、`php.ini` ファイルに `variables_order = "EGPCS"` （Environment、Get、Post、Cookie、Server）を設定する必要があります。 詳しくは、[PHP のドキュメント ](https://www.php.net/manual/en/ini.core.php) を参照してください。
>
>- クラウドインフラストラクチャー上のAdobe Commerceの場合、[Project Web Interface](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project) を使用して設定を上書きしようとすると、変数名の先頭に `env:` を付ける必要があります。 例：
>
>![ 環境変数の例 ](../../assets/configuration/cloud-console-envvariable.png)
