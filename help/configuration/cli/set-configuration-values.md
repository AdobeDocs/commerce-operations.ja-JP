---
title: 設定値の設定
description: Adobe Commerceで設定値を設定し、ロックされた管理者値を変更する方法について説明します。 高度な設定コマンドとテクニックをご紹介します。
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '1122'
ht-degree: 0%

---

# 設定値の設定

{{file-system-owner}}

このトピックでは、次の目的で使用できる高度な設定コマンドについて説明します。

- コマンドラインから任意の設定オプションを設定します
- オプションで設定オプションをロックして、その値を管理者で変更できないようにします
- 管理者でロックされている設定オプションの変更

これらのコマンドを使用して、Commerce設定を手動またはスクリプトを使用して設定できます。 設定オプションは、_設定パス_&#x200B;を使用して設定できます。これは、設定オプションを一意に識別する`/`区切りの文字列です。 次の参照で設定パスを見つけることができます。

- [機密性の高いシステム固有の設定パスの参照](../reference/config-reference-sens.md)
- [支払設定パスの参照](../reference/config-reference-payment.md)
- [一般設定パスのリファレンス](../reference/config-reference-general.md)
- [Commerce Enterprise B2B拡張機能の設定パスのリファレンス](../reference/config-reference-b2b.md)

次のタイミングで値を設定できます。

- Commerceをインストールする前に、デフォルトスコープの設定値のみを設定できます。これは、デフォルトスコープが唯一の有効なスコープであるためです。

- Commerceをインストールした後、web サイトまたはストアビューのスコープの設定値を設定できます。

次のコマンドを使用します。

- `bin/magento config:set`は、設定パスによって機密性のない設定値を設定します
- `bin/magento config:sensitive:set`は、設定パスによって機密性の高い設定値を設定します
- `bin/magento config:show`には保存された設定値が表示されます。暗号化された設定の値はアスタリスクとして表示されます

## 前提条件

設定値を設定するには、少なくとも次のいずれかを把握している必要があります。

- 設定パス
- 特定のスコープの設定値を設定するには、スコープコードを把握している必要があります。

  デフォルトのスコープの設定値を設定するには、何もする必要はありません。

### 設定パスの検索

次の参照を参照してください。

- [機密性の高いシステム固有の設定パスの参照](../reference/config-reference-sens.md)
- [支払設定パスの参照](../reference/config-reference-payment.md)
- [その他の設定パスの参照](../reference/config-reference-general.md)
- [Commerce Enterprise B2B拡張機能の設定パスのリファレンス](../reference/config-reference-b2b.md)

### スコープコードの検索

スコープコードは、Commerce データベースまたはCommerce管理者で確認できます。

**管理者**&#x200B;でスコープ コードを検索するには：

1. Web サイトとストアビューを表示できるユーザーとして管理者にログインします。
1. **[!UICONTROL Stores]** / 設定/ **[!UICONTROL All Stores]**&#x200B;をクリックします。
1. 右側のペインで、web サイトまたはストアビューの名前をクリックして、そのコードを表示します。

   次の図は、web サイトのコードの例を示しています。

   ![管理者からweb サイトまたはストアビューコードを取得](../../assets/configuration/website-code.png)

