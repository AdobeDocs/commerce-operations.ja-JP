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

の値を上書きできます _いずれか_ 環境変数を使用した設定。ただし、Adobeでは、共有設定ファイル `config.php`システム固有の設定ファイル `env.php`で説明されているように [デプロイメントの一般的な概要](../deployment/overview.md).

>[!TIP]
>
>を確認してください。 [環境の設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) のトピック _クラウドインフラストラクチャー上のCommerce ガイド_.

## 環境変数

環境変数名は、スコープと、特定の形式の設定パスで構成されます。 次の節では、変数名を決定する方法について詳しく説明します。

変数は、次のいずれかの場合に使用できます。

- [機密性の高い値](config-reference-sens.md) 環境変数またはを使用して設定する必要があります [`magento config:sensitive:set`](../cli/set-configuration-values.md) コマンド。
- システム固有の値は、次を使用して設定する必要があります。

   - 環境変数
   - この [`magento config:set`](../cli/set-configuration-values.md) コマンド
   - 管理者に続いて [`magento app:config:dump` コマンド](../cli/export-configuration.md)

設定パスは次の場所にあります。

- [機密およびシステム固有の設定パスのリファレンス](config-reference-sens.md)
- [支払構成パス参照](config-reference-payment.md)
- [Commerce B2B Extension 設定パスのリファレンス](config-reference-b2b.md)
- [その他の設定パスのリファレンス](config-reference-general.md)

### 変数名

