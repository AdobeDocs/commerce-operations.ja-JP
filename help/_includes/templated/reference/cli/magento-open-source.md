---
source-git-commit: 23d55385046de18b238c90f6a99be692f1ce7561
workflow-type: tm+mt
source-wordcount: '14684'
ht-degree: 0%

---
# bin/magento(Magento Open Source)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**バージョン**:2.4.5

このリファレンスには、 `bin/magento` コマンドラインツールを使用します。
最初のリストは、 `bin/magento list` コマンドを使用して
以下を使用： [CLI コマンドの追加](https://developer.adobe.com/commerce/php/development/cli-commands/) カスタム CLI コマンドの追加に関するガイド

>[!NOTE]
>
>次の呼び出しが可能： `bin/magento` フル・コマンド名の代わりにショートカットを使用する CLI コマンド。 例えば、 `bin/magento setup:upgrade` using `bin/magento s:up`, `bin/magento s:upg`. 詳しくは、 [ショートカット構文](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) を参照してください。

>[!NOTE]
>
>この参照は、アプリケーションのコードベースから生成されます。 コンテンツを変更するには、 [codebase](https://github.com/magento) リポジトリを作成し、変更をレビュー用に送信します。 もう 1 つの方法は、次の操作です。 _フィードバックを提供_ （右上にあるリンクを見つけます）。 貢献のガイドラインについては、 [コード貢献](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `help`

コマンドのヘルプを表示する

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

コマンド名

- デフォルト： `help`


### `--format`

出力形式 (txt、xml、json、md)

- デフォルト： `txt`
- 値が必要です

### `--raw`

生のコマンドのヘルプを出力するには

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `list`

リストコマンド

```bash
bin/magento list [--raw] [--format FORMAT] [--] [<namespace>]
```


### `namespace`

名前空間名


### `--raw`

生のコマンドリストを出力するには

- デフォルト： `false`
- 値を受け入れない

### `--format`

出力形式 (txt、xml、json、md)

- デフォルト： `txt`
- 値が必要です


## `admin:adobe-ims:disable`

Adobe IMSモジュールを無効にする

```bash
bin/magento admin:adobe-ims:disable
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `admin:adobe-ims:enable`

Adobe IMSモジュールを有効にします。

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

### `--organization-id`, `-o`

組織設定の組織 ID をAdobe IMSします。 モジュールを有効にする場合に必須

- 値を受け入れる

### `--client-id`, `-c`

クライアント ID を設定してAdobe IMSを設定します。 モジュールを有効にする場合に必須

- 値を受け入れる

### `--client-secret`, `-s`

クライアントの秘密鍵をAdobe IMS設定に設定します。 モジュールを有効にする場合に必須

- 値を受け入れる

### `--2fa`, `-t`

2FA がAdobe Admin Consoleの組織に対して有効になっているかどうかを確認します。 モジュールを有効にする場合に必須

- 値を受け入れる

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `admin:adobe-ims:info`

Adobe IMS・モジュールの設定

```bash
bin/magento admin:adobe-ims:info
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `admin:adobe-ims:status`

Adobe IMS・モジュールのステータス

```bash
bin/magento admin:adobe-ims:status
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


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

（必須）管理者用電子メール

- 値が必要です

### `--admin-firstname`

（必須）管理者の名

- 値が必要です

### `--admin-lastname`

（必須）管理者の姓

- 値が必要です

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `admin:user:unlock`

管理者アカウントのロック解除

```bash
bin/magento admin:user:unlock <username>
```


### `username`

ロックを解除する管理者ユーザー名

- 必須

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `app:config:dump`

アプリケーションのダンプを作成

```bash
bin/magento app:config:dump [<config-types>...]
```


### `config-types`

設定タイプのスペース区切りリストを表示するか、すべてをダンプする場合は省略します。 [スコープ、テーマ、システム、i18n]

- デフォルト： `[]`

- 配列

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `app:config:import`

共有構成ファイルから適切なデータストレージにデータを読み込む

```bash
bin/magento app:config:import
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `app:config:status`

設定の伝達に更新が必要かどうかを確認します

```bash
bin/magento app:config:status
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `braintree:migrate`

保存されたカードをMagento1 データベースから移行する

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

データベースのユーザー名。 読み取りアクセス権が必要

- 値が必要です

### `--password`

パスワード

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `cache:clean`

キャッシュの種類をクリーンアップします

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

キャッシュタイプのスペース区切りのリストを指定するか、すべてのキャッシュタイプに適用する場合は省略します。

- デフォルト： `[]`

- 配列

### `--bootstrap`

ブートストラップのパラメータを追加または上書き

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `cache:disable`

キャッシュタイプを無効にします

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

キャッシュタイプのスペース区切りのリストを指定するか、すべてのキャッシュタイプに適用する場合は省略します。

- デフォルト： `[]`

- 配列

### `--bootstrap`

ブートストラップのパラメータを追加または上書き

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `cache:enable`

キャッシュタイプを有効にする

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

キャッシュタイプのスペース区切りのリストを指定するか、すべてのキャッシュタイプに適用する場合は省略します。

- デフォルト： `[]`

- 配列

### `--bootstrap`

ブートストラップのパラメータを追加または上書き

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `cache:flush`

キャッシュタイプで使用されるキャッシュストレージをフラッシュします

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

キャッシュタイプのスペース区切りのリストを指定するか、すべてのキャッシュタイプに適用する場合は省略します。

- デフォルト： `[]`

- 配列

### `--bootstrap`

ブートストラップのパラメータを追加または上書き

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `cache:status`

キャッシュの状態を確認します

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

### `--bootstrap`

ブートストラップのパラメータを追加または上書き

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `catalog:images:resize`

サイズ変更された製品画像を作成

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

### `--async`, `-a`

非同期モードでの画像のサイズ変更

- デフォルト： `false`
- 値を受け入れない

### `--skip_hidden_images`

製品ページで非表示とマークされた画像を処理しない

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `catalog:product:attributes:cleanup`

未使用の製品属性を削除します。

```bash
bin/magento catalog:product:attributes:cleanup
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `cms:wysiwyg:restrict`

ユーザーHTMLコンテンツの検証を実施するか、代わりに警告を表示するかを設定します

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```


### `restrict`

y\n

- 必須

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `config:sensitive:set`

機密設定値の設定

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```


### `path`

設定パス（例：group/section/field_name）


### `value`

設定値


### `--interactive`, `-i`

すべての機密変数を設定するインタラクティブモードを有効にする

- デフォルト： `false`
- 値を受け入れない

### `--scope`

設定の範囲（設定されていない場合）は、「デフォルト」を使用します

- デフォルト： `default`
- 値を受け入れる

### `--scope-code`

設定のスコープコード、デフォルトでは空の文字列

- デフォルト：&quot;
- 値を受け入れる

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `config:set`

システム構成の変更

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

設定範囲（デフォルト、Web サイト、ストア）

- デフォルト： `default`
- 値が必要です

### `--scope-code`

スコープコード（スコープが「デフォルト」でない場合にのみ必須）

- 値が必要です

### `--lock-env`, `-e`

値をロックし、管理での変更を防ぎます (app/etc/env.phpに保存されます )

- デフォルト： `false`
- 値を受け入れない

### `--lock-config`, `-c`

値を他のインストールとロックして共有し、管理者での変更を防ぎます (app/etc/config.phpに保存されます )

- デフォルト： `false`
- 値を受け入れない

### `--lock`, `-l`

非推奨です。代わりに、 —lock-env オプションを使用してください。

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `config:show`

指定されたパスの設定値を表示します。 path を指定しない場合は、保存されている値がすべて表示されます

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```


### `path`

設定パス（例：section_id/group_id/field_id）


### `--scope`

設定の範囲を指定しない場合は、「デフォルト」の範囲が使用されます

- デフォルト： `default`
- 値を受け入れる

### `--scope-code`

スコープコード（スコープがない場合にのみ必要） `default`)

- デフォルト：&quot;
- 値を受け入れる

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `cron:install`

現在のユーザーの crontab を生成してインストールします

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

### `--force`, `-f`

インストールタスクを強制

- デフォルト： `false`
- 値を受け入れない

### `--non-optional`, `-d`

オプション以外（デフォルト）のタスクのみをインストールする

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `cron:remove`

crontab からタスクを削除します

```bash
bin/magento cron:remove
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `cron:run`

スケジュール別にジョブを実行

```bash
bin/magento cron:run [--group GROUP] [--bootstrap BOOTSTRAP]
```

### `--group`

指定したグループからのみジョブを実行

- 値が必要です

### `--bootstrap`

ブートストラップのパラメータを追加または上書き

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `customer:hash:upgrade`

最新のアルゴリズムに従って顧客のハッシュをアップグレード

```bash
bin/magento customer:hash:upgrade
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `deploy:mode:set`

アプリケーションモードを設定します。

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```


### `mode`

設定するアプリケーションモード。 「開発者」または「実稼動」のオプションを使用できます。

- 必須

### `--skip-compilation`, `-s`

静的コンテンツ（生成されたコード、事前処理された CSS、pub/static/内のアセット）の消去と再生成をスキップします。

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `deploy:mode:show`

現在のアプリケーションモードを表示します。

```bash
bin/magento deploy:mode:show
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dev:di:info`

コマンドの [ 依存挿入 ] 設定に関する情報を提供します。

```bash
bin/magento dev:di:info <class>
```


### `class`

クラス名

- 必須

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dev:email:newsletter-compatibility-check`

ニュースレターテンプレートをスキャンして、変数の使用に関する互換性の問題の可能性を調べます

```bash
bin/magento dev:email:newsletter-compatibility-check
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dev:email:override-compatibility-check`

電子メールテンプレートの上書きをスキャンして、変数使用の互換性の問題の可能性を調べます

```bash
bin/magento dev:email:override-compatibility-check
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dev:profiler:disable`

プロファイラを無効にします。

```bash
bin/magento dev:profiler:disable
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dev:profiler:enable`

プロファイラを有効にします。

```bash
bin/magento dev:profiler:enable [<type>]
```


### `type`

プロファイラーのタイプ


### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dev:query-log:disable`

DB クエリログを無効にする

```bash
bin/magento dev:query-log:disable
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dev:query-log:enable`

DB クエリログを有効にする

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

呼び出しスタックを含めます。 [true\|false]

- デフォルト： `true`
- 値を受け入れる

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dev:source-theme:deploy`

テーマのソースファイルを収集し、公開します。

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```


### `file`

前処理するファイル（ファイルの拡張子は指定しないでください）

- デフォルト： `css/styles-mcss/styles-l`

- 配列

### `--type`

ソースファイルのタイプ： [less]

- デフォルト： `less`
- 値が必要です

### `--locale`

ロケール： [en_US]

- デフォルト： `en_US`
- 値が必要です

### `--area`

面積： [frontend\|adminhtml]

- デフォルト： `frontend`
- 値が必要です

### `--theme`

テーマ： [ベンダー/テーマ]

- デフォルト： `Magento/luma`
- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dev:template-hints:disable`

フロントエンドテンプレートのヒントを無効にします。 キャッシュのフラッシュが必要な場合があります。

```bash
bin/magento dev:template-hints:disable
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dev:template-hints:enable`

フロントエンドテンプレートのヒントを有効にします。 キャッシュのフラッシュが必要な場合があります。

```bash
bin/magento dev:template-hints:enable
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dev:template-hints:status`

フロントエンドテンプレートヒントの状態を表示します。

```bash
bin/magento dev:template-hints:status
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dev:tests:run`

テストを実行

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```


### `type`

実行するテストのタイプ。 使用可能なタイプ：すべて，単位，統合，統合 — すべて，静的，静的，静的，整合性，レガシー，デフォルト

- デフォルト： `default`


### `--arguments`, `-c`

PHPUnit の追加引数。 例：&quot;-c&#39;—filter=MyTest&#39;&quot; （スペースなし）

- デフォルト：&quot;
- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dev:urn-catalog:generate`

XML をハイライト表示する IDE の*.xsd マッピングへの URN のカタログを生成します。

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```


### `path`

カタログを出力するファイルのパス。 PhpStorm の場合は、.idea/misc.xmlを使用します。

- 必須

### `--ide`

カタログを生成する形式。 サポート対象： [phstorm、vscode]

- デフォルト： `phpstorm`
- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dev:xml:convert`

XSL スタイルシートを使用して XML ファイルを変換します

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```


### `xml-file`

変換される XML ファイルへのパス

- 必須

### `processor`

XML ファイルに適用される XSL スタイルシートのパス

- 必須

### `--overwrite`, `-o`

XML ファイルを上書き

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `downloadable:domains:add`

ダウンロード可能なドメインのホワイトリストにドメインを追加する

```bash
bin/magento downloadable:domains:add [<domains>...]
```


### `domains`

ドメイン名

- デフォルト： `[]`

- 配列

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `downloadable:domains:remove`

ダウンロード可能なドメインのホワイトリストからドメインを削除する

```bash
bin/magento downloadable:domains:remove [<domains>...]
```


### `domains`

ドメイン名

- デフォルト： `[]`

- 配列

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `downloadable:domains:show`

ダウンロード可能なドメインのホワイトリストを表示

```bash
bin/magento downloadable:domains:show
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `encryption:payment-data:update`

暗号化されたクレジットカードデータを最新の暗号化暗号で再暗号化します。

```bash
bin/magento encryption:payment-data:update
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `i18n:collect-phrases`

コードベース内のフレーズを検出

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```


### `directory`

解析するディレクトリパス。 —magento フラグが設定されている場合は不要です。


### `--output`, `-o`

出力ファイルへのパス（ファイル名を含む）。 ファイルを指定しない場合、デフォルトは stdout になります。

- 値が必要です

### `--magento`, `-m`

—magento パラメーターを使用して、現在のMagento・コードベースを解析します。 ディレクトリを指定する場合は、このパラメーターを省略します。

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `i18n:pack`

言語パッケージを保存します

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```


### `source`

翻訳を含むソース辞書ファイルへのパス

- 必須

### `locale`

辞書のターゲットロケール（「de_DE」など）

- 必須

### `--mode`, `-m`

辞書の保存モード — &quot;replace&quot; — 新しい言語パックで言語パックを置き換える — &quot;merge&quot; — 言語パッケージを結合し、デフォルトで&quot;replace&quot;

- デフォルト： `replace`
- 値が必要です

### `--allow-duplicates`, `-d`

翻訳の重複を保存できるようにするには、 —allow-duplicates パラメーターを使用します。 それ以外の場合は、パラメーターを省略します。

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `i18n:uninstall`

言語パッケージのアンインストール

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```


### `package`

言語パッケージ名

- デフォルト： `[]`

- 必須
- 配列

### `--backup-code`, `-b`

コードと設定ファイルのバックアップ（一時ファイルを除く）を作成する

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `indexer:info`

許可されているインデクサーを表示

```bash
bin/magento indexer:info
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `indexer:reindex`

データの再インデックス

```bash
bin/magento indexer:reindex [<index>...]
```


### `index`

すべてのインデックスに適用する場合は、インデックスタイプのスペース区切りリストを指定するか、省略します。

- デフォルト： `[]`

- 配列

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `indexer:reset`

インデクサーの状態を無効にリセットします

```bash
bin/magento indexer:reset [<index>...]
```


### `index`

すべてのインデックスに適用する場合は、インデックスタイプのスペース区切りリストを指定するか、省略します。

- デフォルト： `[]`

- 配列

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `indexer:set-dimensions-mode`

インデクサーDimensionモードの設定

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```


### `indexer`

インデクサー名 [catalog_product_price]


### `mode`

インデクサーディメンションモード catalog_product_price none,website,customer_group,website_and_customer_group


### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `indexer:set-mode`

インデックスモードの種類を設定します

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```


### `mode`

インデクサーモードのタイプ [リアルタイム|スケジュール]


### `index`

すべてのインデックスに適用する場合は、インデックスタイプのスペース区切りリストを指定するか、省略します。

- デフォルト： `[]`

- 配列

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `indexer:show-dimensions-mode`

インデクサーDimensionモードを表示

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```


### `indexer`

すべてのインデックスに適用する場合は、インデックスタイプのスペース区切りリストを指定するか、省略します (catalog_product_price)

- デフォルト： `[]`

- 配列

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `indexer:show-mode`

インデックスモードを表示

```bash
bin/magento indexer:show-mode [<index>...]
```


### `index`

すべてのインデックスに適用する場合は、インデックスタイプのスペース区切りリストを指定するか、省略します。

- デフォルト： `[]`

- 配列

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `indexer:status`

インデクサーのステータスを表示

```bash
bin/magento indexer:status [<index>...]
```


### `index`

すべてのインデックスに適用する場合は、インデックスタイプのスペース区切りリストを指定するか、省略します。

- デフォルト： `[]`

- 配列

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `info:adminuri`

Magento管理 URI を表示

```bash
bin/magento info:adminuri
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `info:backups:list`

使用可能なバックアップファイルの一覧を印刷します

```bash
bin/magento info:backups:list
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `info:currency:list`

使用可能な通貨のリストを表示します

```bash
bin/magento info:currency:list
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `info:dependencies:show-framework`

Magento・フレームワークへの依存関係の数を表示

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

### `--output`, `-o`

レポートファイル名

- デフォルト： `framework-dependencies.csv`
- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `info:dependencies:show-modules`

モジュール間の依存関係の数を表示

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

### `--output`, `-o`

レポートファイル名

- デフォルト： `modules-dependencies.csv`
- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


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

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `info:language:list`

使用可能な言語ロケールのリストを表示します

```bash
bin/magento info:language:list
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `info:timezone:list`

使用可能なタイムゾーンのリストを表示します

```bash
bin/magento info:timezone:list
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `inventory:reservation:create-compensations`

指定された報酬引数で予約を作成

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```


### `compensations`

報酬引数のリスト（形式「 」）&lt;order_increment_id>:&lt;sku>:&lt;quantity>:&lt;stock-id>&quot;

- デフォルト： `[]`

- 配列

### `--raw`, `-r`

生の出力

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `inventory:reservation:list-inconsistencies`

販売可能な数量の不整合を持つすべての注文と製品を表示

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

### `--complete-orders`, `-c`

注文の完了に対して矛盾のみを表示

- デフォルト： `false`
- 値を受け入れない

### `--incomplete-orders`, `-i`

不完全な注文に対して矛盾のみを表示

- デフォルト： `false`
- 値を受け入れない

### `--bunch-size`, `-b`

一度に読み込まれる注文の数を定義します

- デフォルト： `50`
- 値を受け入れる

### `--raw`, `-r`

生の出力

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `inventory-geonames:import`

ソース選択アルゴリズムの地域名をダウンロードおよび読み込みます

```bash
bin/magento inventory-geonames:import <countries>...
```


### `countries`

インポートする国コードのリスト

- デフォルト： `[]`

- 必須
- 配列

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `maintenance:allow-ips`

メンテナンスモードの除外 IP を設定します

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```


### `ip`

許可されている IP アドレス

- デフォルト： `[]`

- 配列

### `--none`

許可されている IP アドレスをクリア

- デフォルト： `false`
- 値を受け入れない

### `--add`

既存のリストに IP アドレスを追加

- デフォルト： `false`
- 値を受け入れない

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `maintenance:disable`

メンテナンスモードを無効にする

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

許可されている IP アドレス（許可されている IP リストをクリアするには「なし」を使用）

- デフォルト： `[]`
- 値が必要です

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `maintenance:enable`

メンテナンスモードを有効にする

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

許可されている IP アドレス（許可されている IP リストをクリアするには「なし」を使用）

- デフォルト： `[]`
- 値が必要です

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `maintenance:status`

メンテナンスモードのステータスを表示

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `media-content:sync`

コンテンツをアセットと同期

```bash
bin/magento media-content:sync
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `media-gallery:sync`

データベース内のメディアストレージとメディアアセットを同期

```bash
bin/magento media-gallery:sync
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `module:config:status`

「app/etc/config.php」ファイル内のモジュール設定をチェックし、最新かどうかを報告します

```bash
bin/magento module:config:status
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `module:disable`

指定したモジュールを無効にします

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

モジュールの名前

- デフォルト： `[]`

- 配列

### `--force`, `-f`

依存関係チェックをバイパス

- デフォルト： `false`
- 値を受け入れない

### `--all`

すべてのモジュールを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--clear-static-content`, `-c`

生成された静的ビューファイルをクリアします。 モジュールに静的ビューファイルがある場合に必要

- デフォルト： `false`
- 値を受け入れない

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `module:enable`

指定したモジュールを有効にする

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

モジュールの名前

- デフォルト： `[]`

- 配列

### `--force`, `-f`

依存関係チェックをバイパス

- デフォルト： `false`
- 値を受け入れない

### `--all`

すべてのモジュールを有効にする

- デフォルト： `false`
- 値を受け入れない

### `--clear-static-content`, `-c`

生成された静的ビューファイルをクリアします。 モジュールに静的ビューファイルがある場合に必要

- デフォルト： `false`
- 値を受け入れない

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `module:status`

モジュールのステータスを表示

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```


### `module-names`

オプションのモジュール名

- デフォルト： `[]`

- 配列

### `--enabled`

有効なモジュールのみを印刷

- デフォルト： `false`
- 値を受け入れない

### `--disabled`

無効なモジュールのみを印刷

- デフォルト： `false`
- 値を受け入れない

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `module:uninstall`

Composer によってインストールされたモジュールをアンインストールします

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
- 値を受け入れない

### `--backup-code`

コードと設定ファイルのバックアップ（一時ファイルを除く）を作成する

- デフォルト： `false`
- 値を受け入れない

### `--backup-media`

メディアのバックアップを取る

- デフォルト： `false`
- 値を受け入れない

### `--backup-db`

完全なデータベースバックアップを作成

- デフォルト： `false`
- 値を受け入れない

### `--non-composer`

ここで過去になるすべてのモジュールは、非コンポーザーベースです

- デフォルト： `false`
- 値を受け入れない

### `--clear-static-content`, `-c`

生成された静的ビューファイルをクリアします。 モジュールに静的ビューファイルがある場合に必要

- デフォルト： `false`
- 値を受け入れない

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `newrelic:create:deploy-marker`

エントリのデプロイキューをチェックし、適切なデプロイマーカーを作成します。

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```


### `message`

メッセージをデプロイしますか？

- 必須

### `change_log`

変更ログを表示しますか？

- 必須

### `user`

デプロイメントユーザ


### `revision`

リビジョン


### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `queue:consumers:list`

MessageQueue コンシューマーのリスト

```bash
bin/magento queue:consumers:list
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `queue:consumers:start`

MessageQueue コンシューマーを開始

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```


### `consumer`

開始するコンシューマーの名前。

- 必須

### `--max-messages`

プロセスが終了する前に消費者が処理するメッセージの数。 指定されていない場合 — キューに登録されているすべてのメッセージを処理した後に終了します。

- 値が必要です

### `--batch-size`

バッチあたりのメッセージ数。 バッチ・コンシューマにのみ適用されます。

- 値が必要です

### `--area-code`

優先領域（global、adminhtml など）のデフォルトは global です。

- 値が必要です

### `--single-thread`

このオプションを使用すると、1 つのコンシューマーの複数のコピーを同時に実行できなくなります。

- デフォルト： `false`
- 値を受け入れない

### `--multi-process`

コンシューマーごとのプロセスの数。

- 値を受け入れる

### `--pid-file-path`

PID を保存するためのファイルパス（このオプションは廃止されています。代わりに —single-thread を使用してください）

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `remote-storage:sync`

メディアファイルをリモートストレージと同期します。

```bash
bin/magento remote-storage:sync
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `sampledata:deploy`

コンポーザーベースのインストール用のサンプルデータモジュールのMagento

```bash
bin/magento sampledata:deploy [--no-update]
```

### `--no-update`

composer の更新を実行せずに composer.json を更新

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `sampledata:remove`

composer.json からすべてのサンプルデータパッケージを削除します。

```bash
bin/magento sampledata:remove [--no-update]
```

### `--no-update`

composer の更新を実行せずに composer.json を更新

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `sampledata:reset`

再インストール用にすべてのサンプルデータモジュールをリセット

```bash
bin/magento sampledata:reset
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `security:recaptcha:disable-for-user-forgot-password`

管理者ユーザーのパスワードを忘れた場合の reCAPTCHA を無効にします

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `security:recaptcha:disable-for-user-login`

管理者ユーザーログインフォームの reCAPTCHA を無効にする

```bash
bin/magento security:recaptcha:disable-for-user-login
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


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

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `security:tfa:providers`

使用可能なすべてのプロバイダーのリスト

```bash
bin/magento security:tfa:providers
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


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

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:backup`

Magento・アプリケーション・コード・ベース、メディア、データベースのバックアップを作成

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code`

コードと設定ファイルのバックアップ（一時ファイルを除く）を作成する

- デフォルト： `false`
- 値を受け入れない

### `--media`

メディアのバックアップを取る

- デフォルト： `false`
- 値を受け入れない

### `--db`

完全なデータベースバックアップを作成

- デフォルト： `false`
- 値を受け入れない

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:config:set`

デプロイメント設定を作成または変更します

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

バックエンドの frontname （見つからない場合は自動生成されます）

- 値が必要です

### `--enable-debug-logging`

デバッグログを有効にする

- 値が必要です

### `--enable-syslog-logging`

syslog ログを有効にする

- 値が必要です

### `--remote-storage-driver`

リモートストレージドライバ

- 値が必要です

### `--remote-storage-prefix`

リモートストレージのプレフィックス

- デフォルト：&quot;
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

リモートストレージアクセスキー

- デフォルト：&quot;
- 値が必要です

### `--remote-storage-secret`

リモートストレージの秘密鍵

- デフォルト：&quot;
- 値が必要です

### `--remote-storage-path-style`

リモートストレージパスのスタイル

- デフォルト： `0`
- 値が必要です

### `--amqp-host`

Amqp サーバーホスト

- デフォルト：&quot;
- 値が必要です

### `--amqp-port`

Amqp サーバーポート

- デフォルト： `5672`
- 値が必要です

### `--amqp-user`

Amqp サーバーのユーザー名

- デフォルト：&quot;
- 値が必要です

### `--amqp-password`

Amqp サーバーのパスワード

- デフォルト：&quot;
- 値が必要です

### `--amqp-virtualhost`

Amqp virtualhost

- デフォルト： `/`
- 値が必要です

### `--amqp-ssl`

Amqp SSL

- デフォルト：&quot;
- 値が必要です

### `--amqp-ssl-options`

Amqp SSL オプション (JSON)

- デフォルト：&quot;
- 値が必要です

### `--consumers-wait-for-messages`

コンシューマーはキューからのメッセージを待つ必要がありますか？ 1 — はい、0 — いいえ

- 値が必要です

### `--queue-default-connection`

メッセージキューのデフォルト接続。 「db」、「amqp」、またはカスタムキューシステムを指定できます。キューシステムをインストールして設定する必要があります。設定しないと、メッセージが正しく処理されません。

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

データベースのコマンドの初期セット

- 値が必要です

### `--skip-db-validation`, `-s`

指定した場合、db 接続の検証はスキップされます

- デフォルト： `false`
- 値を受け入れない

### `--http-cache-hosts`

http キャッシュホスト

- 値が必要です

### `--db-ssl-key`

SSL を介した db 接続を確立するためのクライアントキーファイルのフルパス

- デフォルト：&quot;
- 値が必要です

### `--db-ssl-cert`

SSL を介した db 接続を確立するためのクライアント証明書ファイルのフルパス

- デフォルト：&quot;
- 値が必要です

### `--db-ssl-ca`

SSL を介した db 接続を確立するためのサーバー証明書ファイルのフルパス

- デフォルト：&quot;
- 値が必要です

### `--db-ssl-verify`

サーバー証明書の検証

- デフォルト： `false`
- 値を受け入れない

### `--session-save`

セッション保存ハンドラー

- 値が必要です

### `--session-save-redis-host`

UNIX ソケットを使用する場合は、完全修飾ホスト名、IP アドレス、または絶対パス

- 値が必要です

### `--session-save-redis-port`

Redis サーバーのリスンポート

- 値が必要です

### `--session-save-redis-password`

Redis サーバーのパスワード

- 値が必要です

### `--session-save-redis-timeout`

接続タイムアウト（秒）

- 値が必要です

### `--session-save-redis-persistent-id`

永続的な接続を有効にする一意の文字列

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

Redis ログレベル。 値：0 （最も詳細でない）～ 7 （最も詳細な）

- 値が必要です

### `--session-save-redis-max-concurrency`

1 つのセッションでロックを待機できるプロセスの最大数

- 値が必要です

### `--session-save-redis-break-after-frontend`

フロントエンドセッションのロックを解除しようとするまでの待機時間（秒）

- 値が必要です

### `--session-save-redis-break-after-adminhtml`

管理セッションのロックを解除しようとするまでの待機時間（秒）

- 値が必要です

### `--session-save-redis-first-lifetime`

最初の書き込み時の非ボットのセッションの有効期間（秒）（0 を使用して無効にする）

- 値が必要です

### `--session-save-redis-bot-first-lifetime`

最初の書き込み時のボットのセッションの有効期間（秒）（0 を使用して無効にする）

- 値が必要です

### `--session-save-redis-bot-lifetime`

後続の書き込みでのボットのセッションの有効期間（0 を使用して無効にする）

- 値が必要です

### `--session-save-redis-disable-locking`

ロックを無効にします。 値：false（デフォルト）、true

- 値が必要です

### `--session-save-redis-min-lifetime`

Redis 最小セッションの有効期間（秒）

- 値が必要です

### `--session-save-redis-max-lifetime`

Redis の最大セッション有効期間（秒）

- 値が必要です

### `--session-save-redis-sentinel-master`

Redis Sentinel のマスター

- 値が必要です

### `--session-save-redis-sentinel-servers`

Redis Sentinel サーバ、コンマ区切り

- 値が必要です

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel 検証マスター。 値：false （デフォルト）、true

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

Redis サーバーのリスンポート

- 値が必要です

### `--cache-backend-redis-password`

Redis サーバーのパスワード

- 値が必要です

### `--cache-backend-redis-compress-data`

圧縮を無効にするには 0 に設定します（デフォルトは 1、有効）。

- 値が必要です

### `--cache-backend-redis-compression-lib`

使用する圧縮ライブラリ [snappy,lzf,l4z,zstd,gzip] （自動的に決定する場合は空白のままにします）

- 値が必要です

### `--cache-id-prefix`

キャッシュキーの ID プレフィックス

- 値が必要です

### `--allow-parallel-generation`

ノンブロッキング方式でキャッシュを生成する

- デフォルト： `false`
- 値を受け入れない

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

Redis サーバーのリスンポート

- 値が必要です

### `--page-cache-redis-password`

Redis サーバーのパスワード

- 値が必要です

### `--page-cache-redis-compress-data`

1 に設定すると、フルページキャッシュが圧縮されます（0 に設定すると無効になります）

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

ロックの競合を避けるための、インストール固有のロックプレフィックス

- 値が必要です

### `--lock-zookeeper-host`

Zookeeper クラスターに接続するホストとポート。 例：127.0.0.1:2181

- 値が必要です

### `--lock-zookeeper-path`

Zookeeper がロックを保存するパス。 デフォルトのパスは次のとおりです。/magento/locks

- 値が必要です

### `--lock-file-path`

ファイルロックが保存されるパス。

- 値が必要です

### `--document-root-is-pub`

表示するフラグは、ルート上にあるパブです。true または false のみを指定できます

- 値が必要です

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:db-data:upgrade`

DB 内のデータのインストールとアップグレード

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:db-declaration:generate-patch`

パッチを生成し、特定のフォルダーに配置します。

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

パッチが元に戻せるかどうかを確認します。

- デフォルト： `false`
- 値を受け入れる

### `--type`

生成するパッチのタイプを確認します。 使用可能な値： `data`, `schema`.

- デフォルト： `data`
- 値を受け入れる

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:db-declaration:generate-whitelist`

宣言インストーラーで編集可能なテーブルと列のホワイトリストを生成

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

### `--module-name`

ホワイトリストが生成されるモジュールの名前

- デフォルト： `all`
- 値を受け入れる

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:db-schema:upgrade`

DB スキーマをインストールおよびアップグレードします

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--convert-old-scripts`

古いスクリプト (InstallSchema、UpgradeSchema) を db_schema.xml 形式に変換できます

- デフォルト： `false`
- 値を受け入れる

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:db:status`

DB スキーマまたはデータがアップグレードを必要とするかどうかを確認します

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:di:compile`

DI 設定と、自動生成可能なすべての欠落したクラスを生成します

```bash
bin/magento setup:di:compile
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:install`

Magento

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

バックエンドの frontname （見つからない場合は自動生成されます）

- 値が必要です

### `--enable-debug-logging`

デバッグログを有効にする

- 値が必要です

### `--enable-syslog-logging`

syslog ログを有効にする

- 値が必要です

### `--remote-storage-driver`

リモートストレージドライバ

- 値が必要です

### `--remote-storage-prefix`

リモートストレージのプレフィックス

- デフォルト：&quot;
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

リモートストレージアクセスキー

- デフォルト：&quot;
- 値が必要です

### `--remote-storage-secret`

リモートストレージの秘密鍵

- デフォルト：&quot;
- 値が必要です

### `--remote-storage-path-style`

リモートストレージパスのスタイル

- デフォルト： `0`
- 値が必要です

### `--amqp-host`

Amqp サーバーホスト

- デフォルト：&quot;
- 値が必要です

### `--amqp-port`

Amqp サーバーポート

- デフォルト： `5672`
- 値が必要です

### `--amqp-user`

Amqp サーバーのユーザー名

- デフォルト：&quot;
- 値が必要です

### `--amqp-password`

Amqp サーバーのパスワード

- デフォルト：&quot;
- 値が必要です

### `--amqp-virtualhost`

Amqp virtualhost

- デフォルト： `/`
- 値が必要です

### `--amqp-ssl`

Amqp SSL

- デフォルト：&quot;
- 値が必要です

### `--amqp-ssl-options`

Amqp SSL オプション (JSON)

- デフォルト：&quot;
- 値が必要です

### `--consumers-wait-for-messages`

コンシューマーはキューからのメッセージを待つ必要がありますか？ 1 — はい、0 — いいえ

- 値が必要です

### `--queue-default-connection`

メッセージキューのデフォルト接続。 「db」、「amqp」、またはカスタムキューシステムを指定できます。キューシステムをインストールして設定する必要があります。設定しないと、メッセージが正しく処理されません。

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

データベースのコマンドの初期セット

- 値が必要です

### `--skip-db-validation`, `-s`

指定した場合、db 接続の検証はスキップされます

- デフォルト： `false`
- 値を受け入れない

### `--http-cache-hosts`

http キャッシュホスト

- 値が必要です

### `--db-ssl-key`

SSL を介した db 接続を確立するためのクライアントキーファイルのフルパス

- デフォルト：&quot;
- 値が必要です

### `--db-ssl-cert`

SSL を介した db 接続を確立するためのクライアント証明書ファイルのフルパス

- デフォルト：&quot;
- 値が必要です

### `--db-ssl-ca`

SSL を介した db 接続を確立するためのサーバー証明書ファイルのフルパス

- デフォルト：&quot;
- 値が必要です

### `--db-ssl-verify`

サーバー証明書の検証

- デフォルト： `false`
- 値を受け入れない

### `--session-save`

セッション保存ハンドラー

- 値が必要です

### `--session-save-redis-host`

UNIX ソケットを使用する場合は、完全修飾ホスト名、IP アドレス、または絶対パス

- 値が必要です

### `--session-save-redis-port`

Redis サーバーのリスンポート

- 値が必要です

### `--session-save-redis-password`

Redis サーバーのパスワード

- 値が必要です

### `--session-save-redis-timeout`

接続タイムアウト（秒）

- 値が必要です

### `--session-save-redis-persistent-id`

永続的な接続を有効にする一意の文字列

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

Redis ログレベル。 値：0 （最も詳細でない）～ 7 （最も詳細な）

- 値が必要です

### `--session-save-redis-max-concurrency`

1 つのセッションでロックを待機できるプロセスの最大数

- 値が必要です

### `--session-save-redis-break-after-frontend`

フロントエンドセッションのロックを解除しようとするまでの待機時間（秒）

- 値が必要です

### `--session-save-redis-break-after-adminhtml`

管理セッションのロックを解除しようとするまでの待機時間（秒）

- 値が必要です

### `--session-save-redis-first-lifetime`

最初の書き込み時の非ボットのセッションの有効期間（秒）（0 を使用して無効にする）

- 値が必要です

### `--session-save-redis-bot-first-lifetime`

最初の書き込み時のボットのセッションの有効期間（秒）（0 を使用して無効にする）

- 値が必要です

### `--session-save-redis-bot-lifetime`

後続の書き込みでのボットのセッションの有効期間（0 を使用して無効にする）

- 値が必要です

### `--session-save-redis-disable-locking`

ロックを無効にします。 値：false（デフォルト）、true

- 値が必要です

### `--session-save-redis-min-lifetime`

Redis 最小セッションの有効期間（秒）

- 値が必要です

### `--session-save-redis-max-lifetime`

Redis の最大セッション有効期間（秒）

- 値が必要です

### `--session-save-redis-sentinel-master`

Redis Sentinel のマスター

- 値が必要です

### `--session-save-redis-sentinel-servers`

Redis Sentinel サーバ、コンマ区切り

- 値が必要です

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel 検証マスター。 値：false （デフォルト）、true

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

Redis サーバーのリスンポート

- 値が必要です

### `--cache-backend-redis-password`

Redis サーバーのパスワード

- 値が必要です

### `--cache-backend-redis-compress-data`

圧縮を無効にするには 0 に設定します（デフォルトは 1、有効）。

- 値が必要です

### `--cache-backend-redis-compression-lib`

使用する圧縮ライブラリ [snappy,lzf,l4z,zstd,gzip] （自動的に決定する場合は空白のままにします）

- 値が必要です

### `--cache-id-prefix`

キャッシュキーの ID プレフィックス

- 値が必要です

### `--allow-parallel-generation`

ノンブロッキング方式でキャッシュを生成する

- デフォルト： `false`
- 値を受け入れない

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

Redis サーバーのリスンポート

- 値が必要です

### `--page-cache-redis-password`

Redis サーバーのパスワード

- 値が必要です

### `--page-cache-redis-compress-data`

1 に設定すると、フルページキャッシュが圧縮されます（0 に設定すると無効になります）

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

ロックの競合を避けるための、インストール固有のロックプレフィックス

- 値が必要です

### `--lock-zookeeper-host`

Zookeeper クラスターに接続するホストとポート。 例：127.0.0.1:2181

- 値が必要です

### `--lock-zookeeper-path`

Zookeeper がロックを保存するパス。 デフォルトのパスは次のとおりです。/magento/locks

- 値が必要です

### `--lock-file-path`

ファイルロックが保存されるパス。

- 値が必要です

### `--document-root-is-pub`

表示するフラグは、ルート上にあるパブです。true または false のみを指定できます

- 値が必要です

### `--base-url`

ストアを使用できると想定される URL。 非推奨です。パス web/unsecure/base_url で config:set を使用してください

- 値が必要です

### `--language`

デフォルトの言語コード。 廃止されました。パス general/locale/code で config:set を使用してください

- 値が必要です

### `--timezone`

デフォルトのタイムゾーンコード。 廃止されました。パス general/locale/timezone で config:set を使用してください

- 値が必要です

### `--currency`

デフォルトの通貨コード。 廃止されました。パス currency/options/base、currency/options/default および currency/options/allow で config:set を使用してください

- 値が必要です

### `--use-rewrites`

書き換えを使用します。 廃止されました。パス web/seo/use_rewrites で config:set を使用してください

- 値が必要です

### `--use-secure`

セキュア URL を使用します。 SSL が使用可能な場合にのみ、このオプションを有効にします。 廃止されました。パス web/secure/use_in_frontend で config:set を使用してください

- 値が必要です

### `--base-url-secure`

SSL 接続のベース URL。 廃止されました。パス web/secure/base_url で config:set を使用してください

- 値が必要です

### `--use-secure-admin`

SSL で管理インターフェイスを実行します。 廃止されました。パス web/secure/use_in_adminhtml で config:set を使用してください

- 値が必要です

### `--admin-use-security-key`

Magento管理 URL とフォームの「セキュリティキー」機能を使用するかどうか。 廃止されました。パス admin/security/use_form_key で config:set を使用してください

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

検索エンジン。 値：elasticsearch5, elasticsearch6, elasticsearch7

- 値が必要です

### `--elasticsearch-host`

Elasticsearchサーバーホスト。

- 値が必要です

### `--elasticsearch-port`

Elasticsearchサーバーポート。

- 値が必要です

### `--elasticsearch-enable-auth`

認証を有効にするには、1 に設定します。 （デフォルトは 0、無効）

- 値が必要です

### `--elasticsearch-username`

Elasticsearchユーザー名。 HTTP 認証が有効な場合にのみ適用されます

- 値が必要です

### `--elasticsearch-password`

Elasticsearchパスワード。 HTTP 認証が有効な場合にのみ適用されます

- 値が必要です

### `--elasticsearch-index-prefix`

Elasticsearchインデックスのプレフィックス。

- 値が必要です

### `--elasticsearch-timeout`

Elasticsearchサーバーのタイムアウト。

- 値が必要です

### `--cleanup-database`

インストール前にデータベースをクリーンアップする

- デフォルト： `false`
- 値を受け入れない

### `--sales-order-increment-prefix`

販売注文番号のプレフィックス

- 値が必要です

### `--use-sample-data`

サンプルデータを使用

- デフォルト： `false`
- 値を受け入れない

### `--enable-modules`

コンマ区切りのモジュール名のリスト。 インストール時に含める必要があります。 使用可能なマジックパラメーター「all」。

- 値を受け入れる

### `--disable-modules`

コンマ区切りのモジュール名のリスト。 インストール時には避ける必要があります。 使用可能なマジックパラメーター「all」。

- 値を受け入れる

### `--convert-old-scripts`

古いスクリプト (InstallSchema、UpgradeSchema) を db_schema.xml 形式に変換できます

- デフォルト： `false`
- 値を受け入れる

### `--interactive`, `-i`

インタラクティブMagentoのインストール

- デフォルト： `false`
- 値を受け入れない

### `--safe-mode`

列の削除など、破壊的な操作に対するダンプを含むMagentoの安全なインストール

- 値を受け入れる

### `--data-restore`

ダンプから削除されたデータを復元

- 値を受け入れる

### `--dry-run`

Magentoのインストールは、ドライランモードで実行されます

- デフォルト： `false`
- 値を受け入れる

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:performance:generate-fixtures`

器具を生成

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```


### `profile`

プロファイル設定ファイルのパス

- 必須

### `--skip-reindex`, `-s`

再インデックスをスキップ

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:rollback`

Magento・アプリケーション・コードベース、メディア、データベースをロールバックします。

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code-file`, `-c`

var/backups 内のコードバックアップファイルのベース名

- 値が必要です

### `--media-file`, `-m`

var/backups 内のメディアバックアップファイルのベース名

- 値が必要です

### `--db-file`, `-d`

var/backups 内の db バックアップ・ファイルのベース名

- 値が必要です

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:static-content:deploy`

静的ビューファイルをデプロイします

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
- 値を受け入れない

### `--strategy`, `-s`

指定した方法を使用してファイルをデプロイします。

- デフォルト： `quick`
- 値を受け入れる

### `--area`, `-a`

指定した領域に対してのみファイルを生成します。

- デフォルト： `all`
- 複数の値を受け入れる

### `--exclude-area`

指定した領域に対してファイルを生成しないでください。

- デフォルト： `none`
- 複数の値を受け入れる

### `--theme`, `-t`

指定したテーマのみに静的ビューファイルを生成します。

- デフォルト： `all`
- 複数の値を受け入れる

### `--exclude-theme`

指定したテーマのファイルを生成しないでください。

- デフォルト： `none`
- 複数の値を受け入れる

### `--language`, `-l`

指定した言語のファイルのみを生成します。

- デフォルト： `all`
- 複数の値を受け入れる

### `--exclude-language`

指定した言語のファイルを生成しないでください。

- デフォルト： `none`
- 複数の値を受け入れる

### `--jobs`, `-j`

指定したジョブ数を使用して並列処理を有効にします。

- デフォルト： `0`
- 値を受け入れる

### `--max-execution-time`

デプロイメント静的プロセスの予想最大実行時間（秒）です。

- デフォルト： `900`
- 値を受け入れる

### `--symlink-locale`

これらのロケールのファイルの symlink を作成します。このファイルはデプロイ用に渡されますが、カスタマイズは行われません。

- デフォルト： `false`
- 値を受け入れない

### `--content-version`

静的コンテンツのカスタムバージョンは、複数のノードでデプロイメントを実行する場合に使用でき、静的コンテンツのバージョンが同じで、キャッシュが正しく機能することを確認できます。

- 値が必要です

### `--refresh-content-version-only`

静的コンテンツのバージョンの更新は、ブラウザーキャッシュと CDN キャッシュの静的コンテンツを更新する場合にのみ使用できます。

- デフォルト： `false`
- 値を受け入れない

### `--no-javascript`

JavaScript ファイルをデプロイしないでください。

- デフォルト： `false`
- 値を受け入れない

### `--no-js-bundle`

JavaScript バンドルファイルをデプロイしないでください。

- デフォルト： `false`
- 値を受け入れない

### `--no-css`

CSS ファイルをデプロイしないでください。

- デフォルト： `false`
- 値を受け入れない

### `--no-less`

LESS ファイルをデプロイしないでください。

- デフォルト： `false`
- 値を受け入れない

### `--no-images`

画像をデプロイしないでください。

- デフォルト： `false`
- 値を受け入れない

### `--no-fonts`

フォントファイルを展開しないでください。

- デフォルト： `false`
- 値を受け入れない

### `--no-html`

HTML・ファイルを展開しない。

- デフォルト： `false`
- 値を受け入れない

### `--no-misc`

他のタイプのファイル（.md、.jbf、.csv など）をデプロイしないでください。

- デフォルト： `false`
- 値を受け入れない

### `--no-html-minify`

HTMLファイルを縮小しない。

- デフォルト： `false`
- 値を受け入れない

### `--no-parent`

親テーマをコンパイルしないでください。 迅速で標準的な戦略でのみサポートされます。

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:store-config:set`

ストア設定をインストールします。 2.2.0 以降で非推奨です。代わりに、config:set を使用してください。

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--base-url`

ストアを使用できると想定される URL。 非推奨です。パス web/unsecure/base_url で config:set を使用してください

- 値が必要です

### `--language`

デフォルトの言語コード。 廃止されました。パス general/locale/code で config:set を使用してください

- 値が必要です

### `--timezone`

デフォルトのタイムゾーンコード。 廃止されました。パス general/locale/timezone で config:set を使用してください

- 値が必要です

### `--currency`

デフォルトの通貨コード。 廃止されました。パス currency/options/base、currency/options/default および currency/options/allow で config:set を使用してください

- 値が必要です

### `--use-rewrites`

書き換えを使用します。 廃止されました。パス web/seo/use_rewrites で config:set を使用してください

- 値が必要です

### `--use-secure`

セキュア URL を使用します。 SSL が使用可能な場合にのみ、このオプションを有効にします。 廃止されました。パス web/secure/use_in_frontend で config:set を使用してください

- 値が必要です

### `--base-url-secure`

SSL 接続のベース URL。 廃止されました。パス web/secure/base_url で config:set を使用してください

- 値が必要です

### `--use-secure-admin`

SSL で管理インターフェイスを実行します。 廃止されました。パス web/secure/use_in_adminhtml で config:set を使用してください

- 値が必要です

### `--admin-use-security-key`

Magento管理 URL とフォームの「セキュリティキー」機能を使用するかどうか。 廃止されました。パス admin/security/use_form_key で config:set を使用してください

- 値が必要です

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:uninstall`

アプリケーションをアンMagento

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `setup:upgrade`

Magento・アプリケーション、DB データ、スキーマをアップグレード

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--keep-generated`

生成されたファイルが削除されないようにします。 実稼動環境にデプロイする場合を除き、このオプションを使用することはお勧めしません。 詳しくは、システムインテグレーターまたは管理者にお問い合わせください。

- デフォルト： `false`
- 値を受け入れない

### `--convert-old-scripts`

古いスクリプト (InstallSchema、UpgradeSchema) を db_schema.xml 形式に変換できます

- デフォルト： `false`
- 値を受け入れる

### `--safe-mode`

列の削除など、破壊的な操作に対するダンプを含むMagentoの安全なインストール

- 値を受け入れる

### `--data-restore`

ダンプから削除されたデータを復元

- 値を受け入れる

### `--dry-run`

Magentoのインストールは、ドライランモードで実行されます

- デフォルト： `false`
- 値を受け入れる

### `--magento-init-params`

任意のコマンドに追加して、Magento初期化パラメータをカスタマイズします。次に例を示します。&quot;MAGE_MODE=developer&amp;MAGE_DIRS[ベース][path]=/var/www/example.com&amp;MAGE_DIRS[キャッシュ][path]=/var/tmp/cache&quot;

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `store:list`

店舗のリストを表示

```bash
bin/magento store:list
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `store:website:list`

Web サイトのリストを表示します

```bash
bin/magento store:website:list
```

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `theme:uninstall`

テーマをアンインストール

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```


### `theme`

テーマのパス。 テーマのパスは、領域/ベンダー/名前のフルパスとして指定する必要があります。 例： frontend/blank

- デフォルト： `[]`

- 必須
- 配列

### `--backup-code`

コードのバックアップを作成（一時ファイルを除く）

- デフォルト： `false`
- 値を受け入れない

### `--clear-static-content`, `-c`

生成された静的ビューファイルをクリアします。

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `varnish:vcl:generate`

Vanish VCL を生成し、コマンドラインにエコーします

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

### `--access-list`

Vanish をパージできる IP アクセスリスト

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

Vanish ファイルのバージョン

- デフォルト： `4`
- 値が必要です

### `--grace-period`

猶予期間（秒）

- デフォルト： `300`
- 値が必要です

### `--output-file`

vcl を書き込むファイルのパス

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

- デフォルト： `false`
- 値を受け入れない

### `--quiet`, `-q`

メッセージを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる：通常の出力の場合は 1、より詳細な出力の場合は 2、デバッグの場合は 3

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--ansi`

ANSI 出力を強制

- デフォルト： `false`
- 値を受け入れない

### `--no-ansi`

ANSI 出力を無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない
