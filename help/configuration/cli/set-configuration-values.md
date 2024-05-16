---
title: 設定値を設定
description: 管理者で設定値を設定し、ロックされている値を変更する方法について説明します。
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 473ab09f83a4cfc1809adff854d52a11ad49d3af
workflow-type: tm+mt
source-wordcount: '1038'
ht-degree: 0%

---

# 設定値を設定

{{file-system-owner}}

このトピックでは、次の目的で使用できる高度な設定コマンドについて説明します。

- コマンドラインからの設定オプションの設定
- オプションで、設定オプションをロックして、管理者でその値を変更できないようにします。
- 管理者でロックされている設定オプションの変更

これらのコマンドを使用して、Commerceの設定を手動で、またはスクリプトを使用して行うことができます。 設定オプションを設定するには、 _設定パス_。これは `/`その設定オプションを一意に識別する区切り文字列。 設定パスは、次の参照で確認できます。

- [機密およびシステム固有の設定パスのリファレンス](../reference/config-reference-sens.md)
- [支払構成パス参照](../reference/config-reference-payment.md)
- [一般設定パスのリファレンス](../reference/config-reference-general.md)
- [Commerce Enterprise B2B Extension 設定パスのリファレンス](../reference/config-reference-b2b.md)

次のタイミングで値を設定できます。

- Commerceは唯一の有効なスコープであるため、インストールする前に、デフォルトスコープの設定値のみを設定することができます。

- Commerceのインストール後、任意の web サイトやストアビューの範囲に対して設定値を指定できます。

次のコマンドを使用します。

- `bin/magento config:set` は、設定パスによって、大文字と小文字を区別しない設定値を設定します
- `bin/magento config:sensitive:set` は、設定パスによって機密設定値を設定します
- `bin/magento config:show` 保存された設定値を表示します。暗号化された設定値はアスタリスクで表示されます。

## 前提条件

設定値を設定するには、次のうち少なくとも 1 つを知っている必要があります。

- 設定パス
- 特定のスコープの設定値を設定するには、スコープ コードを知っている必要があります。

  デフォルトスコープの設定値を設定する場合は、何もする必要はありません。

### 設定パスの検索

以下のリファレンスを参照してください。

- [機密およびシステム固有の設定パスのリファレンス](../reference/config-reference-sens.md)
- [支払構成パス参照](../reference/config-reference-payment.md)
- [その他の設定パスのリファレンス](../reference/config-reference-general.md)
- [Commerce Enterprise B2B Extension 設定パスのリファレンス](../reference/config-reference-b2b.md)

### スコープ コードの検索

スコープコードは、Commerce データベースまたはCommerce Admin のいずれかで確認できます。

**Admin でスコープ コードを検索するには**:

1. Web サイトの表示や表示の保存を行えるユーザーとして管理者にログインします。
1. クリック **[!UICONTROL Stores]** > 設定 > **[!UICONTROL All Stores]**.
1. 右側のウィンドウで、web サイトまたはストアビューの名前をクリックして、そのコードを表示します。

   次の図に、サンプル Web サイトコードを示します。

   ![管理者から web サイトまたはストアビューコードを取得します](../../assets/configuration/website-code.png)

