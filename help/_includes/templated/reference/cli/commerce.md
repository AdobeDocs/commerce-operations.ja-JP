---
source-git-commit: a5777f437430bc48b87aaea65c0e101d4ecd6574
workflow-type: tm+mt
source-wordcount: '19002'
ht-degree: 0%

---
# magento-cloud(Adobe Commerce on cloud infrastructure)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**バージョン**:1.38.1 <!-- app.version -->

このリファレンスには、 `magento-cloud` コマンドラインツールを使用します。
最初のリストは、 `magento-cloud list` コマンドを使用して

>[!NOTE]
>
>この参照は、アプリケーションのコードベースから生成されます。 コンテンツを変更するには、 [codebase](https://github.com/magento) リポジトリを作成し、変更をレビュー用に送信します。 もう 1 つの方法は、次の操作です。 _フィードバックを提供_ （右上にあるリンクを見つけます）。 貢献のガイドラインについては、 [コード貢献](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_completion`

BASH 完了フック。

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--generate-hook`, `-g`



このアプリケーションの完了を設定する BASH コードを生成します。
- デフォルト： `false`
- 値を受け入れない



### `--program`, `-p`



プログラムの完了に必要なトリガー名 &lt;comment>（デフォルトはアプリケーションの絶対パス）&lt;/comment>.
- 値が必要です



### `--multiple`, `-m`



生成されたフックは、複数のアプリケーションで使用できます。
- デフォルト： `false`
- 値を受け入れない


### `--shell-type`

シェルタイプ（zsh または bash）を設定します。 それ以外の場合は、これは自動的に決定されます。
- 値を受け入れる <!-- options --> <!-- options.size -->

## `bot`

Magentoクラウドボット

```bash
magento-cloud bot [--party] [--parrot]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--party`


- デフォルト： `false`
- 値を受け入れない


### `--parrot`


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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `clear-cache`

CLI キャッシュをクリアする

```bash
magento-cloud clear-cache
```

<!-- app.name -->

```bash
clearcache
```

<!-- app.name -->

```bash
cc
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



このヘルプメッセージを表示
- デフォルト： `false`
- 値を受け入れない



### `--quiet`, `-q`



メッセージを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--verbose`, `-v|-vv|-vvv`



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `decode`

エンコードされた文字列 ( 例えば、MAGENTO_CLOUD_VARIABLES) をデコードする

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```

<!-- app.name --> <!-- command.usage -->

### `value`

デコードする変数値
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



変数内で表示するプロパティ
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `docs`

オンラインドキュメントを開く

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```

<!-- app.name --> <!-- command.usage -->

### `search`

検索語句

- デフォルト： `[]`

- 配列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--browser`

URL を開くために使用するブラウザー。 なしには 0 を設定します。
- 値が必要です


### `--pipe`

URL を stdout に出力します。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `help`

コマンドのヘルプを表示します

```bash
help [--format FORMAT] [--raw] [--] [<command_name>]
```

<!-- app.name --> <!-- command.usage -->

### `command_name`

コマンド名
- デフォルト： `help`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `legacy-migrate`

従来のファイル構造からの移行

```bash
magento-cloud legacy-migrate [--no-backup]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-backup`

プロジェクトのバックアップを作成しないでください。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `list`

コマンドを一覧表示

```bash
list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```

<!-- app.name --> <!-- command.usage -->

### `namespace`

名前空間名
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

生のコマンドリストを出力するには
- デフォルト： `false`
- 値を受け入れない


### `--format`

出力形式 (txt、xml、json、md)
- デフォルト： `txt`
- 値が必要です <!-- options --> <!-- options.size -->

## `multi`

複数のプロジェクトでコマンドを実行する

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd>
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

実行するコマンド
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--projects`, `-p`



プロジェクト ID のリスト（コンマや空白で区切る）
- 値が必要です


### `--continue`

例外が発生した場合でもコマンドの実行を続行する
- デフォルト： `false`
- 値を受け入れない


### `--sort`

プロジェクトオプションのリストを並べ替えるプロパティ
- デフォルト： `title`
- 値が必要です


### `--reverse`

プロジェクトオプションの順序を逆にする
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `web`

Web UI を開く

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--browser`

URL を開くために使用するブラウザー。 なしには 0 を設定します。
- 値が必要です


### `--pipe`

URL を stdout に出力します。
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `welcome`

Magentoクラウドへようこそ

```bash
magento-cloud welcome
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



このヘルプメッセージを表示
- デフォルト： `false`
- 値を受け入れない



### `--quiet`, `-q`



メッセージを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--verbose`, `-v|-vv|-vvv`



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `winky`



```bash
magento-cloud winky
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



このヘルプメッセージを表示
- デフォルト： `false`
- 値を受け入れない



### `--quiet`, `-q`



メッセージを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--verbose`, `-v|-vv|-vvv`



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `activity:cancel`

アクティビティのキャンセル

```bash
magento-cloud activity:cancel [--type TYPE] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

アクティビティ ID。 デフォルトで、キャンセル可能な最新のアクティビティに設定されます。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

タイプでフィルター（デフォルトのアクティビティを選択する場合）
- 値が必要です



### `--all`, `-a`



すべての環境で最近のアクティビティを確認する（デフォルトのアクティビティを選択する場合）
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `activity:get`

単一のアクティビティの詳細情報の表示

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

アクティビティ ID。 デフォルトで、最新のアクティビティに設定されます。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



表示するプロパティ
- 値が必要です


### `--type`

タイプでフィルター（デフォルトのアクティビティを選択する場合）
- 値が必要です


### `--state`

状態でフィルター（デフォルトのアクティビティを選択する場合）:in_progress、pending、complete または cancelled
- デフォルト： `[]`
- 値が必要です


### `--result`

結果でフィルター（デフォルトのアクティビティを選択する場合）:成功または失敗
- 値が必要です



### `--incomplete`, `-i`



（デフォルトのアクティビティを選択する場合）不完全なアクティビティのみを含めます。 これはの略記法です &lt;info>—state=in_progress,pending&lt;/info>
- デフォルト： `false`
- 値を受け入れない



### `--all`, `-a`



すべての環境で最近のアクティビティを確認する（デフォルトのアクティビティを選択する場合）
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `activity:list`

環境またはプロジェクトのアクティビティのリストの取得

```bash
magento-cloud activity:list [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
activities
```

<!-- app.name -->

```bash
act
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

タイプによるアクティビティのフィルタリング
- 値が必要です


### `--limit`

表示する結果の数を制限
- デフォルト： `10`
- 値が必要です


### `--start`

この日付より前に作成されたアクティビティのみが表示されます
- 値が必要です


### `--state`

状態でアクティビティをフィルター：in_progress、pending、complete または cancelled
- デフォルト： `[]`
- 値が必要です


### `--result`

結果でアクティビティをフィルター：成功または失敗
- 値が必要です



### `--incomplete`, `-i`



不完全なアクティビティのみをリスト
- デフォルト： `false`
- 値を受け入れない



### `--all`, `-a`



すべての環境のアクティビティのリスト
- デフォルト： `false`
- 値を受け入れない


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `activity:log`

アクティビティのログを表示

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

アクティビティ ID。 デフォルトで、最新のアクティビティに設定されます。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

アクティビティの更新間隔（秒）。 更新を無効にするには、0 に設定します。
- デフォルト： `3`
- 値が必要です



### `--timestamps`, `-t`



各メッセージの横にタイムスタンプを表示
- デフォルト： `false`
- 値を受け入れない


### `--type`

タイプでフィルター（デフォルトのアクティビティを選択する場合）
- 値が必要です


### `--state`

状態でフィルター（デフォルトのアクティビティを選択する場合）:in_progress、pending、complete または cancelled
- デフォルト： `[]`
- 値が必要です


### `--result`

結果でフィルター（デフォルトのアクティビティを選択する場合）:成功または失敗
- 値が必要です



### `--incomplete`, `-i`



（デフォルトのアクティビティを選択する場合）不完全なアクティビティのみを含めます。 これはの略記法です &lt;info>—state=in_progress,pending&lt;/info>
- デフォルト： `false`
- 値を受け入れない



### `--all`, `-a`



すべての環境で最近のアクティビティを確認する（デフォルトのアクティビティを選択する場合）
- デフォルト： `false`
- 値を受け入れない


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `api:curl`

認証済み cURL リクエストをMagentoCloud API で実行する

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

API パス
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



使用するリクエストメソッド
- 値が必要です



### `--data`, `-d`



送信するデータ
- 値が必要です



### `--include`, `-i`



出力にヘッダーを含める
- デフォルト： `false`
- 値を受け入れない



### `--head`, `-I`



ヘッダーのみを取得
- デフォルト： `false`
- 値を受け入れない


### `--disable-compression`

curl —compressed フラグは使用しないでください
- デフォルト： `false`
- 値を受け入れない


### `--enable-glob`

curl グロビングを有効にする（ —globoff フラグを削除）
- デフォルト： `false`
- 値を受け入れない



### `--header`, `-H`



追加のヘッダー
- デフォルト： `[]`
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `app:config-get`

アプリの設定を表示

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



表示する設定プロパティ
- 値が必要です


### `--refresh`

キャッシュを更新するかどうか
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です



### `--identity-file`, `-i`



[非推奨（廃止予定）のオプション。廃止]
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `app:list`

プロジェクト内のアプリのリスト

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
apps
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

キャッシュを更新するかどうか
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `auth:api-token-login`

API トークンを使用してMagentoクラウドにログインします。

```bash
magento-cloud auth:api-token-login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



このヘルプメッセージを表示
- デフォルト： `false`
- 値を受け入れない



### `--quiet`, `-q`



メッセージを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--verbose`, `-v|-vv|-vvv`



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `auth:browser-login`

ブラウザーを使用してMagentoクラウドにログインします。

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```

<!-- app.name -->

```bash
login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



既にログインしている場合でも、再度ログインする
- デフォルト： `false`
- 値を受け入れない


### `--browser`

URL を開くために使用するブラウザー。 なしには 0 を設定します。
- 値が必要です


### `--pipe`

URL を stdout に出力します。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `auth:info`

アカウント情報を表示

```bash
magento-cloud auth:info [-P|--property PROPERTY] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<property>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

表示するアカウントプロパティ
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



表示するアカウントプロパティ（代替構文）
- 値が必要です


### `--refresh`

キャッシュを更新するかどうか
- デフォルト： `false`
- 値を受け入れない


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `auth:logout`

Magentoクラウドからログアウト

```bash
magento-cloud logout [-a|--all] [--other]
```

<!-- app.name -->

```bash
logout
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



すべてのローカルセッションからログアウト
- デフォルト： `false`
- 値を受け入れない


### `--other`

他のローカルセッションからログアウト
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 非推奨 ]&lt;/> ユーザー名とパスワードを使用してMagentoクラウドにログインします

```bash
magento-cloud auth:password-login
```

<!-- app.name -->

```bash
auth:login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



このヘルプメッセージを表示
- デフォルト： `false`
- 値を受け入れない



### `--quiet`, `-q`



メッセージを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--verbose`, `-v|-vv|-vvv`



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `auth:token`

MagentoCloud API へのリクエスト用の OAuth 2 アクセストークンの取得

```bash
magento-cloud auth:token
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



このヘルプメッセージを表示
- デフォルト： `false`
- 値を受け入れない



### `--quiet`, `-q`



メッセージを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--verbose`, `-v|-vv|-vvv`



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `blackfire:setup`

プロジェクトのBlackfire.io 統合を設定します

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--server_id`

サーバー ID
- 値が必要です


### `--server_token`

サーバートークン
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `certificate:add`

プロジェクトに SSL 証明書を追加します

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--cert`

証明書ファイルへのパス
- 値が必要です


### `--key`

証明書の秘密鍵ファイルへのパス
- 値が必要です


### `--chain`

証明書チェーンファイルへのパス
- デフォルト： `[]`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `certificate:delete`

プロジェクトから証明書を削除

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

証明書 ID（またはその最初）
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `certificate:get`

証明書を表示

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

証明書 ID（またはその最初）
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



表示する証明書プロパティ
- 値が必要です


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `certificate:list`

プロジェクト証明書のリスト

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
certificates
```

<!-- app.name -->

```bash
certs
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--domain`

ドメイン名でフィルター（大文字と小文字を区別しない検索）
- 値が必要です


### `--exclude-domain`

ドメイン名で一致する証明書を除外する（大文字と小文字を区別しない検索）
- 値が必要です


### `--issuer`

発行者でフィルター
- 値が必要です


### `--only-auto`

自動プロビジョニングされた証明書のみを表示
- デフォルト： `false`
- 値を受け入れない


### `--no-auto`

手動で追加された証明書のみを表示
- デフォルト： `false`
- 値を受け入れない


### `--ignore-expiry`

期限切れ証明書と期限切れでない証明書の両方を表示
- デフォルト： `false`
- 値を受け入れない


### `--only-expired`

期限切れの証明書のみを表示
- デフォルト： `false`
- 値を受け入れない


### `--no-expired`

期限切れでない証明書のみを表示（デフォルト）
- デフォルト： `false`
- 値を受け入れない


### `--pipe-domains`

証明書でカバーされるドメイン名の一覧のみを返す
- デフォルト： `false`
- 値を受け入れない


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `commit:get`

コミットの詳細を表示

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<commit>]
```

<!-- app.name --> <!-- command.usage -->

### `commit`

コミット SHA。 また、親コミットの&quot;HEAD&quot;、キャレット (^) またはチルダ (～) のサフィックスを受け付けることもできます。
- デフォルト： `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



表示するコミットプロパティ。
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
- 値が必要です


### `--format`

非推奨
- 値が必要です


### `--columns`

非推奨
- デフォルト： `[]`
- 値が必要です


### `--no-header`

非推奨
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `commit:list`

リストのコミット

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```

<!-- app.name -->

```bash
commits
```

<!-- app.name --> <!-- command.usage -->

### `commit`

開始 Git コミット SHA。 また、親コミットの&quot;HEAD&quot;、キャレット (^) またはチルダ (～) のサフィックスを受け付けることもできます。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--limit`

表示するコミット数。
- デフォルト： `10`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `db:dump`

リモートデータベースのローカルダンプを作成する

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
sql-dump
```

<!-- app.name -->

```bash
environment:sql-dump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--schema`

ダンプするスキーマ。 デフォルトのスキーマ（通常は「main」）を使用する場合は省略します。
- 値が必要です



### `--file`, `-f`



ダンプのカスタムファイル名
- 値が必要です



### `--directory`, `-d`



ダンプ用のカスタムディレクトリ
- 値が必要です



### `--gzip`, `-z`



gzip を使用してダンプを圧縮
- デフォルト： `false`
- 値を受け入れない



### `--timestamp`, `-t`



ダンプファイル名にタイムスタンプを追加する
- デフォルト： `false`
- 値を受け入れない



### `--stdout`, `-o`



ファイルではなく STDOUT に出力
- デフォルト： `false`
- 値を受け入れない


### `--table`

含めるテーブル
- デフォルト： `[]`
- 値が必要です


### `--exclude-table`

除外するテーブル
- デフォルト： `[]`
- 値が必要です


### `--schema-only`

スキーマのみをダンプし、データはダウンプしない
- デフォルト： `false`
- 値を受け入れない


### `--charset`

ダンプの文字セットエンコーディング
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です



### `--relationship`, `-r`



使用するサービス関係
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `db:size`

データベースのディスク使用量の見積もり

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



サイズをバイト単位で表示します。
- デフォルト： `false`
- 値を受け入れない



### `--cleanup`, `-C`



テーブルをクリーンアップできるかどうかを確認し、推奨を表示する（InnoDb のみ）。
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です



### `--relationship`, `-r`



使用するサービス関係
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `db:sql`

リモートデータベースで SQL を実行

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```

<!-- app.name -->

```bash
sql
```

<!-- app.name -->

```bash
environment:sql
```

<!-- app.name --> <!-- command.usage -->

### `query`

実行する SQL 文
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

生の非表形式出力を生成する
- デフォルト： `false`
- 値を受け入れない


### `--schema`

使用するスキーマ。 デフォルトのスキーマ（通常は「main」）を使用する場合は省略します。 スキーマを使用しない場合は、空の文字列を渡します。
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です



### `--relationship`, `-r`



使用するサービス関係
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `domain:add`

プロジェクトに新しいドメインを追加

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

ドメイン名
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

このドメインの証明書ファイルへのパス
- 値が必要です


### `--key`

指定した証明書の秘密鍵ファイルへのパス。
- 値が必要です


### `--chain`

指定した証明書の証明書チェーンファイルへのパス
- デフォルト： `[]`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `domain:delete`

プロジェクトからドメインを削除

```bash
magento-cloud domain:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

ドメイン名
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `domain:get`

ドメインの詳細情報を表示

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

ドメイン名
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



表示するドメインプロパティ
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `domain:list`

すべてのドメインのリストを取得する

```bash
magento-cloud domains [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
domains
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `domain:update`

ドメインの更新

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

ドメイン名
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

このドメインの証明書ファイルへのパス
- 値が必要です


### `--key`

指定した証明書の秘密鍵ファイルへのパス。
- 値が必要です


### `--chain`

指定した証明書の証明書チェーンファイルへのパス
- デフォルト： `[]`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:activate`

環境のアクティブ化

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name --> <!-- command.usage -->

### `environment`

アクティブ化する環境

- デフォルト： `[]`

- 配列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--parent`

アクティブ化する前に新しい環境の親を設定
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:branch`

環境の分岐

```bash
magento-cloud branch [--title TITLE] [--force] [--no-clone-parent] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```

<!-- app.name -->

```bash
branch
```

<!-- app.name --> <!-- command.usage -->

### `id`

新しい環境の ID （ブランチ名）
<!-- argument -->

### `parent`

新しい環境の親
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--title`

新しい環境のタイトル
- 値が必要です


### `--force`

ブランチをローカルにチェックアウトできない場合でも、新しい環境を作成します
- デフォルト： `false`
- 値を受け入れない


### `--no-clone-parent`

親ブランチのデータを複製しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
- デフォルト： `false`
- 値を受け入れない



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:checkout`

環境のチェックアウト

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```

<!-- app.name -->

```bash
checkout
```

<!-- app.name --> <!-- command.usage -->

### `id`

チェックアウトする環境の ID。 例：&quot;sprint2&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:delete`

環境の削除

```bash
magento-cloud environment:deactivate [--delete-branch] [--no-delete-branch] [--inactive] [--merged] [--exclude EXCLUDE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name -->

```bash
environment:deactivate
```

<!-- app.name --> <!-- command.usage -->

### `environment`

削除する環境

- デフォルト： `[]`

- 配列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--delete-branch`

リモート Git ブランチも削除します
- デフォルト： `false`
- 値を受け入れない


### `--no-delete-branch`

リモート Git ブランチを削除しないでください
- デフォルト： `false`
- 値を受け入れない


### `--inactive`

非アクティブな環境をすべて削除
- デフォルト： `false`
- 値を受け入れない


### `--merged`

すべての結合環境を削除
- デフォルト： `false`
- 値を受け入れない


### `--exclude`

削除しない環境
- デフォルト： `[]`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:http-access`

環境の HTTP アクセス設定の更新

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
httpaccess
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--access`

「permission:address」形式のアクセス制限。 0 を使用して、すべてのアドレスをクリアします。
- デフォルト： `[]`
- 値が必要です


### `--auth`

HTTP Basic 認証資格情報（「username:password」形式）。 0 を使用してすべての資格情報をクリアします。
- デフォルト： `[]`
- 値が必要です


### `--enabled`

アクセス制御を有効にする必要があるかどうか：1 は有効に、0 は無効にします
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:info`

環境のプロパティの読み取りまたは設定

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
environment:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

プロパティの名前
<!-- argument -->

### `value`

プロパティに新しい値を設定する
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

キャッシュを更新するかどうか
- デフォルト： `false`
- 値を受け入れない


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:init`

パブリック Git リポジトリーから環境を初期化します

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```

<!-- app.name --> <!-- command.usage -->

### `url`

Git リポジトリへの URL
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--profile`

プロファイルの名前
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:list`

環境のリストの取得

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
environments
```

<!-- app.name -->

```bash
env
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--no-inactive`, `-I`



非アクティブな環境を表示しない
- デフォルト： `false`
- 値を受け入れない


### `--pipe`

環境 ID の単純なリストを出力します。
- デフォルト： `false`
- 値を受け入れない


### `--refresh`

リストを更新するかどうか。
- デフォルト： `1`
- 値が必要です


### `--sort`

並べ替えに使用するプロパティ
- デフォルト： `title`
- 値が必要です


### `--reverse`

逆順（降順）に並べ替え
- デフォルト： `false`
- 値を受け入れない


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:logs`

環境のログの読み取り

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [--] [<type>]
```

<!-- app.name -->

```bash
log
```

<!-- app.name -->

```bash
logs
```

<!-- app.name --> <!-- command.usage -->

### `type`

ログのタイプ。例：&quot;access&quot;または&quot;error&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--lines`

表示するライン数
- デフォルト： `100`
- 値が必要です


### `--tail`

ログの末尾を継続的に表示
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です


### `--worker`

作業者名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:merge`

環境の結合

```bash
magento-cloud merge [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
merge
```

<!-- app.name --> <!-- command.usage -->

### `environment`

結合する環境
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:push`

コードを環境にプッシュ

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--branch] [--parent PARENT] [-W|--no-wait] [--wait] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```

<!-- app.name -->

```bash
push
```

<!-- app.name --> <!-- command.usage -->

### `source`

ソース参照：ブランチ名またはコミットハッシュ
- デフォルト： `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

ターゲットブランチ名
- 値が必要です



### `--force`, `-f`



非早送り更新を許可
- デフォルト： `false`
- 値を受け入れない


### `--force-with-lease`

リモートトラッキングブランチが最新の場合に、早送りでない更新を許可します
- デフォルト： `false`
- 値を受け入れない



### `--set-upstream`, `-u`



ターゲット環境をソースブランチのアップストリームとして設定します。
- デフォルト： `false`
- 値を受け入れない


### `--activate`

プッシュ前の環境のアクティブ化
- デフォルト： `false`
- 値を受け入れない


### `--branch`

廃止：—activate のエイリアス
- デフォルト： `false`
- 値を受け入れない


### `--parent`

新しい環境の親を設定します（ —activate または —branch でのみ使用）
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:redeploy`

環境の再デプロイ

```bash
magento-cloud redeploy [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
redeploy
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:relationships`

環境の関係を表示

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```

<!-- app.name -->

```bash
relationships
```

<!-- app.name --> <!-- command.usage -->

### `environment`

環境
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



表示する関係プロパティ
- 値が必要です


### `--refresh`

関係を更新するかどうか
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:scp`

scp を使用して現在の環境との間でファイルをコピーする

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```

<!-- app.name -->

```bash
scp
```

<!-- app.name --> <!-- command.usage -->

### `files`

コピーするファイル。 リモートを使用：リモートの場所を定義するプレフィックス。

- デフォルト： `[]`

- 配列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--recursive`, `-r`



ディレクトリ全体を再帰的にコピーする
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です


### `--worker`

作業者名
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:set-remote`

ブランチにマッピングするリモート環境を設定

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```

<!-- app.name --> <!-- command.usage -->

### `environment`

環境マシン名。 ブランチのマッピングを削除するには 0 に設定します
- 必須

   <!-- argument -->

### `branch`

マッピングする Git ブランチ（デフォルトは現在のブランチ）
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



このヘルプメッセージを表示
- デフォルト： `false`
- 値を受け入れない



### `--quiet`, `-q`



メッセージを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--verbose`, `-v|-vv|-vvv`



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:ssh`

現在の環境に対する SSH

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```

<!-- app.name -->

```bash
ssh
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

環境で実行するコマンド。

- デフォルト： `[]`

- 配列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

SSH URL のみを出力します。
- デフォルト： `false`
- 値を受け入れない


### `--all`

すべての SSH URL を出力します（すべてのアプリ）。
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です


### `--worker`

作業者名
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:synchronize`

環境のコードやデータを親から同期する

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```

<!-- app.name -->

```bash
sync
```

<!-- app.name --> <!-- command.usage -->

### `synchronize`

同期対象：&quot;code&quot;、&quot;data&quot;またはその両方

- デフォルト： `[]`

- 配列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--rebase`

結合する代わりに再ベース化してコードを同期
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:url`

環境のパブリック URL の取得

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
url
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--primary`, `-1`



プライマリルートの URL のみを返す
- デフォルト： `false`
- 値を受け入れない


### `--browser`

URL を開くために使用するブラウザー。 なしには 0 を設定します。
- 値が必要です


### `--pipe`

URL を stdout に出力します。
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `environment:xdebug`

環境で Xdebug へのトンネルを開きます。

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
xdebug
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

ローカルポート
- デフォルト： `9000`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です


### `--worker`

作業者名
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `integration:activity:get`

単一の統合アクティビティの詳細情報の表示

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

統合 ID。 リストから選択するには、空白のままにします。
<!-- argument -->

### `activity`

アクティビティ ID。 デフォルトでは、最新の統合アクティビティに設定されます。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



表示するプロパティ
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



[非推奨のオプション（未使用）]
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `integration:activity:list`

統合のアクティビティのリストの取得

```bash
magento-cloud i:act [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name -->

```bash
i:act
```

<!-- app.name -->

```bash
integration:activities
```

<!-- app.name --> <!-- command.usage -->

### `id`

統合 ID。 リストから選択するには、空白のままにします。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

タイプによるアクティビティのフィルタリング
- 値が必要です


### `--limit`

表示する結果の数を制限
- デフォルト： `10`
- 値が必要です


### `--start`

この日付より前に作成されたアクティビティのみが表示されます
- 値が必要です


### `--state`

状態別のアクティビティのフィルタリング
- デフォルト： `[]`
- 値が必要です


### `--result`

結果でアクティビティをフィルタリング
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



[非推奨のオプション（未使用）]
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `integration:activity:log`

統合アクティビティのログの表示

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

統合 ID。 リストから選択するには、空白のままにします。
<!-- argument -->

### `activity`

アクティビティ ID。 デフォルトでは、最新の統合アクティビティに設定されます。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--timestamps`, `-t`



各メッセージの横にタイムスタンプを表示
- デフォルト： `false`
- 値を受け入れない


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



[非推奨のオプション（未使用）]
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `integration:add`

プロジェクトへの統合の追加

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

統合のタイプ (「bitbucket」、「bitbucket_server」、「github」、「gitlab」、「hipchat」、「webhook」、「health.email」、「health.pagerduty」、「health.slack」、「health.webhook」、「script」)
- 値が必要です


### `--base-url`

サーバーインストールのベース URL
- 値が必要です


### `--username`

ビットバケットサーバーのユーザー名
- 値が必要です


### `--token`

統合のアクセストークン
- 値が必要です


### `--key`

Bitbucket OAuth 消費者キー
- 値が必要です


### `--secret`

Bitbucket OAuth 消費者シークレット
- 値が必要です


### `--server-project`

プロジェクト ( 例：&#39;namespace/repo&#39;)
- 値が必要です


### `--repository`

追跡するリポジトリ ( 例：&#39;所有者/リポジトリ&#39;)
- 値が必要です


### `--build-merge-requests`

GitLab:環境としての結合リクエストの作成
- デフォルト： `true`
- 値が必要です


### `--build-pull-requests`

すべてのプルリクエストを環境として構築
- デフォルト： `true`
- 値が必要です


### `--build-draft-pull-requests`

下書きのプル要求の作成
- デフォルト： `true`
- 値が必要です


### `--build-pull-requests-post-merge`

結合後の状態に基づいてプル要求を作成する
- デフォルト： `false`
- 値が必要です


### `--build-wip-merge-requests`

GitLab:WIP マージ要求の作成
- デフォルト： `true`
- 値が必要です


### `--merge-requests-clone-parent-data`

GitLab:結合リクエストのデータを複製
- デフォルト： `true`
- 値が必要です


### `--pull-requests-clone-parent-data`

プル要求に対する親環境のデータのクローン
- デフォルト： `true`
- 値が必要です


### `--resync-pull-requests`

すべてのビルドでプルリクエスト環境データを再同期
- デフォルト： `false`
- 値が必要です


### `--fetch-branches`

リモートから（非アクティブな環境として）すべてのブランチを取得
- デフォルト： `true`
- 値が必要です


### `--prune-branches`

リモートに存在しないブランチを削除
- デフォルト： `true`
- 値が必要です


### `--room`

HipChat ルーム ID
- 値が必要です


### `--url`

ウェブフック：JSON データを受け取るための URL
- 値が必要です


### `--shared-key`

ウェブフック：JWS 共有秘密鍵
- 値が必要です


### `--file`

アップロードするスクリプトが含まれるローカルファイルの名前
- 値が必要です


### `--events`

実行するイベントのリスト（environment.push など）
- デフォルト： `*`
- 値が必要です


### `--states`

実行する状態のリスト（例： pending、in_progress、complete）
- デフォルト： `complete`
- 値が必要です


### `--environments`

含める環境 ID
- デフォルト： `*`
- 値が必要です


### `--excluded-environments`

除外する環境 ID。
- デフォルト： `[]`
- 値が必要です


### `--from-address`

[オプション] アラートメールのカスタム送信元アドレス
- 値が必要です


### `--recipients`

受信者の E メールアドレス
- デフォルト： `[]`
- 値が必要です


### `--channel`

Slackチャネル
- 値が必要です


### `--routing-key`

PagerDuty ルーティングキー
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `integration:delete`

プロジェクトからの統合の削除

```bash
magento-cloud integration:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

統合 ID。 リストから選択するには、空白のままにします。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `integration:get`

統合の詳細の表示

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

統合 ID。 リストから選択するには、空白のままにします。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



表示する統合プロパティ
- 値を受け入れる


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `integration:list`

プロジェクト統合のリストを表示

```bash
magento-cloud integrations [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
integrations
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `integration:update`

統合の更新

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

更新する統合の ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

統合のタイプ (「bitbucket」、「bitbucket_server」、「github」、「gitlab」、「hipchat」、「webhook」、「health.email」、「health.pagerduty」、「health.slack」、「health.webhook」、「script」)
- 値が必要です


### `--base-url`

サーバーインストールのベース URL
- 値が必要です


### `--username`

ビットバケットサーバーのユーザー名
- 値が必要です


### `--token`

統合のアクセストークン
- 値が必要です


### `--key`

Bitbucket OAuth 消費者キー
- 値が必要です


### `--secret`

Bitbucket OAuth 消費者シークレット
- 値が必要です


### `--server-project`

プロジェクト ( 例：&#39;namespace/repo&#39;)
- 値が必要です


### `--repository`

追跡するリポジトリ ( 例：&#39;所有者/リポジトリ&#39;)
- 値が必要です


### `--build-merge-requests`

GitLab:環境としての結合リクエストの作成
- デフォルト： `true`
- 値が必要です


### `--build-pull-requests`

すべてのプルリクエストを環境として構築
- デフォルト： `true`
- 値が必要です


### `--build-draft-pull-requests`

下書きのプル要求の作成
- デフォルト： `true`
- 値が必要です


### `--build-pull-requests-post-merge`

結合後の状態に基づいてプル要求を作成する
- デフォルト： `false`
- 値が必要です


### `--build-wip-merge-requests`

GitLab:WIP マージ要求の作成
- デフォルト： `true`
- 値が必要です


### `--merge-requests-clone-parent-data`

GitLab:結合リクエストのデータを複製
- デフォルト： `true`
- 値が必要です


### `--pull-requests-clone-parent-data`

プル要求に対する親環境のデータのクローン
- デフォルト： `true`
- 値が必要です


### `--resync-pull-requests`

すべてのビルドでプルリクエスト環境データを再同期
- デフォルト： `false`
- 値が必要です


### `--fetch-branches`

リモートから（非アクティブな環境として）すべてのブランチを取得
- デフォルト： `true`
- 値が必要です


### `--prune-branches`

リモートに存在しないブランチを削除
- デフォルト： `true`
- 値が必要です


### `--room`

HipChat ルーム ID
- 値が必要です


### `--url`

ウェブフック：JSON データを受け取るための URL
- 値が必要です


### `--shared-key`

ウェブフック：JWS 共有秘密鍵
- 値が必要です


### `--file`

アップロードするスクリプトが含まれるローカルファイルの名前
- 値が必要です


### `--events`

実行するイベントのリスト（environment.push など）
- デフォルト： `*`
- 値が必要です


### `--states`

実行する状態のリスト（例： pending、in_progress、complete）
- デフォルト： `complete`
- 値が必要です


### `--environments`

含める環境 ID
- デフォルト： `*`
- 値が必要です


### `--excluded-environments`

除外する環境 ID。
- デフォルト： `[]`
- 値が必要です


### `--from-address`

[オプション] アラートメールのカスタム送信元アドレス
- 値が必要です


### `--recipients`

受信者の E メールアドレス
- デフォルト： `[]`
- 値が必要です


### `--channel`

Slackチャネル
- 値が必要です


### `--routing-key`

PagerDuty ルーティングキー
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `integration:validate`

既存の統合の検証

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

統合 ID。 リストから選択するには、空白のままにします。
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `local:build`

現在のプロジェクトをローカルにビルドする

```bash
magento-cloud build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```

<!-- app.name -->

```bash
build
```

<!-- app.name --> <!-- command.usage -->

### `app`

ビルドするアプリケーションを指定

- デフォルト： `[]`

- 配列 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--abslinks`, `-a`



絶対リンクを使用
- デフォルト： `false`
- 値を受け入れない



### `--source`, `-s`



ソースディレクトリ。 デフォルトでは、現在のプロジェクトのルートに設定されます。
- 値が必要です



### `--destination`, `-d`



各アプリの Web ルートのシンボリックリンク先。 デフォルト：_www
- 値が必要です



### `--copy`, `-c`



ソースからのシンボリックリンクではなく、ビルドディレクトリにコピーします。
- デフォルト： `false`
- 値を受け入れない


### `--clone`

Git を使用して、現在のディレクトリをビルドHEADに複製します
- デフォルト： `false`
- 値を受け入れない


### `--run-deploy-hooks`

デプロイフックまたは post_deploy フックを実行します。
- デフォルト： `false`
- 値を受け入れない


### `--no-clean`

古いビルドを削除しない
- デフォルト： `false`
- 値を受け入れない


### `--no-archive`

ビルドアーカイブを作成または使用しない
- デフォルト： `false`
- 値を受け入れない


### `--no-backup`

以前のビルドをバックアップしない
- デフォルト： `false`
- 値を受け入れない


### `--no-cache`

キャッシュの無効化
- デフォルト： `false`
- 値を受け入れない


### `--no-build-hooks`

ビルド後のフックを実行しない
- デフォルト： `false`
- 値を受け入れない


### `--no-deps`

ビルドの依存関係をローカルにインストールしない
- デフォルト： `false`
- 値を受け入れない


### `--working-copy`

ドラッシュ：単にバージョンをダウンロードするのではなく、git を使用して各 Drupal モジュールのリポジトリのクローンを作成する
- デフォルト： `false`
- 値を受け入れない


### `--concurrency`

ドラッシュ：同時に処理される同時プロジェクト数を設定
- デフォルト： `4`
- 値が必要です


### `--lock`

ドラッシュ：ロックファイルを作成または更新します（Drush バージョン 7 以降でのみ利用可能）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `local:clean`

古いプロジェクトビルドを削除

```bash
magento-cloud clean [--keep KEEP] [--max-age MAX-AGE] [--include-active]
```

<!-- app.name -->

```bash
clean
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--keep`

保持するビルドの最大数
- デフォルト： `5`
- 値が必要です


### `--max-age`

ビルドの最大経過時間（秒）。 設定されていない場合は無視されます。
- 値が必要です


### `--include-active`

アクティブなビルドも削除
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `local:dir`

ローカルプロジェクトのルートを検索

```bash
magento-cloud dir [<subdir>]
```

<!-- app.name -->

```bash
dir
```

<!-- app.name --> <!-- command.usage -->

### `subdir`

検索するサブディレクトリ（「local」、「web」または「shared」）
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



このヘルプメッセージを表示
- デフォルト： `false`
- 値を受け入れない



### `--quiet`, `-q`



メッセージを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--verbose`, `-v|-vv|-vvv`



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `mount:download`

rsync を使用して、マウントからファイルをダウンロード

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



すべてのマウントからダウンロード
- デフォルト： `false`
- 値を受け入れない



### `--mount`, `-m`



マウント（アプリの相対パス）
- 値が必要です


### `--target`

ファイルのダウンロード先ディレクトリ。 —all を使用した場合、マウントパスが追加されます。
- 値が必要です


### `--source-path`

—all を使用する場合は、マウントのソースパス（マウントパスではなく）をターゲットのサブディレクトリとして使用します。
- デフォルト： `false`
- 値を受け入れない


### `--delete`

ターゲットディレクトリ内の不要なファイルを削除するかどうか
- デフォルト： `false`
- 値を受け入れない


### `--exclude`

ダウンロードから除外するファイル（パターン）
- デフォルト： `[]`
- 値が必要です


### `--include`

ダウンロードに含めるファイル（パターン）
- デフォルト： `[]`
- 値が必要です


### `--refresh`

キャッシュを更新するかどうか
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です


### `--worker`

作業者名
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `mount:list`

マウントのリストを取得

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name -->

```bash
mounts
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--paths`

マウント・パスを出力する（1 行に 1 つ）
- デフォルト： `false`
- 値を受け入れない


### `--refresh`

キャッシュを更新するかどうか
- デフォルト： `false`
- 値を受け入れない


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です


### `--worker`

作業者名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `mount:size`

マウントのディスク使用量を確認します。

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



サイズをバイト単位で表示
- デフォルト： `false`
- 値を受け入れない


### `--refresh`

キャッシュの更新
- デフォルト： `false`
- 値を受け入れない


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です


### `--worker`

作業者名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `mount:upload`

rsync を使用してファイルをマウントにアップロード

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--source`

アップロードするファイルを含むディレクトリ
- 値が必要です



### `--mount`, `-m`



マウント（アプリの相対パス）
- 値が必要です


### `--delete`

マウント内の不要なファイルを削除するかどうか
- デフォルト： `false`
- 値を受け入れない


### `--exclude`

アップロードから除外するファイル（パターン）
- デフォルト： `[]`
- 値が必要です


### `--include`

アップロードに含めるファイル（パターン）
- デフォルト： `[]`
- 値が必要です


### `--refresh`

キャッシュを更新するかどうか
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です


### `--worker`

作業者名
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `project:clear-build-cache`

プロジェクトのビルドキャッシュをクリアする

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT] [--host HOST]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `project:curl`

プロジェクトの API で認証済み cURL リクエストを実行する

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [-p|--project PROJECT] [--host HOST] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

API パス
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



使用するリクエストメソッド
- 値が必要です



### `--data`, `-d`



送信するデータ
- 値が必要です



### `--include`, `-i`



出力にヘッダーを含める
- デフォルト： `false`
- 値を受け入れない



### `--head`, `-I`



ヘッダーのみを取得
- デフォルト： `false`
- 値を受け入れない


### `--disable-compression`

curl —compressed フラグは使用しないでください
- デフォルト： `false`
- 値を受け入れない


### `--enable-glob`

curl グロビングを有効にする（ —globoff フラグを削除）
- デフォルト： `false`
- 値を受け入れない



### `--header`, `-H`



追加のヘッダー
- デフォルト： `[]`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `project:get`

プロジェクトをローカルに複製

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [--host HOST] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```

<!-- app.name -->

```bash
get
```

<!-- app.name --> <!-- command.usage -->

### `project`

プロジェクト ID
<!-- argument -->

### `directory`

複製先のディレクトリ。 デフォルトでプロジェクトタイトルに設定されます
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--environment`, `-e`



複製する環境 ID。 デフォルトはプロジェクトのデフォルト、または最初に使用可能な環境です
- 値が必要です


### `--depth`

シャロークローンを作成する：履歴内のコミット数を制限する
- 値が必要です


### `--build`

複製後にプロジェクトを構築
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `project:info`

プロジェクトのプロパティを読み取る、または設定する

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
project:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

プロパティの名前
<!-- argument -->

### `value`

プロパティに新しい値を設定する
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

キャッシュを更新するかどうか
- デフォルト： `false`
- 値を受け入れない


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `project:list`

すべてのアクティブなプロジェクトのリストを取得する

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
projects
```

<!-- app.name -->

```bash
pro
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--pipe`

プロジェクト ID の単純なリストの出力
- デフォルト： `false`
- 値を受け入れない


### `--host`

地域のホスト名でフィルター（完全一致）
- 値が必要です


### `--title`

タイトルでフィルター（大文字と小文字を区別しない検索）
- 値が必要です


### `--my`

所有しているプロジェクトのみを表示
- デフォルト： `false`
- 値を受け入れない


### `--refresh`

リストを更新するかどうか
- デフォルト： `1`
- 値が必要です


### `--sort`

並べ替えに使用するプロパティ
- デフォルト： `title`
- 値が必要です


### `--reverse`

逆順（降順）に並べ替え
- デフォルト： `false`
- 値を受け入れない


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `project:set-remote`

現在の Git リポジトリのリモートプロジェクトを設定

```bash
magento-cloud project:set-remote [<project>]
```

<!-- app.name --> <!-- command.usage -->

### `project`

プロジェクト ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



このヘルプメッセージを表示
- デフォルト： `false`
- 値を受け入れない



### `--quiet`, `-q`



メッセージを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--verbose`, `-v|-vv|-vvv`



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 非推奨 ]&lt;/> プロジェクトから変数を削除

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

