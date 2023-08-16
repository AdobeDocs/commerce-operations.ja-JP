---
title: 設定の上書き
description: 環境変数を使用して設定を上書きする方法を説明します。
exl-id: 788fd3cd-f8c1-4514-8141-547fed36e9ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 0%

---

# 設定の上書き

このトピックでは、設定パスを知って環境変数名を導き出す方法について説明します。 環境変数を使用して、Adobe Commerceの設定を上書きできます。 例えば、実稼働システムで支払い処理者のライブ URL の値を上書きできます。

次の値を上書きできます： _任意_ 環境変数を使用した設定。ただし、Adobeでは、共有設定ファイルを使用して一貫性のある設定を維持することをお勧めします。 `config.php`、およびシステム固有の設定ファイル `env.php`（を参照） [デプロイメントの一般的な概要](../deployment/overview.md).

>[!TIP]
>
>以下を確認します。 [環境の設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) トピック _Commerce on Cloud Infrastructure ガイド_.

## 環境変数

環境変数名は、スコープと、その特定の形式の設定パスで構成されます。 次の節では、変数名をより詳細に決定する方法について説明します。

次のいずれかに対して変数を使用できます。

- [機密値](config-reference-sens.md) は、環境変数または [`magento config:sensitive:set`](../cli/set-configuration-values.md) コマンドを使用します。
- システム固有の値は、次を使用して設定する必要があります。

   - 環境変数
   - The [`magento config:set`](../cli/set-configuration-values.md) command
   - 管理者が [`magento app:config:dump` command](../cli/export-configuration.md)

設定パスは、次の場所にあります。

- [機密性の高いシステム固有の設定パスの参照](config-reference-sens.md)
- [支払設定パスの参照](config-reference-payment.md)
- [Commerce B2B 拡張機能の設定パスの参照](config-reference-b2b.md)
- [その他の設定パスの参照](config-reference-general.md)

### 変数名