1. 続行 [値を設定](#set-values).

**データベースでスコープ コードを検索するには**:

Commerce Web サイトおよびストアビューのスコープコードは、 `store_website` および `store` それぞれテーブル。

1. Commerce データベースに接続します。

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. 次のコマンドを入力します。

   ```shell
   use <Commerce database name>;
   ```

   ```shell
   SELECT * FROM store;
   ```

   ```shell
   SELECT * FROM store_website;
   ```

   次に結果の例を示します。

   ```terminal
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   の値を使用します。 `code` 列。

1. 次の節に進みます。

## 値を設定

**システム固有の設定値を設定するには**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**機密性の高い設定値を設定するには**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

以下の表で、 `set` コマンド パラメーター：

| パラメーター | 説明 |
| --- | --- |
| `--scope` | 設定のスコープ。 使用可能な値は次のとおりです `default`, `website`、または `store`. デフォルトはです `default`. |
| `--scope-code` | 設定の範囲コード（web サイトコードまたはストア表示コード） |
| `-e or --lock-env` | 値をロックして管理者で編集できないようにするか、既に管理者でロックされている設定を変更します。 このコマンドは、値を `<Commerce base dir>/app/etc/env.php` ファイル。 |
| `-c or --lock-config` | 値をロックして管理者で編集できないようにするか、既に管理者でロックされている設定を変更します。 このコマンドは、値を `<Commerce base dir>/app/etc/config.php` ファイル。 この `--lock-config` オプションの上書き `--lock-env` 両方のオプションを指定した場合。 |
| `path` | _必須_. 設定パス |
| `value` | _必須_. 設定の値 |

>[!INFO]
>
>Commerce 2.2.4 以降、 `--lock-env` および `--lock-config` を置き換えるオプション `--lock` オプション。
>
>使用する場合 `--lock-env` または `--lock-config` オプション値を設定または変更するには、を使用する必要があります [`bin/magento app:config:import` コマンド](../cli/import-configuration.md) をクリックして、管理者またはストアフロントにアクセスする前に設定を読み込みます。

間違った設定パスを入力すると、このコマンドはエラーを返します

```text
The "wrong/config/path" does not exist
```

詳しくは、次のいずれかの節を参照してください。

- [管理者が編集できる設定値を設定します。](#set-configuration-values-that-can-be-edited-in-the-admin)
- [管理者が編集できない設定値を設定します。](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### 管理者が編集できる設定値を設定します。

使用方法 `bin/magento config:set` _なし_ `--lock-env` または `--lock-config` データベースに値を書き込みます。 この方法で設定した値は、管理者で編集できます。

ストアベース URL の設定例を次に示します。

デフォルトスコープのベース URL を設定します。

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

のベース URL を設定 `base` web サイト：

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

のベース URL を設定 `test` ストア表示：

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### 管理者が編集できない設定値を設定します。

使用する場合 `--lock-env`  オプションが次の場合、コマンドは設定値をに保存します。 `<Commerce base dir>/app/etc/env.php` 管理者でこの値を編集するフィールドを無効にします。

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

を使用できます `--lock-env` Commerceがインストールされていない場合に設定値を設定するオプション。 ただし、デフォルトの範囲の値のみを設定できます。

>[!INFO]
>
>この `env.php` ファイルはシステム固有です。 別のシステムに転送しないでください。 これを使用して、データベースの設定値を上書きできます。 例えば、別のシステムからデータベースダンプを取得して、を上書きできます `base_url` およびその他の値を指定できるので、データベースを変更する必要はありません。

使用する場合 `--lock-config` オプションが次の場合、設定値はに保存されます。 `<Commerce base dir>/app/etc/config.php`. 管理者でこの値を編集するフィールドは無効になっています。

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

次を使用できます `--lock-config` Commerceがインストールされていない場合に設定値を設定します。 ただし、デフォルトの範囲の値のみを設定できます。

>[!INFO]
>
>転送できます `config.php` を別のシステムに送信して、そこで同じ設定値を使用できるようにします。 例えば、テストシステムがある場合は、同じを使用します `config.php` は、同じ設定値を再度設定する必要がないことを意味します。

## 構成設定の値を表示

コマンドオプション：

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

ここで、

- `--scope` は設定の範囲（デフォルト、web サイト、ストア）です。 デフォルト値はです `default`
- `--scope-code` は、設定のスコープコード（web サイトコードまたはストア表示コード）です。
- `path` は、first_part/second_part/third_part/etc 形式の設定パスです（_必須_）

>[!INFO]
>
>この `bin/magento config:show` コマンドは、次のいずれかの値を表示します [暗号化された値](../reference/config-reference-sens.md) 一連のアスタリスクとして： `******`.

### 例

**保存されているすべての設定を表示するには**:

```bash
bin/magento config:show
```

結果：

```terminal
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**のすべての保存済み設定を表示するには： `base` web サイト**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

結果：

```terminal
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**既定のスコープのベース URL を表示するには**:

```bash
bin/magento config:show web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example.com/
```

**のベース URL を表示するには `base` web サイト**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example-for-website.com/
```

**のベース URL を表示するには `default` store**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>スコープ コードには、文字（a ～ z または A ～ Z）、数字（0 ～ 9）、およびアンダースコア （_）のみを使用できます。 また、最初の文字は文字である必要があります。 Web サイト表示またはストア表示を作成する際に大文字または大文字を使用すると、内部的に一致させる際に大文字と小文字が区別されず、環境変数による設定の上書きに対応します。 参照： [環境変数を使用して設定を上書きする](../reference/override-config-settings.md#environment-variables).

