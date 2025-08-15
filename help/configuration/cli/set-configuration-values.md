---
title: 設定値を設定
description: 管理者で設定値を設定し、ロックされている値を変更する方法について説明します。
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
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

これらのコマンドを使用して、Commerceの設定を手動で、またはスクリプトを使用して行うことができます。 設定オプションは、その設定オプションを一意に識別する _区切りの文字列である_ 設定パス `/` を使用して設定します。 設定パスは、次の参照で確認できます。

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
- `bin/magento config:show` は保存された設定値を表示します。暗号化された設定値はアスタリスクで表示されます

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

**管理者でスコープコードを検索するには**:

1. Web サイトの表示や表示の保存を行えるユーザーとして管理者にログインします。
1. **[!UICONTROL Stores]** /設定/ **[!UICONTROL All Stores]** をクリックします。
1. 右側のウィンドウで、web サイトまたはストアビューの名前をクリックして、そのコードを表示します。

   次の図に、サンプル Web サイトコードを示します。

   ![ 管理者から web サイトまたはストアの表示コードを取得する ](../../assets/configuration/website-code.png)

1. [ 値を設定 ](#set-values) を続行します。

**データベースでスコープ コードを検索するには**:

Web サイトおよびストアビューのスコープコードは、それぞれCommerce データベースの `store_website` テーブルおよび `store` テーブルに格納されます。

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

   ```
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   `code` 列の値を使用します。

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

次の表に、`set` のコマンドパラメーターを示します。

| パラメーター | 説明 |
| --- | --- |
| `--scope` | 設定のスコープ。 使用できる値は、`default`、`website`、`store` です。 デフォルトは `default` です。 |
| `--scope-code` | 設定の範囲コード（web サイトコードまたはストア表示コード） |
| `-e or --lock-env` | 値をロックして管理者で編集できないようにするか、既に管理者でロックされている設定を変更します。 このコマンドは、`<Commerce base dir>/app/etc/env.php` ファイルに値を書き込みます。 |
| `-c or --lock-config` | 値をロックして管理者で編集できないようにするか、既に管理者でロックされている設定を変更します。 このコマンドは、`<Commerce base dir>/app/etc/config.php` ファイルに値を書き込みます。 両方のオプションを指定した場合、`--lock-config` オプションは `--lock-env` を上書きします。 |
| `path` | _必須_。 設定パス |
| `value` | _必須_。 設定の値 |

>[!INFO]
>
>Commerce 2.2.4 以降では、「`--lock-env`」オプションと「`--lock-config`」オプションが「`--lock`」オプションに置き換わります。
>
>`--lock-env` または `--lock-config` オプションを使用して値を設定または変更する場合は、[`bin/magento app:config:import` コマンドを使用して設定を読み込んでから ](../cli/import-configuration.md) 管理者またはストアフロントにアクセスする必要があります。

間違った設定パスを入力すると、このコマンドはエラーを返します

```text
The "wrong/config/path" does not exist
```

詳しくは、次のいずれかの節を参照してください。

- [管理者が編集できる設定値を設定します。](#set-configuration-values-that-can-be-edited-in-the-admin)
- [管理者が編集できない設定値を設定します。](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### 管理者が編集できる設定値を設定します。

値をデータベースに書き込むには、`bin/magento config:set` _without_ `--lock-env` または `--lock-config` を使用します。 この方法で設定した値は、管理者で編集できます。

ストアベース URL の設定例を次に示します。

デフォルトスコープのベース URL を設定します。

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

`base` の web サイトのベース URL を設定します。

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

`test` ストア表示のベース URL を設定してください：

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### 管理者が編集できない設定値を設定します。

次のように `--lock-env` オプションを使用すると、コマンドは設定値を `<Commerce base dir>/app/etc/env.php` に保存し、Admin でこの値を編集するためのフィールドを無効にします。

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Commerceがインストールされていない場合は、`--lock-env` オプションを使用して設定値を設定できます。 ただし、デフォルトの範囲の値のみを設定できます。

>[!INFO]
>
>`env.php` のファイルは、システムに固有です。 別のシステムに転送しないでください。 これを使用して、データベースの設定値を上書きできます。 例えば、別のシステムからデータベースダンプを取得し、`base_url` と他の値を上書きして、データベースを変更する必要がないようにすることができます。

次のように `--lock-config` オプションを使用すると、設定値は `<Commerce base dir>/app/etc/config.php` に保存されます。 管理者でこの値を編集するフィールドは無効になっています。

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Commerceがインストールされていない場合は、`--lock-config` を使用して設定値を設定できます。 ただし、デフォルトの範囲の値のみを設定できます。

>[!INFO]
>
>`config.php` を別のシステムに転送して、そこで同じ設定値を使用することができます。 例えば、テストシステムがある場合、同じ `config.php` を使用すると、同じ設定値を再度設定する必要がなくなります。

## 構成設定の値を表示

コマンドオプション：

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

ここで、

- `--scope` は、設定の範囲（デフォルト、web サイト、ストア）です。 デフォルト値は `default` です
- `--scope-code` は設定のスコープ コードです（web サイト コードまたはストア表示コード）
- `path` は、first_part/second_part/third_part/etc 形式の設定パスです（_必須_）。

>[!INFO]
>
>`bin/magento config:show` コマンドは、[ 暗号化された値 ](../reference/config-reference-sens.md) の値を一連のアスタリスク（`**&#x200B;**&#x200B;**`）として表示します。

### 例

**保存されているすべての設定を表示するには**:

```bash
bin/magento config:show
```

結果：

```
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**`base` の web サイトに保存されているすべての設定を表示するには**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

結果：

```
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**デフォルトスコープのベース URL を表示するには**:

```bash
bin/magento config:show web/unsecure/base_url
```

結果：

```
web/unsecure/base_url - http://example.com/
```

**`base` Web サイトのベース URL を表示するには**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

結果：

```
web/unsecure/base_url - http://example-for-website.com/
```

**`default` ストアのベース URL を表示するには**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

結果：

```
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>スコープ コードには、文字（a ～ z または A ～ Z）、数字（0 ～ 9）、およびアンダースコア （_）のみを使用できます。 また、最初の文字は文字である必要があります。 Web サイト表示またはストア表示を作成する際に大文字または大文字を使用すると、内部的に一致させる際に大文字と小文字が区別されず、環境変数による設定の上書きに対応します。 [ 環境変数を使用して設定を上書き ](../reference/override-config-settings.md#environment-variables) を参照してください。