変数名
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 非推奨 ]&lt;/> プロジェクトの変数を表示

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name -->

```bash
project-variables
```

<!-- app.name -->

```bash
pvget
```

<!-- app.name -->

```bash
project:variable:list
```

<!-- app.name --> <!-- command.usage -->

### `name`

変数の名前
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

完全な変数値のみを出力します（「名前」を指定する必要があります）
- デフォルト： `false`
- 値を受け入れない


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 非推奨 ]&lt;/> プロジェクトの変数を設定する

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
pvset
```

<!-- app.name --> <!-- command.usage -->

### `name`

変数名
- 必須

   <!-- argument -->

### `value`

変数の値
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

値を JSON としてマーク
- デフォルト： `false`
- 値を受け入れない


### `--no-visible-build`

ビルド時にこの変数を公開しない
- デフォルト： `false`
- 値を受け入れない


### `--no-visible-runtime`

実行時にこの変数を公開しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `repo:cat`

プロジェクトリポジトリ内のファイルを読み取る

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] <path>
```

<!-- app.name --> <!-- command.usage -->

### `path`

ファイルへのパス
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--commit`, `-c`



コミット SHA。 また、親コミットの&quot;HEAD&quot;、キャレット (^) またはチルダ (～) のサフィックスを受け付けることもできます。
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `repo:ls`

プロジェクトリポジトリ内のファイルのリスト

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

サブディレクトリへのパス
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--directories`, `-d`



