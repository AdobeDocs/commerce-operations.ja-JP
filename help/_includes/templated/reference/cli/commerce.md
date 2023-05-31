---
source-git-commit: adb585771fb1353614ea600117f18ba8b55b65f0
workflow-type: tm+mt
source-wordcount: '21307'
ht-degree: 0%

---
# magento-cloud(Adobe Commerce on cloud infrastructure)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**バージョン**:1.43.0

このリファレンスには、 `magento-cloud` コマンドラインツールを使用します。
最初のリストは、 `magento-cloud list` クラウドインフラストラクチャ上のAdobe Commerceでコマンドを実行します。

>[!NOTE]
>
>この参照は、アプリケーションのコードベースから生成されます。 コンテンツを変更するには、 [codebase](https://github.com/magento) リポジトリを作成し、変更をレビュー用に送信します。 もう 1 つの方法は、次の操作です。 _フィードバックを提供_ （右上にあるリンクを見つけます）。 貢献のガイドラインについては、 [コード貢献](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `clear-cache`

CLI キャッシュをクリアする

```bash
magento-cloud clear-cache
```

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `decode`

エンコードされた文字列 ( 例えば、MAGENTO_CLOUD_VARIABLES) をデコードする

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```


### `value`

デコードする変数値

- 必須

### `--property`, `-P`

変数内で表示するプロパティ

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `docs`

オンラインドキュメントを開く

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```


### `search`

検索語句

- デフォルト： `[]`

- 配列

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `help`

コマンドのヘルプを表示します

```bash
magento-cloud help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

コマンド名

- デフォルト： `help`


### `--format`

出力形式 (txt、json、md)

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `list`

コマンドを一覧表示

```bash
magento-cloud list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```


### `command`

実行するコマンド

- 必須

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

### `--all`

隠しコマンドを含むすべてのコマンドを表示

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `multi`

複数のプロジェクトでコマンドを実行する

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd> (<cmd>)...
```


### `cmd`

実行するコマンド

- デフォルト： `[]`

- 必須
- 配列

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `web`

Web UI を開く

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

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

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `activity:cancel`

アクティビティのキャンセル

```bash
magento-cloud activity:cancel [--type TYPE] [--exclude-type EXCLUDE-TYPE] [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

アクティビティ ID。 デフォルトで、キャンセル可能な最新のアクティビティに設定されます。


### `--type`

タイプでフィルター（デフォルトのアクティビティを選択する場合）。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。 %または*文字は、そのタイプのワイルドカードとして使用できます。例：&#39;%var%&#39;で変数関連のアクティビティを選択します。

- デフォルト： `[]`
- 値が必要です

### `--exclude-type`

タイプ別に除外（デフォルトのアクティビティを選択する場合） リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。 %または*文字は、タイプを除外するワイルドカードとして使用できます。

- デフォルト： `[]`
- 値が必要です

### `--all`, `-a`

すべての環境で最近のアクティビティを確認する（デフォルトのアクティビティを選択する場合）

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `activity:get`

単一のアクティビティの詳細情報の表示

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```


### `id`

アクティビティ ID。 デフォルトで、最新のアクティビティに設定されます。


### `--property`, `-P`

表示するプロパティ

- 値が必要です

### `--type`

タイプでフィルター（デフォルトのアクティビティを選択する場合）。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。 %または*文字は、そのタイプのワイルドカードとして使用できます。例：&#39;%var%&#39;で変数関連のアクティビティを選択します。

- デフォルト： `[]`
- 値が必要です

### `--exclude-type`

タイプ別に除外（デフォルトのアクティビティを選択する場合） リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。 %または*文字は、タイプを除外するワイルドカードとして使用できます。

- デフォルト： `[]`
- 値が必要です

### `--state`

状態でフィルター（デフォルトのアクティビティを選択する場合）:in_progress、pending、complete または cancelled。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `activity:list`

環境またはプロジェクトのアクティビティのリストの取得

```bash
magento-cloud activity:list [-t|--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--type`, `-t`

タイプでアクティビティをフィルターリストに単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。 %または*文字は、そのタイプのワイルドカードとして使用できます。例：&#39;%var%&#39;で変数関連のアクティビティを選択します。

- デフォルト： `[]`
- 値が必要です

### `--exclude-type`, `-x`

タイプ別にアクティビティを除外します。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。 %または*文字は、タイプを除外するワイルドカードとして使用できます。

- デフォルト： `[]`
- 値が必要です

### `--limit`

表示する結果の数を制限

- デフォルト： `10`
- 値が必要です

### `--start`

この日付より前に作成されたアクティビティのみが表示されます

- 値が必要です

### `--state`

状態でアクティビティをフィルター：in_progress、pending、complete または cancelled。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：id*, created*, description*, progress*, state*, result*, completed, environments, type （* =デフォルトの列） 「+」文字は、デフォルト列のプレースホルダーとして使用できます。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `activity:log`

アクティビティのログを表示

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

アクティビティ ID。 デフォルトで、最新のアクティビティに設定されます。


### `--refresh`

アクティビティの更新間隔（秒）。 更新を無効にするには、0 に設定します。

- デフォルト： `3`
- 値が必要です

### `--timestamps`, `-t`

各メッセージの横にタイムスタンプを表示

- デフォルト： `false`
- 値を受け入れない

### `--type`

タイプでフィルター（デフォルトのアクティビティを選択する場合）。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。 %または*文字は、そのタイプのワイルドカードとして使用できます。例：&#39;%var%&#39;で変数関連のアクティビティを選択します。

- デフォルト： `[]`
- 値が必要です

### `--exclude-type`

タイプ別に除外（デフォルトのアクティビティを選択する場合） リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。 %または*文字は、タイプを除外するワイルドカードとして使用できます。

- デフォルト： `[]`
- 値が必要です

### `--state`

状態でフィルター（デフォルトのアクティビティを選択する場合）:in_progress、pending、complete または cancelled。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `app:config-get`

アプリの設定を表示

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `app:list`

プロジェクト内のアプリのリスト

```bash
magento-cloud app:list [--refresh] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```

### `--refresh`

キャッシュを更新するかどうか

- デフォルト： `false`
- 値を受け入れない

### `--pipe`

アプリ名のリストのみを出力

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：name*, type*, disk, path, size （* =デフォルトの列） 「+」文字は、デフォルト列のプレースホルダーとして使用できます。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `auth:api-token-login`

API トークンを使用してMagentoクラウドにログインします。

```bash
magento-cloud auth:api-token-login
```

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `auth:browser-login`

ブラウザーを使用してMagentoクラウドにログインします。

```bash
magento-cloud auth:browser-login [-f|--force] [--browser BROWSER] [--pipe]
```

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `auth:info`

アカウント情報を表示

```bash
magento-cloud auth:info [--no-auto-login] [-P|--property PROPERTY] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--] [<property>]
```


### `property`

表示するアカウントプロパティ


### `--no-auto-login`

自動ログインをスキップします。 ログインしない場合は何も出力されず、終了コードは 0 になります（他のエラーはないと仮定）。

- デフォルト： `false`
- 値を受け入れない

### `--property`, `-P`

表示するアカウントプロパティ（代替構文）

- 値が必要です

### `--refresh`

キャッシュを更新するかどうか

- デフォルト： `false`
- 値を受け入れない

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `auth:logout`

Magentoクラウドからログアウト

```bash
magento-cloud auth:logout [-a|--all] [--other]
```

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `blackfire:setup`

プロジェクトのBlackfire.io 統合を設定します

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--server_id`

サーバー ID

- 値が必要です

### `--server_token`

サーバートークン

- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `certificate:add`

プロジェクトに SSL 証明書を追加します

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `certificate:delete`

プロジェクトから証明書を削除

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <id>
```


### `id`

証明書 ID（またはその最初）

- 必須

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `certificate:get`

証明書を表示

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--] <id>
```


### `id`

証明書 ID（またはその最初）

- 必須

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

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `certificate:list`

プロジェクト証明書のリスト

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```

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

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：created、domains、expires、id、issuer。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--no-header`

テーブルヘッダーを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `commit:get`

コミットの詳細を表示

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--] [<commit>]
```


