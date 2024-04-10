---
source-git-commit: 755ea50a75924cc16f690ff888367abd305565e9
workflow-type: tm+mt
source-wordcount: '21455'
ht-degree: 0%

---
# bin/magento （Adobe Commerce オンプレミス）

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->

**バージョン**: 2.4.7

このリファレンスには、を介して使用できる 141 のコマンドが含まれています `bin/magento` コマンドラインツール。
最初のリストは、 `bin/magento list` Adobe Commerceでコマンドを実行します。
の使用 [「CLI コマンドの追加」](https://developer.adobe.com/commerce/php/development/cli-commands/) カスタム CLI コマンドを追加するためのガイド。

>[!NOTE]
>
>を呼び出すことができます `bin/magento` 完全なコマンド名の代わりにショートカットを使用する CLI コマンド。 例えば、 `bin/magento setup:upgrade` 使用 `bin/magento s:up`, `bin/magento s:upg`. 参照： [ショートカット構文](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) を参照して、CLI コマンドでショートカットを使用する方法を理解します。

>[!NOTE]
>
>この参照は、アプリケーションコードベースから生成されます。 コンテンツを変更するには、対応するコマンド実装のソースコードを [コードベース](https://github.com/magento) 変更をレビュー用にリポジトリーして送信します。 もう 1 つの方法は、 _フィードバックを提供_ （右上のリンクを見つけます）。 投稿のガイドラインについては、を参照してください。 [コードの投稿](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

シェル補完の候補を提供する内部コマンド

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

### `--shell`, `-s`

シェル型（「bash」、「fish」、「zsh」）

- 値が必要です

### `--input`, `-i`

入力トークンの配列（例：COMP_WORDS または argv）

- デフォルト： `[]`
- 値が必要です

### `--current`, `-c`

カーソルがある「入力」配列のインデックス （例：COMP_CWORD）

- 値が必要です

### `--api-version`, `-a`

完了スクリプトの API バージョン

- 値が必要です

### `--symfony`, `-S`

非推奨

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `completion`

シェル完了スクリプトをダンプ

```bash
bin/magento completion [--debug] [--] [<shell>]
```


### `shell`

シェルの型（例：&#39;&#39;bash&#39;&#39;）は、&#39;&#39;$SHELL&#39;&#39;環境変数の値が指定されていない場合に使用されます


### `--debug`

完了デバッグログのテール

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `help`

コマンドのヘルプを表示する

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

コマンド名

- デフォルト： `help`


### `--format`

出力形式（txt、xml、json、md）

- デフォルト： `txt`
- 値が必要です

### `--raw`

生のコマンド ヘルプを出力するには

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `list`

コマンドのリスト

```bash
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```


### `namespace`

名前空間名


### `--raw`

生のコマンド リストを出力するには

- デフォルト： `false`
- 値を受け入れません

### `--format`

出力形式（txt、xml、json、md）

- デフォルト： `txt`
- 値が必要です

### `--short`

説明コマンドの引数をスキップするには

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `admin:adobe-ims:disable`

Adobe IMSモジュールを無効にする

```bash
bin/magento admin:adobe-ims:disable
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `admin:adobe-ims:enable`

Adobe IMSモジュールを有効にします。

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

### `--organization-id`, `-o`

Adobe IMS設定の組織 ID を設定します。 モジュールを有効にする場合は必須です

- 値を受け入れる

### `--client-id`, `-c`

Adobe IMS設定のクライアント ID を設定します。 モジュールを有効にする場合は必須です

- 値を受け入れる

### `--client-secret`, `-s`

Adobe IMS設定用のクライアント秘密鍵を設定します。 モジュールを有効にする場合は必須です

- 値を受け入れる

### `--2fa`, `-t`

Adobe Admin Consoleで 2FA が組織に対して有効になっているかどうかを確認します。 モジュールを有効にする場合は必須です

- 値を受け入れる

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `admin:adobe-ims:info`

Adobe IMSモジュールの設定に関する情報

```bash
bin/magento admin:adobe-ims:info
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `admin:adobe-ims:status`

Adobe IMSモジュールのステータス

```bash
bin/magento admin:adobe-ims:status
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `admin:user:create`

管理者を作成

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--admin-user`

（必須）管理者ユーザー

- 値が必要です

### `--admin-password`

（必須）管理者パスワード

- 値が必要です

### `--admin-email`

（必須）管理者の電子メール

- 値が必要です

### `--admin-firstname`

（必須）管理者の名

- 値が必要です

### `--admin-lastname`

（必須）管理者の姓

- 値が必要です

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `admin:user:unlock`

管理者アカウントのロックを解除

```bash
bin/magento admin:user:unlock <username>
```


### `username`

ロックを解除する管理者ユーザー名

- 必須

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `app:config:dump`

アプリケーションのダンプを作成

```bash
bin/magento app:config:dump [<config-types>...]
```


### `config-types`

設定タイプのスペース区切りリスト、またはすべてをダンプするには省略 [スコープ，システム，テーマ，i18n]

- デフォルト： `[]`

- 配列

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `app:config:import`

共有設定ファイルから適切なデータストレージへのデータの読み込み

```bash
bin/magento app:config:import
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `app:config:status`

構成の伝達に更新が必要かどうかを確認します

```bash
bin/magento app:config:status
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `braintree:migrate`

保管されたカードをMagento1 データベースから移行する

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

### `--host`

ホスト名/IP。 ポートはオプションです

- 値が必要です

### `--dbname`

データベース名

- 値が必要です

### `--username`

データベースユーザー名。 読み取りアクセスが必要

- 値が必要です

### `--password`

パスワード

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `cache:clean`

キャッシュタイプをクリーンアップします

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

キャッシュタイプのスペース区切りリスト。すべてのキャッシュタイプに適用する場合は省略します。

- デフォルト： `[]`

- 配列

### `--bootstrap`

bootstrap のパラメーターの追加または上書き

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `cache:disable`

キャッシュタイプを無効にします

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

キャッシュタイプのスペース区切りリスト。すべてのキャッシュタイプに適用する場合は省略します。

- デフォルト： `[]`

- 配列

### `--bootstrap`

bootstrap のパラメーターの追加または上書き

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `cache:enable`

キャッシュタイプを有効にする

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

キャッシュタイプのスペース区切りリスト。すべてのキャッシュタイプに適用する場合は省略します。

- デフォルト： `[]`

- 配列

### `--bootstrap`

bootstrap のパラメーターの追加または上書き

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `cache:flush`

キャッシュタイプで使用されるキャッシュストレージをフラッシュします

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

キャッシュタイプのスペース区切りリスト。すべてのキャッシュタイプに適用する場合は省略します。

- デフォルト： `[]`

- 配列

### `--bootstrap`

bootstrap のパラメーターの追加または上書き

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `cache:status`

キャッシュステータスを確認します

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

### `--bootstrap`

bootstrap のパラメーターの追加または上書き

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `catalog:images:resize`

サイズ変更された製品画像を作成

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

### `--async`, `-a`

非同期モードでの画像のサイズ変更

- デフォルト： `false`
- 値を受け入れません

### `--skip_hidden_images`

製品ページで非表示とマークされた画像を処理しない

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `catalog:product:attributes:cleanup`

未使用の製品属性を削除します。

```bash
bin/magento catalog:product:attributes:cleanup
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `cms:wysiwyg:restrict`

ユーザーHTML コンテンツの検証を強制するか、代わりに警告を表示するかを設定します

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```


### `restrict`

y\n

- 必須

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `config:sensitive:set`

機密性の高い設定値を設定

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```


### `path`

設定パス （例：group/section/field_name）


### `value`

設定値


### `--interactive`, `-i`

インタラクティブモードを有効にしてすべての機密変数を設定

- デフォルト： `false`
- 値を受け入れません

### `--scope`

設定されていない場合は、「default」を使用する設定の範囲

- デフォルト： `default`
- 値を受け入れる

### `--scope-code`

設定のスコープコード。デフォルトでは空の文字列です

- デフォルト : &quot;
- 値を受け入れる

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `config:set`

システム設定の変更

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```


### `path`

section/group/field_name 形式の設定パス

- 必須

### `value`

設定値

- 必須

### `--scope`

設定範囲（デフォルト、web サイトまたはストア）

- デフォルト： `default`
- 値が必要です

### `--scope-code`

スコープ コード （スコープが&#39;default&#39;でない場合のみ必要）

- 値が必要です

### `--lock-env`, `-e`

管理者で変更できないようにするロック値（app/etc/env.phpに保存されます）

- デフォルト： `false`
- 値を受け入れません

### `--lock-config`, `-c`

ロックして他のインストールと価値を共有、管理者での変更を防ぐ（app/etc/config.phpに保存されます）

- デフォルト： `false`
- 値を受け入れません

### `--lock`, `-l`

非推奨（廃止予定）です。代わりに – lock-env オプションを使用してください。

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `config:show`

指定されたパスの設定値を表示します。 パスを指定しない場合、保存されたすべての値が表示されます

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```


### `path`

設定パス（例：section_id/group_id/field_id）


### `--scope`

設定のスコープ。指定しない場合は、「デフォルト」スコープが使用されます

- デフォルト： `default`
- 値を受け入れる

### `--scope-code`

スコープコード （スコープが指定されていない場合のみ必須） `default`）

- デフォルト : &quot;
- 値を受け入れる

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `cron:install`

現在のユーザーの crontab を生成してインストールします

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

### `--force`, `-f`

インストールタスクを強制

- デフォルト： `false`
- 値を受け入れません

### `--non-optional`, `-d`

オプション以外（デフォルト）のタスクのみをインストールする

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `cron:remove`

crontab からタスクを削除します

```bash
bin/magento cron:remove
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `cron:run`

スケジュール別にジョブを実行

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

### `--group`

指定したグループからのみジョブを実行する

- 値が必要です

### `--exclude-group`

指定したグループからジョブを除外

- デフォルト： `[]`
- 複数の値を使用できます

### `--bootstrap`

ブートストラップのパラメータの追加または上書き

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `customer:hash:upgrade`

最新のアルゴリズムに従って顧客のハッシュをアップグレードする

```bash
bin/magento customer:hash:upgrade
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `deploy:mode:set`

アプリケーション モードを設定します。

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```


### `mode`

設定するアプリケーション モードです。 使用可能なオプションは、「開発者」または「実稼動」です

- 必須

### `--skip-compilation`, `-s`

静的コンテンツ（生成されたコード、前処理された CSS および pub/static/内のアセット）のクリアと再生成をスキップします

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `deploy:mode:show`

現在のアプリケーション モードを表示します。

```bash
bin/magento deploy:mode:show
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `dev:di:info`

コマンドの依存関係の挿入構成に関する情報を提供します。

```bash
bin/magento dev:di:info <class>
```


### `class`

クラス名

- 必須

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `dev:email:newsletter-compatibility-check`

ニュースレターテンプレートをスキャンして、変数の使用に関する互換性の潜在的な問題がないか確認します

```bash
bin/magento dev:email:newsletter-compatibility-check
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `dev:email:override-compatibility-check`

メールテンプレートの上書きをスキャンして、変数の使用に関する潜在的な互換性の問題を調べます

```bash
bin/magento dev:email:override-compatibility-check
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `dev:profiler:disable`

プロファイラーを無効にします。

```bash
bin/magento dev:profiler:disable
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `dev:profiler:enable`

プロファイラーを有効にします。

```bash
bin/magento dev:profiler:enable [<type>]
```


### `type`

プロファイラータイプ


### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `dev:query-log:disable`

DB クエリ ログを無効にする

```bash
bin/magento dev:query-log:disable
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `dev:query-log:enable`

DB クエリ ログを有効にする

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

### `--include-all-queries`

すべてのクエリをログに記録します。 [true\|false]

- デフォルト： `true`
- 値を受け入れる

### `--query-time-threshold`

クエリ時間のしきい値。

- デフォルト： `0.001`
- 値を受け入れる

### `--include-call-stack`

コールスタックを含めます。 [true\|false]

- デフォルト： `true`
- 値を受け入れる

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `dev:source-theme:deploy`

テーマのソースファイルを収集して公開します。

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```


### `file`

前処理するファイル （ファイルは拡張子なしで指定する必要があります）

- デフォルト： `css/styles-mcss/styles-l`

- 配列

### `--type`

ソースファイルの種類： [より小さい]

- デフォルト： `less`
- 値が必要です

### `--locale`

ロケール： [en_US]

- デフォルト： `en_US`
- 値が必要です

### `--area`

領域： [frontend\|adminhtml]

- デフォルト： `frontend`
- 値が必要です

### `--theme`

テーマ： [ベンダー/テーマ]

- デフォルト： `Magento/luma`
- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `dev:template-hints:disable`

フロントエンドテンプレートヒントを無効にします。 キャッシュのフラッシュが必要になる場合があります。

```bash
bin/magento dev:template-hints:disable
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `dev:template-hints:enable`

フロントエンドテンプレートヒントを有効にする。 キャッシュのフラッシュが必要になる場合があります。

```bash
bin/magento dev:template-hints:enable
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `dev:template-hints:status`

フロントエンドテンプレートヒントのステータスを表示。

```bash
bin/magento dev:template-hints:status
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `dev:tests:run`

テストの実行

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```


### `type`

実行するテストのタイプ。 使用可能なタイプ：all、unit、integration、integration-all、static、static-all、integrity、legacy、default

- デフォルト： `default`


### `--arguments`, `-c`

PHPUnit の追加の引数。 例：「– c&#39;—filter=MyTest&#39;&#39;」（スペースなし）

- デフォルト : &quot;
- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `dev:urn-catalog:generate`

IDE が XML をハイライトするために、*.xsd マッピングへの URN のカタログを生成します。

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```


### `path`

カタログを出力するファイルのパス。 PhpStorm の場合は、.idea/misc.xmlを使用します。

- 必須

### `--ide`

カタログが生成される形式。 サポート対象： [phpstorm、vscode]

- デフォルト： `phpstorm`
- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `dev:xml:convert`

XSL スタイルシートを使用して XML ファイルを変換します

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```


### `xml-file`

変換される XML ファイルへのパス

- 必須

### `processor`

XML ファイルに適用される XSL スタイルシートへのパス

- 必須

### `--overwrite`, `-o`

XML ファイルを上書き

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `downloadable:domains:add`

ダウンロード可能ドメインの許可リストにドメインを追加

```bash
bin/magento downloadable:domains:add [<domains>...]
```


### `domains`

ドメイン名

- デフォルト： `[]`

- 配列

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `downloadable:domains:remove`

ダウンロード可能なドメインの許可リストからドメインを削除

```bash
bin/magento downloadable:domains:remove [<domains>...]
```


### `domains`

ドメイン名

- デフォルト： `[]`

- 配列

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `downloadable:domains:show`

ダウンロード可能ドメインのホワイトリストを表示

```bash
bin/magento downloadable:domains:show
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `encryption:payment-data:update`

暗号化されたクレジット カード データを最新の暗号化暗号で再暗号化します。

```bash
bin/magento encryption:payment-data:update
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `events:create-event-provider`

このインスタンスのAdobe I/Oイベントにカスタムイベントプロバイダーを作成します。 ラベルおよび説明オプションを指定しない場合は、システムのapp/etc/event-types.json ファイルで定義する必要があります。

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]
```


```bash
bin/magento events:provider:create 
```

### `--label`

カスタムプロバイダーを定義するラベル。

- 値を受け入れる

### `--description`

プロバイダーの説明。

- 値を受け入れる

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `events:generate:module`

プラグインリストに基づいてモジュールを生成

```bash
bin/magento events:generate:module
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `events:info`

指定したイベントのペイロードを返します。

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```


### `event-code`

イベントコード

- 必須

### `--depth`

返されるイベントペイロード内のレベル数

- デフォルト： `2`
- 値を受け入れる

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `events:list`

購読しているイベントのリストを表示

```bash
bin/magento events:list
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `events:list:all`

指定されたモジュールで定義された購読可能なイベントのリストを返します

```bash
bin/magento events:list:all <module_name>
```


### `module_name`

モジュール名

- 必須

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `events:metadata:populate`

設定リスト（XML およびアプリケーション設定）からAdobe I/O内にメタデータを作成します

```bash
bin/magento events:metadata:populate
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `events:provider:info`

設定されたイベントプロバイダーの詳細を返します

```bash
bin/magento events:provider:info
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `events:registrations:list`

App Builder プロジェクトのイベント登録をリストします

```bash
bin/magento events:registrations:list
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `events:subscribe`

イベントを購読

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [-d|--destination DESTINATION] [--] <event-code>
```


### `event-code`

イベントコード

- 必須

### `--force`, `-f`

指定したイベントがローカルで定義されていない場合でも、購読するように強制します。

- デフォルト： `false`
- 値を受け入れません

### `--fields`

イベントデータペイロードのフィールドのリスト。

- デフォルト： `[]`
- 値が必要です

### `--parent`

ルール付きイベント購読の親イベントコード。

- 値が必要です

### `--rules`

イベント購読のルールのリスト。各ルールは「field\|operator\|value」の形式になります。

- デフォルト： `[]`
- 値が必要です

### `--priority`, `-p`

このイベントの送信を高速化します。 すぐに配信する必要があるイベントには、このオプションを指定します。 デフォルトでは、イベントは cron から 1 分ごとに 1 回送信されます。

- デフォルト： `false`
- 値を受け入れません

### `--destination`, `-d`

このイベントの宛先。 カスタムの宛先に配信するイベントに、このオプションを指定します。

- デフォルト： `default`
- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `events:sync-events-metadata`

このインスタンスのイベントメタデータを同期

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

### `--delete`, `-d`

イベントメタデータの削除は不要になりました

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `events:unsubscribe`

指定されたイベントのサブスクリプションを削除します

```bash
bin/magento events:unsubscribe <event-code>
```


### `event-code`

登録解除するイベントコード

- 必須

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `i18n:collect-phrases`

コードベース内のフレーズを検出します

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```


### `directory`

解析するディレクトリパス。 —magento フラグが設定されている場合は不要


### `--output`, `-o`

出力ファイルへのパス（ファイル名を含む）。 ファイルを指定しない場合、デフォルトは stdout になります。

- 値が必要です

### `--magento`, `-m`

現在のMagentoコードベースを解析するには、—magento パラメータを使用します。 ディレクトリが指定されている場合は、パラメーターを省略します。

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `i18n:pack`

言語パッケージを保存します

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```


### `source`

翻訳付きソースディクショナリファイルのパス

- 必須

### `locale`

辞書のターゲットロケール（「de_DE」など）

- 必須

### `--mode`, `-m`

辞書の保存モード – 「置換」 – 言語パックを新しいものに置き換える – 「結合」 – 言語パッケージを結合、デフォルトでは「置換」

- デフォルト： `replace`
- 値が必要です

### `--allow-duplicates`, `-d`

—allow-duplicates パラメーターを使用すると、翻訳の重複を保存できます。 それ以外の場合は、パラメーターを省略します。

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `i18n:uninstall`

言語パッケージをアンインストールします

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```


### `package`

言語パッケージ名

- デフォルト： `[]`

- 必須
- 配列

### `--backup-code`, `-b`

コードおよび設定ファイルのバックアップを作成（一時ファイルを除く）

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `indexer:info`

許可されているインデクサーを表示

```bash
bin/magento indexer:info
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `indexer:reindex`

データのインデックスを再作成

```bash
bin/magento indexer:reindex [<index>...]
```


### `index`

インデックスタイプのスペース区切りリスト、またはすべてのインデックスに適用する場合は省略。

- デフォルト： `[]`

- 配列

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `indexer:reset`

インデクサーのステータスを無効にリセットします

```bash
bin/magento indexer:reset [<index>...]
```


### `index`

インデックスタイプのスペース区切りリスト、またはすべてのインデックスに適用する場合は省略。

- デフォルト： `[]`

- 配列

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `indexer:set-dimensions-mode`

インデクサーDimensionモードの設定

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```


### `indexer`

インデクサー名 [catalog_product_price|catalogpermissions_category]


### `mode`

インデクサーディメンションモード catalog_product_price none,website,customer_group,website_and_customer_group catalogpermissions_category none,customer_group


### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `indexer:set-mode`

インデックスモードのタイプを設定します

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```


### `mode`

インデクサーモードのタイプ [リアルタイム|スケジュール]


### `index`

インデックスタイプのスペース区切りリスト、またはすべてのインデックスに適用する場合は省略。

- デフォルト： `[]`

- 配列

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `indexer:set-status`

指定されたインデクサーのステータスを設定します

```bash
bin/magento indexer:set-status <status> [<index>...]
```


### `status`

インデクサーのステータスタイプ [無効|中断|有効]

- 必須

### `index`

インデックスタイプのスペース区切りリスト、またはすべてのインデックスに適用する場合は省略。

- デフォルト： `[]`

- 配列

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `indexer:show-dimensions-mode`

インデクサーのDimensionモードを表示

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```


### `indexer`

すべてのインデックスに適用するインデックスタイプまたは省略のスペース区切りのリスト （catalog_product_price、catalogpermissions_category）

- デフォルト： `[]`

- 配列

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `indexer:show-mode`

インデックスモードを表示

```bash
bin/magento indexer:show-mode [<index>...]
```


### `index`

インデックスタイプのスペース区切りリスト、またはすべてのインデックスに適用する場合は省略。

- デフォルト： `[]`

- 配列

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `indexer:status`

インデクサーのステータスを表示

```bash
bin/magento indexer:status [<index>...]
```


### `index`

インデックスタイプのスペース区切りリスト、またはすべてのインデックスに適用する場合は省略。

- デフォルト： `[]`

- 配列

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `info:adminuri`

Magento管理者 URI を表示します

```bash
bin/magento info:adminuri
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `info:backups:list`

使用可能なバックアップ ファイルの一覧を出力します

```bash
bin/magento info:backups:list
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `info:currency:list`

使用可能な通貨のリストを表示

```bash
bin/magento info:currency:list
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `info:dependencies:show-framework`

Magentoフレームワークへの依存関係数を表示します

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

### `--output`, `-o`

レポートファイル名

- デフォルト： `framework-dependencies.csv`
- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `info:dependencies:show-modules`

モジュール間の依存関係数を表示します

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

### `--output`, `-o`

レポートファイル名

- デフォルト： `modules-dependencies.csv`
- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `info:dependencies:show-modules-circular`

モジュール間の循環依存関係の数を表示します

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

### `--output`, `-o`

レポートファイル名

- デフォルト： `modules-circular-dependencies.csv`
- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `info:language:list`

使用可能な言語ロケールの一覧を表示します

```bash
bin/magento info:language:list
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `info:timezone:list`

利用可能なタイムゾーンのリストを表示します

```bash
bin/magento info:timezone:list
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `inventory:reservation:create-compensations`

指定された報酬引数による引当の作成

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```


### `compensations`

「\」形式の報酬引数のリスト&lt;order_increment_id>:\&lt;sku>:\&lt;quantity>:\&lt;stock-id>“

- デフォルト： `[]`

- 配列

### `--raw`, `-r`

生の出力

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `inventory:reservation:list-inconsistencies`

販売可能な数量に不整合があるすべての注文および製品を表示します

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

### `--complete-orders`, `-c`

完了注文の不整合のみを表示

- デフォルト： `false`
- 値を受け入れません

### `--incomplete-orders`, `-i`

未完了の注文の不整合のみを表示

- デフォルト： `false`
- 値を受け入れません

### `--bunch-size`, `-b`

一度に読み込まれる注文の数を定義します

- デフォルト： `50`
- 値を受け入れる

### `--raw`, `-r`

生の出力

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `inventory-geonames:import`

ソース選択アルゴリズムの地域名のダウンロードと読み込み

```bash
bin/magento inventory-geonames:import <countries>...
```


### `countries`

インポートする国コードのリスト

- デフォルト： `[]`

- 必須
- 配列

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `maintenance:allow-ips`

メンテナンスモード除外 IP を設定します

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```


### `ip`

許可されている IP アドレス

- デフォルト： `[]`

- 配列

### `--none`

許可された IP アドレスのクリア

- デフォルト： `false`
- 値を受け入れません

### `--add`

既存のリストへの IP アドレスの追加

- デフォルト： `false`
- 値を受け入れません

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `maintenance:disable`

メンテナンスモードを無効にします

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

許可された IP アドレス （許可された IP リストをクリアするには「なし」を使用）

- デフォルト： `[]`
- 値が必要です

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `maintenance:enable`

メンテナンスモードを有効にする

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

許可された IP アドレス （許可された IP リストをクリアするには「なし」を使用）

- デフォルト： `[]`
- 値が必要です

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `maintenance:status`

メンテナンスモードのステータスを表示

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `media-content:sync`

コンテンツとアセットの同期

```bash
bin/magento media-content:sync
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `media-gallery:sync`

データベース内のメディアストレージとメディアアセットの同期

```bash
bin/magento media-gallery:sync
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `module:config:status`

「app/etc/config.php」ファイルのモジュール設定を確認し、モジュールが最新かどうかを報告します

```bash
bin/magento module:config:status
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `module:disable`

指定されたモジュールを無効にします

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

モジュールの名前

- デフォルト： `[]`

- 配列

### `--force`, `-f`

依存関係チェックのバイパス

- デフォルト： `false`
- 値を受け入れません

### `--all`

すべてのモジュールを無効にする

- デフォルト： `false`
- 値を受け入れません

### `--clear-static-content`, `-c`

生成された静的ビューファイルをクリアします。 必要（モジュールに静的ビューファイルがある場合）

- デフォルト： `false`
- 値を受け入れません

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `module:enable`

指定されたモジュールを有効にします

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

モジュールの名前

- デフォルト： `[]`

- 配列

### `--force`, `-f`

依存関係チェックのバイパス

- デフォルト： `false`
- 値を受け入れません

### `--all`

すべてのモジュールを有効にする

- デフォルト： `false`
- 値を受け入れません

### `--clear-static-content`, `-c`

生成された静的ビューファイルをクリアします。 必要（モジュールに静的ビューファイルがある場合）

- デフォルト： `false`
- 値を受け入れません

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `module:status`

モジュールのステータスを表示

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```


### `module-names`

オプションモジュール名

- デフォルト： `[]`

- 配列

### `--enabled`

有効化されたモジュールのみを印刷

- デフォルト： `false`
- 値を受け入れません

### `--disabled`

無効なモジュールのみを印刷

- デフォルト： `false`
- 値を受け入れません

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `module:uninstall`

コンポーザーによってインストールされたモジュールをアンインストールします

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```


### `module`

モジュールの名前

- デフォルト： `[]`

- 必須
- 配列

### `--remove-data`, `-r`

モジュールによってインストールされたデータを削除

- デフォルト： `false`
- 値を受け入れません

### `--backup-code`

コードおよび設定ファイルのバックアップを作成（一時ファイルを除く）

- デフォルト： `false`
- 値を受け入れません

### `--backup-media`

メディア バックアップの作成

- デフォルト： `false`
- 値を受け入れません

### `--backup-db`

完全なデータベースバックアップの実行

- デフォルト： `false`
- 値を受け入れません

### `--non-composer`

ここで過去に発生するすべてのモジュールは、コンポーザベースではありません

- デフォルト： `false`
- 値を受け入れません

### `--clear-static-content`, `-c`

生成された静的ビューファイルをクリアします。 必要（モジュールに静的ビューファイルがある場合）

- デフォルト： `false`
- 値を受け入れません

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `newrelic:create:deploy-marker`

デプロイキューのエントリを確認し、適切なデプロイマーカーを作成します。

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```


### `message`

メッセージをデプロイしますか？

- 必須

### `change_log`

変更ログ？

- 必須

### `user`

デプロイメントユーザー


### `revision`

リビジョン


### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `queue:consumers:list`

MessageQueue コンシューマーのリスト

```bash
bin/magento queue:consumers:list
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `queue:consumers:restart`

MessageQueue コンシューマーの再起動

```bash
bin/magento queue:consumers:restart
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `queue:consumers:start`

MessageQueue コンシューマーを開始

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```


### `consumer`

開始するコンシューマーの名前。

- 必須

### `--max-messages`

プロセス終了前にコンシューマーが処理するメッセージの数。 指定しない場合 – キュー内のすべてのメッセージを処理した後に終了します。

- 値が必要です

### `--batch-size`

バッチごとのメッセージ数。 バッチコンシューマーにのみ適用できます。

- 値が必要です

### `--area-code`

優先領域（グローバル、管理など）のデフォルトは、グローバルです。

- 値が必要です

### `--single-thread`

このオプションにより、1 つのコンシューマーの複数のコピーを同時に実行するのを防ぎます。

- デフォルト： `false`
- 値を受け入れません

### `--multi-process`

コンシューマーごとのプロセスの数。

- 値を受け入れる

### `--pid-file-path`

PID を保存するためのファイルパス （このオプションは非推奨です。代わりに – single-thread を使用してください）

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `remote-storage:sync`

メディア ファイルをリモート ストレージと同期します。

```bash
bin/magento remote-storage:sync
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `saas:resync`

フィード データを SaaS サービスに再同期します。

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync]
```

### `--feed`

SaaS サービスに完全に再同期するためのフィード名。 使用可能なフィード：Payment Services Order Production、Payment Services Order Sandbox、Payment Services Order Status Production、Payment Services Order Status Sandbox、Payment Services Store Production、Payment Services Store Sandbox

- 値が必要です

### `--no-reindex`

フィードデータの再送信を SaaS サービスにのみ実行します。 再インデックスは行われません。 （このオプションは、製品、製品のオーバーライド、価格フィードには適用されません）

- デフォルト： `false`
- 値を受け入れません

### `--cleanup-feed`

同期前にフィードインデクサーテーブルを強制的にクリーンアップします。

- デフォルト： `false`
- 値を受け入れません

### `--dry-run`

ドライラン。 データは書き出されません。 ログファイル var/log/saas-export.logにペイロードを保存するには、環境変数 EXPORTER_EXTENDED_LOG=1 を指定して実行します。

- デフォルト： `false`
- 値を受け入れません

### `--thread-count`

同期スレッド数を設定します。

- 値が必要です

### `--batch-size`

同期のバッチサイズの設定

- 値が必要です

### `--continue-resync`

最後に保存された位置から再同期を続行します（このオプションは、製品、製品オーバーライド、価格フィードに適用されます）

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `sampledata:deploy`

Composer ベースのMagento インストール用のサンプル データ モジュールの導入

```bash
bin/magento sampledata:deploy [--no-update]
```

### `--no-update`

composer の更新を実行せずに composer.json を更新

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `sampledata:remove`

composer.json からすべてのサンプルデータパッケージを削除します。

```bash
bin/magento sampledata:remove [--no-update]
```

### `--no-update`

composer の更新を実行せずに composer.json を更新

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `sampledata:reset`

再インストール用にすべてのサンプルデータモジュールをリセット

```bash
bin/magento sampledata:reset
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `security:recaptcha:disable-for-user-forgot-password`