システム設定の変数名の一般的な形式は次のとおりです。

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` 次のいずれかを指定できます。

- グローバル範囲（グローバル設定） _all_ スコープ）

  グローバルスコープ変数の形式は次のとおりです。

  `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- 特定の範囲（つまり、設定は指定されたストア表示または web サイトにのみ影響します）

  例えば、ストア表示のスコープ変数の形式は次のようになります。

  `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

  範囲の詳細については、次を参照してください。

   - [手順 1:web サイトまたはストア表示の範囲の値を見つける](#step-1-find-the-website-or-store-view-scope-value)
   - [対象範囲に関するCommerce ユーザーガイドのトピック](https://docs.magento.com/user-guide/configuration/scope.html)
   - [範囲のクイックリファレンス](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` は、に代わって 2 つのアンダースコア文字を持つ設定パスです。 `/`. 詳しくは、を参照してください [手順 2：システム変数の設定](#step-2-set-global-website-or-store-view-variables).

### 変数形式

`<SCOPE>` 次と分離されています `<SYSTEM__VARIABLE__NAME>` 2 つのアンダースコア文字。

`<SYSTEM__VARIABLE__NAME>` は、設定のから派生します _設定パス_。これは `/` 特定の設定を一意に識別する区切り文字列。 それぞれを置換 `/` システム変数を作成するための 2 つのアンダースコア文字を含む設定パス内の文字。

設定パスにアンダースコア文字が含まれている場合、アンダースコア文字は変数に残ります。

設定パスの完全なリストは、次の場所で確認できます。

- [機密およびシステム固有の設定パスのリファレンス](config-reference-sens.md)
- [支払構成パス参照](config-reference-payment.md)
- [Commerce Enterprise B2B Extension 設定パスのリファレンス](config-reference-b2b.md)
- [その他の設定パスのリファレンス](config-reference-general.md)

## 手順 1:web サイトまたはストア表示の範囲の値を見つける

このセクションでは、次の方法でシステム設定値を検索して設定する方法について説明します _範囲_ （ストア表示または web サイト）。 グローバル スコープ変数を設定するには、を参照してください。 [手順 2：グローバル、web サイトまたはストア表示の変数を設定する](#step-2-set-global-website-or-store-view-variables).

範囲の値はから取得されます。 `store`, `store_group`、および `store_website` テーブル。

- この `store` テーブルはストア ビュー名とコードを指定します
- この `store_website` 表：Web サイト名とコードを指定します

また、Admin を使用してコード値を検索することもできます。

テーブルの読み方：

- `Path in Admin` 列

  コンマの前の値は、管理ナビゲーションのパスです。 コンマの後の値が、右側のペインのオプションです。

- `Variable name` column は、対応する環境変数の名前です。

  必要に応じて、これらの設定パラメーターのシステム値を環境変数として指定することもできます。

   - 変数名全体は常に ALL CAPS です
   - 変数名の開始 `CONFIG__` （アンダースコア 2 文字）
   - 次を見つけることができます `<STORE_VIEW_CODE>` または `<WEBSITE_CODE>` 次の節で示すように、Admin またはCommerce データベースの変数名の一部。
   - 次を見つけることができます `<SYSTEM__VARIABLE__NAME>` ～で議論されているように [手順 2：グローバル、web サイトまたはストア表示の変数を設定する](#step-2-set-global-website-or-store-view-variables).

### 管理画面で web サイトまたはストアの表示範囲を検索する

次の表に、管理者で web サイトまたはストアビューの値を検索する方法を示します。

| 説明 | 管理画面のパス | 変数名 |
|--------------|--------------|----------------------|
| ストアビューの作成、編集、削除 | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Web サイトの作成、編集、削除 | **[!UICONTROL Stores]** > **[!UICONTROL All Store]秒** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

例えば、管理画面で web サイトまたはストアの表示範囲の値を検索するには、次のようにします。

1. Web サイトの表示を許可されたユーザーとして管理者にログインします。
1. クリック **[!UICONTROL Stores]** > **[!UICONTROL All Store]秒**.
1. Web サイトまたはストアビューの名前をクリックします。

   次のような右側のパネルが表示されます。

   ![Web サイトコードを検索](../../assets/configuration/website-code.png)

1. スコープ名は **[!UICONTROL Code]** フィールド。
1. 続行 [手順 2：グローバル、web サイトまたはストア表示の変数を設定する](#step-2-set-global-website-or-store-view-variables).

### データベース内で web サイトまたはストアの表示範囲を検索する

データベースからこれらの値を取得するには：

1. まだファイルシステムの所有者として開発システムにログインしない場合は、ログインします。
1. 次のコマンドを入力します。

   ```bash
   mysql -u <database-username> -p
   ```

1. 時刻 `mysql>` プロンプトに従って、次のコマンドを表示された順序で入力します。

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

1. の値を使用します `code` 列をスコープ名として使用し、 `name` の値。

   例えば、テスト web サイトの設定変数を設定するには、次の形式を使用します。

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   ここで、 `<SYSTEM__VARIABLE__NAME>` 次のセクションから取り込みます。

## 手順 2：グローバル、web サイトまたはストア表示の変数を設定する

この節では、システム変数の設定方法について説明します。

- グローバルスコープ（すべての web サイト、ストア、ストアビュー）の値を設定するには、変数名をから開始します。 `CONFIG__DEFAULT__`.

- 特定のストア ビューまたは Web サイトの値を設定するには、の説明に従って変数名を開始します [手順 1：範囲の値を見つける](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- 変数名の最後の部分は設定パスで、設定ごとに一意になります。

[いくつかの例を参照](#examples).

次の表に、変数の例をいくつか示します。

| 説明 | 管理画面のパス （省略） **ストア** > **設定** > **設定**） | 変数名 |
|--------------|--------------|----------------------|
| Elasticsearchサーバーのホスト名 | カタログ > **カタログ**, **Elasticsearchサーバーのホスト名** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearchサーバーポート | カタログ > **カタログ**, **Elasticsearchサーバーポート** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| 配送先国の起源 | 売上 > **発送設定** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| カスタム管理 URL | 詳細 > **Admin** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| カスタム管理パス | 詳細 > **Admin** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## 例

この節では、いくつかのサンプル変数の値を検索する方法について説明します。

### Elasticsearchサーバーのホスト名

グローバルHTML縮小用の変数名を見つけるには：

1. 範囲を決定します。

   これはグローバルスコープなので、変数名はで始まります。 `CONFIG__DEFAULT__`

1. 残りの変数名はです。 `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **結果**：変数名はです `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### 配送先国の起源

出荷国の出荷元の変数名を検索する手順は、次のとおりです。

1. 範囲を決定します。

   でスコープを検索します。 [データベース](#find-a-website-or-store-view-scope-in-the-database) 「手順 1:Web サイトまたはストア表示の範囲の値を検索する」で説明したとおり。 （に示すように、管理者でも値を見つけることができます。 [「手順 2：グローバル、web サイトまたはストア表示の変数を設定する」の表]（#step-2-set-global-website-or-store-view-variables。

   例えば、次のような範囲があります。 `CONFIG__WEBSITES__DEFAULT`.

1. 残りの変数名はです。 `SHIPPING__ORIGIN__COUNTRY_ID`.

   **結果**：変数名はです `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## 環境変数の使用方法

PHP のを使用して、設定値を変数として設定します。 [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) 配列を関連付けます。 Commerceの実行時に実行される任意の PHP スクリプトで値を設定できます。

>[!TIP]
>
>変数値の設定 `index.php` または `pub/index.php` web サーバーの設定によって異なるアプリケーションエントリポイントを使用できるので、は常に期待どおりに機能するとは限りません。 配置によって `$_ENV` 内のディレクティブ `app/bootstrap.php` ファイル（アプリケーションのエントリポイントの違いに関係なく）、 `$_ENV` ディレクティブは常に以下の場合以降に実行する： `app/bootstrap.php` Commerce アーキテクチャの一部としてファイルが読み込まれます。

2 を設定した例 `$_ENV` 値は次のとおりです。

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

ステップバイステップの例を次に示します [環境変数を使用して設定値を設定する](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- で設定した値を使用するには `$_ENV` 配列、を設定する必要があります `variables_order = "EGPCS"`（環境、Get、Post、Cookie およびサーバー） `php.ini` ファイル。 詳しくは、を参照してください [PHP のドキュメント](https://www.php.net/manual/en/ini.core.php).
>
>- クラウドインフラストラクチャー上のAdobe Commerceの場合、を使用して設定を上書きしようとした場合、 [Project Web インターフェイス](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)は、変数名の前にを付ける必要があります `env:`. 例：
>
>![環境変数の例](../../assets/configuration/cloud-console-envvariable.png)