ディレクトリのみを表示
- デフォルト： `false`
- 値を受け入れない



### `--files`, `-f`



ファイルのみを表示
- デフォルト： `false`
- 値を受け入れない


### `--git-style`

「git ls-tree」に類似したスタイル出力
- デフォルト： `false`
- 値を受け入れない



### `--commit`, `-c`



コミット SHA。 また、親コミットの&quot;HEAD&quot;、キャレット (^) またはチルダ (～) のサフィックスを受け付けることもできます。
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `route:get`

ルートに関する詳細情報の表示

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```

<!-- app.name --> <!-- command.usage -->

### `route`

ルートの元の URL
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--id`

選択するルート ID
- 値が必要です



### `--primary`, `-1`



プライマリルートを選択
- デフォルト： `false`
- 値を受け入れない



### `--property`, `-P`



表示するプロパティ
- 値が必要です


### `--refresh`

ルートのキャッシュをバイパス
- デフォルト： `false`
- 値を受け入れない


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



[非推奨（廃止予定）のオプション。廃止]
- 値が必要です



### `--identity-file`, `-i`



[非推奨（廃止予定）のオプション。廃止]
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `route:list`

環境のすべてのルートのリスト

```bash
magento-cloud routes [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<environment>]
```

<!-- app.name -->