管理者ユーザーのパスワードを忘れた場合の reCAPTCHA の無効化フォーム

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `security:recaptcha:disable-for-user-login`

管理者ユーザーログインフォームの reCAPTCHA を無効にする

```bash
bin/magento security:recaptcha:disable-for-user-login
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `security:tfa:google:set-secret`

Google OTP の生成に使用する秘密鍵を設定します。

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```


### `user`

ユーザー名

- 必須

### `secret`

秘密鍵

- 必須

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `security:tfa:providers`

使用可能なすべてのプロバイダーを一覧表示

```bash
bin/magento security:tfa:providers
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `security:tfa:reset`

1 人のユーザーの設定をリセット

```bash
bin/magento security:tfa:reset <user> <provider>
```


### `user`

ユーザー名

- 必須

### `provider`

プロバイダーコード

- 必須

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `server:run`

アプリケーションサーバーの実行

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-wn|--workerNum [WORKERNUM]] [-dm|--dispatchMode [DISPATCHMODE]] [-mr|--maxRequests [MAXREQUESTS]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]] [-mwt|--maxWaitTime [MAXWAITTIME]] [--state-monitor]
```

### `--port`, `-p`

ポートから serv へ

- デフォルト： `9501`
- 値を受け入れる

### `--background`, `-b`