システム設定の変数名の一般的な形式は次のとおりです。

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` 次のいずれかを指定できます。

- グローバルスコープ ( つまり、 _すべて_ スコープ )

  グローバルスコープ変数の形式は次のとおりです。

  `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- 特定の範囲（つまり、この設定が影響するのは、指定したストア表示または Web サイトのみです）

  例えば、ストアビュースコープ変数の形式は次のとおりです。

  `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

  スコープの詳細については、次を参照してください。

   - [手順 1:Web サイトを検索するか、Web サイトビューの範囲の値を格納します。](#step-1-find-the-website-or-store-view-scope-value)
   - [範囲に関するコマースユーザーガイドのトピック](https://docs.magento.com/user-guide/configuration/scope.html)
   - [範囲のクイックリファレンス](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` は、次の文字に置き換えられた二重のアンダースコア文字を含む設定パスです。 `/`. 詳しくは、 [手順 2：システム変数の設定](#step-2-set-global-website-or-store-view-variables).

### 変数の形式

`<SCOPE>` が次の値と区切られている `<SYSTEM__VARIABLE__NAME>` 2 つのアンダースコア文字を使用します。

`<SYSTEM__VARIABLE__NAME>` は、設定の _設定パス_( これは、 `/` 特定の設定を一意に識別する区切り文字列。 次を置き換え `/` 構成パス内の文字に 2 つのアンダースコア文字を付けて、システム変数を作成します。

設定パスにアンダースコア文字が含まれている場合、アンダースコア文字は変数内に残ります。

設定パスの完全なリストは、次の場所で確認できます。

- [機密性の高いシステム固有の設定パスの参照](config-reference-sens.md)
- [支払設定パスの参照](config-reference-payment.md)
- [Commerce Enterprise B2B 拡張機能の設定パスのリファレンス](config-reference-b2b.md)
- [その他の設定パスの参照](config-reference-general.md)

## 手順 1:Web サイトを検索するか、Web サイトビューの範囲の値を格納します。

この項では、次の単位でシステム構成値を検索して設定する方法について説明します。 _範囲_ （ストア表示または web サイト）。 グローバルスコープ変数を設定するには、 [手順 2：グローバル、Web サイト、またはストア表示変数を設定する](#step-2-set-global-website-or-store-view-variables).

スコープの値は `store`, `store_group`、および `store_website` テーブル。

- The `store` テーブルは、ストアビューの名前とコードを指定します。
- The `store_website` 表は、ウェブサイトの名前とコードを指定します。

また、管理者を使用してコード値を検索できます。

表の読み方：

- `Path in Admin` 列

  コンマの前の値は、管理ナビゲーションのパスです。 コンマの後の値は、右側のウィンドウのオプションです。

- `Variable name` 列は、対応する環境変数の名前です。

  必要に応じて、これらの設定パラメータのシステム値を環境変数として指定するオプションがあります。

   - 変数名全体は常にオールキャップス
   - 変数名をで始めます。 `CONFIG__` （アンダースコア文字が 2 つあることに注意）。
   - 次の項目が見つかります。 `<STORE_VIEW_CODE>` または `<WEBSITE_CODE>` 以下の節で示すように、Admin または Commerce データベース内の変数名の一部。
   - 以下を見つけることができます。 `<SYSTEM__VARIABLE__NAME>` で説明されているように [手順 2：グローバル、Web サイト、またはストア表示変数を設定する](#step-2-set-global-website-or-store-view-variables).

### Admin で Web サイトまたはストア表示範囲を見つける

次の表に、Web サイトを検索する方法、または Admin で View 値を格納する方法をまとめます。

| 説明 | 管理でのパス | 変数名 |
|--------------|--------------|----------------------|
| ストアビューの作成、編集、削除 | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Web サイトの作成、編集、削除 | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

例えば、Web サイトを検索する場合や、Admin に Store View Scope の値を格納する場合は、次の手順を実行します。

1. Web サイトの表示を許可されたユーザーとして管理者にログインします。
1. クリック **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Web サイトまたはストア表示の名前をクリックします。

   次のように、右側のウィンドウが表示されます。

   ![Web サイトコードの検索](../../assets/configuration/website-code.png)

1. スコープ名が **[!UICONTROL Code]** フィールドに入力します。
1. 次で続行 [手順 2：グローバル、Web サイト、またはストア表示変数を設定する](#step-2-set-global-website-or-store-view-variables).

### データベース内で Web サイトまたはストア表示範囲を見つける

データベースからこれらの値を取得する手順は、次のとおりです。

1. ファイルシステムの所有者として開発システムにログインします（まだログインしていない場合）。
1. 次のコマンドを入力します。

   ```bash
   mysql -u <database-username> -p
   ```

1. 次の場合： `mysql>` プロンプトで、次のコマンドを次の順序で入力します。

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

1. 次の値を使用： `code` 列をスコープ名として指定し、 `name` の値です。

   例えば、テスト Web サイトの設定変数を設定するには、次の形式を使用します。

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   場所 `<SYSTEM__VARIABLE__NAME>` は次の節から取り上げます。

## 手順 2：グローバル、Web サイト、またはストア表示変数を設定する

このセクションでは、システム変数を設定する方法について説明します。

- グローバルスコープ（すべての Web サイト、ストア、ストア表示）の値を設定するには、変数名をで始めます。 `CONFIG__DEFAULT__`.

- 特定のストア表示または Web サイトの値を設定するには、変数名を開始します ( [手順 1：スコープ値を検索する](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- 変数名の最後の部分は設定パスで、各設定で一意です。

[いくつかの例を見る](#examples).

次の表に、いくつかのサンプル変数を示します。

| 説明 | 管理でのパス（省略） **ストア** > **設定** > **設定**) | 変数名 |
|--------------|--------------|----------------------|
| Elasticsearchサーバーのホスト名 | カタログ > **カタログ**, **Elasticsearchサーバーのホスト名** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearchサーバーポート | カタログ > **カタログ**, **Elasticsearchサーバーポート** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| 輸送先の国の起源 | セールス > **発送設定** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| カスタム管理 URL | 詳細 > **管理者** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| カスタム管理パス | 詳細 > **管理者** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## 例

この節では、一部のサンプル変数の値を検索する方法を示します。

### Elasticsearchサーバーのホスト名

グローバル・HTML縮小の変数名を検索する手順は、次のとおりです。

1. 範囲を決定します。

   変数名がで始まるのはグローバルスコープです。 `CONFIG__DEFAULT__`

1. 変数名の残りの部分はです。 `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **結果**：変数名はです。 `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### 輸送先の国の起源

出荷元の変数名を検索する手順は、次のとおりです。

1. 範囲を決定します。

   でスコープを検索します。 [データベース](#find-a-website-or-store-view-scope-in-the-database) 手順 1: web サイトを検索するか、store view の範囲の値を参照してください。 ( また、 [手順 2 の表：グローバル、Web サイト、またはストア表示の変数を設定する](#step-2-set-global-website-or-store-view-variables.

   例えば、範囲は `CONFIG__WEBSITES__DEFAULT`.

1. 変数名の残りの部分はです。 `SHIPPING__ORIGIN__COUNTRY_ID`.

   **結果**：変数名はです。 `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## 環境変数の使用方法

PHP の [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) 配列を関連付けます。 値は、Commerce の実行時に実行される任意の PHP スクリプトで設定できます。

>[!TIP]
>
>で変数値を設定しています `index.php` または `pub/index.php` が必ずしも期待どおりに機能するわけではありません。web サーバーの設定に応じて、異なるアプリケーションエントリポイントを使用できるからです。 配置 `$_ENV` 指令 `app/bootstrap.php` ファイル（異なるアプリケーションエントリポイントに関係なく） `$_ENV` ディレクティブが常に実行されるのは、 `app/bootstrap.php` ファイルは、コマースアーキテクチャの一部として読み込まれます。

2 つの `$_ENV` の値は次のとおりです。

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

詳細な手順の例を、 [環境変数を使用した設定値の設定](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- を使用して、 `$_ENV` 配列、 `variables_order = "EGPCS"`（環境、取得、投稿、Cookie、サーバー） `php.ini` ファイル。 詳しくは、 [PHP ドキュメント](https://www.php.net/manual/en/ini.core.php).
>
>- クラウドインフラストラクチャ上のAdobe Commerceの場合、 [Project Web インターフェイス](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)を使用する場合は、変数名の前にを付ける必要があります。 `env:`. 例：
>
>![環境変数の例](../../assets/configuration/cloud-console-envvariable.png)