```bash
routes
```

<!-- app.name -->

```bash
environment:routes
```

<!-- app.name --> <!-- command.usage -->

### `environment`

環境 ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

ルートのキャッシュをバイパス
- デフォルト： `false`
- 値を受け入れない


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `self:install`

CLI 構成ファイルをインストールまたは更新

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```

<!-- app.name -->

```bash
local:install
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--shell-type`

オートコンプリーション用のシェルタイプ（bash または zsh）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `self:stats`

GitHub パッケージのダウンロードに関する統計を表示

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--page`, `-p`



ページ番号
- デフォルト： `1`
- 値が必要です



### `--count`, `-c`



1 ページあたりの結果数 ( 最大：100)
- デフォルト： `20`
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `self:update`

CLI を最新バージョンに更新する

```bash
magento-cloud self-update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```

<!-- app.name -->

```bash
self-update
```

<!-- app.name -->

```bash
update
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-major`

マイナーバージョンまたはパッチバージョン間のみ更新
- デフォルト： `false`
- 値を受け入れない


### `--unstable`

新しい不安定なバージョンに更新します（使用可能な場合）
- デフォルト： `false`
- 値を受け入れない


### `--manifest`

マニフェストファイルの場所を上書き
- 値が必要です


### `--current-version`

現在のバージョンを上書き
- 値が必要です