背景モードフラグ

- デフォルト： `0`
- 値を受け入れる

### `--workerNum`, `-wn`

開始するワーカープロセスの数

- デフォルト： `4`
- 値を受け入れる

### `--dispatchMode`, `-dm`

ワーカープロセスへの接続のディスパッチのモード

- デフォルト： `3`
- 値を受け入れる

### `--maxRequests`, `-mr`

ワーカープロセスが再開される前の最大要求数

- デフォルト： `10000`
- 値を受け入れる

### `--area`, `-a`

アプリケーションサーバー領域

- デフォルト： `graphql`
- 値を受け入れる

### `--magento-init-params`, `-mip`

magento bootstrap init パラメーター

- デフォルト : &quot;
- 値を受け入れる

### `--maxWaitTime`, `-mwt`

再読み込み後のワーカーの待機時間（例： 設定の変更）を削除する前に以下を行います

- デフォルト： `3600`
- 値を受け入れる

### `--state-monitor`

状態の監視を有効にします。 これは状態の問題をデバッグする場合にのみ使用してください。

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `server:state-monitor:aggregate-output`

ApplicationServer の状態モニターからの集計出力

```bash
bin/magento server:state-monitor:aggregate-output
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:backup`

Magentoのアプリケーション コード ベース、メディア、およびデータベースをバックアップします

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code`

コードおよび設定ファイルのバックアップを作成（一時ファイルを除く）

- デフォルト： `false`
- 値を受け入れません

### `--media`

メディア バックアップの作成

- デフォルト： `false`
- 値を受け入れません

### `--db`

完全なデータベースバックアップの実行

- デフォルト： `false`
- 値を受け入れません

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:config:set`