1. [値を設定](#set-values)で続行します。

**データベース内のスコープ コードを検索するには**:

Web サイトとストアビューのスコープ コードは、それぞれ`store_website`および`store` テーブルのCommerce データベースに保存されます。

1. Commerce データベースに接続します。

   ```shell
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

   サンプル結果は次のとおりです。

   ```ini
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   `code`列の値を使用します。

1. 次のセクションに進みます。

## 値を設定

**システム固有の設定値を設定するには**:

```shell
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**機密性の高い設定値を設定するには**:

```shell
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path
```

次の表に、`set` コマンド パラメーターを示します。

| パラメーター | 説明 |
| --- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `--scope` | 設定の範囲。 指定できる値は`default`、`website`または`store`です。 デフォルトは`default`です。 |
| `--scope-code` | 設定のスコープコード（web サイトコードまたはストアビューコード） |
| `-e or --lock-env` | 管理者で編集できないように値をロックするか、管理者で既にロックされている設定を変更します。 コマンドは、値を`<Commerce base dir>/app/etc/env.php` ファイルに書き込みます。 |
| `-c or --lock-config` | 管理者で編集できないように値をロックするか、管理者で既にロックされている設定を変更します。 コマンドは、値を`<Commerce base dir>/app/etc/config.php` ファイルに書き込みます。 両方のオプションを指定すると、`--lock-config` オプションは`--lock-env`を上書きします。 |
| `path` | _必須_。 設定パス |
| `value` | _必須_。 設定の値。 CLI コマンドでは別の引数として渡すことができますが、Adobeでは元のコマンドでは指定しないことをお勧めします。 代わりに、値なしでコマンドを実行し、プロンプトが表示されたら値を入力します。 この方法を使用すると、機密性の高いアクセス値をbash_historyに書き込むことができなくなります。これは、設定を設定する最も安全な方法です。 |

>[!INFO]
>
>Commerce 2.2.4では、`--lock-env`および`--lock-config` オプションが`--lock` オプションに代わっています。 これらのオプションのいずれかを使用すると、値は`app/etc/env.php`または`app/etc/config.php` ファイルに直接書き込まれ、管理者では読み取り専用になります。 これらのファイルから構成の変更をデータベースに読み込むには、`bin/magento app:config:import` コマンドを実行します。例えば、ファイルを手動で編集または再デプロイした後です。

設定パスが正しくない場合、このコマンドはエラーを返します

```text
The "wrong/config/path" does not exist
```

詳しくは、次のいずれかの節を参照してください。

- [管理者で編集可能な設定値を設定する](#set-configuration-values-that-can-be-edited-in-the-admin)
- [管理者で編集できない設定値を設定する](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### 管理者で編集可能な設定値を設定する

値をデータベースに書き込むには、`bin/magento config:set` __ `--lock-env`または`--lock-config`を使用せずに使用します。 この方法で設定した値は、管理者で編集できます。

ストアベース URLを設定する例をいくつか紹介します。

デフォルトスコープのベース URLを設定します。

```shell
bin/magento config:set web/unsecure/base_url http://example.com/
```

`base` web サイトのベース URLを設定します。

```shell
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

`test` ストアビューのベース URLを設定します。

```shell
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### 管理者で編集できない設定値を設定する

次のように`--lock-env` オプションを使用すると、コマンドは設定値を`<Commerce base dir>/app/etc/env.php`に保存し、この値を管理者で編集するためのフィールドを無効にします。

```shell
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Commerceがインストールされていない場合は、`--lock-env` オプションを使用して設定値を設定できます。 ただし、デフォルトの範囲に対してのみ値を設定できます。

>[!INFO]
>
>`env.php` ファイルはシステム固有です。 別のシステムに転送しないでください。 これを使用すると、データベースから設定値を上書きできます。 例えば、別のシステムからデータベースダンプを取得し、`base_url`およびその他の値を上書きして、データベースを変更する必要がないようにすることができます。

次のように`--lock-config` オプションを使用すると、設定値は`<Commerce base dir>/app/etc/config.php`に保存されます。 管理者でこの値を編集するためのフィールドが無効になっています。

```shell
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Commerceがインストールされていない場合は、`--lock-config`を使用して設定値を設定できます。 ただし、デフォルトの範囲に対してのみ値を設定できます。

>[!INFO]
>
>`config.php`を別のシステムに転送して、同じ設定値を別のシステムで使用できます。 例えば、テストシステムがある場合、同じ`config.php`を使用すると、同じ設定値を再度設定する必要がなくなります。

## 構成設定の値の表示

コマンドオプション：

```shell
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

どこで

- `--scope`は設定の範囲（既定、web サイト、ストア）です。 デフォルト値は`default`です
- `--scope-code`は設定のスコープ コード （web サイト コードまたはストア ビューのコード）です
- `path`は、first _part/second_ part/third_part/etc形式の設定パスです（_必須_）

>[!INFO]
>
>`bin/magento config:show` コマンドは、[暗号化された値](../reference/config-reference-sens.md)の値を一連のアスタリスクとして表示します：`******`。

### 例

**保存されたすべての設定を表示するには**:

```shell
bin/magento config:show
```

施策：

```text
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**`base` web サイト**&#x200B;のすべての保存済み設定を表示するには：

```shell
bin/magento config:show --scope=websites --scope-code=base
```

施策：

```text
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**デフォルトスコープ**&#x200B;のベース URLを表示するには：

```shell
bin/magento config:show web/unsecure/base_url
```

施策：

```text
web/unsecure/base_url - http://example.com/
```

**`base` web サイト**&#x200B;のベース URLを表示するには：

```shell
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

施策：

```text
web/unsecure/base_url - http://example-for-website.com/
```

**`default` ストアのベース URLを表示するには**:

```shell
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

施策：

```text
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>スコープコードには、文字（a ～ zまたはA ～ Z）、数字（0 ～ 9）、およびアンダースコア（_）のみを含めることができます。 また、最初の文字は文字でなければなりません。 Web サイトまたはストアビューの作成時に大文字またはキャメルケースを使用する場合、内部的に一致は大文字と小文字を区別せず、環境変数を使用して設定設定を上書きできます。 [環境変数を使用して構成設定を上書きする](../reference/override-config-settings.md#environment-variables)を参照してください。