### `--timeout`

バージョンチェックのタイムアウト
- デフォルト： `30`
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `service:list`

プロジェクト内のサービスのリスト

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
services
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

キャッシュを更新するかどうか
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `service:mongo:dump`

MongoDB からデータのバイナリアーカイブダンプを作成する

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongodump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



ダンプするコレクション
- 値が必要です



### `--gzip`, `-z`



gzip を使用してダンプを圧縮
- デフォルト： `false`
- 値を受け入れない



### `--stdout`, `-o`



ファイルではなく STDOUT に出力
- デフォルト： `false`
- 値を受け入れない



### `--relationship`, `-r`



使用するサービス関係
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `service:mongo:export`

MongoDB からのデータのエクスポート

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongoexport
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



書き出すコレクション
- 値が必要です


### `--jsonArray`

データを単一の JSON 配列として書き出し
- デフォルト： `false`
- 値を受け入れない


### `--type`

書き出しタイプ。例：&quot;csv&quot;
- 値が必要です



### `--fields`, `-f`



エクスポートするフィールド
- デフォルト： `[]`
- 値が必要です



### `--relationship`, `-r`



使用するサービス関係
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `service:mongo:restore`

データのバイナリアーカイブダンプを MongoDB に復元

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongorestore
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



復元するコレクション
- 値が必要です