デプロイメント設定を作成または変更します

```bash
bin/magento setup:config:set [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--enable-debug-logging`

デバッグログを有効にする

- 値が必要です

### `--enable-syslog-logging`

syslog ログを有効にする

- 値が必要です

### `--backend-frontname`

バックエンドの frontname （見つからない場合は自動生成されます）

- 値が必要です

### `--remote-storage-driver`

リモート記憶域ドライバー

- 値が必要です

### `--remote-storage-prefix`

リモートストレージプレフィックス

- デフォルト : &quot;
- 値が必要です

### `--remote-storage-endpoint`

リモートストレージエンドポイント

- 値が必要です

### `--remote-storage-bucket`

リモートストレージバケット

- 値が必要です

### `--remote-storage-region`

リモートストレージ領域

- 値が必要です

### `--remote-storage-key`

リモート記憶域アクセス キー

- デフォルト : &quot;
- 値が必要です

### `--remote-storage-secret`

リモート記憶域の秘密鍵

- デフォルト : &quot;
- 値が必要です

### `--remote-storage-path-style`

リモートストレージパスのスタイル

- デフォルト： `0`
- 値が必要です

### `--id_salt`

GraphQl Salt

- 値が必要です

### `--config-async`

非同期管理設定保存を有効にしますか？ 1 – はい、0 – いいえ

- 値が必要です

### `--checkout-async`

非同期順序処理を有効にしますか？ 1 – はい、0 – いいえ

- 値が必要です

### `--amqp-host`

Amqp サーバー・ホスト

- デフォルト : &quot;
- 値が必要です

### `--amqp-port`

Amqp サーバーポート

- デフォルト： `5672`
- 値が必要です

### `--amqp-user`

Amqp サーバーのユーザー名

- デフォルト : &quot;
- 値が必要です

### `--amqp-password`

Amqp サーバーのパスワード

- デフォルト : &quot;
- 値が必要です

### `--amqp-virtualhost`

Amqp virtualhost

- デフォルト： `/`
- 値が必要です

### `--amqp-ssl`

Amqp SSL

- デフォルト : &quot;
- 値が必要です

### `--amqp-ssl-options`

Amqp SSL オプション（JSON）

- デフォルト : &quot;
- 値が必要です

### `--consumers-wait-for-messages`

消費者はキューからのメッセージを待つ必要がありますか？ 1 – はい、0 – いいえ

- 値が必要です

### `--queue-default-connection`

メッセージキューのデフォルト接続。 「db」、「amqp」またはカスタムキューシステムを指定できます。キューシステムをインストールして設定する必要があります。そうしないと、メッセージが正しく処理されません。

- 値が必要です

### `--deferred-total-calculating`

