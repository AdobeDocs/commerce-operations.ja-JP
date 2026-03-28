---
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '8012'
ht-degree: 1%

---
# bin/magento （Adobe Commerce オンプレミス）

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->

**バージョン**: 2.4.8

このリファレンスには、`bin/magento` コマンドラインツールを通じて利用できる145のコマンドが含まれています。
最初のリストは、Adobe Commerceの`bin/magento list` コマンドを使用して自動生成されます。

## 一般

カスタム CLI コマンドを追加するには、[&#x200B; 「CLI コマンドを追加」 &#x200B;](https://developer.adobe.com/commerce/php/development/cli-commands/) ガイドを使用します。

完全なコマンド名の代わりにショートカットを使用して、`bin/magento`個のCLI コマンドを呼び出すことができます。 例えば、`bin/magento setup:upgrade`、`bin/magento s:up`を使用して`bin/magento s:upg`を呼び出すことができます。 任意のCLI コマンドでショートカットを使用する方法については、[&#x200B; ショートカット構文](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax)を参照してください。

このリファレンスドキュメントは、アプリケーションのソースコードから生成されます。 ドキュメントを変更するには、を開きます
関連する[codebase](https://github.com/magento) リポジトリ内の対応するコマンドに対するプルリクエスト。 を参照
詳細については、[&#x200B; コードの投稿](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)を参照してください。

### グローバルオプション

#### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合は、list コマンドのdisplay help

- 既定：`false`
- 値を受け付けません

#### `--quiet`, `-q`

メッセージを出力しない

- 既定：`false`
- 値を受け付けません

#### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長性を上げます。通常の出力は1、詳細な出力は2、デバッグは3

- 既定：`false`
- 値を受け付けません

#### `--version`, `-V`

このアプリケーションのバージョンを表示

- 既定：`false`
- 値を受け付けません

#### `--ansi`

ANSI出力を強制（または – no-ansiを無効にする）

- 値を受け付けません

#### `--no-ansi`

「 – ansi」オプションを無効にする

- 既定：`false`
- 値を受け付けません

#### `--no-interaction`, `-n`

インタラクティブな質問は避けてください

- 既定：`false`
- 値を受け付けません


## `_complete`

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

シェル補完の提案を提供する内部コマンド

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--shell`, `-s`

シェルタイプ （&quot;bash&quot;, &quot;fish&quot;, &quot;zsh&quot;）

- 値が必要です

#### `--input`, `-i`

入力トークンの配列（例：COMP_WORDSまたはargv）

- 既定：`[]`
- 値が必要です

#### `--current`, `-c`

カーソルが置かれている「input」配列のインデックス（例：COMP_CWORD）

- 値が必要です

#### `--api-version`, `-a`

完了スクリプトのAPI バージョン

- 値が必要です

#### `--symfony`, `-S`

非推奨

- 値が必要です


## `completion`

```bash
bin/magento completion [--debug] [--] [<shell>]
```

シェル完了スクリプトをダンプします

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    bin/magento completion  | sudo tee /etc/bash_completion.d/magento

Or dump the script to a local file and source it:

    bin/magento completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/www/html/magento2/bin/magento completion )"
```

### 引数

#### `shell`

シェルタイプ （例：「bash」）、環境変数「$SHELL」の値が指定されていない場合は使用されます

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--debug`

完了デバッグログのテール

- 既定：`false`
- 値を受け付けません


## `help`

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```

コマンドのヘルプの表示

```
The help command displays help for a given command:

  bin/magento help list

You can also output the help in other formats by using the --format option:

  bin/magento help --format=xml list

To display the list of available commands, please use the list command.
```

### 引数

#### `command_name`

コマンド名

- 既定：`help`

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--format`

出力形式（txt、xml、json、md）

- 既定：`txt`
- 値が必要です

#### `--raw`

Raw コマンド ヘルプを出力するには

- 既定：`false`
- 値を受け付けません


## `list`

```bash
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

リストコマンド

```
The list command lists all commands:

  bin/magento list

You can also display the commands for a specific namespace:

  bin/magento list test

You can also output the information in other formats by using the --format option:

  bin/magento list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  bin/magento list --raw
```

### 引数

#### `namespace`

名前空間名

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--raw`

Raw コマンドリストを出力するには

- 既定：`false`
- 値を受け付けません

#### `--format`

出力形式（txt、xml、json、md）

- 既定：`txt`
- 値が必要です

#### `--short`

コマンドの引数の記述をスキップするには

- 既定：`false`
- 値を受け付けません


## `admin:adobe-ims:disable`

```bash
bin/magento admin:adobe-ims:disable
```

Adobe IMSモジュールを無効にする

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `admin:adobe-ims:enable`

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

Adobe IMSモジュールを有効にします。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--organization-id`, `-o`

Adobe IMS設定の組織IDを設定します。 モジュールを有効にする際に必須

- 値を受け入れる

#### `--client-id`, `-c`

Adobe IMS設定のクライアント IDを設定します。 モジュールを有効にする際に必須

- 値を受け入れる

#### `--client-secret`, `-s`

Adobe IMS設定のクライアントシークレットを設定します。 モジュールを有効にする際に必須

- 値を受け入れる

#### `--2fa`, `-t`

Adobe Admin Consoleの組織で2FAが有効になっているかどうかを確認します。 モジュールを有効にする際に必須

- 値を受け入れる


## `admin:adobe-ims:info`

```bash
bin/magento admin:adobe-ims:info
```

Adobe IMSモジュール設定の情報

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `admin:adobe-ims:status`

```bash
bin/magento admin:adobe-ims:status
```

Adobe IMSモジュールのステータス

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `admin:user:create`

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

管理者を作成します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--admin-user`

（必須）管理者ユーザー

- 値が必要です

#### `--admin-password`

（必須）管理者パスワード

- 値が必要です

#### `--admin-email`

（必須）管理者のメールアドレス

- 値が必要です

#### `--admin-firstname`

（必須）管理者の名前

- 値が必要です

#### `--admin-lastname`

（必須）管理者の姓

- 値が必要です

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `admin:user:unlock`

```bash
bin/magento admin:user:unlock <username>
```

管理者アカウントのロック解除

```
This command unlocks an admin account by its username.
To unlock:
      bin/magento admin:user:unlock username
```

### 引数

#### `username`

ロックを解除する管理者ユーザー名

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `app:config:dump`

```bash
bin/magento app:config:dump [<config-types>...]
```

アプリケーションのダンプを作成

### 引数

#### `config-types`

設定タイプのスペース区切りリストまたは省略して、すべての[ スコープ、テーマ、システム、i18n]をダンプします

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `app:config:import`

```bash
bin/magento app:config:import
```

共有コンフィギュレーションファイルから適切なデータストレージにデータをインポートする

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `app:config:status`

```bash
bin/magento app:config:status
```

設定の伝達に更新が必要かどうかを確認します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `braintree:migrate`

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

Magento 1 データベースからのストアド カードの移行

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--host`

ホスト名/IP。 ポートはオプションです

- 値が必要です

#### `--dbname`

データベース名

- 値が必要です

#### `--username`

データベースユーザー名。 読み取りアクセスが必要

- 値が必要です

#### `--password`

パスワード

- 値が必要です


## `cache:clean`

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

キャッシュの種類を消去

### 引数

#### `types`

すべてのキャッシュタイプに適用するキャッシュタイプまたは省略のスペース区切りリスト。

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--bootstrap`

ブートストラップのパラメーターの追加または上書き

- 値が必要です


## `cache:clean:payment_services_merchant_scopes`

```bash
bin/magento cache:clean:payment_services_merchant_scopes
```

Clean Payment Services Merchant scopes cache

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `cache:disable`

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

キャッシュタイプを無効にします

### 引数

#### `types`

すべてのキャッシュタイプに適用するキャッシュタイプまたは省略のスペース区切りリスト。

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--bootstrap`

ブートストラップのパラメーターの追加または上書き

- 値が必要です


## `cache:enable`

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

キャッシュタイプを有効にします

### 引数

#### `types`

すべてのキャッシュタイプに適用するキャッシュタイプまたは省略のスペース区切りリスト。

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--bootstrap`

ブートストラップのパラメーターの追加または上書き

- 値が必要です


## `cache:flush`

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

キャッシュタイプで使用されるキャッシュストレージをフラッシュします

### 引数

#### `types`

すべてのキャッシュタイプに適用するキャッシュタイプまたは省略のスペース区切りリスト。

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--bootstrap`

ブートストラップのパラメーターの追加または上書き

- 値が必要です


## `cache:status`

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

キャッシュステータスをチェック

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--bootstrap`

ブートストラップのパラメーターの追加または上書き

- 値が必要です


## `catalog:images:resize`

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

サイズ変更された商品画像の作成

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--async`, `-a`

非同期モードでの画像のサイズ変更

- 既定：`false`
- 値を受け付けません

#### `--skip_hidden_images`

商品ページから非表示としてマークされた画像を処理しない

- 既定：`false`
- 値を受け付けません


## `catalog:product:attributes:cleanup`

```bash
bin/magento catalog:product:attributes:cleanup
```

未使用の製品属性を削除します。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `cms:wysiwyg:restrict`

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

ユーザーHTML コンテンツ検証を強制するか、代わりに警告を表示するかを設定します

### 引数

#### `restrict`

y\n

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `config:sensitive:set`

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

機密性の高い設定値の設定

### 引数

#### `path`

group/section/field_nameの例の設定パス


#### `value`

設定値

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--interactive`, `-i`

インタラクティブモードを有効にして、すべての機密変数を設定

- 既定：`false`
- 値を受け付けません

#### `--scope`

設定のスコープ （設定しない場合は「デフォルト」を使用）

- 既定：`default`
- 値を受け入れる

#### `--scope-code`

設定のスコープコード、デフォルトでは空の文字列

- デフォルト：&quot;
- 値を受け入れる


## `config:set`

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

システム設定の変更

### 引数

#### `path`

section/group/field_name形式の設定パス

- 必須


#### `value`

設定値

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--scope`

設定の範囲（デフォルト、web サイト、またはストア）

- 既定：`default`
- 値が必要です

#### `--scope-code`

スコープコード （スコープが「デフォルト」でない場合にのみ必要）

- 値が必要です

#### `--lock-env`, `-e`

管理者での変更を妨げるロック値（app/etc/env.phpに保存されます）

- 既定：`false`
- 値を受け付けません

#### `--lock-config`, `-c`

他のインストールで値をロックして共有し、管理者の変更を防ぎます（app/etc/config.phpに保存されます）。

- 既定：`false`
- 値を受け付けません

#### `--lock`, `-l`

非推奨です。代わりに – lock-env オプションを使用してください。

- 既定：`false`
- 値を受け付けません


## `config:show`

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

指定されたパスの設定値を表示します。 パスを指定しない場合、保存されたすべての値が表示されます

### 引数

#### `path`

設定パス（例：section_id/group_id/field_id）

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--scope`

設定のスコープが指定されていない場合は、「デフォルト」スコープが使用されます

- 既定：`default`
- 値を受け入れる

#### `--scope-code`

スコープコード （スコープが`default`でない場合にのみ必要）

- デフォルト：&quot;
- 値を受け入れる


## `cron:install`

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

現在のユーザーのcrontabを生成してインストールします

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--force`, `-f`

インストールタスクの強制

- 既定：`false`
- 値を受け付けません

#### `--non-optional`, `-d`

オプション以外（デフォルト）のタスクのみをインストールします

- 既定：`false`
- 値を受け付けません


## `cron:remove`

```bash
bin/magento cron:remove
```

crontabからタスクを削除します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `cron:run`

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

スケジュール別にジョブを実行

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--group`

指定したグループからのみジョブを実行

- 値が必要です

#### `--exclude-group`

指定したグループからジョブを除外

- 既定：`[]`
- 複数の値を受け入れる

#### `--bootstrap`

ブートストラップのパラメーターの追加または上書き

- 値が必要です


## `customer:hash:upgrade`

```bash
bin/magento customer:hash:upgrade
```

最新のアルゴリズムに従ってお客様のハッシュをアップグレードする

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `deploy:mode:set`

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

アプリケーションモードを設定します。

### 引数

#### `mode`

設定するアプリケーションモード。 使用可能なオプションは、「開発者」または「実稼動環境」です

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--skip-compilation`, `-s`

静的コンテンツ（生成されたコード、前処理されたCSS、pub/static/のアセット）のクリアと再生をスキップします。

- 既定：`false`
- 値を受け付けません


## `deploy:mode:show`

```bash
bin/magento deploy:mode:show
```

現在のアプリケーションモードを表示します。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `dev:di:info`

```bash
bin/magento dev:di:info <class> [<area>]
```

コマンドの依存関係インジェクション設定に関する情報を提供します。

### 引数

#### `class`

クラス名

- 必須


#### `area`

市外局番

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `dev:email:newsletter-compatibility-check`

```bash
bin/magento dev:email:newsletter-compatibility-check
```

変数の互換性に関する潜在的な問題について、ニュースレターテンプレートをスキャンします

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `dev:email:override-compatibility-check`

```bash
bin/magento dev:email:override-compatibility-check
```

変数の互換性に関する潜在的な問題について、メールテンプレートの上書きをスキャンします

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `dev:profiler:disable`

```bash
bin/magento dev:profiler:disable
```

プロファイラーを無効にします。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `dev:profiler:enable`

```bash
bin/magento dev:profiler:enable [<type>]
```

プロファイラーを有効にします。

### 引数

#### `type`

プロファイラータイプ

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `dev:query-log:disable`

```bash
bin/magento dev:query-log:disable
```

DB クエリログを無効にする

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `dev:query-log:enable`

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

DB クエリログを有効にする

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--include-all-queries`

すべてのクエリをログに記録します。 [true\|false]

- 既定：`true`
- 値を受け入れる

#### `--query-time-threshold`

クエリ時間のしきい値：

- 既定：`0.001`
- 値を受け入れる

#### `--include-call-stack`

コールスタックを含めます。 [true\|false]

- 既定：`true`
- 値を受け入れる


## `dev:source-theme:deploy`

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

テーマのソースファイルを収集して公開します。

### 引数

#### `file`

前処理するファイル（拡張子なしで指定する必要があります）

- 既定：`css/styles-mcss/styles-l`

- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--type`

ソースファイルの種類：[より少ない]

- 既定：`less`
- 値が必要です

#### `--locale`

ロケール：[en_US]

- 既定：`en_US`
- 値が必要です

#### `--area`

領域：[frontend\|adminhtml]

- 既定：`frontend`
- 値が必要です

#### `--theme`

テーマ：[ ベンダー/テーマ ]

- 既定：`Magento/luma`
- 値が必要です


## `dev:template-hints:disable`

```bash
bin/magento dev:template-hints:disable
```

フロントエンドテンプレートヒントを無効にします。 キャッシュフラッシュが必要な場合があります。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `dev:template-hints:enable`

```bash
bin/magento dev:template-hints:enable
```

フロントエンドテンプレートヒントを有効にします。 キャッシュフラッシュが必要な場合があります。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `dev:template-hints:status`

```bash
bin/magento dev:template-hints:status
```

フロントエンドテンプレートヒントのステータスを表示します。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `dev:tests:run`

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

テストの実行

### 引数

#### `type`

実行するテストのタイプ。 使用可能なタイプ：all、unit、integration、integration-all、static、static-all、integrity、legacy、default

- 既定：`default`

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--arguments`, `-c`

PHPUnitの追加引数。 例：&quot;-c&#39;—filter=MyTest&#39;&quot; （スペースなし）

- デフォルト：&quot;
- 値が必要です


## `dev:urn-catalog:generate`

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

IDEでXMLをハイライト表示するための*.xsd マッピングへのURN カタログを生成します。

### 引数

#### `path`

カタログを出力するファイルへのパス。 PhpStormの場合は、.idea/misc.xmlを使用します。

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--ide`

カタログを生成する形式。 サポート対象：[phpstorm, vscode]

- 既定：`phpstorm`
- 値が必要です


## `dev:xml:convert`

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

XSL スタイルシートを使用してXML ファイルを変換

### 引数

#### `xml-file`

変換するXML ファイルへのパス

- 必須


#### `processor`

XML ファイルに適用されるXSL スタイルシートへのパス

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--overwrite`, `-o`

XML ファイルを上書き

- 既定：`false`
- 値を受け付けません


## `downloadable:domains:add`

```bash
bin/magento downloadable:domains:add [<domains>...]
```

ダウンロード可能なドメインのホワイトリストへのドメインの追加

### 引数

#### `domains`

ドメイン名

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `downloadable:domains:remove`

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

ダウンロード可能なドメインのホワイトリストからドメインを削除する

### 引数

#### `domains`

ドメイン名

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `downloadable:domains:show`

```bash
bin/magento downloadable:domains:show
```

ダウンロード可能なドメインのホワイトリスト表示

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `encryption:data:list-re-encryptors`

```bash
bin/magento encryption:data:list-re-encryptors
```

使用可能なデータ再暗号化機能のリストを表示します。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `encryption:data:re-encrypt`

```bash
bin/magento encryption:data:re-encrypt [<encryptors>...]
```

現在の暗号化キーを使用して、暗号化されたデータを再暗号化します。

### 引数

#### `encryptors`

使用する再暗号化子のスペース区切りリスト。

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `encryption:key:change`

```bash
bin/magento encryption:key:change [-k|--key [KEY]]
```

env.php ファイル内の暗号化キーを変更します。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--key`, `-k`

キーは32文字の長い文字列である必要があります。 指定しない場合、ランダムなキーが生成されます。

- 値を受け入れる


## `encryption:payment-data:update`

```bash
bin/magento encryption:payment-data:update
```

最新の暗号化暗号で暗号化されたクレジットカードのデータを再暗号化します。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `events:create-event-provider`

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]events:provider:create 
```

このインスタンスのAdobe I/O Eventsでカスタムイベントプロバイダーを作成します。 ラベルと説明オプションを指定しない場合は、システム app/etc/event-types.json ファイルで定義する必要があります。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--label`

カスタムプロバイダーを定義するためのラベル。

- 値を受け入れる

#### `--description`

プロバイダーの説明。

- 値を受け入れる


## `events:generate:module`

```bash
bin/magento events:generate:module
```

プラグインリストに基づくモジュールの生成

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `events:info`

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```

指定したイベントのペイロードを返します。

### 引数

#### `event-code`

イベントコード

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--depth`

返すイベントペイロードのレベル数

- 既定：`2`
- 値を受け入れる


## `events:list`

```bash
bin/magento events:list
```

購読したイベントのリストを表示します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `events:list:all`

```bash
bin/magento events:list:all <module_name>
```

指定されたモジュールで定義された購読可能なイベントのリストを返します

### 引数

#### `module_name`

モジュール名

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `events:metadata:populate`

```bash
bin/magento events:metadata:populate
```

設定リスト（XMLおよびアプリケーション設定）からAdobe I/Oのメタデータを作成します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `events:provider:info`

```bash
bin/magento events:provider:info
```

設定されたイベントプロバイダーに関する詳細を返します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `events:registrations:list`

```bash
bin/magento events:registrations:list
```

App Builder プロジェクト内のイベント登録のリスト

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `events:subscribe`

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [-d|--destination DESTINATION] [--hipaaAuditRequired] [--] <event-code>
```

イベントの購読

### 引数

#### `event-code`

イベントコード

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--force`, `-f`

指定したイベントがローカルで定義されていなくても、強制的にサブスクライブされます。

- 既定：`false`
- 値を受け付けません

#### `--fields`

イベントデータペイロードのフィールドのリスト。

- 既定：`[]`
- 値が必要です

#### `--parent`

ルールまたはエイリアスを持つイベントサブスクリプションの親イベントコード。

- 値が必要です

#### `--rules`

イベント購読のルールのリスト。各ルールは「field\|operator\|value」としてフォーマットされます。 このオプションを使用するには、「親」オプションも指定する必要があります。

- 既定：`[]`
- 値が必要です

#### `--priority`, `-p`

このイベントの送信を迅速化します。 すぐに配信する必要があるイベントに対して、このオプションを指定します。 デフォルトでは、cronによって1分に1回イベントが送信されます。

- 既定：`false`
- 値を受け付けません

#### `--destination`, `-d`

このイベントの宛先。 カスタム宛先に配信するイベントに対して、このオプションを指定します。

- 既定：`default`
- 値が必要です

#### `--hipaaAuditRequired`

イベントにHIPAA監査の対象となるデータが含まれていることを示します。

- 既定：`false`
- 値を受け付けません


## `events:sync-events-metadata`

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

このインスタンスのイベントメタデータの同期

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--delete`, `-d`

イベントのメタデータの削除は不要になりました

- 既定：`false`
- 値を受け付けません


## `events:unsubscribe`

```bash
bin/magento events:unsubscribe <event-code>
```

指定されたイベントへのサブスクリプションを削除します

### 引数

#### `event-code`

登録解除するイベントコード

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `i18n:collect-phrases`

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

コードベース内のフレーズを見つける

### 引数

#### `directory`

解析するディレクトリパス。 —magento フラグが設定されている場合は不要

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--output`, `-o`

出力ファイルへのパス（ファイル名を含む）。 ファイルを指定しない場合、デフォルトはstdoutになります。

- 値が必要です

#### `--magento`, `-m`

—magento パラメーターを使用して、現在のMagento コードベースを解析します。 ディレクトリが指定されている場合は、パラメーターを省略します。

- 既定：`false`
- 値を受け付けません


## `i18n:pack`

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

言語パッケージを保存

### 引数

#### `source`

翻訳付きソースディクショナリファイルへのパス

- 必須


#### `locale`

辞書のターゲットロケール （例：「de_DE」）

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--mode`, `-m`

辞書の保存モード – 「置換」 – 言語パックを新しいものに置き換える – 「結合」 – デフォルトで「置換」する言語パッケージを結合

- 既定：`replace`
- 値が必要です

#### `--allow-duplicates`, `-d`

—allow-duplicates パラメーターを使用すると、翻訳の重複を保存できます。 それ以外の場合はパラメーターを省略します。

- 既定：`false`
- 値を受け付けません


## `i18n:uninstall`

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

言語パッケージのアンインストール

### 引数

#### `package`

言語パッケージ名

- 既定：`[]`
- 必須

- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--backup-code`, `-b`

コードと設定ファイルのバックアップを作成（一時ファイルを除く）

- 既定：`false`
- 値を受け付けません


## `indexer:info`

```bash
bin/magento indexer:info
```

許可されたインデクサーを表示

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `indexer:reindex`

```bash
bin/magento indexer:reindex [<index>...]
```

データのインデックス再作成

### 引数

#### `index`

すべてのインデックスに適用するインデックスタイプまたは省略のスペース区切りリスト。

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `indexer:reset`

```bash
bin/magento indexer:reset [<index>...]
```

インデクサーステータスを無効にリセットします

### 引数

#### `index`

すべてのインデックスに適用するインデックスタイプまたは省略のスペース区切りリスト。

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `indexer:set-dimensions-mode`

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

インデクサーディメンションモードの設定

### 引数

#### `indexer`

インデクサー名[catalog_product_price|catalogpermissions_category]


#### `mode`

インデクサーディメンションモード catalog_product_price          none,website,customer_group,website_and_customer_group catalogpermissions_category    none,customer_group

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `indexer:set-mode`

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

インデックスモードタイプを設定します

### 引数

#### `mode`

インデクサーモードの種類[ リアルタイム|スケジュール ]


#### `index`

すべてのインデックスに適用するインデックスタイプまたは省略のスペース区切りリスト。

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `indexer:set-status`

```bash
bin/magento indexer:set-status <status> [<index>...]
```

指定したインデクサーステータスを設定します

### 引数

#### `status`

インデクサーの状態タイプ [無効|一時停止|有効]

- 必須


#### `index`

すべてのインデックスに適用するインデックスタイプまたは省略のスペース区切りリスト。

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `indexer:show-dimensions-mode`

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

インデクサーのDimension モードを表示

### 引数

#### `indexer`

索引タイプのスペース区切りリストまたはすべての索引に適用する省略（catalog_product_price、catalogpermissions_category）

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `indexer:show-mode`

```bash
bin/magento indexer:show-mode [<index>...]
```

索引モードを表示

### 引数

#### `index`

すべてのインデックスに適用するインデックスタイプまたは省略のスペース区切りリスト。

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `indexer:status`

```bash
bin/magento indexer:status [<index>...]
```

インデクサーのステータスを表示

### 引数

#### `index`

すべてのインデックスに適用するインデックスタイプまたは省略のスペース区切りリスト。

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `info:adminuri`

```bash
bin/magento info:adminuri
```

Magento管理者URIを表示します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `info:backups:list`

```bash
bin/magento info:backups:list
```

使用可能なバックアップファイルのリストを印刷

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `info:currency:list`

```bash
bin/magento info:currency:list
```

使用可能な通貨のリストを表示します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `info:dependencies:show-framework`

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

Magento frameworkへの依存関係の数を表示します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--output`, `-o`

レポートファイル名

- 既定：`framework-dependencies.csv`
- 値が必要です


## `info:dependencies:show-modules`

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

モジュール間の依存関係の数を表示します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--output`, `-o`

レポートファイル名

- 既定：`modules-dependencies.csv`
- 値が必要です


## `info:dependencies:show-modules-circular`

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

モジュール間の循環依存関係の数を表示します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--output`, `-o`

レポートファイル名

- 既定：`modules-circular-dependencies.csv`
- 値が必要です


## `info:language:list`

```bash
bin/magento info:language:list
```

使用可能な言語ロケールのリストを表示します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `info:timezone:list`

```bash
bin/magento info:timezone:list
```

使用可能なタイムゾーンのリストを表示します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `inventory:reservation:create-compensations`

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

指定された補償引数による予約の作成

### 引数

#### `compensations`

形式「:::」の補償引数のリスト

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--raw`, `-r`

Raw出力

- 既定：`false`
- 値を受け付けません


## `inventory:reservation:list-inconsistencies`

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

販売可能な数量の不整合を伴うすべての注文と製品を表示します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--complete-orders`, `-c`

完了した注文の不整合のみを表示

- 既定：`false`
- 値を受け付けません

#### `--incomplete-orders`, `-i`

不完全な注文の不整合のみを表示

- 既定：`false`
- 値を受け付けません

#### `--bunch-size`, `-b`

一度にロードされる注文数を定義します

- 既定：`50`
- 値を受け入れる

#### `--raw`, `-r`

Raw出力

- 既定：`false`
- 値を受け付けません


## `inventory-geonames:import`

```bash
bin/magento inventory-geonames:import <countries>...
```

ソース選択アルゴリズムの地理名のダウンロードと読み込み

### 引数

#### `countries`

インポートする国コードのリスト

- 既定：`[]`
- 必須

- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `maintenance:allow-ips`

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

メンテナンスモードの除外IPを設定します

### 引数

#### `ip`

許可されたIP アドレス

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--none`

許可されたIP アドレスをクリア

- 既定：`false`
- 値を受け付けません

#### `--add`

既存のリストにIP アドレスを追加する

- 既定：`false`
- 値を受け付けません

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `maintenance:disable`

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

メンテナンスモードを無効にします

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--ip`

許可されたIP アドレス （許可されたIP リストをクリアするには「なし」を使用）

- 既定：`[]`
- 値が必要です

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `maintenance:enable`

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

メンテナンスモードを有効にします

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--ip`

許可されたIP アドレス （許可されたIP リストをクリアするには「なし」を使用）

- 既定：`[]`
- 値が必要です

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `maintenance:status`

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

メンテナンスモードのステータスを表示

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `media-content:sync`

```bash
bin/magento media-content:sync
```

コンテンツとアセットの同期

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `media-gallery:sync`

```bash
bin/magento media-gallery:sync
```

データベース内のメディア ストレージとメディア アセットの同期

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `module:config:status`

```bash
bin/magento module:config:status
```

「app/etc/config.php」ファイルのモジュール設定を確認し、モジュールが最新であるかどうかをレポートします

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `module:disable`

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

指定したモジュールを無効にする

### 引数

#### `module`

モジュールの名前

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--force`, `-f`

依存関係チェックのバイパス

- 既定：`false`
- 値を受け付けません

#### `--all`

すべてのモジュールを無効にする

- 既定：`false`
- 値を受け付けません

#### `--clear-static-content`, `-c`

生成された静的ビューファイルをクリアします。 必要。モジュールに静的ビューファイルがある場合

- 既定：`false`
- 値を受け付けません

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `module:enable`

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

指定したモジュールを有効にします

### 引数

#### `module`

モジュールの名前

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--force`, `-f`

依存関係チェックのバイパス

- 既定：`false`
- 値を受け付けません

#### `--all`

すべてのモジュールを有効化

- 既定：`false`
- 値を受け付けません

#### `--clear-static-content`, `-c`

生成された静的ビューファイルをクリアします。 必要。モジュールに静的ビューファイルがある場合

- 既定：`false`
- 値を受け付けません

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `module:status`

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

モジュールのステータスを表示

### 引数

#### `module-names`

オプションのモジュール名

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--enabled`

有効なモジュールのみを印刷

- 既定：`false`
- 値を受け付けません

#### `--disabled`

無効なモジュールのみを印刷

- 既定：`false`
- 値を受け付けません

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `module:uninstall`

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

Composerによってインストールされたモジュールをアンインストールします

### 引数

#### `module`

モジュールの名前

- 既定：`[]`
- 必須

- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--remove-data`, `-r`

モジュールによってインストールされたデータの削除

- 既定：`false`
- 値を受け付けません

#### `--backup-code`

コードと設定ファイルのバックアップを作成（一時ファイルを除く）

- 既定：`false`
- 値を受け付けません

#### `--backup-media`

メディアバックアップを作成

- 既定：`false`
- 値を受け付けません

#### `--backup-db`

データベースの完全なバックアップを実行

- 既定：`false`
- 値を受け付けません

#### `--non-composer`

ここで過ぎると思われるすべてのモジュールは、コンポーザーベースではありません

- 既定：`false`
- 値を受け付けません

#### `--clear-static-content`, `-c`

生成された静的ビューファイルをクリアします。 必要。モジュールに静的ビューファイルがある場合

- 既定：`false`
- 値を受け付けません

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `newrelic:create:deploy-marker`

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

エントリのデプロイキューを確認し、適切なデプロイマーカーを作成します。

### 引数

#### `message`

メッセージを展開しますか？

- 必須


#### `change_log`

ログを変更しますか？

- 必須


#### `user`

デプロイメントユーザー


#### `revision`

リビジョン

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `queue:consumers:list`

```bash
bin/magento queue:consumers:list
```

MessageQueue コンシューマーのリスト

```
This command shows list of MessageQueue consumers.
```

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `queue:consumers:restart`

```bash
bin/magento queue:consumers:restart
```

MessageQueue コンシューマーの再起動

```
Command put poison pill for MessageQueue consumers and force to restart them after next status check.
```

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `queue:consumers:start`

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

MessageQueue コンシューマーの開始

```
This command starts MessageQueue consumer by its name.

To start consumer which will process all queued messages and terminate execution:

    bin/magento queue:consumers:start someConsumer

To specify the number of messages which should be processed by consumer before its termination:

    bin/magento queue:consumers:start someConsumer --max-messages=50

To specify the number of messages per batch for the batch consumer:

    bin/magento queue:consumers:start someConsumer --batch-size=500

To specify the preferred area:

    bin/magento queue:consumers:start someConsumer --area-code='adminhtml'

To do not run multiple copies of one consumer simultaneously:

    bin/magento queue:consumers:start someConsumer --single-thread

To save PID enter path (This option is deprecated, use --single-thread instead):

    bin/magento queue:consumers:start someConsumer --pid-file-path='/var/someConsumer.pid'

To define the number of processes per consumer:

    bin/magento queue:consumers:start someConsumer --multi-process=4
```

### 引数

#### `consumer`

開始するコンシューマーの名前。

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--max-messages`

処理終了前に消費者が処理するメッセージの数。 指定しない場合 – キューに入れたすべてのメッセージを処理した後に終了します。

- 値が必要です

#### `--batch-size`

バッチあたりのメッセージ数。 バッチコンシューマーにのみ適用できます。

- 値が必要です

#### `--area-code`

好ましい領域（グローバル、adminhtmlなど）のデフォルトはグローバルです。

- 値が必要です

#### `--single-thread`

このオプションは、1つのコンシューマーの複数のコピーを同時に実行することを防ぎます。

- 既定：`false`
- 値を受け付けません

#### `--multi-process`

コンシューマーあたりのプロセス数。

- 値を受け入れる

#### `--pid-file-path`

PIDを保存するためのファイルパス （このオプションは非推奨です。代わりに – single-threadを使用してください）

- 値が必要です


## `remote-storage:sync`

```bash
bin/magento remote-storage:sync
```

メディアファイルをリモートストレージと同期します。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `saas:resync`

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync] [--by-ids BY-IDS] [--id-type ID-TYPE]
```

SaaS サービスにフィードデータを再同期します。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--feed`

名前をフィードして、SaaS サービスに完全に再同期します。 利用可能なフィード：決済サービス注文生産、決済サービス注文サンドボックス、決済サービス注文状態生産、決済サービス注文状況サンドボックス、決済サービスストア生産、決済サービスストアのサンドボックス

- 値が必要です

#### `--no-reindex`

フィード データの再送信をSaaS サービスにのみ実行します。 インデックスを再作成しません。 （このオプションは、製品、製品オーバーライド、価格フィードには適用されません）

- 既定：`false`
- 値を受け付けません

#### `--cleanup-feed`

同期する前にフィード インデクサーテーブルをクリーンアップする必要があります。

- 既定：`false`
- 値を受け付けません

#### `--dry-run`

ドライラン。 データは書き出されません。 ペイロードをログファイル var/log/saas-export.logに保存するには、環境変数EXPORTER_EXTENDED_LOG=1で実行します。

- 既定：`false`
- 値を受け付けません

#### `--thread-count`

同期スレッド数を設定します。

- 値が必要です

#### `--batch-size`

同期バッチサイズの設定

- 値が必要です

#### `--continue-resync`

最後に保存した位置から再同期を続行します（このオプションは、製品、製品オーバーライド、価格フィードに適用されます）

- 既定：`false`
- 値を受け付けません

#### `--by-ids`

指定された識別子のリストによって部分的に再同期します。 （このオプションは、製品、製品オーバーライド、価格フィードに適用されます）

- 値が必要です

#### `--id-type`

部分再同期の識別子のタイプ （例：sku、productIdなど）

- 値が必要です


## `sampledata:deploy`

```bash
bin/magento sampledata:deploy [--no-update]
```

コンポーザベースのMagento インストール用のサンプルデータモジュールのデプロイ

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--no-update`

コンポーザー更新を実行せずにcomposer.jsonを更新する

- 既定：`false`
- 値を受け付けません


## `sampledata:remove`

```bash
bin/magento sampledata:remove [--no-update]
```

composer.jsonからすべてのサンプルデータパッケージを削除する

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--no-update`

コンポーザー更新を実行せずにcomposer.jsonを更新する

- 既定：`false`
- 値を受け付けません


## `sampledata:reset`

```bash
bin/magento sampledata:reset
```

再インストール用にすべてのサンプルデータモジュールをリセット

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `security:recaptcha:disable-for-user-forgot-password`

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

管理者ユーザーがパスワードフォームを忘れた場合のreCAPTCHAの無効化

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `security:recaptcha:disable-for-user-login`

```bash
bin/magento security:recaptcha:disable-for-user-login
```

管理者ユーザーログインフォームのreCAPTCHAを無効にする

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `security:tfa:google:set-secret`

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

Google OTPの生成に使用するシークレットを設定します。

### 引数

#### `user`

ユーザー名

- 必須


#### `secret`

秘密鍵

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `security:tfa:providers`

```bash
bin/magento security:tfa:providers
```

利用可能なプロバイダーをすべて一覧表示

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `security:tfa:reset`

```bash
bin/magento security:tfa:reset <user> <provider>
```

1人のユーザーの設定をリセット

### 引数

#### `user`

ユーザー名

- 必須


#### `provider`

プロバイダーコード

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `server:run`

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-wn|--workerNum [WORKERNUM]] [-dm|--dispatchMode [DISPATCHMODE]] [-mr|--maxRequests [MAXREQUESTS]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]] [-mwt|--maxWaitTime [MAXWAITTIME]] [--state-monitor]
```

アプリケーションサーバーの実行

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--port`, `-p`

ポートからサービスを提供する

- 既定：`9501`
- 値を受け入れる

#### `--background`, `-b`

背景モードフラグ

- 既定：`0`
- 値を受け入れる

#### `--workerNum`, `-wn`

開始するワーカープロセスの数

- 既定：`4`
- 値を受け入れる

#### `--dispatchMode`, `-dm`

ワーカープロセスへの接続をディスパッチするモード

- 既定：`3`
- 値を受け入れる

#### `--maxRequests`, `-mr`

ワーカープロセスを再開する前の最大要求

- 既定：`10000`
- 値を受け入れる

#### `--area`, `-a`

アプリケーションサーバー領域

- 既定：`graphql`
- 値を受け入れる

#### `--magento-init-params`, `-mip`

magento bootstrap init パラメーター

- デフォルト：&quot;
- 値を受け入れる

#### `--maxWaitTime`, `-mwt`

リロード後のワーカーの待機時間（例： config change）を押す前に

- 既定：`3600`
- 値を受け入れる

#### `--state-monitor`

状態監視を有効にします。 状態の問題のデバッグにのみ使用してください。

- 既定：`false`
- 値を受け付けません


## `server:state-monitor:aggregate-output`

```bash
bin/magento server:state-monitor:aggregate-output
```

ApplicationServerの状態モニターからの出力を集計します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `setup:backup`

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Magento アプリケーションのコードベース、メディア、データベースのバックアップを取ります

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--code`

コードと設定ファイルのバックアップを作成（一時ファイルを除く）

- 既定：`false`
- 値を受け付けません

#### `--media`

メディアバックアップを作成

- 既定：`false`
- 値を受け付けません

#### `--db`

データベースの完全なバックアップを実行

- 既定：`false`
- 値を受け付けません

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `setup:config:set`

```bash
bin/magento setup:config:set [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

デプロイメント設定を作成または変更します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--remote-storage-driver`

リモートストレージドライバー

- 値が必要です

#### `--remote-storage-prefix`

リモートストレージのプレフィックス

- デフォルト：&quot;
- 値が必要です

#### `--remote-storage-endpoint`

リモートストレージエンドポイント

- 値が必要です

#### `--remote-storage-bucket`

リモートストレージバケット

- 値が必要です

#### `--remote-storage-region`

リモートストレージ領域

- 値が必要です

#### `--remote-storage-key`

リモートストレージアクセスキー

- デフォルト：&quot;
- 値が必要です

#### `--remote-storage-secret`

リモートストレージ秘密鍵

- デフォルト：&quot;
- 値が必要です

#### `--remote-storage-path-style`

リモートストレージパスのスタイル

- 既定：`0`
- 値が必要です

#### `--backend-frontname`

バックエンドのfrontname （見つからない場合は自動生成されます）

- 値が必要です

#### `--enable-debug-logging`

デバッグログを有効にする

- 値が必要です

#### `--enable-syslog-logging`

syslog ログを有効にする

- 値が必要です

#### `--id_salt`

GraphQl Salt

- 値が必要です

#### `--checkout-async`

非同期注文処理を有効にする 1 – はい、0 – いいえ

- 値が必要です

#### `--config-async`

非同期管理設定の保存を有効にする 1 – はい、0 – いいえ

- 値が必要です

#### `--amqp-host`

Amqp サーバーホスト

- デフォルト：&quot;
- 値が必要です

#### `--amqp-port`

Amqp サーバーポート

- 既定：`5672`
- 値が必要です

#### `--amqp-user`

Amqp サーバーのユーザー名

- デフォルト：&quot;
- 値が必要です

#### `--amqp-password`

Amqp サーバーのパスワード

- デフォルト：&quot;
- 値が必要です

#### `--amqp-virtualhost`

Amqp virtualhost

- 既定：`/`
- 値が必要です

#### `--amqp-ssl`

Amqp SSL

- デフォルト：&quot;
- 値が必要です

#### `--amqp-ssl-options`

Amqp SSL オプション（JSON）

- デフォルト：&quot;
- 値が必要です

#### `--consumers-wait-for-messages`

消費者はキューからのメッセージを待つべきですか？ 1 – はい、0 – いいえ

- 値が必要です

#### `--queue-default-connection`

メッセージキューはデフォルトの接続をキューに入れます。 「db」、「amqp」またはカスタムキューシステムを指定できます。キューシステムをインストールして設定する必要があります。そうしないと、メッセージが正しく処理されません。

- 値が必要です

#### `--deferred-total-calculating`

遅延合計計算を有効にしますか？ 1 – はい、0 – いいえ

- 値が必要です

#### `--key`

暗号化キー

- 値が必要です

#### `--db-host`

データベースサーバーホスト

- 値が必要です

#### `--db-name`

データベース名

- 値が必要です

#### `--db-user`

データベースサーバーのユーザー名

- 値が必要です

#### `--db-engine`

データベースサーバーエンジン

- 値が必要です

#### `--db-password`

データベースサーバーのパスワード

- 値が必要です

#### `--db-prefix`

データベーステーブルの接頭辞

- 値が必要です

#### `--db-model`

データベースの種類

- 値が必要です

#### `--db-init-statements`

データベースの最初のコマンド セット

- 値が必要です

#### `--skip-db-validation`, `-s`

指定した場合、db接続検証はスキップされます

- 既定：`false`
- 値を受け付けません

#### `--http-cache-hosts`

http Cache ホスト

- 値が必要です

#### `--db-ssl-key`

SSLを介したdb接続を確立するためのクライアントキーファイルのフルパス

- デフォルト：&quot;
- 値が必要です

#### `--db-ssl-cert`

SSLを介したdb接続を確立するためのクライアント証明書ファイルのフルパス

- デフォルト：&quot;
- 値が必要です

#### `--db-ssl-ca`

SSLを介したdb接続を確立するためのサーバー証明書ファイルのフルパス

- デフォルト：&quot;
- 値が必要です

#### `--db-ssl-verify`

サーバー証明書の確認

- 既定：`false`
- 値を受け付けません

#### `--session-save`

セッション保存ハンドラー

- 値が必要です

#### `--session-save-redis-host`

UNIX ソケットを使用する場合は、完全修飾ホスト名、IP アドレス、または絶対パス

- 値が必要です

#### `--session-save-redis-port`

Redis サーバーのリッスン ポート

- 値が必要です

#### `--session-save-redis-password`

Redis サーバーパスワード

- 値が必要です

#### `--session-save-redis-timeout`

接続タイムアウト （秒）

- 値が必要です

#### `--session-save-redis-retries`

Redis接続の再試行。

- 値が必要です

#### `--session-save-redis-persistent-id`

永続的な接続を有効にする一意の文字列

- 値が必要です

#### `--session-save-redis-db`

Redis データベース番号

- 値が必要です

#### `--session-save-redis-compression-threshold`

Redis圧縮しきい値

- 値が必要です

#### `--session-save-redis-compression-lib`

Redis圧縮ライブラリ 値：gzip （デフォルト）、lzf、lz4、snappy

- 値が必要です

#### `--session-save-redis-log-level`

Redis ログレベル。 値：0 （最小冗長）から7 （最も冗長）

- 値が必要です

#### `--session-save-redis-max-concurrency`

1つのセッションでロックを待機できるプロセスの最大数

- 値が必要です

#### `--session-save-redis-break-after-frontend`

フロントエンドセッションのロックを解除する前に待機する秒数

- 値が必要です

#### `--session-save-redis-break-after-adminhtml`

管理者セッションのロックを解除する前に待機する秒数

- 値が必要です

#### `--session-save-redis-first-lifetime`

最初の書き込み時の非ボットのセッションの有効期間（秒単位）（無効にするには0を使用）

- 値が必要です

#### `--session-save-redis-bot-first-lifetime`

最初の書き込み時のボットのセッションの有効期間（秒単位）（無効にするには0を使用）

- 値が必要です

#### `--session-save-redis-bot-lifetime`

後続の書き込み時のボットのセッションの有効期間（無効にするには0を使用）

- 値が必要です

#### `--session-save-redis-disable-locking`

Redisはロックを無効にします。 値：false （デフォルト）、true

- 値が必要です

#### `--session-save-redis-min-lifetime`

Redis最小セッション有効期間（秒）

- 値が必要です

#### `--session-save-redis-max-lifetime`

Redis最大セッション有効期間（秒単位）

- 値が必要です

#### `--session-save-redis-sentinel-master`

Redis Sentinel マスター

- 値が必要です

#### `--session-save-redis-sentinel-servers`

Redis Sentinel サーバー、コンマ区切り

- 値が必要です

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel検証マスター。 値：false （デフォルト）、true

- 値が必要です

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel接続の再試行。

- 値が必要です

#### `--cache-backend`

デフォルトのキャッシュハンドラー

- 値が必要です

#### `--cache-backend-redis-server`

Redis サーバー

- 値が必要です

#### `--cache-backend-redis-db`

キャッシュのデータベース番号

- 値が必要です

#### `--cache-backend-redis-port`

Redis サーバーのリッスン ポート

- 値が必要です

#### `--cache-backend-redis-password`

Redis サーバーパスワード

- 値が必要です

#### `--cache-backend-redis-compress-data`

圧縮を無効にするには0に設定します（デフォルトは1、有効）

- 値が必要です

#### `--cache-backend-redis-compression-lib`

[snappy,lzf,l4z,zstd,gzip]を使用する圧縮ライブラリ（自動的に決定するには空白のままにする）

- 値が必要です

#### `--cache-backend-redis-use-lua`

luaを有効にするには1に設定します（デフォルトは0、無効）

- 値が必要です

#### `--cache-backend-redis-use-lua-on-gc`

ガベージコレクションでLUAを無効にするには0に設定します（デフォルトは1、有効）

- 値が必要です

#### `--cache-id-prefix`

キャッシュキーのID プレフィックス

- 値が必要です

#### `--allow-parallel-generation`

ブロックしない方法でのキャッシュ生成を許可

- 既定：`false`
- 値を受け付けません

#### `--page-cache`

デフォルトのキャッシュハンドラー

- 値が必要です

#### `--page-cache-redis-server`

Redis サーバー

- 値が必要です

#### `--page-cache-redis-db`

キャッシュのデータベース番号

- 値が必要です

#### `--page-cache-redis-port`

Redis サーバーのリッスン ポート

- 値が必要です

#### `--page-cache-redis-password`

Redis サーバーパスワード

- 値が必要です

#### `--page-cache-redis-compress-data`

ページ全体のキャッシュを圧縮するには1に設定します（無効にするには0を使用します）

- 値が必要です

#### `--page-cache-redis-compression-lib`

[snappy,lzf,l4z,zstd,gzip]を使用する圧縮ライブラリ （自動的に決定するには空白のままにします）

- 値が必要です

#### `--page-cache-id-prefix`

キャッシュキーのID プレフィックス

- 値が必要です

#### `--lock-provider`

プロバイダー名をロック

- 値が必要です

#### `--lock-db-prefix`

ロックの競合を避けるためのインストール固有のロック接頭辞

- 値が必要です

#### `--lock-zookeeper-host`

Zookeeper クラスターに接続するためのホストとポート。 例：127.0.0.1:2181

- 値が必要です

#### `--lock-zookeeper-path`

Zookeeperがロックを保存するパス。 デフォルトのパスは/magento/locksです。

- 値が必要です

#### `--lock-file-path`

ファイルロックが保存されるパス。

- 値が必要です

#### `--document-root-is-pub`

表示するフラグは、Pubがルート上にあることであり、trueまたはfalseのみ可能です

- 値が必要です

#### `--backpressure-logger`

バックプレッシャーロガーハンドラー

- 値が必要です

#### `--backpressure-logger-redis-server`

Redis サーバー

- 値が必要です

#### `--backpressure-logger-redis-port`

Redis サーバーのリッスン ポート

- 値が必要です

#### `--backpressure-logger-redis-timeout`

Redis サーバーのタイムアウト

- 値が必要です

#### `--backpressure-logger-redis-persistent`

Redis persistent

- 値が必要です

#### `--backpressure-logger-redis-db`

Redis DB番号

- 値が必要です

#### `--backpressure-logger-redis-password`

Redis サーバーパスワード

- 値が必要です

#### `--backpressure-logger-redis-user`

Redis サーバーユーザー

- 値が必要です

#### `--backpressure-logger-id-prefix`

キーのID プレフィックス

- 値が必要です

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `setup:db-data:upgrade`

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

DB内のデータのインストールとアップグレード

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `setup:db-declaration:generate-patch`

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

パッチを生成し、特定のフォルダーに配置します。

### 引数

#### `module`

モジュール名

- 必須


#### `patch`

パッチ名

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--revertable`

パッチが元に戻せるかどうかを確認します。

- 既定：`false`
- 値を受け入れる

#### `--type`

どのようなパッチを生成すべきかを調べます。 使用可能な値：`data`、`schema`。

- 既定：`data`
- 値を受け入れる


## `setup:db-declaration:generate-whitelist`

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

宣言インストーラーで編集できるテーブルと列のホワイトリストを生成します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--module-name`

ホワイトリストが生成されるモジュールの名前

- 既定：`all`
- 値を受け入れる


## `setup:db-schema:add-slave`

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

チェックアウト見積もり関連テーブルを別のDB サーバーに移動する

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--host`

スレーブ DB サーバーホスト

- 既定：`localhost`
- 値が必要です

#### `--dbname`

スレーブデータベース名

- 値が必要です

#### `--username`

スレーブ DBのユーザー名

- 既定：`root`
- 値が必要です

#### `--password`

スレーブ DB ユーザーパスワード

- 値を受け入れる

#### `--connection`

スレーブ接続名

- 既定：`default`
- 値を受け入れる

#### `--resource`

スレーブリソース名

- 既定：`default`
- 値を受け入れる

#### `--maxAllowedLag`

最大許可ラグ スレーブ接続（秒単位）

- デフォルト：&quot;
- 値を受け入れる

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `setup:db-schema:split-quote`

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

チェックアウト見積もり関連テーブルを別のDB サーバーに移動します。 2.4.2以降で非推奨（廃止予定）となり、削除されます

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--host`

チェックアウト DB Server ホスト

- 値が必要です

#### `--dbname`

チェックアウト データベース名

- 値が必要です

#### `--username`

チェックアウト DB ユーザー名

- 値が必要です

#### `--password`

チェックアウト DB ユーザーパスワード

- 値を受け入れる

#### `--connection`

チェックアウト接続名

- 既定：`checkout`
- 値を受け入れる

#### `--resource`

チェックアウトリソース名

- 既定：`checkout`
- 値を受け入れる

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `setup:db-schema:split-sales`

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

セールス関連テーブルを別のDB サーバーに移動します。 2.4.2以降で非推奨（廃止予定）となり、削除されます

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--host`

Sales DB Server ホスト

- 値が必要です

#### `--dbname`

営業データベース名

- 値が必要です

#### `--username`

Sales DB ユーザー名

- 値が必要です

#### `--password`

Sales DB ユーザーパスワード

- 値を受け入れる

#### `--connection`

セールス接続名

- 既定：`sales`
- 値を受け入れる

#### `--resource`

セールスリソース名

- 既定：`sales`
- 値を受け入れる

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `setup:db-schema:upgrade`

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

DB スキーマのインストールとアップグレード

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--convert-old-scripts`

古いスクリプト （InstallSchema、UpgradeSchema）をdb_schema.xml形式に変換できます

- 既定：`false`
- 値を受け入れる

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `setup:db:status`

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

DB スキーマまたはデータをアップグレードする必要があるかどうかを確認します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `setup:di:compile`

```bash
bin/magento setup:di:compile
```

DI設定と、自動生成可能なすべての欠落クラスを生成します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `setup:install`

```bash
bin/magento setup:install [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Magento アプリケーションをインストールします

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--remote-storage-driver`

リモートストレージドライバー

- 値が必要です

#### `--remote-storage-prefix`

リモートストレージのプレフィックス

- デフォルト：&quot;
- 値が必要です

#### `--remote-storage-endpoint`

リモートストレージエンドポイント

- 値が必要です

#### `--remote-storage-bucket`

リモートストレージバケット

- 値が必要です

#### `--remote-storage-region`

リモートストレージ領域

- 値が必要です

#### `--remote-storage-key`

リモートストレージアクセスキー

- デフォルト：&quot;
- 値が必要です

#### `--remote-storage-secret`

リモートストレージ秘密鍵

- デフォルト：&quot;
- 値が必要です

#### `--remote-storage-path-style`

リモートストレージパスのスタイル

- 既定：`0`
- 値が必要です

#### `--backend-frontname`

バックエンドのfrontname （見つからない場合は自動生成されます）

- 値が必要です

#### `--enable-debug-logging`

デバッグログを有効にする

- 値が必要です

#### `--enable-syslog-logging`

syslog ログを有効にする

- 値が必要です

#### `--id_salt`

GraphQl Salt

- 値が必要です

#### `--checkout-async`

非同期注文処理を有効にする 1 – はい、0 – いいえ

- 値が必要です

#### `--config-async`

非同期管理設定の保存を有効にする 1 – はい、0 – いいえ

- 値が必要です

#### `--amqp-host`

Amqp サーバーホスト

- デフォルト：&quot;
- 値が必要です

#### `--amqp-port`

Amqp サーバーポート

- 既定：`5672`
- 値が必要です

#### `--amqp-user`

Amqp サーバーのユーザー名

- デフォルト：&quot;
- 値が必要です

#### `--amqp-password`

Amqp サーバーのパスワード

- デフォルト：&quot;
- 値が必要です

#### `--amqp-virtualhost`

Amqp virtualhost

- 既定：`/`
- 値が必要です

#### `--amqp-ssl`

Amqp SSL

- デフォルト：&quot;
- 値が必要です

#### `--amqp-ssl-options`

Amqp SSL オプション（JSON）

- デフォルト：&quot;
- 値が必要です

#### `--consumers-wait-for-messages`

消費者はキューからのメッセージを待つべきですか？ 1 – はい、0 – いいえ

- 値が必要です

#### `--queue-default-connection`

メッセージキューはデフォルトの接続をキューに入れます。 「db」、「amqp」またはカスタムキューシステムを指定できます。キューシステムをインストールして設定する必要があります。そうしないと、メッセージが正しく処理されません。

- 値が必要です

#### `--deferred-total-calculating`

遅延合計計算を有効にしますか？ 1 – はい、0 – いいえ

- 値が必要です

#### `--key`

暗号化キー

- 値が必要です

#### `--db-host`

データベースサーバーホスト

- 値が必要です

#### `--db-name`

データベース名

- 値が必要です

#### `--db-user`

データベースサーバーのユーザー名

- 値が必要です

#### `--db-engine`

データベースサーバーエンジン

- 値が必要です

#### `--db-password`

データベースサーバーのパスワード

- 値が必要です

#### `--db-prefix`

データベーステーブルの接頭辞

- 値が必要です

#### `--db-model`

データベースの種類

- 値が必要です

#### `--db-init-statements`

データベースの最初のコマンド セット

- 値が必要です

#### `--skip-db-validation`, `-s`

指定した場合、db接続検証はスキップされます

- 既定：`false`
- 値を受け付けません

#### `--http-cache-hosts`

http Cache ホスト

- 値が必要です

#### `--db-ssl-key`

SSLを介したdb接続を確立するためのクライアントキーファイルのフルパス

- デフォルト：&quot;
- 値が必要です

#### `--db-ssl-cert`

SSLを介したdb接続を確立するためのクライアント証明書ファイルのフルパス

- デフォルト：&quot;
- 値が必要です

#### `--db-ssl-ca`

SSLを介したdb接続を確立するためのサーバー証明書ファイルのフルパス

- デフォルト：&quot;
- 値が必要です

#### `--db-ssl-verify`

サーバー証明書の確認

- 既定：`false`
- 値を受け付けません

#### `--session-save`

セッション保存ハンドラー

- 値が必要です

#### `--session-save-redis-host`

UNIX ソケットを使用する場合は、完全修飾ホスト名、IP アドレス、または絶対パス

- 値が必要です

#### `--session-save-redis-port`

Redis サーバーのリッスン ポート

- 値が必要です

#### `--session-save-redis-password`

Redis サーバーパスワード

- 値が必要です

#### `--session-save-redis-timeout`

接続タイムアウト （秒）

- 値が必要です

#### `--session-save-redis-retries`

Redis接続の再試行。

- 値が必要です

#### `--session-save-redis-persistent-id`

永続的な接続を有効にする一意の文字列

- 値が必要です

#### `--session-save-redis-db`

Redis データベース番号

- 値が必要です

#### `--session-save-redis-compression-threshold`

Redis圧縮しきい値

- 値が必要です

#### `--session-save-redis-compression-lib`

Redis圧縮ライブラリ 値：gzip （デフォルト）、lzf、lz4、snappy

- 値が必要です

#### `--session-save-redis-log-level`

Redis ログレベル。 値：0 （最小冗長）から7 （最も冗長）

- 値が必要です

#### `--session-save-redis-max-concurrency`

1つのセッションでロックを待機できるプロセスの最大数

- 値が必要です

#### `--session-save-redis-break-after-frontend`

フロントエンドセッションのロックを解除する前に待機する秒数

- 値が必要です

#### `--session-save-redis-break-after-adminhtml`

管理者セッションのロックを解除する前に待機する秒数

- 値が必要です

#### `--session-save-redis-first-lifetime`

最初の書き込み時の非ボットのセッションの有効期間（秒単位）（無効にするには0を使用）

- 値が必要です

#### `--session-save-redis-bot-first-lifetime`

最初の書き込み時のボットのセッションの有効期間（秒単位）（無効にするには0を使用）

- 値が必要です

#### `--session-save-redis-bot-lifetime`

後続の書き込み時のボットのセッションの有効期間（無効にするには0を使用）

- 値が必要です

#### `--session-save-redis-disable-locking`

Redisはロックを無効にします。 値：false （デフォルト）、true

- 値が必要です

#### `--session-save-redis-min-lifetime`

Redis最小セッション有効期間（秒）

- 値が必要です

#### `--session-save-redis-max-lifetime`

Redis最大セッション有効期間（秒単位）

- 値が必要です

#### `--session-save-redis-sentinel-master`

Redis Sentinel マスター

- 値が必要です

#### `--session-save-redis-sentinel-servers`

Redis Sentinel サーバー、コンマ区切り

- 値が必要です

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel検証マスター。 値：false （デフォルト）、true

- 値が必要です

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel接続の再試行。

- 値が必要です

#### `--cache-backend`

デフォルトのキャッシュハンドラー

- 値が必要です

#### `--cache-backend-redis-server`

Redis サーバー

- 値が必要です

#### `--cache-backend-redis-db`

キャッシュのデータベース番号

- 値が必要です

#### `--cache-backend-redis-port`

Redis サーバーのリッスン ポート

- 値が必要です

#### `--cache-backend-redis-password`

Redis サーバーパスワード

- 値が必要です

#### `--cache-backend-redis-compress-data`

圧縮を無効にするには0に設定します（デフォルトは1、有効）

- 値が必要です

#### `--cache-backend-redis-compression-lib`

[snappy,lzf,l4z,zstd,gzip]を使用する圧縮ライブラリ（自動的に決定するには空白のままにする）

- 値が必要です

#### `--cache-backend-redis-use-lua`

luaを有効にするには1に設定します（デフォルトは0、無効）

- 値が必要です

#### `--cache-backend-redis-use-lua-on-gc`

ガベージコレクションでLUAを無効にするには0に設定します（デフォルトは1、有効）

- 値が必要です

#### `--cache-id-prefix`

キャッシュキーのID プレフィックス

- 値が必要です

#### `--allow-parallel-generation`

ブロックしない方法でのキャッシュ生成を許可

- 既定：`false`
- 値を受け付けません

#### `--page-cache`

デフォルトのキャッシュハンドラー

- 値が必要です

#### `--page-cache-redis-server`

Redis サーバー

- 値が必要です

#### `--page-cache-redis-db`

キャッシュのデータベース番号

- 値が必要です

#### `--page-cache-redis-port`

Redis サーバーのリッスン ポート

- 値が必要です

#### `--page-cache-redis-password`

Redis サーバーパスワード

- 値が必要です

#### `--page-cache-redis-compress-data`

ページ全体のキャッシュを圧縮するには1に設定します（無効にするには0を使用します）

- 値が必要です

#### `--page-cache-redis-compression-lib`

[snappy,lzf,l4z,zstd,gzip]を使用する圧縮ライブラリ （自動的に決定するには空白のままにします）

- 値が必要です

#### `--page-cache-id-prefix`

キャッシュキーのID プレフィックス

- 値が必要です

#### `--lock-provider`

プロバイダー名をロック

- 値が必要です

#### `--lock-db-prefix`

ロックの競合を避けるためのインストール固有のロック接頭辞

- 値が必要です

#### `--lock-zookeeper-host`

Zookeeper クラスターに接続するためのホストとポート。 例：127.0.0.1:2181

- 値が必要です

#### `--lock-zookeeper-path`

Zookeeperがロックを保存するパス。 デフォルトのパスは/magento/locksです。

- 値が必要です

#### `--lock-file-path`

ファイルロックが保存されるパス。

- 値が必要です

#### `--document-root-is-pub`

表示するフラグは、Pubがルート上にあることであり、trueまたはfalseのみ可能です

- 値が必要です

#### `--backpressure-logger`

バックプレッシャーロガーハンドラー

- 値が必要です

#### `--backpressure-logger-redis-server`

Redis サーバー

- 値が必要です

#### `--backpressure-logger-redis-port`

Redis サーバーのリッスン ポート

- 値が必要です

#### `--backpressure-logger-redis-timeout`

Redis サーバーのタイムアウト

- 値が必要です

#### `--backpressure-logger-redis-persistent`

Redis persistent

- 値が必要です

#### `--backpressure-logger-redis-db`

Redis DB番号

- 値が必要です

#### `--backpressure-logger-redis-password`

Redis サーバーパスワード

- 値が必要です

#### `--backpressure-logger-redis-user`

Redis サーバーユーザー

- 値が必要です

#### `--backpressure-logger-id-prefix`

キーのID プレフィックス

- 値が必要です

#### `--base-url`

ストアが利用できるURL。 非推奨、パス web/unsecure/base_urlでconfig:setを使用

- 値が必要です

#### `--language`

デフォルトの言語コード。 非推奨、パス general/locale/codeでconfig:setを使用

- 値が必要です

#### `--timezone`

デフォルトのタイムゾーンコード： 非推奨、パス general/locale/timezoneでconfig:setを使用

- 値が必要です

#### `--currency`

デフォルトの通貨コード。 非推奨、パス currency/options/base、currency/options/defaultおよびcurrency/options/allowでconfig:setを使用

- 値が必要です

#### `--use-rewrites`

書き換えを使用します。 非推奨、パス web/seo/use_rewritesでconfig:setを使用

- 値が必要です

#### `--use-secure`

安全なURLの利用： SSLが使用可能な場合にのみ、このオプションを有効にします。 非推奨、パス web/secure/use_in_frontendでconfig:setを使用

- 値が必要です

#### `--base-url-secure`

SSL接続のベース URL。 非推奨、パス web/secure/base_urlでconfig:setを使用

- 値が必要です

#### `--use-secure-admin`

SSLを使用して管理インターフェイスを実行します。 非推奨、パス web/secure/use_in_adminhtmlでconfig:setを使用

- 値が必要です

#### `--admin-use-security-key`

Magento管理者URLとフォームで「セキュリティキー」機能を使用するかどうか。 非推奨、パスに設定:setを使用するadmin/security/use_form_key

- 値が必要です

#### `--admin-user`

管理者ユーザー

- 値を受け入れる

#### `--admin-password`

管理者パスワード

- 値を受け入れる

#### `--admin-email`

管理者メール

- 値を受け入れる

#### `--admin-firstname`

管理者の名

- 値を受け入れる

#### `--admin-lastname`

管理者の姓

- 値を受け入れる

#### `--search-engine`

検索エンジン： 値：elasticsearch8、opensearch

- 値が必要です

#### `--elasticsearch-host`

Elasticsearch サーバーホスト。

- 値が必要です

#### `--elasticsearch-port`

Elasticsearch サーバーポート。

- 値が必要です

#### `--elasticsearch-enable-auth`

認証を有効にするには、1に設定します。 （デフォルトは0、無効）

- 値が必要です

#### `--elasticsearch-username`

Elasticsearch ユーザー名。 HTTP認証が有効になっている場合にのみ適用されます

- 値が必要です

#### `--elasticsearch-password`

Elasticsearchのパスワード HTTP認証が有効になっている場合にのみ適用されます

- 値が必要です

#### `--elasticsearch-index-prefix`

Elasticsearch インデックスの接頭辞。

- 値が必要です

#### `--elasticsearch-timeout`

Elasticsearch サーバーのタイムアウト。

- 値が必要です

#### `--opensearch-host`

OpenSearch サーバーホスト。

- 値が必要です

#### `--opensearch-port`

OpenSearch サーバーポート。

- 値が必要です

#### `--opensearch-enable-auth`

認証を有効にするには、1に設定します。 （デフォルトは0、無効）

- 値が必要です

#### `--opensearch-username`

OpenSearch ユーザー名。 HTTP認証が有効になっている場合にのみ適用されます

- 値が必要です

#### `--opensearch-password`

OpenSearch パスワード。 HTTP認証が有効になっている場合にのみ適用されます

- 値が必要です

#### `--opensearch-index-prefix`

OpenSearch インデックスの接頭辞。

- 値が必要です

#### `--opensearch-timeout`

OpenSearch サーバーのタイムアウトです。

- 値が必要です

#### `--cleanup-database`

インストール前にデータベースをクリーンアップする

- 既定：`false`
- 値を受け付けません

#### `--sales-order-increment-prefix`

販売注文番号の接頭辞

- 値が必要です

#### `--use-sample-data`

サンプルデータの使用

- 既定：`false`
- 値を受け付けません

#### `--enable-modules`

コンマ区切りのモジュール名のリスト。 これはインストール時に含める必要があります。 利用可能なマジックパラメーター「すべて」。

- 値を受け入れる

#### `--disable-modules`

コンマ区切りのモジュール名のリスト。 これはインストール時に避ける必要があります。 利用可能なマジックパラメーター「すべて」。

- 値を受け入れる

#### `--convert-old-scripts`

古いスクリプト （InstallSchema、UpgradeSchema）をdb_schema.xml形式に変換できます

- 既定：`false`
- 値を受け入れる

#### `--interactive`, `-i`

Magentoのインタラクティブなインストール

- 既定：`false`
- 値を受け付けません

#### `--safe-mode`

Magentoを安全にインストールし、列の削除などの破壊的な操作にダンプを追加

- 値を受け入れる

#### `--data-restore`

削除されたデータをダンプから復元する

- 値を受け入れる

#### `--dry-run`

Magento インストールはドライランモードで実行されます

- 既定：`false`
- 値を受け入れる

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `setup:performance:generate-fixtures`

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

器具を生成します

### 引数

#### `profile`

プロファイル設定ファイルへのパス

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--skip-reindex`, `-s`

再インデックスをスキップ

- 既定：`false`
- 値を受け付けません


## `setup:rollback`

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Magento アプリケーションのコードベース、メディア、データベースをロールバックします

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--code-file`, `-c`

var/backupsのコードバックアップファイルのベースネーム

- 値が必要です

#### `--media-file`, `-m`

var/backups内のメディア・バックアップ・ファイルのベースネーム

- 値が必要です

#### `--db-file`, `-d`

var/backups内のdb バックアップファイルのベースネーム

- 値が必要です

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `setup:static-content:deploy`

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

静的ビューファイルをデプロイ

### 引数

#### `languages`

静的ビューファイルを出力するISO-639言語コードのスペース区切りリスト。

- 既定：`[]`
- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--force`, `-f`

任意のモードでファイルをデプロイします。

- 既定：`false`
- 値を受け付けません

#### `--strategy`, `-s`

指定した戦略を使用してファイルをデプロイします。

- 既定：`quick`
- 値を受け入れる

#### `--area`, `-a`

指定した領域のファイルのみを生成します。

- 既定：`all`
- 複数の値を受け入れる

#### `--exclude-area`

指定した領域のファイルは生成しないでください。

- 既定：`none`
- 複数の値を受け入れる

#### `--theme`, `-t`

指定したテーマの静的ビューファイルのみを生成します。

- 既定：`all`
- 複数の値を受け入れる

#### `--exclude-theme`

指定したテーマのファイルは生成しないでください。

- 既定：`none`
- 複数の値を受け入れる

#### `--language`, `-l`

指定した言語のファイルのみを生成します。

- 既定：`all`
- 複数の値を受け入れる

#### `--exclude-language`

指定した言語のファイルは生成しないでください。

- 既定：`none`
- 複数の値を受け入れる

#### `--jobs`, `-j`

指定したジョブ数を使用して並列処理を有効にします。

- 既定：`0`
- 値を受け入れる

#### `--max-execution-time`

デプロイメント静的プロセスの予想最大実行時間（秒単位）。

- 既定：`900`
- 値を受け入れる

#### `--symlink-locale`

これらのロケールのファイルのシンボリックリンクを作成します。このロケールはデプロイメント用に渡されますが、カスタマイズはありません。

- 既定：`false`
- 値を受け付けません

#### `--content-version`

複数のノードでデプロイメントを実行して、静的コンテンツバージョンが同じで、キャッシュが適切に動作することを確認する場合は、静的コンテンツのカスタムバージョンを使用できます。

- 値が必要です

#### `--refresh-content-version-only`

静的コンテンツのバージョンの更新は、ブラウザーキャッシュとCDN キャッシュ内の静的コンテンツの更新にのみ使用できます。

- 既定：`false`
- 値を受け付けません

#### `--no-javascript`

JavaScript ファイルはデプロイしないでください。

- 既定：`false`
- 値を受け付けません

#### `--no-js-bundle`

JavaScript バンドルファイルはデプロイしないでください。

- 既定：`false`
- 値を受け付けません

#### `--no-css`

CSS ファイルはデプロイしないでください。

- 既定：`false`
- 値を受け付けません

#### `--no-less`

LESS ファイルはデプロイしないでください。

- 既定：`false`
- 値を受け付けません

#### `--no-images`

画像はデプロイしないでください。

- 既定：`false`
- 値を受け付けません

#### `--no-fonts`

フォントファイルはデプロイしないでください。

- 既定：`false`
- 値を受け付けません

#### `--no-html`

HTML ファイルはデプロイしないでください。

- 既定：`false`
- 値を受け付けません

#### `--no-misc`

他のタイプ（.md、.jbf、.csvなど）のファイルはデプロイしないでください。

- 既定：`false`
- 値を受け付けません

#### `--no-html-minify`

HTML ファイルを縮小しないでください。

- 既定：`false`
- 値を受け付けません

#### `--no-parent`

親テーマはコンパイルしないでください。 クイックおよび標準的な戦略でのみサポートされます。

- 既定：`false`
- 値を受け付けません


## `setup:store-config:set`

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

ストア設定をインストールします。 2.2.0から非推奨（廃止予定）。代わりにconfig:setを使用してください

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--base-url`

ストアが利用できるURL。 非推奨、パス web/unsecure/base_urlでconfig:setを使用

- 値が必要です

#### `--language`

デフォルトの言語コード。 非推奨、パス general/locale/codeでconfig:setを使用

- 値が必要です

#### `--timezone`

デフォルトのタイムゾーンコード： 非推奨、パス general/locale/timezoneでconfig:setを使用

- 値が必要です

#### `--currency`

デフォルトの通貨コード。 非推奨、パス currency/options/base、currency/options/defaultおよびcurrency/options/allowでconfig:setを使用

- 値が必要です

#### `--use-rewrites`

書き換えを使用します。 非推奨、パス web/seo/use_rewritesでconfig:setを使用

- 値が必要です

#### `--use-secure`

安全なURLの利用： SSLが使用可能な場合にのみ、このオプションを有効にします。 非推奨、パス web/secure/use_in_frontendでconfig:setを使用

- 値が必要です

#### `--base-url-secure`

SSL接続のベース URL。 非推奨、パス web/secure/base_urlでconfig:setを使用

- 値が必要です

#### `--use-secure-admin`

SSLを使用して管理インターフェイスを実行します。 非推奨、パス web/secure/use_in_adminhtmlでconfig:setを使用

- 値が必要です

#### `--admin-use-security-key`

Magento管理者URLとフォームで「セキュリティキー」機能を使用するかどうか。 非推奨、パスに設定:setを使用するadmin/security/use_form_key

- 値が必要です

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `setup:uninstall`

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

Magento アプリケーションをアンインストールします

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `setup:upgrade`

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Magento アプリケーション、DB データ、スキーマをアップグレードします

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--keep-generated`

生成されたファイルが削除されないようにします。 実稼動環境にデプロイする場合を除き、このオプションを使用することはお勧めしません。 詳細については、システム インテグレータまたは管理者に問い合わせてください。

- 既定：`false`
- 値を受け付けません

#### `--convert-old-scripts`

古いスクリプト （InstallSchema、UpgradeSchema）をdb_schema.xml形式に変換できます

- 既定：`false`
- 値を受け入れる

#### `--safe-mode`

Magentoを安全にインストールし、列の削除などの破壊的な操作にダンプを追加

- 値を受け入れる

#### `--data-restore`

削除されたデータをダンプから復元する

- 値を受け入れる

#### `--dry-run`

Magento インストールはドライランモードで実行されます

- 既定：`false`
- 値を受け入れる

#### `--magento-init-params`

任意のコマンドに追加して、Magentoの初期化パラメーターをカスタマイズします。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache`

- 値が必要です


## `store:list`

```bash
bin/magento store:list
```

ストアのリストを表示します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `store:website:list`

```bash
bin/magento store:website:list
```

Web サイトのリストを表示します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `support:backup:code`

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

コードのバックアップを作成

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--name`

ダンプ名

- 値を受け入れる

#### `--output`, `-o`

出力パス

- 値を受け入れる

#### `--logs`, `-l`

ログを含める

- 既定：`false`
- 値を受け付けません


## `support:backup:db`

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

DB バックアップの作成

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--name`

ダンプ名

- 値を受け入れる

#### `--output`, `-o`

出力パス

- 値を受け入れる

#### `--logs`, `-l`

ログを含める

- 既定：`false`
- 値を受け付けません

#### `--ignore-sanitize`, `-i`

サニタイズを無視

- 既定：`false`
- 値を受け付けません


## `support:utility:check`

```bash
bin/magento support:utility:check [--hide-paths]
```

必要なバックアップユーティリティの確認

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--hide-paths`

必要なコンソールユーティリティのみを確認する

- 既定：`false`
- 値を受け付けません


## `support:utility:paths`

```bash
bin/magento support:utility:paths [-f|--force]
```

ユーティリティ パス リストの作成

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--force`, `-f`

力

- 既定：`false`
- 値を受け付けません


## `theme:uninstall`

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

テーマをアンインストールします

### 引数

#### `theme`

テーマのパス。 テーマパスは、エリア/ベンダー/名前のフルパスとして指定する必要があります。 例えば、フロントエンド/Magento/blankなどです

- 既定：`[]`
- 必須

- 配列

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--backup-code`

コードのバックアップ（一時ファイルを除く）を取る

- 既定：`false`
- 値を受け付けません

#### `--clear-static-content`, `-c`

生成された静的ビューファイルをクリアします。

- 既定：`false`
- 値を受け付けません


## `varnish:vcl:generate`

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

Varnish VCLを生成し、コマンドラインにエコーします

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--access-list`

VarnishをパージできるIP アクセスリスト

- 既定：`localhost`
- 値が必要です

#### `--backend-host`

Web バックエンドのホスト

- 既定：`localhost`
- 値が必要です

#### `--backend-port`

Web バックエンドのポート

- 既定：`8080`
- 値が必要です

#### `--export-version`

Varnish ファイルのバージョン

- 既定：`6`
- 値が必要です

#### `--grace-period`

猶予期間（秒）

- 既定：`300`
- 値が必要です

#### `--input-file`

vclを生成する入力ファイル

- 値が必要です

#### `--output-file`

vclを書き込むファイルへのパス

- 値が必要です


## `webhooks:dev:run`

```bash
bin/magento webhooks:dev:run <name> <payload>
```

開発目的で登録されたWebhookを実行します。

### 引数

#### `name`

Webhook名

- 必須


#### `payload`

JSON形式のWebhook ペイロード

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `webhooks:generate:module`

```bash
bin/magento webhooks:generate:module
```

Webhook登録に基づくプラグインの生成

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `webhooks:info`

```bash
bin/magento webhooks:info [--depth [DEPTH]] [--] <webhook-name> [<webhook-type>]
```

指定されたWebhookのペイロードを返します。

### 引数

#### `webhook-name`

Webhook メソッド名

- 必須


#### `webhook-type`

Webhook タイプ （前、後）

- 既定：`before`

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--depth`

返すWebhook ペイロードのレベル数

- 既定：`3`
- 値を受け入れる


## `webhooks:list`

```bash
bin/magento webhooks:list
```

購読したWebhookのリストを表示します

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `webhooks:list:all`

```bash
bin/magento webhooks:list:all <module_name>
```

指定されたモジュールでサポートされているWebhook メソッド名のリストを返します

### 引数

#### `module_name`

モジュール名

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。