### `--relationship`, `-r`



使用するサービス関係
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `service:mongo:shell`

MongoDB シェルの使用

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongo
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--eval`

JavaScript フラグメントをシェルに渡す
- 値が必要です



### `--relationship`, `-r`



使用するサービス関係
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `service:redis-cli`

Redis CLI へのアクセス

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```

<!-- app.name -->

```bash
redis
```

<!-- app.name --> <!-- command.usage -->

### `args`

Redis コマンドに追加する引数
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--relationship`, `-r`



使用するサービス関係
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ベータ版 ]&lt;/> セッション間の切り替え

```bash
magento-cloud session:switch [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

新しいセッション ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



このヘルプメッセージを表示
- デフォルト： `false`
- 値を受け入れない



### `--quiet`, `-q`



メッセージを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--verbose`, `-v|-vv|-vvv`



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `snapshot:create`

環境のスナップショットを作成する

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
backup
```

<!-- app.name -->

```bash
backup:create
```

<!-- app.name -->

```bash
environment:backup
```

<!-- app.name --> <!-- command.usage -->

### `environment`

環境
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--live`

ライブバックアップ：環境を停止しないでください。 設定した場合、バックアップ中に環境が実行され、接続に対して開かれた状態になります。 これにより、データのバックアップが不整合な状態になるリスクが生じ、ダウンタイムが短縮されます。
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `snapshot:list`

環境の使用可能なスナップショットのリスト

```bash
magento-cloud snapshots [--limit LIMIT] [--start START] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
snapshots
```

<!-- app.name -->

```bash
backups
```

<!-- app.name -->

```bash
backup:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--limit`

リストに表示するスナップショット数を制限
- デフォルト： `10`
- 値が必要です


### `--start`

この日付より前に作成されたスナップショットのみが表示されます
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `snapshot:restore`

環境スナップショットの復元

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```

<!-- app.name -->

```bash
environment:restore
```

<!-- app.name -->

```bash
snapshot:restore
```

<!-- app.name --> <!-- command.usage -->

### `snapshot`

スナップショットの名前。 デフォルトで最新のものに設定されます
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

復元先の環境。 デフォルトでは、スナップショットの現在の環境に設定されます
- 値が必要です


### `--branch-from`

—target がまだ存在しない場合は、新しい環境の親を指定します。
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ベータ版 ]&lt;/> ソース操作を実行します

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```

<!-- app.name --> <!-- command.usage -->

### `operation`

操作名
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--variable`