遅延合計計算を有効にしますか？ 1 – はい、0 – いいえ

- 値が必要です

### `--key`

暗号化キー

- 値が必要です

### `--db-host`

データベースサーバーホスト

- 値が必要です

### `--db-name`

データベース名

- 値が必要です

### `--db-user`

データベースサーバーのユーザー名

- 値が必要です

### `--db-engine`

データベースサーバーエンジン

- 値が必要です

### `--db-password`

データベースサーバーのパスワード

- 値が必要です

### `--db-prefix`

データベーステーブルのプレフィックス

- 値が必要です

### `--db-model`

データベースタイプ

- 値が必要です

### `--db-init-statements`

データベースの初期コマンド・セット

- 値が必要です

### `--skip-db-validation`, `-s`

指定した場合、DB 接続の検証はスキップされます

- デフォルト： `false`
- 値を受け入れません

### `--http-cache-hosts`

http キャッシュホスト

- 値が必要です

### `--db-ssl-key`

SSL 経由でデータベース接続を確立するためのクライアントキーファイルのフルパス

- デフォルト : &quot;
- 値が必要です

### `--db-ssl-cert`

SSL 経由で DB 接続を確立するためのクライアント証明書ファイルのフルパス

- デフォルト : &quot;
- 値が必要です

### `--db-ssl-ca`

SSL 経由で DB 接続を確立するためのサーバー証明書ファイルのフルパス

- デフォルト : &quot;
- 値が必要です

### `--db-ssl-verify`

サーバー認証の確認

- デフォルト： `false`
- 値を受け入れません

### `--session-save`

セッション保存ハンドラー

- 値が必要です

### `--session-save-redis-host`

完全修飾ホスト名、IP アドレス、または UNIX ソケットを使用する場合は絶対パス

- 値が必要です

### `--session-save-redis-port`

Redis サーバーリッスンポート

- 値が必要です

### `--session-save-redis-password`

Redis サーバーパスワード

- 値が必要です

### `--session-save-redis-timeout`

接続タイムアウト （秒）

- 値が必要です

### `--session-save-redis-persistent-id`

永続接続を有効にする一意の文字列

- 値が必要です

### `--session-save-redis-db`

Redis データベース番号

- 値が必要です

### `--session-save-redis-compression-threshold`

Redis 圧縮しきい値

- 値が必要です

### `--session-save-redis-compression-lib`

Redis 圧縮ライブラリ。 値：gzip （デフォルト）、lzf、lz4、snappy

- 値が必要です

### `--session-save-redis-log-level`

Redis ログレベル。 値：0 （最小の詳細） ～ 7 （最大の詳細）

- 値が必要です

### `--session-save-redis-max-concurrency`

1 つのセッションでロックを待機できるプロセスの最大数

- 値が必要です

### `--session-save-redis-break-after-frontend`

フロントエンドセッションのロックを解除しようとする前の待機秒数

- 値が必要です

### `--session-save-redis-break-after-adminhtml`

管理セッションのロックを解除するまでの待機秒数

- 値が必要です

### `--session-save-redis-first-lifetime`

最初の書き込み時の非ボットのセッションの有効期間（秒単位） （0 を使用すると無効になります）

- 値が必要です

### `--session-save-redis-bot-first-lifetime`

最初の書き込み時のボットのセッションの有効期間（秒単位） （0 を使用すると無効になります）

- 値が必要です

### `--session-save-redis-bot-lifetime`

以降の書き込み時のボットのセッションの有効期間（無効にするには 0 を使用）

- 値が必要です

### `--session-save-redis-disable-locking`

Redis ロックを無効にします。 値：false （デフォルト）、true

- 値が必要です

### `--session-save-redis-min-lifetime`

Redis 最小セッション有効期間（秒）

- 値が必要です

### `--session-save-redis-max-lifetime`

Redis 最大セッション有効期間（秒）

- 値が必要です

### `--session-save-redis-sentinel-master`

レディス センティネル マスター

- 値が必要です

### `--session-save-redis-sentinel-servers`

Redis Sentinel サーバー、コンマ区切り

- 値が必要です

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel がマスターを確認します。 値：false （デフォルト）、true

- 値が必要です

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel 接続の再試行。

- 値が必要です

### `--cache-backend`

デフォルトのキャッシュハンドラー

- 値が必要です

### `--cache-backend-redis-server`

Redis サーバー

- 値が必要です

### `--cache-backend-redis-db`

キャッシュのデータベース番号

- 値が必要です

### `--cache-backend-redis-port`

Redis サーバーリッスンポート

- 値が必要です

### `--cache-backend-redis-password`

Redis サーバーパスワード

- 値が必要です

### `--cache-backend-redis-compress-data`

0 に設定すると、圧縮が無効になります（デフォルトは 1、有効）

- 値が必要です

### `--cache-backend-redis-compression-lib`

使用する圧縮ライブラリ [snappy,lzf,l4z,zstd,gzip] （自動的に決定する場合は空白のままにします）

- 値が必要です

### `--cache-backend-redis-use-lua`

1 に設定すると、lua が有効になります（デフォルトは 0、無効）

- 値が必要です

### `--cache-id-prefix`

キャッシュキーの ID プレフィックス

- 値が必要です

### `--allow-parallel-generation`

ノンブロッキング方式でキャッシュを生成できるようにする

- デフォルト： `false`
- 値を受け入れません

### `--page-cache`

デフォルトのキャッシュハンドラー

- 値が必要です

### `--page-cache-redis-server`

Redis サーバー

- 値が必要です

### `--page-cache-redis-db`

キャッシュのデータベース番号

- 値が必要です

### `--page-cache-redis-port`

Redis サーバーリッスンポート

- 値が必要です

### `--page-cache-redis-password`

Redis サーバーパスワード

- 値が必要です

### `--page-cache-redis-compress-data`

1 に設定すると、フルページキャッシュを圧縮します（0 を使用すると無効になります）

- 値が必要です

### `--page-cache-redis-compression-lib`

使用する圧縮ライブラリ [snappy,lzf,l4z,zstd,gzip] （自動的に決定する場合は空白のままにします）

- 値が必要です

### `--page-cache-id-prefix`

キャッシュキーの ID プレフィックス

- 値が必要です

### `--lock-provider`

プロバイダー名をロック

- 値が必要です

### `--lock-db-prefix`

ロックの競合を回避するためのインストール固有のロックプレフィックス

- 値が必要です

### `--lock-zookeeper-host`

Zookeeper クラスターに接続するホストおよびポート。 例：127.0.0.1:2181

- 値が必要です

### `--lock-zookeeper-path`

Zookeeper がロックを保存するパス。 デフォルトのパスは/magento/locks です。

- 値が必要です

### `--lock-file-path`

ファイルのロックが保存されるパス。

- 値が必要です

### `--document-root-is-pub`

表示するフラグ：Pub is on root。true または false のみ指定可能

- 値が必要です

### `--backpressure-logger`

Backpressure ロガーハンドラー

- 値が必要です

### `--backpressure-logger-redis-server`

Redis サーバー

- 値が必要です

### `--backpressure-logger-redis-port`

Redis サーバーリッスンポート

- 値が必要です

### `--backpressure-logger-redis-timeout`

Redis サーバータイムアウト

- 値が必要です

### `--backpressure-logger-redis-persistent`

Redis 永続

- 値が必要です

### `--backpressure-logger-redis-db`

Redis db 番号

- 値が必要です

### `--backpressure-logger-redis-password`

Redis サーバーパスワード

- 値が必要です

### `--backpressure-logger-redis-user`

Redis サーバーユーザー

- 値が必要です

### `--backpressure-logger-id-prefix`

キーの ID プレフィックス

- 値が必要です

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:db-data:upgrade`

DB 内のデータのインストールとアップグレード

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:db-declaration:generate-patch`

パッチを生成して特定のフォルダーに配置します。

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```


### `module`

モジュール名

- 必須

### `patch`

パッチ名

- 必須

### `--revertable`

パッチが元に戻すことができるかどうかを確認します。

- デフォルト： `false`
- 値を受け入れる

### `--type`

生成するパッチの種類を調べます。 使用可能な値： `data`, `schema`.

- デフォルト： `data`
- 値を受け入れる

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:db-declaration:generate-whitelist`

宣言インストーラーによって編集できるテーブルおよび列の許可リストを生成します

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

### `--module-name`

許可リストが生成されるモジュールの名前

- デフォルト： `all`
- 値を受け入れる

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:db-schema:add-slave`

チェックアウト引用関連テーブルを別の DB サーバーに移動する

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

スレーブ DB サーバーホスト

- デフォルト： `localhost`
- 値が必要です

### `--dbname`

スレーブ データベース名

- 値が必要です

### `--username`

スレーブ DB ユーザー名

- デフォルト： `root`
- 値が必要です

### `--password`

スレーブ DB ユーザーパスワード

- 値を受け入れる

### `--connection`

スレーブ接続名

- デフォルト： `default`
- 値を受け入れる

### `--resource`

スレーブリソース名

- デフォルト： `default`
- 値を受け入れる

### `--maxAllowedLag`

最大許容ラグ スレーブ接続（秒）

- デフォルト : &quot;
- 値を受け入れる

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:db-schema:split-quote`

