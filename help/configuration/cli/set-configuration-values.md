---
title: 設定値の設定
description: 設定値を設定し、管理でロックされている値を変更する方法について説明します。
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 064be78a16142fc18bf64256eafde4b14c3ad529
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 0%

---

# 設定値の設定

{{file-system-owner}}

このトピックでは、次の目的で使用できる高度な設定コマンドについて説明します。

- コマンドラインから任意の設定オプションを設定します。
- オプションで、設定オプションをロックして、管理で値を変更できないようにします
- 管理者でロックされている設定オプションの変更

これらのコマンドを使用して、コマース設定を手動で設定するか、スクリプトを使用して設定できます。 設定オプションは、 _設定パス_( これは、 `/`設定オプションを一意に識別する区切り文字列。 設定パスは、次の参照で確認できます。

- [機密性の高いシステム固有の設定パスの参照](../reference/config-reference-sens.md)
- [支払設定パスの参照](../reference/config-reference-payment.md)
- [一般的な設定パスの参照](../reference/config-reference-general.md)
- [Commerce Enterprise B2B 拡張機能の設定パスのリファレンス](../reference/config-reference-b2b.md)

値は次の時間に設定できます。

- Commerce をインストールする前に、デフォルトのスコープの設定値のみを設定できます。これは、有効なスコープのみであるからです。

- Commerce をインストールした後、任意の Web サイトまたはストア表示範囲の設定値を設定できます。

次のコマンドを使用します。

- `bin/magento config:set` 設定パスによって、機密性のない設定値を設定します
- `bin/magento config:sensitive:set` 設定パスによって機密設定値を設定します
- `bin/magento config:show` は、保存された設定値を表示します。暗号化された設定の値は、アスタリスクとして表示されます

## 前提条件

設定値を設定するには、次のうち少なくとも 1 つを理解しておく必要があります。

- 設定パス
- 特定のスコープの設定値を設定するには、スコープコードを把握しておく必要があります。

  デフォルトのスコープの設定値を設定する場合は、何もする必要はありません。

### 設定パスを検索

次の参照を参照してください。

- [機密性の高いシステム固有の設定パスの参照](../reference/config-reference-sens.md)
- [支払設定パスの参照](../reference/config-reference-payment.md)
- [その他の設定パスの参照](../reference/config-reference-general.md)
- [Commerce Enterprise B2B 拡張機能の設定パスのリファレンス](../reference/config-reference-b2b.md)

### スコープコードを検索します。

スコープコードは、コマースデータベースまたはコマース管理で確認できます。

**管理者でスコープコードを検索するには**:

1. Web サイトを表示し、ビューを保存できるユーザーとして管理者にログインします。
1. クリック **[!UICONTROL Stores]** /設定/ **[!UICONTROL All Stores]**.
1. 右側のウィンドウで、Web サイトまたはストア表示の名前をクリックして、コードを確認します。

   次の図は、Web サイトコードのサンプルを示しています。

   ![管理者から Web サイトまたはストアビューコードを取得する](../../assets/configuration/website-code.png)

1. 続行 [値を設定](#set-values).

**データベース内のスコープコードを検索するには**:

Web サイトおよびストア表示のスコープコードは、Commerce データベースの `store_website` および `store` 表に含まれます。

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

   結果の例を次に示します。

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

   値を `code` 列。

1. 次の節に進みます。

## 値を設定

**システム固有の設定値を設定するには**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**機密設定値を設定するには**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

次の表に、 `set` コマンドパラメータ：

| パラメータ | 説明 |
| --- | --- |
| `--scope` | 設定の範囲。 指定できる値は次のとおりです。 `default`, `website`または `store`. デフォルトはです。 `default`. |
| `--scope-code` | 設定のスコープコード（Web サイトコードまたはストアビューコード） |
| `-e or --lock-env` | 値をロックして管理で編集できなくするか、管理で既にロックされている設定を変更します。 このコマンドは、値を `<Commerce base dir>/app/etc/env.php` ファイル。 |
| `-c or --lock-config` | 値をロックして管理で編集できなくするか、管理で既にロックされている設定を変更します。 このコマンドは、値を `<Commerce base dir>/app/etc/config.php` ファイル。 この `--lock-config` オプションが上書きされます `--lock-env` 両方のオプションを指定した場合。 |
| `path` | _必須_. 設定パス |
| `value` | _必須_. 設定の値 |

>[!INFO]
>
>Commerce 2.2.4 以降、 `--lock-env` および `--lock-config` オプションは `--lock` オプション。
>
>次の `--lock-env` または `--lock-config` オプションを使用して値を設定または変更する場合は、 [`bin/magento app:config:import` command](../cli/import-configuration.md) をクリックして、管理者またはストアフロントにアクセスする前に設定を読み込みます。

誤った設定パスを入力した場合、このコマンドはエラーを返します

```text
The "wrong/config/path" does not exist
```

詳しくは、次のセクションの 1 つを参照してください。

- [管理者で編集可能な設定値を設定](#set-configuration-values-that-can-be-edited-in-the-admin)
- [管理者で編集できない設定値を設定](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### 管理者で編集可能な設定値を設定

用途 `bin/magento config:set` _なし_ `--lock-env` または `--lock-config` データベースに値を書き込みます。 この方法で設定した値は、管理者で編集できます。

ストアのベース URL を設定する例を以下に示します。

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

### 管理者で編集できない設定値を設定

次の `--lock-env`  オプションを次のように指定すると、設定値はに保存されます。 `<Commerce base dir>/app/etc/env.php` また、管理でこの値を編集するためのフィールドを無効にします。

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

以下を使用して、 `--lock-env` Commerce がインストールされていない場合に設定値を設定するオプション。 ただし、デフォルトのスコープに対してのみ値を設定できます。

>[!INFO]
>
>この `env.php` ファイルはシステム固有です。 別のシステムに転送しないでください。 これを使用して、データベースの設定値を上書きできます。 たとえば、別のシステムからデータベースダンプを取り出し、 `base_url` およびその他の値を使用することで、データベースを変更する必要がなくなります。

次の `--lock-config` オプションを使用する場合、設定値は `<Commerce base dir>/app/etc/config.php`. 管理者でこの値を編集するためのフィールドは無効です。

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

以下を使用できます。 `--lock-config` Commerce がインストールされていない場合に設定値を設定します。 ただし、デフォルトのスコープに対してのみ値を設定できます。

>[!INFO]
>
>転送は可能です `config.php` を別のシステムに追加して、同じ設定値を使用します。 例えば、同じを使用するテストシステムがある場合、 `config.php` は、同じ設定値を再度設定する必要がないことを意味します。

## 設定の値を表示

コマンドオプション：

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

場所

- `--scope` は、設定の範囲（デフォルト、web サイト、ストア）です。 デフォルト値は `default`
- `--scope-code` は、設定のスコープコード（web サイトコードまたはストアビューコード）です。
- `path` は first_part/second_part/third_part/etc 形式の設定パスです (_必須_)

>[!INFO]
>
>この `bin/magento config:show` コマンドは、任意の [暗号化された値](../reference/config-reference-sens.md) 一連のアスタリスクとして： `******`.

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

**の保存されているすべての設定を表示するには `base` web サイト**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

結果：

```terminal
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**デフォルトスコープのベース URL を表示するには**:

```bash
bin/magento config:show web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example.com/
```

**のベース URL を表示するには、以下を実行します。 `base` web サイト**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example-for-website.com/
```

**のベース URL を表示するには、以下を実行します。 `default` ストア**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>スコープコードには、文字（a ～ z または A ～ Z）、数字 (0 ～ 9)、アンダースコア (_) のみを含めることができます。 また、最初の文字は文字にする必要があります。 新しい Web サイトまたはストアビューを作成する際に大文字またはキャメルケースを使用した場合、内部的な一致では、環境変数を使用した設定の上書きに対応するため、大文字と小文字が区別されません。 詳しくは、 [環境変数を使用して設定を上書きする](../reference/override-config-settings.md#environment-variables).