操作中に設定する変数（形式） &lt;info>type:name=value&lt;/info>
- デフォルト： `[]`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `ssh-cert:info`

現在の SSH 証明書に関する情報を表示

```bash
magento-cloud ssh-cert:info [--no-refresh] [-P|--property PROPERTY] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-refresh`

証明書が無効な場合は更新しない
- デフォルト： `false`
- 値を受け入れない



### `--property`, `-P`



表示する証明書プロパティ
- 値が必要です


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `ssh-cert:load`

SSH 証明書の生成

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh-only`

必要に応じて、証明書の更新のみをおこないます（SSH 設定を記述しないでください）。
- デフォルト： `false`
- 値を受け入れない


### `--new`

証明書の更新を強制
- デフォルト： `false`
- 値を受け入れない


### `--new-key`

[非推奨] 代わりに —new を使用します。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `ssh-key:add`

新しい SSH キーを追加

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

既存の SSH 公開鍵へのパス
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--name`

キーを識別する名前
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `ssh-key:delete`

SSH キーの削除

```bash
magento-cloud ssh-key:delete [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

削除する SSH キーの ID
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



このヘルプメッセージを表示
- デフォルト： `false`
- 値を受け入れない



### `--quiet`, `-q`



メッセージを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--verbose`, `-v|-vv|-vvv`



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `ssh-key:list`

アカウント内の SSH キーのリストを取得する

```bash
magento-cloud ssh-keys [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
ssh-keys
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `subscription:info`

配信登録プロパティの読み取りまたは変更

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<property>] [<value>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

プロパティの名前
<!-- argument -->

### `value`

プロパティに新しい値を設定する
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--id`, `-s`



購読 ID
- 値が必要です


### `--date-fmt`

日付の形式（PHP の日付形式文字列）
- デフォルト： `c`
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `tunnel:close`