チェックアウト引用関連テーブルを別の DB サーバーに移動します。 2.4.2 以降で非推奨（廃止予定）となり、削除される予定です

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

DB サーバーホストのチェックアウト

- 値が必要です

### `--dbname`

チェックアウト データベース名

- 値が必要です

### `--username`

チェックアウト DB ユーザー名

- 値が必要です

### `--password`

チェックアウト DB ユーザーパスワード

- 値を受け入れる

### `--connection`

接続名をチェックアウト

- デフォルト： `checkout`
- 値を受け入れる

### `--resource`

チェックアウトリソース名

- デフォルト： `checkout`
- 値を受け入れる

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:db-schema:split-sales`

販売関連テーブルを別の DB サーバーに移動します。 2.4.2 以降で非推奨（廃止予定）となり、削除される予定です

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

セールス DB サーバ・ホスト

- 値が必要です

### `--dbname`

営業データベース名

- 値が必要です

### `--username`

販売 DB ユーザー名

- 値が必要です

### `--password`

Sales DB ユーザーのパスワード

- 値を受け入れる

### `--connection`

営業接続名

- デフォルト： `sales`
- 値を受け入れる

### `--resource`

販売リソース名

- デフォルト： `sales`
- 値を受け入れる

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:db-schema:upgrade`

DB スキーマのインストールとアップグレード

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--convert-old-scripts`

古いスクリプト （InstallSchema、UpgradeSchema）を db_schema.xml 形式に変換できるようにします

- デフォルト： `false`
- 値を受け入れる

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:db:status`