### `commit`

コミット SHA。 また、親コミットの&quot;HEAD&quot;、キャレット (^) またはチルダ (～) のサフィックスを受け付けることもできます。

- デフォルト： `HEAD`


### `--property`, `-P`

表示するコミットプロパティ。

- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--date-fmt`

日付の形式（PHP の日付形式文字列）

- デフォルト： `c`
- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `commit:list`

リストのコミット

```bash
magento-cloud commit:list [--limit LIMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```


### `commit`

開始 Git コミット SHA。 また、親コミットの&quot;HEAD&quot;、キャレット (^) またはチルダ (～) のサフィックスを受け付けることもできます。


### `--limit`

表示するコミット数。

- デフォルト： `10`
- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：作成者、日付、sha、概要。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `db:dump`

リモートデータベースのローカルダンプを作成する

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `db:size`

データベースのディスク使用量の見積もり

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

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

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：max、percent_used、used。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `db:sql`

リモートデータベースで SQL を実行

```bash
magento-cloud db:sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```


### `query`

実行する SQL 文


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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `domain:add`

プロジェクトに新しいドメインを追加

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-r|--replace REPLACE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

ドメイン名

- 必須

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

### `--replace`, `-r`

環境のルートでこのドメインが置き換える実稼動ドメイン（実稼動環境以外のドメインで必要）

- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `domain:delete`

プロジェクトからドメインを削除

```bash
magento-cloud domain:delete [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

ドメイン名

- 必須

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `domain:get`

ドメインの詳細情報を表示

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<name>]
```


### `name`

ドメイン名


### `--property`, `-P`

表示するドメインプロパティ

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `domain:list`

すべてのドメインのリストを取得する

```bash
magento-cloud domain:list [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：name*, ssl*, created_at*, registered_name, replacement_for, type, updated_at （* =デフォルトの列） 「+」文字は、デフォルト列のプレースホルダーとして使用できます。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--no-header`

テーブルヘッダーを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `domain:update`

ドメインの更新

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

ドメイン名

- 必須

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:activate`

環境のアクティブ化

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


### `environment`

アクティブ化する環境

- デフォルト： `[]`

- 配列

### `--parent`

アクティブ化する前に新しい環境の親を設定

- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:branch`

環境の分岐

```bash
magento-cloud environment:branch [--title TITLE] [--type TYPE] [--force] [--no-clone-parent] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```


### `id`

新しい環境の ID （ブランチ名）


### `parent`

新しい環境の親


### `--title`

新しい環境のタイトル

- 値が必要です

### `--type`

新しい環境のタイプ

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:checkout`

環境のチェックアウト

```bash
magento-cloud environment:checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```


### `id`

チェックアウトする環境の ID。 例：&quot;sprint2&quot;


### `--identity-file`, `-i`

使用する SSH ID（秘密鍵）

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:delete`

1 つ以上の環境の削除

```bash
magento-cloud environment:delete [--delete-branch] [--no-delete-branch] [--type TYPE] [-t|--only-type ONLY-TYPE] [--exclude EXCLUDE] [--exclude-type EXCLUDE-TYPE] [--inactive] [--merged] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


### `environment`

削除する環境。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`

- 配列

### `--delete-branch`

Git ブランチ（非アクティブな環境）を削除

- デフォルト： `false`
- 値を受け入れない

### `--no-delete-branch`

Git ブランチ（非アクティブな環境）を削除しない

- デフォルト： `false`
- 値を受け入れない

### `--type`

タイプのすべての環境を削除します（選択した他の環境に追加します）リストに単一の値 ( 例：&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--only-type`, `-t`

特定の型の環境のみを削除するリストが単一の値 ( 例：&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--exclude`

削除しない環境。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--exclude-type`

削除しない環境タイプリストに単一の値 ( 例：&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--inactive`

非アクティブな環境をすべて削除（選択した他の環境に追加）

- デフォルト： `false`
- 値を受け入れない

### `--merged`

すべての結合環境を削除（他の選択した環境に追加）

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:http-access`

環境の HTTP アクセス設定の更新

```bash
magento-cloud environment:http-access [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:info`

環境のプロパティの読み取りまたは設定

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```


### `property`

プロパティの名前


### `value`

プロパティに新しい値を設定する


### `--refresh`

キャッシュを更新するかどうか

- デフォルト： `false`
- 値を受け入れない

### `--date-fmt`

日付の形式（PHP の日付形式文字列）

- デフォルト： `c`
- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--no-header`

テーブルヘッダーを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:init`

パブリック Git リポジトリーから環境を初期化します

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```


### `url`

Git リポジトリへの URL

- 必須

### `--profile`

プロファイルの名前

- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:list`

環境のリストの取得

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--type TYPE] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```

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

### `--type`

環境タイプでリストをフィルターします。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：id*, title*, status*, type*, created, machine_name, updated （* =デフォルトの列） 「+」文字は、デフォルト列のプレースホルダーとして使用できます。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--no-header`

テーブルヘッダーを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:logs`

環境のログの読み取り

```bash
magento-cloud environment:logs [--lines LINES] [--tail] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [--] [<type>]
```


### `type`

ログのタイプ。例：&quot;access&quot;または&quot;error&quot;


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

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--app`, `-A`

リモートアプリケーション名

- 値が必要です

### `--worker`

作業者名

- 値が必要です

### `--instance`, `-I`

インスタンス ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:merge`

環境の結合

```bash
magento-cloud environment:merge [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```


### `environment`

結合する環境


### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:push`

コードを環境にプッシュ

```bash
magento-cloud environment:push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--parent PARENT] [--type TYPE] [--no-clone-parent] [-W|--no-wait] [--wait] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```


### `source`

ソース参照：ブランチ名またはコミットハッシュ

- デフォルト： `HEAD`


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

### `--parent`

新しい環境の親を設定します（ —activate と一緒に使用する場合のみ）

- 値が必要です

### `--type`

環境タイプを設定します（ —activate と一緒に使用する場合のみ）

- 値が必要です

### `--no-clone-parent`

親ブランチのデータをクローンしない（ —activate と一緒に使用）

- デフォルト： `false`
- 値を受け入れない

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:redeploy`

環境の再デプロイ

```bash
magento-cloud environment:redeploy [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:relationships`

環境の関係を表示

```bash
magento-cloud environment:relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```


### `environment`

環境


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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:scp`

scp を使用して環境間でファイルをコピーする

```bash
magento-cloud environment:scp [-r|--recursive] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```


### `files`

コピーするファイル。 リモートを使用：リモートの場所を定義するプレフィックス。

- デフォルト： `[]`

- 配列

### `--recursive`, `-r`

ディレクトリ全体を再帰的にコピーする

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

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

### `--instance`, `-I`

インスタンス ID

- 値が必要です

### `--identity-file`, `-i`

使用する SSH ID（秘密鍵）

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:ssh`

現在の環境に対する SSH

```bash
magento-cloud environment:ssh [--pipe] [--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```


### `cmd`

環境で実行するコマンド。

- デフォルト： `[]`

- 配列

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

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--app`, `-A`

リモートアプリケーション名

- 値が必要です

### `--worker`

作業者名

- 値が必要です

### `--instance`, `-I`

インスタンス ID

- 値が必要です

### `--identity-file`, `-i`

使用する SSH ID（秘密鍵）

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:synchronize`

環境のコードやデータを親から同期する

```bash
magento-cloud environment:synchronize [--rebase] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```


### `synchronize`

同期対象：&quot;code&quot;、&quot;data&quot;またはその両方

- デフォルト： `[]`

- 配列

### `--rebase`

結合する代わりに再ベース化してコードを同期

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:url`

環境のパブリック URL の取得

```bash
magento-cloud environment:url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

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

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `environment:xdebug`

環境で Xdebug へのトンネルを開きます。

```bash
magento-cloud environment:xdebug [--port PORT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```

### `--port`

ローカルポート

- デフォルト： `9000`
- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

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

### `--instance`, `-I`

インスタンス ID

- 値が必要です

### `--identity-file`, `-i`

使用する SSH ID（秘密鍵）

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `integration:activity:get`

単一の統合アクティビティの詳細情報の表示

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```


### `integration`

統合 ID。 リストから選択するには、空白のままにします。


### `activity`

アクティビティ ID。 デフォルトでは、最新の統合アクティビティに設定されます。


### `--property`, `-P`

表示するプロパティ

- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

[非推奨のオプション（未使用）]

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `integration:activity:list`

統合のアクティビティのリストの取得

```bash
magento-cloud integration:activity:list [--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

統合 ID。 リストから選択するには、空白のままにします。


### `--type`

タイプでアクティビティをフィルタリングします。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--exclude-type`, `-x`

タイプ別にアクティビティを除外します。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。 %または*文字は、タイプを除外するワイルドカードとして使用できます。

- デフォルト： `[]`
- 値が必要です

### `--limit`

表示する結果の数を制限

- デフォルト： `10`
- 値が必要です

### `--start`

この日付より前に作成されたアクティビティのみが表示されます

- 値が必要です

### `--state`

アクティビティを状態でフィルタリングします。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--result`

結果でアクティビティをフィルタリング

- 値が必要です

### `--incomplete`, `-i`

不完全なアクティビティのみをリスト

- デフォルト： `false`
- 値を受け入れない

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：id*, created*, description*, type*, state*, result*, completed （* =デフォルトの列） 「+」文字は、デフォルト列のプレースホルダーとして使用できます。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--environment`, `-e`

[非推奨のオプション（未使用）]

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `integration:activity:log`

統合アクティビティのログの表示

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```


### `integration`

統合 ID。 リストから選択するには、空白のままにします。


### `activity`

アクティビティ ID。 デフォルトでは、最新の統合アクティビティに設定されます。


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

### `--environment`, `-e`

[非推奨のオプション（未使用）]

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `integration:add`

プロジェクトへの統合の追加

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--bitbucket-url BITBUCKET-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--license-key LICENSE-KEY] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [--category CATEGORY] [--index INDEX] [--sourcetype SOURCETYPE] [--protocol PROTOCOL] [--syslog-host SYSLOG-HOST] [--syslog-port SYSLOG-PORT] [--facility FACILITY] [--message-format MESSAGE-FORMAT] [--auth-mode AUTH-MODE] [--auth-token AUTH-TOKEN] [--verify-tls VERIFY-TLS] [--header HEADER] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--type`

統合のタイプ (「bitbucket」、「bitbucket_server」、「gitlab」、「webhook」、「health.pagerduty」、「health.slack」、「health.webhook」、「httplog」、「script」、「splunk」、「sumologic」、「syslog」)

- 値が必要です

### `--base-url`

サーバーインストールのベース URL

- 値が必要です

### `--bitbucket-url`

Bitbucket Server インストールのベース URL

- 値が必要です

### `--username`

ビットバケットサーバーのユーザー名

- 値が必要です

### `--token`

統合の認証またはアクセストークン

- 値が必要です

### `--key`

Bitbucket OAuth 消費者キー

- 値が必要です

### `--secret`

Bitbucket OAuth 消費者シークレット

- 値が必要です

### `--license-key`

New Relic Logs のライセンスキー

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

### `--url`

統合の URL または API エンドポイント

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

### `--category`

フィルタリングに使用する Sumo ロジックカテゴリ

- 値が必要です

### `--index`

Splunk のインデックス

- 値が必要です

### `--sourcetype`

Splunk イベントソースタイプ

- 値が必要です

### `--protocol`

Syslog トランスポートプロトコル (&#39;tcp&#39;、&#39;udp&#39;、&#39;tls&#39;)

- デフォルト： `tls`
- 値が必要です

### `--syslog-host`

Syslog リレー/コレクタホスト

- 値が必要です

### `--syslog-port`

Syslog リレー/コレクタポート

- 値が必要です

### `--facility`

Syslog 機能

- デフォルト： `1`
- 値が必要です

### `--message-format`

Syslog メッセージ形式（「rfc3164」または「rfc5424」）

- デフォルト： `rfc5424`
- 値が必要です

### `--auth-mode`

認証モード（「prefix」または「structured_data」）

- デフォルト： `prefix`
- 値が必要です

### `--auth-token`

認証トークン

- 値が必要です

### `--verify-tls`

HTTPS 証明書の検証を有効にするかどうか（推奨）

- デフォルト： `true`
- 値が必要です

### `--header`

ヘッダーリクエストで使用する HTTPPOST。 名前と値はコロン (:) で区切ります。

- デフォルト： `[]`
- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `integration:delete`

プロジェクトからの統合の削除

```bash
magento-cloud integration:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

統合 ID。 リストから選択するには、空白のままにします。


### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `integration:get`

統合の詳細の表示

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<id>]
```


### `id`

統合 ID。 リストから選択するには、空白のままにします。


### `--property`, `-P`

表示する統合プロパティ

- 値を受け入れる

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--no-header`

テーブルヘッダーを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `integration:list`

プロジェクト統合のリストを表示

```bash
magento-cloud integration:list [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：id、summary、type。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--no-header`

テーブルヘッダーを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `integration:update`

統合の更新

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--bitbucket-url BITBUCKET-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--license-key LICENSE-KEY] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [--category CATEGORY] [--index INDEX] [--sourcetype SOURCETYPE] [--protocol PROTOCOL] [--syslog-host SYSLOG-HOST] [--syslog-port SYSLOG-PORT] [--facility FACILITY] [--message-format MESSAGE-FORMAT] [--auth-mode AUTH-MODE] [--auth-token AUTH-TOKEN] [--verify-tls VERIFY-TLS] [--header HEADER] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

更新する統合の ID


### `--type`

統合のタイプ (「bitbucket」、「bitbucket_server」、「gitlab」、「webhook」、「health.pagerduty」、「health.slack」、「health.webhook」、「httplog」、「script」、「splunk」、「sumologic」、「syslog」)

- 値が必要です

### `--base-url`

サーバーインストールのベース URL

- 値が必要です

### `--bitbucket-url`

Bitbucket Server インストールのベース URL

- 値が必要です

### `--username`

ビットバケットサーバーのユーザー名

- 値が必要です

### `--token`

統合の認証またはアクセストークン

- 値が必要です

### `--key`

Bitbucket OAuth 消費者キー

- 値が必要です

### `--secret`

Bitbucket OAuth 消費者シークレット

- 値が必要です

### `--license-key`

New Relic Logs のライセンスキー

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

### `--url`

統合の URL または API エンドポイント

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

### `--category`

フィルタリングに使用する Sumo ロジックカテゴリ

- 値が必要です

### `--index`

Splunk のインデックス

- 値が必要です

### `--sourcetype`

Splunk イベントソースタイプ

- 値が必要です

### `--protocol`

Syslog トランスポートプロトコル (&#39;tcp&#39;、&#39;udp&#39;、&#39;tls&#39;)

- デフォルト： `tls`
- 値が必要です

### `--syslog-host`

Syslog リレー/コレクタホスト

- 値が必要です

### `--syslog-port`

Syslog リレー/コレクタポート

- 値が必要です

### `--facility`

Syslog 機能

- デフォルト： `1`
- 値が必要です

### `--message-format`

Syslog メッセージ形式（「rfc3164」または「rfc5424」）

- デフォルト： `rfc5424`
- 値が必要です

### `--auth-mode`

認証モード（「prefix」または「structured_data」）

- デフォルト： `prefix`
- 値が必要です

### `--auth-token`

認証トークン

- 値が必要です

### `--verify-tls`

HTTPS 証明書の検証を有効にするかどうか（推奨）

- デフォルト： `true`
- 値が必要です

### `--header`

ヘッダーリクエストで使用する HTTPPOST。 名前と値はコロン (:) で区切ります。

- デフォルト： `[]`
- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `integration:validate`

既存の統合の検証

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--] [<id>]
```


### `id`

統合 ID。 リストから選択するには、空白のままにします。


### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `local:build`

現在のプロジェクトをローカルにビルドする

```bash
magento-cloud local:build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```


### `app`

ビルドするアプリケーションを指定

- デフォルト： `[]`

- 配列

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `local:dir`

ローカルプロジェクトのルートを検索

```bash
magento-cloud local:dir [<subdir>]
```


### `subdir`

検索するサブディレクトリ（「local」、「web」または「shared」）


### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `metrics:all`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;> ベータ版 &lt;/> 環境の CPU、ディスク、メモリの指標を表示する

```bash
magento-cloud metrics [-r|--range RANGE] [-i|--interval INTERVAL] [--to TO] [-1|--latest] [-s|--service SERVICE] [--type TYPE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

### `--range`, `-r`

時間範囲。 指標は、終了時刻 (—to) まで、この期間で読み込まれます。 次の単位を指定できます。時間 (h)、分 (m)、秒 (s) のいずれかです。 最小 &lt;comment>5 分&lt;/comment>，最大 &lt;comment>8 時間&lt;/comment> （プロジェクトに応じて）デフォルト &lt;comment>10m&lt;/comment>.

- 値が必要です

### `--interval`, `-i`

時間間隔。 デフォルトでは、範囲の除算に設定されます。 次の単位を指定できます。時間 (h)、分 (m)、秒 (s) のいずれかです。 最小 &lt;comment>1 分&lt;/comment>，最大 &lt;comment>1 時間&lt;/comment>.

- 値が必要です

### `--to`

終了時間。 デフォルトは現在です。

- 値が必要です

### `--latest`, `-1`

最新の単一のデータポイントのみを表示

- デフォルト： `false`
- 値を受け入れない

### `--service`, `-s`

サービス名またはアプリケーション名でフィルター%文字または*文字をワイルドカードとして使用できます。

- デフォルト： `[]`
- 値が必要です

### `--type`

サービスタイプでフィルターします（ —service が指定されていない場合）。 バージョンは不要です。 ワイルドカードとして%または*文字を使用できます。

- デフォルト： `[]`
- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：timestamp*, service*, cpu_percent*, mem_percent*, disk_percent*, tmp_disk_percent*, cpu_used, disk_limit, disk_used, inodes_limit, inodes_used, inodes_percent, mem_limit, mem_disk_used, tm_d_disk_us, tmp_limit, tmp_in, tmp_i_i タイプ（* =デフォルトの列） 「+」文字は、デフォルト列のプレースホルダーとして使用できます。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `metrics:cpu`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;> ベータ版 &lt;/> 環境の CPU 使用量を表示する

```bash
magento-cloud metrics:cpu [-r|--range RANGE] [-i|--interval INTERVAL] [--to TO] [-1|--latest] [-s|--service SERVICE] [--type TYPE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

### `--range`, `-r`

時間範囲。 指標は、終了時刻 (—to) まで、この期間で読み込まれます。 次の単位を指定できます。時間 (h)、分 (m)、秒 (s) のいずれかです。 最小 &lt;comment>5 分&lt;/comment>，最大 &lt;comment>8 時間&lt;/comment> （プロジェクトに応じて）デフォルト &lt;comment>10m&lt;/comment>.

- 値が必要です

### `--interval`, `-i`

時間間隔。 デフォルトでは、範囲の除算に設定されます。 次の単位を指定できます。時間 (h)、分 (m)、秒 (s) のいずれかです。 最小 &lt;comment>1 分&lt;/comment>，最大 &lt;comment>1 時間&lt;/comment>.

- 値が必要です

### `--to`

終了時間。 デフォルトは現在です。

- 値が必要です

### `--latest`, `-1`

最新の単一のデータポイントのみを表示

- デフォルト： `false`
- 値を受け入れない

### `--service`, `-s`

サービス名またはアプリケーション名でフィルター%文字または*文字をワイルドカードとして使用できます。

- デフォルト： `[]`
- 値が必要です

### `--type`

サービスタイプでフィルターします（ —service が指定されていない場合）。 バージョンは不要です。 ワイルドカードとして%または*文字を使用できます。

- デフォルト： `[]`
- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：timestamp*, service*, used*, limit*,%*, type （* =デフォルトの列） 「+」文字は、デフォルト列のプレースホルダーとして使用できます。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `metrics:disk-usage`

環境のディスク使用量を表示

```bash
magento-cloud metrics:disk-usage [-B|--bytes] [-r|--range RANGE] [-i|--interval INTERVAL] [--to TO] [-1|--latest] [-s|--service SERVICE] [--type TYPE] [--tmp] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

### `--bytes`, `-B`

サイズをバイト単位で表示

- デフォルト： `false`
- 値を受け入れない

### `--range`, `-r`

時間範囲。 指標は、終了時刻 (—to) まで、この期間で読み込まれます。 次の単位を指定できます。時間 (h)、分 (m)、秒 (s) のいずれかです。 最小 &lt;comment>5 分&lt;/comment>，最大 &lt;comment>8 時間&lt;/comment> （プロジェクトに応じて）デフォルト &lt;comment>10m&lt;/comment>.

- 値が必要です

### `--interval`, `-i`

時間間隔。 デフォルトでは、範囲の除算に設定されます。 次の単位を指定できます。時間 (h)、分 (m)、秒 (s) のいずれかです。 最小 &lt;comment>1 分&lt;/comment>，最大 &lt;comment>1 時間&lt;/comment>.

- 値が必要です

### `--to`

終了時間。 デフォルトは現在です。

- 値が必要です

### `--latest`, `-1`

最新の単一のデータポイントのみを表示

- デフォルト： `false`
- 値を受け入れない

### `--service`, `-s`

サービス名またはアプリケーション名でフィルター%文字または*文字をワイルドカードとして使用できます。

- デフォルト： `[]`
- 値が必要です

### `--type`

サービスタイプでフィルターします（ —service が指定されていない場合）。 バージョンは不要です。 ワイルドカードとして%または*文字を使用できます。

- デフォルト： `[]`
- 値が必要です

### `--tmp`

一時ディスク使用量をレポートします ( 列を表示します：タイムスタンプ、サービス、tmp_used、tmp_limit、tmp_percent、tmp_ipercent)

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：timestamp*, service*, used*, limit*, %*, ipercent*, tmp_percent*, ilimit, iused, tmp_ilimit, tmp_ipercent, tmp_iused, tmp_limit, tmp_used, type （* =デフォルトの列） 「+」文字は、デフォルト列のプレースホルダーとして使用できます。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `metrics:memory`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;> ベータ版 &lt;/> 環境のメモリ使用量を表示する

```bash
magento-cloud metrics:memory [-B|--bytes] [-r|--range RANGE] [-i|--interval INTERVAL] [--to TO] [-1|--latest] [-s|--service SERVICE] [--type TYPE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

### `--bytes`, `-B`

サイズをバイト単位で表示

- デフォルト： `false`
- 値を受け入れない

### `--range`, `-r`

時間範囲。 指標は、終了時刻 (—to) まで、この期間で読み込まれます。 次の単位を指定できます。時間 (h)、分 (m)、秒 (s) のいずれかです。 最小 &lt;comment>5 分&lt;/comment>，最大 &lt;comment>8 時間&lt;/comment> （プロジェクトに応じて）デフォルト &lt;comment>10m&lt;/comment>.

- 値が必要です

### `--interval`, `-i`

時間間隔。 デフォルトでは、範囲の除算に設定されます。 次の単位を指定できます。時間 (h)、分 (m)、秒 (s) のいずれかです。 最小 &lt;comment>1 分&lt;/comment>，最大 &lt;comment>1 時間&lt;/comment>.

- 値が必要です

### `--to`

終了時間。 デフォルトは現在です。

- 値が必要です

### `--latest`, `-1`

最新の単一のデータポイントのみを表示

- デフォルト： `false`
- 値を受け入れない

### `--service`, `-s`

サービス名またはアプリケーション名でフィルター%文字または*文字をワイルドカードとして使用できます。

- デフォルト： `[]`
- 値が必要です

### `--type`

サービスタイプでフィルターします（ —service が指定されていない場合）。 バージョンは不要です。 ワイルドカードとして%または*文字を使用できます。

- デフォルト： `[]`
- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：timestamp*, service*, used*, limit*,%*, type （* =デフォルトの列） 「+」文字は、デフォルト列のプレースホルダーとして使用できます。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `mount:download`

rsync を使用して、マウントからファイルをダウンロード

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```

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

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--app`, `-A`

リモートアプリケーション名

- 値が必要です

### `--worker`

作業者名

- 値が必要です

### `--instance`, `-I`

インスタンス ID

- 値が必要です

### `--identity-file`, `-i`

使用する SSH ID（秘密鍵）

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `mount:list`

マウントのリストを取得

```bash
magento-cloud mount:list [--paths] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE]
```

### `--paths`

マウント・パスを出力する（1 行に 1 つ）

- デフォルト： `false`
- 値を受け入れない

### `--refresh`

キャッシュを更新するかどうか

- デフォルト： `false`
- 値を受け入れない

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：定義、パス。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--no-header`

テーブルヘッダーを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

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

### `--instance`, `-I`

インスタンス ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `mount:size`

マウントのディスク使用量を確認します。

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE]
```

### `--bytes`, `-B`

サイズをバイト単位で表示

- デフォルト： `false`
- 値を受け入れない

### `--refresh`

キャッシュの更新

- デフォルト： `false`
- 値を受け入れない

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：available, max, mounts, percent_used, sizes, used. ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--app`, `-A`

リモートアプリケーション名

- 値が必要です

### `--worker`

作業者名

- 値が必要です

### `--instance`, `-I`

インスタンス ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `mount:upload`

rsync を使用してファイルをマウントにアップロード

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```

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

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--app`, `-A`

リモートアプリケーション名

- 値が必要です

### `--worker`

作業者名

- 値が必要です

### `--instance`, `-I`

インスタンス ID

- 値が必要です

### `--identity-file`, `-i`

使用する SSH ID（秘密鍵）

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `project:clear-build-cache`

プロジェクトのビルドキャッシュをクリアする

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT]
```

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `project:get`

プロジェクトをローカルに複製

```bash
magento-cloud project:get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```


### `project`

プロジェクト ID


### `directory`

複製先のディレクトリ。 デフォルトでプロジェクトタイトルに設定されます


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

### `--identity-file`, `-i`

使用する SSH ID（秘密鍵）

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `project:info`

プロジェクトのプロパティを読み取る、または設定する

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```


### `property`

プロパティの名前


### `value`

プロパティに新しい値を設定する


### `--refresh`

キャッシュを更新するかどうか

- デフォルト： `false`
- 値を受け入れない

### `--date-fmt`

日付の形式（PHP の日付形式文字列）

- デフォルト： `c`
- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--no-header`

テーブルヘッダーを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `project:list`

すべてのアクティブなプロジェクトのリストを取得する

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

### `--pipe`

プロジェクト ID の単純なリストを出力します。 ページネーションを無効にします。

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

### `--page`

ページ番号。 これにより、設定や —count にもかかわらず、ページネーションが有効になります。 —pipe を指定した場合は無視されます。

- 値が必要です

### `--count`, `-c`

1 ページに表示するプロジェクトの数。 0 を使用すると、ページネーションが無効になります。 —page が指定されている場合は無視されます。

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`

表示する列。 使用可能な列：id*, title*, region*, created_at, endpoint, organization_id, organization_label, organization_name, region_label, status, ui_url （* =デフォルトの列）. 「+」文字は、デフォルト列のプレースホルダーとして使用できます。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `project:set-remote`

現在の Git リポジトリのリモートプロジェクトを設定

```bash
magento-cloud project:set-remote [<project>]
```


### `project`

プロジェクト ID


### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `repo:cat`

プロジェクトリポジトリ内のファイルを読み取る

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] <path>
```


### `path`

ファイルへのパス

- 必須

### `--commit`, `-c`

コミット SHA。 また、親コミットの&quot;HEAD&quot;、キャレット (^) またはチルダ (～) のサフィックスを受け付けることもできます。

- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `repo:ls`

プロジェクトリポジトリ内のファイルのリスト

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

サブディレクトリへのパス


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

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `repo:read`

プロジェクトリポジトリ内のディレクトリまたはファイルを読み取る

```bash
magento-cloud repo:read [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

ディレクトリまたはファイルへのパス


### `--commit`, `-c`

コミット SHA。 また、親コミットの&quot;HEAD&quot;、キャレット (^) またはチルダ (～) のサフィックスを受け付けることもできます。

- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `route:get`

ルートに関する詳細情報の表示

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```


### `route`

ルートの元の URL


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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `route:list`

環境のすべてのルートのリスト

```bash
magento-cloud route:list [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<environment>]
```


### `environment`

環境 ID


### `--refresh`

ルートのキャッシュをバイパス

- デフォルト： `false`
- 値を受け入れない

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：route*、type*、to*、url （* =デフォルトの列）。 「+」文字は、デフォルト列のプレースホルダーとして使用できます。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--no-header`

テーブルヘッダーを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `self:install`

CLI 構成ファイルをインストールまたは更新

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```

### `--shell-type`

オートコンプリーション用のシェルタイプ（bash または zsh）

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `self:update`

CLI を最新バージョンに更新する

```bash
magento-cloud self:update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `service:list`

プロジェクト内のサービスのリスト

```bash
magento-cloud service:list [--refresh] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```

### `--refresh`

キャッシュを更新するかどうか

- デフォルト： `false`
- 値を受け入れない

### `--pipe`

サービス名のリストのみを出力

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：ディスク、名前、サイズ、タイプ。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `service:mongo:dump`

MongoDB からデータのバイナリアーカイブダンプを作成する

```bash
magento-cloud service:mongo:dump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `service:mongo:export`

MongoDB からのデータのエクスポート

```bash
magento-cloud service:mongo:export [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `service:mongo:restore`

データのバイナリアーカイブダンプを MongoDB に復元

```bash
magento-cloud service:mongo:restore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `service:mongo:shell`

MongoDB シェルの使用

```bash
magento-cloud service:mongo:shell [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `service:redis-cli`

Redis CLI へのアクセス

```bash
magento-cloud service:redis-cli [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```


### `args`

Redis コマンドに追加する引数


### `--relationship`, `-r`

使用するサービス関係

- 値が必要です

### `--identity-file`, `-i`

使用する SSH ID（秘密鍵）

- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `snapshot:create`

環境のスナップショットを作成する

```bash
magento-cloud snapshot:create [--live] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```


### `environment`

環境


### `--live`

ライブバックアップ：環境を停止しないでください。 設定した場合、バックアップ中に環境が実行され、接続に対して開かれた状態になります。 これにより、データのバックアップが不整合な状態になるリスクが生じ、ダウンタイムが短縮されます。

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `snapshot:delete`

環境スナップショットの削除

```bash
magento-cloud snapshot:delete [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

スナップショットの ID。 非インタラクティブモードで必須です。


### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `snapshot:get`

環境スナップショットの表示

```bash
magento-cloud snapshot:get [-P|--property PROPERTY] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--] [<id>]
```


### `id`

スナップショットの ID。 デフォルトで最新の値に設定されます。


### `--property`, `-P`

表示するプロパティ。

- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--date-fmt`

日付の形式（PHP の日付形式文字列）

- デフォルト： `c`
- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `snapshot:list`

環境の使用可能なスナップショットのリスト

```bash
magento-cloud snapshot:list [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `snapshot:restore`

環境スナップショットの復元

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```


### `snapshot`

スナップショットの名前。 デフォルトで最新のものに設定されます


### `--target`

復元先の環境。 デフォルトでは、スナップショットの現在の環境に設定されます

- 値が必要です

### `--branch-from`

—target がまだ存在しない場合は、新しい環境の親を指定します。

- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `source-operation:list`

環境のソース操作のリスト

```bash
magento-cloud source-operation:list [--full] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```

### `--full`

表示するコマンドの長さを制限しないでください。 デフォルトの制限は 24 行です。

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：アプリ、コマンド、操作。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `source-operation:run`

ソース操作の実行

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<operation>]
```


### `operation`

操作名


### `--variable`

操作中に設定する変数（形式） &lt;info>type:name=value&lt;/info>

- デフォルト： `[]`
- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `ssh-cert:load`

SSH 証明書の生成

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `ssh-key:add`

新しい SSH キーを追加

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```


### `path`

既存の SSH 公開鍵へのパス


### `--name`

キーを識別する名前

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `ssh-key:delete`

SSH キーの削除

```bash
magento-cloud ssh-key:delete [<id>]
```


### `id`

削除する SSH キーの ID


### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `ssh-key:list`

アカウント内の SSH キーのリストを取得する

```bash
magento-cloud ssh-key:list [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：id*、title*、path*、fingerprint（* =デフォルトの列）。 「+」文字は、デフォルト列のプレースホルダーとして使用できます。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `subscription:info`

配信登録プロパティの読み取りまたは変更

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<property>] [<value>]
```


### `property`

プロパティの名前


### `value`

プロパティに新しい値を設定する


### `--id`, `-s`

購読 ID

- 値が必要です

### `--date-fmt`

日付の形式（PHP の日付形式文字列）

- デフォルト： `c`
- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--no-header`

テーブルヘッダーを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `tunnel:close`

SSH トンネルを閉じる

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

### `--all`, `-a`

すべてのトンネルを閉じる

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `tunnel:info`

SSH トンネルの関係情報を表示

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

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

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--app`, `-A`

リモートアプリケーション名

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`

表示する列。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `tunnel:list`

SSH トンネルのリスト

```bash
magento-cloud tunnel:list [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```

### `--all`, `-a`

すべてのトンネルを表示

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--app`, `-A`

リモートアプリケーション名

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `tunnel:open`

アプリの関係に対して SSH トンネルを開く

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

### `--gateway-ports`, `-g`

リモートホストからローカル転送ポートへの接続を許可

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `tunnel:single`

1 つのアプリに対する単一の SSH トンネルを開く

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `user:add`

プロジェクトにユーザーを追加する

```bash
magento-cloud user:add [-r|--role ROLE] [--force-invite] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

ユーザーの電子メールアドレス


### `--role`, `-r`

ユーザーのプロジェクトの役割（「管理者」または「閲覧者」）または環境タイプの役割 ( 例：「staging:contributor」または「production:viewer」)。 環境タイプからユーザーを削除するには、役割を「なし」に設定します。 %文字または*文字は、環境タイプのワイルドカードとして使用できます。例：&#39;%:viewer&#39;を使用して、すべてのタイプでユーザに「閲覧者」の役割を付与します。 役割は省略できます（例： ）。&#39;production:v&#39;を参照してください。

- デフォルト： `[]`
- 値が必要です

### `--force-invite`

既に招待メールが送信されている場合でも、招待メールを送信します

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `user:delete`

プロジェクトからのユーザーの削除

```bash
magento-cloud user:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <email>
```


### `email`

ユーザーの電子メールアドレス

- 必須

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `user:get`

ユーザーの役割の表示

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```


### `email`

ユーザーの電子メールアドレス


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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `user:list`

プロジェクトユーザーのリスト

```bash
magento-cloud user:list [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：メール、id、名前、役割。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--no-header`

テーブルヘッダーを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `user:update`

プロジェクトのユーザーの役割を更新

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

ユーザーの電子メールアドレス


### `--role`, `-r`

ユーザーのプロジェクトの役割（「管理者」または「閲覧者」）または環境タイプの役割 ( 例：「staging:contributor」または「production:viewer」)。 環境タイプからユーザーを削除するには、役割を「なし」に設定します。 %文字または*文字は、環境タイプのワイルドカードとして使用できます。例：&#39;%:viewer&#39;を使用して、すべてのタイプでユーザに「閲覧者」の役割を付与します。 役割は省略できます（例： ）。&#39;production:v&#39;を参照してください。

- デフォルト： `[]`
- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `variable:create`

変数の作成

```bash
magento-cloud variable:create [-u|--update] [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```


### `name`

変数名


### `--update`, `-u`

変数が既に存在する場合は更新します

- デフォルト： `false`
- 値を受け入れない

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

変数値が JSON 形式かどうか

- デフォルト： `false`
- 値が必要です

### `--sensitive`

変数値が区別されるかどうか

- デフォルト： `false`
- 値が必要です

### `--prefix`

変数名のプレフィックス。これは変数名のタイプを決定できます。例：&#39;env&#39;. 名前にプレフィックスがまだ含まれていない場合にのみ適用されます。 ( 例：&#39;none&#39;または&#39;env:&#39;)

- デフォルト： `none`
- 値が必要です

### `--enabled`

変数を環境で有効にする必要があるかどうか

- デフォルト： `true`
- 値が必要です

### `--inheritable`

変数が子環境に継承可能かどうか

- デフォルト： `true`
- 値が必要です

### `--visible-build`

ビルド時に変数を表示するかどうか

- 値が必要です

### `--visible-runtime`

実行時に変数を表示するかどうか

- デフォルト： `true`
- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `variable:delete`

変数の削除

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

変数名

- 必須

### `--level`, `-l`

変数レベル（「プロジェクト」、「環境」、「p」または「e」）

- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `variable:get`

変数の表示

```bash
magento-cloud variable:get [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```


### `name`

変数の名前


### `--property`, `-P`

単一の変数プロパティを表示する

- 値が必要です

### `--level`, `-l`

変数レベル（「プロジェクト」、「環境」、「p」または「e」）

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--no-header`

テーブルヘッダーを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `variable:list`

リスト変数

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--level`, `-l`

変数レベル（「プロジェクト」、「環境」、「p」または「e」）

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：is_enabled、level、name、value ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

- デフォルト： `[]`
- 値が必要です

### `--no-header`

テーブルヘッダーを出力しない

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--help`, `-h`

このヘルプメッセージを表示

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

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `variable:update`

変数の更新

```bash
magento-cloud variable:update [--allow-no-change] [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

変数名

- 必須

### `--allow-no-change`

変更が提供されなかった場合は、成功（終了コードなし）を返します。

- デフォルト： `false`
- 値を受け入れない

### `--level`, `-l`

変数レベル（「プロジェクト」、「環境」、「p」または「e」）

- 値が必要です

### `--value`

変数の値

- 値が必要です

### `--json`

変数値が JSON 形式かどうか

- デフォルト： `false`
- 値が必要です

### `--sensitive`

変数値が区別されるかどうか

- デフォルト： `false`
- 値が必要です

### `--enabled`

変数を環境で有効にする必要があるかどうか

- デフォルト： `true`
- 値が必要です

### `--inheritable`

変数が子環境に継承可能かどうか

- デフォルト： `true`
- 値が必要です

### `--visible-build`

ビルド時に変数を表示するかどうか

- 値が必要です

### `--visible-runtime`

実行時に変数を表示するかどうか

- デフォルト： `true`
- 値が必要です

### `--project`, `-p`

プロジェクト ID または URL

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない


## `worker:list`

デプロイ済みのすべてのワーカーのリストを取得する

```bash
magento-cloud worker:list [--refresh] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```

### `--refresh`

キャッシュを更新するかどうか

- デフォルト： `false`
- 値を受け入れない

### `--pipe`

作業者名のリストのみを出力

- デフォルト： `false`
- 値を受け入れない

### `--project`, `-p`

プロジェクト ID または URL

- 値が必要です

### `--environment`, `-e`

環境 ID

- 値が必要です

### `--format`

出力形式は次のとおりです。テーブル、csv、tsv、またはプレーン

- デフォルト： `table`
- 値が必要です

### `--columns`, `-c`

表示する列。 使用可能な列：コマンド、名前、タイプ。 ワイルドカードとして%または*文字を使用できます。 リストが単一の値 (&quot;a,b,c&quot;) コンマや空白で区切られます。

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

### `--verbose`, `-v|-vv|-vvv`

メッセージの詳細度を上げる

- デフォルト： `false`
- 値を受け入れない

### `--version`, `-V`

このアプリケーションバージョンを表示

- デフォルト： `false`
- 値を受け入れない

### `--yes`, `-y`

確認の質問に対しては「はい」と答えます。他の質問に対するデフォルト値を受け入れるインタラクションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`

インタラクティブな質問をしないでください。デフォルト値を受け入れます。 環境変数を使用する場合と同じです。 &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- デフォルト： `false`
- 値を受け入れない