SSH トンネルを閉じる

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



すべてのトンネルを閉じる
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `tunnel:info`

SSH トンネルの関係情報を表示

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



表示する関係プロパティ
- 値が必要です



### `--encode`, `-c`



base64 でエンコードされた JSON として出力
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `tunnel:list`

SSH トンネルのリスト

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
tunnels
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



すべてのトンネルを表示
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `tunnel:open`

アプリの関係に対して SSH トンネルを開く

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--gateway-ports`, `-g`



リモートホストからローカル転送ポートへの接続を許可
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `tunnel:single`

1 つのアプリに対する単一の SSH トンネルを開く

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

ローカルポート
- 値が必要です



### `--gateway-ports`, `-g`



リモートホストからローカル転送ポートへの接続を許可
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--app`, `-A`



リモートアプリケーション名
- 値が必要です



### `--relationship`, `-r`



使用するサービス関係
- 値が必要です



### `--identity-file`, `-i`



使用する SSH ID（秘密鍵）
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `user:add`

プロジェクトにユーザーを追加する

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

ユーザーの電子メールアドレス
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



ユーザーのプロジェクトの役割（「管理者」または「閲覧者」）または環境固有の役割 ( 例：&#39;master:contributor&#39;または&#39;stage:viewer&#39;)。 文字%は、環境 ID でワイルドカードとして使用できます。例：&#39;%:viewer&#39;. 役割は省略できます（例： ）。&#39;master:c&#39;.
- デフォルト： `[]`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `user:delete`

プロジェクトからのユーザーの削除

```bash
magento-cloud user:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <email>
```

<!-- app.name --> <!-- command.usage -->

### `email`

ユーザーの電子メールアドレス
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `user:get`

ユーザーの役割の表示

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```

<!-- app.name -->

```bash
user:role
```

<!-- app.name --> <!-- command.usage -->

### `email`

ユーザーの電子メールアドレス
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



ロールレベル（「プロジェクト」または「環境」）
- 値が必要です


### `--pipe`

ロールを stdout に出力します（変更を加えた後）。
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
- デフォルト： `false`
- 値を受け入れない



### `--role`, `-r`



[廃止：user:update を使用してユーザの役割を変更する]
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `user:list`

プロジェクトユーザーのリスト

```bash
magento-cloud users [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
users
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `user:update`

プロジェクトのユーザーの役割を更新

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

ユーザーの電子メールアドレス
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



ユーザーのプロジェクトの役割（「管理者」または「閲覧者」）または環境固有の役割 ( 例：&#39;master:contributor&#39;または&#39;stage:viewer&#39;)。 文字%は、環境 ID でワイルドカードとして使用できます。例：&#39;%:viewer&#39;. 役割は省略できます（例： ）。&#39;master:c&#39;.
- デフォルト： `[]`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `variable:create`

変数の作成

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

変数名
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



変数を設定するレベル（「プロジェクト」または「環境」）
- 値が必要です


### `--name`

変数名
- 値が必要です


### `--value`

変数の値
- 値が必要です


### `--json`

変数が JSON 形式かどうか
- デフォルト： `false`
- 値が必要です


### `--sensitive`

変数が区別されるかどうか
- デフォルト： `false`
- 値が必要です


### `--prefix`

変数名のプレフィックス ( 例：&#39;none&#39;または&#39;env:&#39;)
- デフォルト： `none`
- 値が必要です


### `--enabled`

変数を有効にする必要があるかどうか
- デフォルト： `true`
- 値が必要です


### `--inheritable`

変数が子環境に継承可能かどうか
- デフォルト： `true`
- 値が必要です


### `--visible-build`

ビルド時に変数を表示するかどうか
- デフォルト： `true`
- 値が必要です


### `--visible-runtime`

実行時に変数を表示するかどうか
- デフォルト： `true`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `variable:delete`

変数の削除

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

変数名
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



変数レベル（「プロジェクト」、「環境」、「p」または「e」）
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 非推奨 ]&lt;/> 有効な環境レベル変数を無効にする

```bash
magento-cloud variable:disable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

変数の名前
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 非推奨 ]&lt;/> 無効な環境レベル変数を有効にする

```bash
magento-cloud variable:enable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

変数の名前
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `variable:get`

変数の表示

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```

<!-- app.name -->

```bash
vget
```

<!-- app.name --> <!-- command.usage -->

### `name`

変数の名前
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



単一の変数プロパティを表示する
- 値が必要です



### `--level`, `-l`



変数レベル（「プロジェクト」、「環境」、「p」または「e」）
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です


### `--pipe`

[非推奨のオプション] 変数値のみを出力
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `variable:list`

リスト変数

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
variables
```

<!-- app.name -->

```bash
var
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--level`, `-l`



変数レベル（「プロジェクト」、「環境」、「p」または「e」）
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 非推奨 ]&lt;/> 環境の変数を設定する

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
vset
```

<!-- app.name --> <!-- command.usage -->

### `name`

変数名
- 必須

   <!-- argument -->

### `value`

変数の値
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

値を JSON としてマーク
- デフォルト： `false`
- 値を受け入れない


### `--disabled`

変数を無効としてマークします
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `variable:update`

変数の更新

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

変数名
- 必須

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



変数レベル（「プロジェクト」、「環境」、「p」または「e」）
- 値が必要です


### `--value`

変数の値
- 値が必要です


### `--json`

変数が JSON 形式かどうか
- デフォルト： `false`
- 値が必要です


### `--sensitive`

変数が区別されるかどうか
- デフォルト： `false`
- 値が必要です


### `--enabled`

変数を有効にする必要があるかどうか
- デフォルト： `true`
- 値が必要です


### `--inheritable`

変数が子環境に継承可能かどうか
- デフォルト： `true`
- 値が必要です


### `--visible-build`

ビルド時に変数を表示するかどうか
- デフォルト： `true`
- 値が必要です


### `--visible-runtime`

実行時に変数を表示するかどうか
- デフォルト： `true`
- 値が必要です



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です



### `--no-wait`, `-W`



操作が完了するのを待たない
- デフォルト： `false`
- 値を受け入れない


### `--wait`

操作が完了するまで待ちます（デフォルト）。
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size -->

## `worker:list`

デプロイ済みのすべてのワーカーのリストを取得する

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
workers
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

キャッシュを更新するかどうか
- デフォルト： `false`
- 値を受け入れない



### `--project`, `-p`



プロジェクト ID または URL
- 値が必要です


### `--host`

プロジェクトの API ホスト名
- 値が必要です



### `--environment`, `-e`



環境 ID
- 値が必要です


### `--format`

出力形式（「table」、「csv」、「tsv」または「plain」）
- デフォルト： `table`
- 値が必要です


### `--columns`

表示する列（コンマ区切りのリストまたは複数の値）
- デフォルト： `[]`
- 値が必要です


### `--no-header`

テーブルヘッダーを出力しない
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



メッセージの詳細度を上げる
- デフォルト： `false`
- 値を受け入れない



### `--version`, `-V`



このアプリケーションバージョンを表示
- デフォルト： `false`
- 値を受け入れない



### `--yes`, `-y`



はい/いいえの質問に対しては「はい」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない



### `--no`, `-n`



はい/いいえの質問に対しては「いいえ」と答えます。インタラクションを無効にする
- デフォルト： `false`
- 値を受け入れない <!-- options --> <!-- options.size --> <!-- commands --> <!-- file -->