DB スキーマまたはデータのアップグレードが必要かどうかを確認します

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:di:compile`

DI 構成と、自動生成できる不足クラスをすべて生成します

```bash
bin/magento setup:di:compile
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:install`

Magentoアプリケーションをインストールします

```bash
bin/magento setup:install [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--enable-debug-logging`

デバッグログを有効にする

- 値が必要です

### `--enable-syslog-logging`

syslog ログを有効にする

- 値が必要です

### `--backend-frontname`

バックエンドの frontname （見つからない場合は自動生成されます）

- 値が必要です

### `--remote-storage-driver`

リモート記憶域ドライバー

- 値が必要です

### `--remote-storage-prefix`

リモートストレージプレフィックス

- デフォルト : &quot;
- 値が必要です

### `--remote-storage-endpoint`

リモートストレージエンドポイント

- 値が必要です

### `--remote-storage-bucket`

リモートストレージバケット

- 値が必要です

### `--remote-storage-region`

リモートストレージ領域

- 値が必要です

### `--remote-storage-key`

リモート記憶域アクセス キー

- デフォルト : &quot;
- 値が必要です

### `--remote-storage-secret`

リモート記憶域の秘密鍵

- デフォルト : &quot;
- 値が必要です

### `--remote-storage-path-style`

リモートストレージパスのスタイル

- デフォルト： `0`
- 値が必要です

### `--id_salt`

GraphQl Salt

- 値が必要です

### `--config-async`

非同期管理設定保存を有効にしますか？ 1 – はい、0 – いいえ

- 値が必要です

### `--checkout-async`

非同期順序処理を有効にしますか？ 1 – はい、0 – いいえ

- 値が必要です

### `--amqp-host`

Amqp サーバー・ホスト

- デフォルト : &quot;
- 値が必要です

### `--amqp-port`

Amqp サーバーポート

- デフォルト： `5672`
- 値が必要です

### `--amqp-user`

Amqp サーバーのユーザー名

- デフォルト : &quot;
- 値が必要です

### `--amqp-password`

Amqp サーバーのパスワード

- デフォルト : &quot;
- 値が必要です

### `--amqp-virtualhost`

Amqp virtualhost

- デフォルト： `/`
- 値が必要です

### `--amqp-ssl`

Amqp SSL

- デフォルト : &quot;
- 値が必要です

### `--amqp-ssl-options`

Amqp SSL オプション（JSON）

- デフォルト : &quot;
- 値が必要です

### `--consumers-wait-for-messages`

消費者はキューからのメッセージを待つ必要がありますか？ 1 – はい、0 – いいえ

- 値が必要です

### `--queue-default-connection`

メッセージキューのデフォルト接続。 「db」、「amqp」またはカスタムキューシステムを指定できます。キューシステムをインストールして設定する必要があります。そうしないと、メッセージが正しく処理されません。

- 値が必要です

### `--deferred-total-calculating`

遅延合計計算を有効にしますか？ 1 – はい、0 – いいえ

- 値が必要です

### `--key`

暗号化キー

- 値が必要です

### `--db-host`

データベースサーバーホスト

- 値が必要です

### `--db-name`

データベース名

- 値が必要です

### `--db-user`

データベースサーバーのユーザー名

- 値が必要です

### `--db-engine`

データベースサーバーエンジン

- 値が必要です

### `--db-password`

データベースサーバーのパスワード

- 値が必要です

### `--db-prefix`

データベーステーブルのプレフィックス

- 値が必要です

### `--db-model`

データベースタイプ

- 値が必要です

### `--db-init-statements`

データベースの初期コマンド・セット

- 値が必要です

### `--skip-db-validation`, `-s`

指定した場合、DB 接続の検証はスキップされます

- デフォルト： `false`
- 値を受け入れません

### `--http-cache-hosts`

http キャッシュホスト

- 値が必要です

### `--db-ssl-key`

SSL 経由でデータベース接続を確立するためのクライアントキーファイルのフルパス

- デフォルト : &quot;
- 値が必要です

### `--db-ssl-cert`

SSL 経由で DB 接続を確立するためのクライアント証明書ファイルのフルパス

- デフォルト : &quot;
- 値が必要です

### `--db-ssl-ca`

SSL 経由で DB 接続を確立するためのサーバー証明書ファイルのフルパス

- デフォルト : &quot;
- 値が必要です

### `--db-ssl-verify`

サーバー認証の確認

- デフォルト： `false`
- 値を受け入れません

### `--session-save`

セッション保存ハンドラー

- 値が必要です

### `--session-save-redis-host`

完全修飾ホスト名、IP アドレス、または UNIX ソケットを使用する場合は絶対パス

- 値が必要です

### `--session-save-redis-port`

Redis サーバーリッスンポート

- 値が必要です

### `--session-save-redis-password`

Redis サーバーパスワード

- 値が必要です

### `--session-save-redis-timeout`

接続タイムアウト （秒）

- 値が必要です

### `--session-save-redis-persistent-id`

永続接続を有効にする一意の文字列

- 値が必要です

### `--session-save-redis-db`

Redis データベース番号

- 値が必要です

### `--session-save-redis-compression-threshold`

Redis 圧縮しきい値

- 値が必要です

### `--session-save-redis-compression-lib`

Redis 圧縮ライブラリ。 値：gzip （デフォルト）、lzf、lz4、snappy

- 値が必要です

### `--session-save-redis-log-level`

Redis ログレベル。 値：0 （最小の詳細） ～ 7 （最大の詳細）

- 値が必要です

### `--session-save-redis-max-concurrency`

1 つのセッションでロックを待機できるプロセスの最大数

- 値が必要です

### `--session-save-redis-break-after-frontend`

フロントエンドセッションのロックを解除しようとする前の待機秒数

- 値が必要です

### `--session-save-redis-break-after-adminhtml`

管理セッションのロックを解除するまでの待機秒数

- 値が必要です

### `--session-save-redis-first-lifetime`

最初の書き込み時の非ボットのセッションの有効期間（秒単位） （0 を使用すると無効になります）

- 値が必要です

### `--session-save-redis-bot-first-lifetime`

最初の書き込み時のボットのセッションの有効期間（秒単位） （0 を使用すると無効になります）

- 値が必要です

### `--session-save-redis-bot-lifetime`

以降の書き込み時のボットのセッションの有効期間（無効にするには 0 を使用）

- 値が必要です

### `--session-save-redis-disable-locking`

Redis ロックを無効にします。 値：false （デフォルト）、true

- 値が必要です

### `--session-save-redis-min-lifetime`

Redis 最小セッション有効期間（秒）

- 値が必要です

### `--session-save-redis-max-lifetime`

Redis 最大セッション有効期間（秒）

- 値が必要です

### `--session-save-redis-sentinel-master`

レディス センティネル マスター

- 値が必要です

### `--session-save-redis-sentinel-servers`

Redis Sentinel サーバー、コンマ区切り

- 値が必要です

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel がマスターを確認します。 値：false （デフォルト）、true

- 値が必要です

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel 接続の再試行。

- 値が必要です

### `--cache-backend`

デフォルトのキャッシュハンドラー

- 値が必要です

### `--cache-backend-redis-server`

Redis サーバー

- 値が必要です

### `--cache-backend-redis-db`

キャッシュのデータベース番号

- 値が必要です

### `--cache-backend-redis-port`

Redis サーバーリッスンポート

- 値が必要です

### `--cache-backend-redis-password`

Redis サーバーパスワード

- 値が必要です

### `--cache-backend-redis-compress-data`

0 に設定すると、圧縮が無効になります（デフォルトは 1、有効）

- 値が必要です

### `--cache-backend-redis-compression-lib`

使用する圧縮ライブラリ [snappy,lzf,l4z,zstd,gzip] （自動的に決定する場合は空白のままにします）

- 値が必要です

### `--cache-backend-redis-use-lua`

1 に設定すると、lua が有効になります（デフォルトは 0、無効）

- 値が必要です

### `--cache-id-prefix`

キャッシュキーの ID プレフィックス

- 値が必要です

### `--allow-parallel-generation`

ノンブロッキング方式でキャッシュを生成できるようにする

- デフォルト： `false`
- 値を受け入れません

### `--page-cache`

デフォルトのキャッシュハンドラー

- 値が必要です

### `--page-cache-redis-server`

Redis サーバー

- 値が必要です

### `--page-cache-redis-db`

キャッシュのデータベース番号

- 値が必要です

### `--page-cache-redis-port`

Redis サーバーリッスンポート

- 値が必要です

### `--page-cache-redis-password`

Redis サーバーパスワード

- 値が必要です

### `--page-cache-redis-compress-data`

1 に設定すると、フルページキャッシュを圧縮します（0 を使用すると無効になります）

- 値が必要です

### `--page-cache-redis-compression-lib`

使用する圧縮ライブラリ [snappy,lzf,l4z,zstd,gzip] （自動的に決定する場合は空白のままにします）

- 値が必要です

### `--page-cache-id-prefix`

キャッシュキーの ID プレフィックス

- 値が必要です

### `--lock-provider`

プロバイダー名をロック

- 値が必要です

### `--lock-db-prefix`

ロックの競合を回避するためのインストール固有のロックプレフィックス

- 値が必要です

### `--lock-zookeeper-host`

Zookeeper クラスターに接続するホストおよびポート。 例：127.0.0.1:2181

- 値が必要です

### `--lock-zookeeper-path`

Zookeeper がロックを保存するパス。 デフォルトのパスは/magento/locks です。

- 値が必要です

### `--lock-file-path`

ファイルのロックが保存されるパス。

- 値が必要です

### `--document-root-is-pub`

表示するフラグ：Pub is on root。true または false のみ指定可能

- 値が必要です

### `--backpressure-logger`

Backpressure ロガーハンドラー

- 値が必要です

### `--backpressure-logger-redis-server`

Redis サーバー

- 値が必要です

### `--backpressure-logger-redis-port`

Redis サーバーリッスンポート

- 値が必要です

### `--backpressure-logger-redis-timeout`

Redis サーバータイムアウト

- 値が必要です

### `--backpressure-logger-redis-persistent`

Redis 永続

- 値が必要です

### `--backpressure-logger-redis-db`

Redis db 番号

- 値が必要です

### `--backpressure-logger-redis-password`

Redis サーバーパスワード

- 値が必要です

### `--backpressure-logger-redis-user`

Redis サーバーユーザー

- 値が必要です

### `--backpressure-logger-id-prefix`

キーの ID プレフィックス

- 値が必要です

### `--base-url`

ストアが使用できる URL。 非推奨（廃止予定）。パス web/unsecure/base_url で config:set を使用してください。

- 値が必要です

### `--language`

デフォルトの言語コード。 非推奨（廃止予定）。パス general/locale/code で config:set を使用してください。

- 値が必要です

### `--timezone`

デフォルトのタイムゾーンコード。 非推奨（廃止予定）。config:set をパス general/locale/timezone と共に使用します。

- 値が必要です

### `--currency`

デフォルトの通貨コード。 非推奨（廃止予定）。パス currency/options/base、currency/options/default および currency/options/allow を指定して config:set を使用します。

- 値が必要です

### `--use-rewrites`

書き換えを使用します。 非推奨（廃止予定）。パス web/seo/use_rewrites で config:set を使用します。

- 値が必要です

### `--use-secure`

セキュア URL を使用します。 SSL が使用可能な場合のみ、このオプションを有効にします。 非推奨（廃止予定）。パス web/secure/use_in_frontend で config:set を使用してください。

- 値が必要です

### `--base-url-secure`

SSL 接続のベース URL。 非推奨（廃止予定）。パス web/secure/base_url で config:set を使用してください。

- 値が必要です

### `--use-secure-admin`

SSL を使用した管理インターフェイスの実行 非推奨（廃止予定）。パス web/secure/use_in_adminhtml で config:set を使用してください。

- 値が必要です

### `--admin-use-security-key`

Magento管理 URL およびフォームで「セキュリティキー」機能を使用するかどうか。 非推奨（廃止予定）。パス admin/security/use_form_key で config:set を使用します。

- 値が必要です

### `--admin-user`

管理者ユーザー

- 値を受け入れる

### `--admin-password`

管理者パスワード

- 値を受け入れる

### `--admin-email`

管理者の電子メール

- 値を受け入れる

### `--admin-firstname`

管理者の名

- 値を受け入れる

### `--admin-lastname`

管理者の姓

- 値を受け入れる

### `--search-engine`

検索エンジン。 値：elasticsearch7、elasticsearch8、opensearch

- 値が必要です

### `--elasticsearch-host`

Elasticsearchサーバーホスト。

- 値が必要です

### `--elasticsearch-port`

Elasticsearchサーバーのポート。

- 値が必要です

### `--elasticsearch-enable-auth`

1 に設定すると、認証が有効になります。 （デフォルトは 0、無効）

- 値が必要です

### `--elasticsearch-username`

Elasticsearchユーザー名。 HTTP 認証が有効な場合にのみ適用されます

- 値が必要です

### `--elasticsearch-password`

Elasticsearchパスワード。 HTTP 認証が有効な場合にのみ適用されます

- 値が必要です

### `--elasticsearch-index-prefix`

Elasticsearchインデックスプレフィックス。

- 値が必要です

### `--elasticsearch-timeout`

Elasticsearchサーバータイムアウト。

- 値が必要です

### `--opensearch-host`

OpenSearch サーバーホスト。

- 値が必要です

### `--opensearch-port`

OpenSearch サーバーポート。

- 値が必要です

### `--opensearch-enable-auth`

1 に設定すると、認証が有効になります。 （デフォルトは 0、無効）

- 値が必要です

### `--opensearch-username`

OpenSearch ユーザー名。 HTTP 認証が有効な場合にのみ適用されます

- 値が必要です

### `--opensearch-password`

OpenSearch パスワード。 HTTP 認証が有効な場合にのみ適用されます

- 値が必要です

### `--opensearch-index-prefix`

OpenSearch インデックスの接頭辞。

- 値が必要です

### `--opensearch-timeout`

OpenSearch サーバーのタイムアウト。

- 値が必要です

### `--cleanup-database`

インストール前のデータベースのクリーンアップ

- デフォルト： `false`
- 値を受け入れません

### `--sales-order-increment-prefix`

販売注文番号プレフィックス

- 値が必要です

### `--use-sample-data`

サンプルデータの使用

- デフォルト： `false`
- 値を受け入れません

### `--enable-modules`

コンマ区切りのモジュール名のリスト。 インストール時に含める必要があります。 使用可能なマジックパラメーター「all」。

- 値を受け入れる

### `--disable-modules`

コンマ区切りのモジュール名のリスト。 インストール中は避ける必要があります。 使用可能なマジックパラメーター「all」。

- 値を受け入れる

### `--convert-old-scripts`

古いスクリプト （InstallSchema、UpgradeSchema）を db_schema.xml 形式に変換できるようにします

- デフォルト： `false`
- 値を受け入れる

### `--interactive`, `-i`

インタラクティブMagentoのインストール

- デフォルト： `false`
- 値を受け入れません

### `--safe-mode`

列の削除などの破壊的なオペレーションのダンプを使用したMagentoの安全なインストール

- 値を受け入れる

### `--data-restore`

ダンプから削除されたデータを復元

- 値を受け入れる

### `--dry-run`

Magentoのインストールはドライランモードで実行されます

- デフォルト： `false`
- 値を受け入れる

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:performance:generate-fixtures`

器具を生成します

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```


### `profile`

プロファイル設定ファイルのパス

- 必須

### `--skip-reindex`, `-s`

再インデックスをスキップ

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:rollback`

Magentoアプリケーションのコードベース、メディア、データベースをロールバックします。

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code-file`, `-c`

var/backups のコードバックアップファイルのベース名

- 値が必要です

### `--media-file`, `-m`

var/backups 内のメディアバックアップファイルのベース名

- 値が必要です

### `--db-file`, `-d`

var/backups のデータベースバックアップファイルのベース名

- 値が必要です

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:static-content:deploy`

静的ビューファイルをデプロイ

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```


### `languages`

静的ビューファイルを出力する ISO-639 言語コードのスペース区切りリスト。

- デフォルト： `[]`

- 配列

### `--force`, `-f`

任意のモードでファイルをデプロイします。

- デフォルト： `false`
- 値を受け入れません

### `--strategy`, `-s`

指定した方法を使用してファイルをデプロイします。

- デフォルト： `quick`
- 値を受け入れる

### `--area`, `-a`

指定した領域のファイルのみを生成します。

- デフォルト： `all`
- 複数の値を使用できます

### `--exclude-area`

指定した領域のファイルを生成しません。

- デフォルト： `none`
- 複数の値を使用できます

### `--theme`, `-t`

指定したテーマのみの静的表示ファイルを生成します。

- デフォルト： `all`
- 複数の値を使用できます

### `--exclude-theme`

指定したテーマのファイルを生成しないでください。

- デフォルト： `none`
- 複数の値を使用できます

### `--language`, `-l`

指定した言語のみのファイルを生成します。

- デフォルト： `all`
- 複数の値を使用できます

### `--exclude-language`

指定した言語のファイルを生成しないでください。

- デフォルト： `none`
- 複数の値を使用できます

### `--jobs`, `-j`

指定されたジョブ数を使用して並列処理を有効にします。

- デフォルト： `0`
- 値を受け入れる

### `--max-execution-time`

デプロイメント静的プロセスの予想される最大実行時間（秒）。

- デフォルト： `900`
- 値を受け入れる

### `--symlink-locale`

これらのロケールのファイルにシンボリックリンクを作成します。これはデプロイメントに渡されますが、カスタマイズは行われません。

- デフォルト： `false`
- 値を受け入れません

### `--content-version`

複数のノードでデプロイメントを実行する場合は、静的コンテンツのカスタムバージョンを使用して、静的コンテンツのバージョンが同じでキャッシュが正しく機能することを確認できます。

- 値が必要です

### `--refresh-content-version-only`

静的コンテンツのバージョンの更新は、ブラウザーキャッシュおよび CDN キャッシュ内の静的コンテンツの更新にのみ使用できます。

- デフォルト： `false`
- 値を受け入れません

### `--no-javascript`

JavaScript ファイルはデプロイしないでください。

- デフォルト： `false`
- 値を受け入れません

### `--no-js-bundle`

JavaScript バンドルファイルをデプロイしないでください。

- デフォルト： `false`
- 値を受け入れません

### `--no-css`

CSS ファイルをデプロイしないでください。

- デフォルト： `false`
- 値を受け入れません

### `--no-less`

LESS ファイルをデプロイしないでください。

- デフォルト： `false`
- 値を受け入れません

### `--no-images`

画像をデプロイしないでください。

- デフォルト： `false`
- 値を受け入れません

### `--no-fonts`

フォントファイルをデプロイしないでください。

- デフォルト： `false`
- 値を受け入れません

### `--no-html`

HTMLファイルをデプロイしないでください。

- デフォルト： `false`
- 値を受け入れません

### `--no-misc`

その他のタイプ（.md、.jbf、.csv など）のファイルはデプロイしないでください。

- デフォルト： `false`
- 値を受け入れません

### `--no-html-minify`

HTMLファイルは縮小しないでください。

- デフォルト： `false`
- 値を受け入れません

### `--no-parent`

親テーマをコンパイルしないでください。 迅速かつ標準的な戦略でのみサポートされます。

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:store-config:set`

ストア設定をインストールします。 2.2.0 以降で非推奨（廃止予定）。代わりに config:set を使用してください。

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--base-url`

ストアが使用できる URL。 非推奨（廃止予定）。パス web/unsecure/base_url で config:set を使用してください。

- 値が必要です

### `--language`

デフォルトの言語コード。 非推奨（廃止予定）。パス general/locale/code で config:set を使用してください。

- 値が必要です

### `--timezone`

デフォルトのタイムゾーンコード。 非推奨（廃止予定）。config:set をパス general/locale/timezone と共に使用します。

- 値が必要です

### `--currency`

デフォルトの通貨コード。 非推奨（廃止予定）。パス currency/options/base、currency/options/default および currency/options/allow を指定して config:set を使用します。

- 値が必要です

### `--use-rewrites`

書き換えを使用します。 非推奨（廃止予定）。パス web/seo/use_rewrites で config:set を使用します。

- 値が必要です

### `--use-secure`

セキュア URL を使用します。 SSL が使用可能な場合のみ、このオプションを有効にします。 非推奨（廃止予定）。パス web/secure/use_in_frontend で config:set を使用してください。

- 値が必要です

### `--base-url-secure`

SSL 接続のベース URL。 非推奨（廃止予定）。パス web/secure/base_url で config:set を使用してください。

- 値が必要です

### `--use-secure-admin`

SSL を使用した管理インターフェイスの実行 非推奨（廃止予定）。パス web/secure/use_in_adminhtml で config:set を使用してください。

- 値が必要です

### `--admin-use-security-key`

Magento管理 URL およびフォームで「セキュリティキー」機能を使用するかどうか。 非推奨（廃止予定）。パス admin/security/use_form_key で config:set を使用します。

- 値が必要です

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:uninstall`

Magentoアプリケーションをアンインストールします

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `setup:upgrade`

Magento アプリケーション、DB データ、およびスキーマをアップグレードします。

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--keep-generated`

生成されたファイルを削除できないようにします。 実稼動環境にデプロイする場合を除き、このオプションは使用しないでください。 詳しくは、システムインテグレーターまたは管理者に問い合わせてください。

- デフォルト： `false`
- 値を受け入れません

### `--convert-old-scripts`

古いスクリプト （InstallSchema、UpgradeSchema）を db_schema.xml 形式に変換できるようにします

- デフォルト： `false`
- 値を受け入れる

### `--safe-mode`

列の削除などの破壊的なオペレーションのダンプを使用したMagentoの安全なインストール

- 値を受け入れる

### `--data-restore`

ダンプから削除されたデータを復元

- 値を受け入れる

### `--dry-run`

Magentoのインストールはドライランモードで実行されます

- デフォルト： `false`
- 値を受け入れる

### `--magento-init-params`

任意のコマンドにを追加して、Magentoの初期化パラメーターをカスタマイズします。例：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `store:list`

ストアのリストを表示します

```bash
bin/magento store:list
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `store:website:list`

Web サイトのリストを表示します

```bash
bin/magento store:website:list
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `support:backup:code`

コードのバックアップを作成

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

### `--name`

ダンプ名

- 値を受け入れる

### `--output`, `-o`

出力パス

- 値を受け入れる

### `--logs`, `-l`

ログを含める

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `support:backup:db`

DB バックアップの作成

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

### `--name`

ダンプ名

- 値を受け入れる

### `--output`, `-o`

出力パス

- 値を受け入れる

### `--logs`, `-l`

ログを含める

- デフォルト： `false`
- 値を受け入れません

### `--ignore-sanitize`, `-i`

不要部分を無視

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `support:utility:check`

必要なバックアップユーティリティの確認

```bash
bin/magento support:utility:check [--hide-paths]
```

### `--hide-paths`

必要なコンソールユーティリティのみを確認する

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `support:utility:paths`

ユーティリティパスリストの作成

```bash
bin/magento support:utility:paths [-f|--force]
```

### `--force`, `-f`

力

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `theme:uninstall`

テーマをアンインストールします

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```


### `theme`

テーマのパス。 テーマのパスは、領域/ベンダー/名前のフルパスとして指定する必要があります。 例：フロントエンド/Magento/空白

- デフォルト： `[]`

- 必須
- 配列

### `--backup-code`

コードのバックアップを作成（一時ファイルを除く）

- デフォルト： `false`
- 値を受け入れません

### `--clear-static-content`, `-c`

生成された静的ビューファイルをクリアします。

- デフォルト： `false`
- 値を受け入れません

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `varnish:vcl:generate`

Varnish VCL を生成し、コマンド ラインにエコーします

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

### `--access-list`

Varnish をパージできる IP アクセスリスト

- デフォルト： `localhost`
- 値が必要です

### `--backend-host`

Web バックエンドのホスト

- デフォルト： `localhost`
- 値が必要です

### `--backend-port`

Web バックエンドのポート

- デフォルト： `8080`
- 値が必要です

### `--export-version`

Varnish ファイルのバージョン

- デフォルト： `6`
- 値が必要です

### `--grace-period`

猶予期間（秒）

- デフォルト： `300`
- 値が必要です

### `--input-file`

vcl を生成する入力ファイル

- 値が必要です

### `--output-file`

vcl を書き込むファイルへのパス

- 値が必要です

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `webhooks:dev:run`

開発目的で登録済みの Webhook を実行します。

```bash
bin/magento webhooks:dev:run <name> <payload>
```


### `name`

Webhook 名

- 必須

### `payload`

JSON 形式の Webhook ペイロード

- 必須

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `webhooks:generate:module`

Webhook 登録に基づくプラグインの生成

```bash
bin/magento webhooks:generate:module
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `webhooks:info`

指定された Webhook のペイロードを返します。

```bash
bin/magento webhooks:info [--depth [DEPTH]] [--] <webhook-name> [<webhook-type>]
```


### `webhook-name`

Webhook メソッド名

- 必須

### `webhook-type`

Webhook タイプ（前、後）

- デフォルト： `before`


### `--depth`

返される Webhook ペイロードのレベル数

- デフォルト： `3`
- 値を受け入れる

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `webhooks:list`

購読している Webhook のリストを表示

```bash
bin/magento webhooks:list
```

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません


## `webhooks:list:all`

指定されたモジュールでサポートされている Webhook メソッド名のリストを返します

```bash
bin/magento webhooks:list:all <module_name>
```


### `module_name`

モジュール名

- 必須

### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合、\の表示ヘルプ&lt;info>list\&lt;/info> コマンド

- デフォルト： `false`
- 値を受け入れません

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れません

### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト： `false`
- 値を受け入れません

### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト： `false`
- 値を受け入れません

### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト： `false`
- 値を受け入れません

### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト： `false`
- 値を受け入れません
