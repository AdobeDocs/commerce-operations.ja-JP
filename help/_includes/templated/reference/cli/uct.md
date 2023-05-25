---
source-git-commit: ad7f05eaa5f144b5a8616307d65be635a0c499eb
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**バージョン**:3.0.3

このリファレンスには、 `bin/uct` コマンドラインツールを使用します。
最初のリストは、 `bin/uct list` Adobe Commerceで

のツールの詳細を説明します。 [概要](/help/upgrade/upgrade-compatibility-tool/overview.md).

>[!NOTE]
>
>この参照は、アプリケーションのコードベースから生成されます。 コンテンツを変更するには、 [codebase](https://github.com/magento) リポジトリを作成し、変更をレビュー用に送信します。 もう 1 つの方法は、次の操作です。 _フィードバックを提供_ （右上にあるリンクを見つけます）。 貢献のガイドラインについては、 [コード貢献](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

シェルの完了候補を示す内部コマンド

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
```

### `--shell`, `-s`

シェルタイプ (&quot;bash&quot;)

- 値が必要です

### `--input`, `-i`

入力トークンの配列（例： COMP_WORDS や argv）

- デフォルト： `[]`
- 値が必要です

### `--current`, `-c`

カーソルが置かれている「入力」配列のインデックス（例： COMP_CWORD）

- 値が必要です

### `--symfony`, `-S`

完了スクリプトのバージョン

- 値が必要です

### `--help`, `-h`

指定したコマンドのヘルプを表示します。 コマンドが指定されていない場合は、 &lt;info>リスト&lt;/info> command

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

ANSI 出力を強制（または無効 —no-ansi）にします

- 値を受け入れない

### `--no-ansi`

「 —ansi」オプションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `completion`

シェル完了スクリプトをダンプします

```bash
bin/uct completion [--debug] [--] [<shell>]
```


### `shell`

シェルのタイプ ( 例：&quot;bash&quot;) の場合、&quot;$SHELL&quot; env var の値は、この値が指定されていない場合に使用されます


### `--debug`

完了デバッグログの末尾を表示

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

指定したコマンドのヘルプを表示します。 コマンドが指定されていない場合は、 &lt;info>リスト&lt;/info> command

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

ANSI 出力を強制（または無効 —no-ansi）にします

- 値を受け入れない

### `--no-ansi`

「 —ansi」オプションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `help`

コマンドのヘルプを表示する

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
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

指定したコマンドのヘルプを表示します。 コマンドが指定されていない場合は、 &lt;info>リスト&lt;/info> command

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

ANSI 出力を強制（または無効 —no-ansi）にします

- 値を受け入れない

### `--no-ansi`

「 —ansi」オプションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `list`

リストコマンド

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
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

### `--short`

コマンドの引数の説明をスキップするには

- デフォルト： `false`
- 値を受け入れない

### `--help`, `-h`

指定したコマンドのヘルプを表示します。 コマンドが指定されていない場合は、 &lt;info>リスト&lt;/info> command

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

ANSI 出力を強制（または無効 —no-ansi）にします

- 値を受け入れない

### `--no-ansi`

「 —ansi」オプションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `refactor`

自動的に修正できる問題を解決します。 指定されたパス内のコードが更新されます。

```bash
bin/uct refactor <path>
```


### `path`

での問題を解決するためのパス。

- 必須

### `--help`, `-h`

指定したコマンドのヘルプを表示します。 コマンドが指定されていない場合は、 &lt;info>リスト&lt;/info> command

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

ANSI 出力を強制（または無効 —no-ansi）にします

- 値を受け入れない

### `--no-ansi`

「 —ansi」オプションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `core:code:changes`

アップグレード互換性ツールは、Adobe Commerceインスタンスと特定のバージョンを照合するコマンドラインツールで、Adobe Commerce以外のモジュールがインストールされている場合は、そのモジュールをすべて分析します。 Adobe Commerceコードの新しいバージョンにアップグレードする前に対処する必要があるエラーと警告のリストを返します。

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```


### `dir`

Adobe Commerceインストールディレクトリ。

- 必須

### `vanilla-dir`

Adobe Commerce vanilla インストールディレクトリ。


### `--output`, `-o`

出力を書き出すファイルのパス（Json 形式）

- 値を受け入れる

### `--help`, `-h`

指定したコマンドのヘルプを表示します。 コマンドが指定されていない場合は、 &lt;info>リスト&lt;/info> command

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

ANSI 出力を強制（または無効 —no-ansi）にします

- 値を受け入れない

### `--no-ansi`

「 —ansi」オプションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `dbschema:diff`

選択した 2 つのバージョン間でAdobe Commerce DB スキーマの違いをリストできます。
利用可能なバージョン：2.3.0 | 2.3.1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4-p1 | 2.3.4-p2 | 2.3.5 | 2.3.5-p1 | 2.3.5-p2 | 2.3.6 | 2.3.6-p1 | 2.3.7 | 2.3.7-p1 | 2.3.7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2.4.0 | 2.4.0-p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2-p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4-p1 | 2.4.5 | 2.4.4-p2 | 2.4.5-p1 | 2.4.4-p3 | 2.4.5-p2 | 2.4.6

```bash
bin/uct dbschema:diff <current-version> <target-version>
```


### `current-version`

現在のバージョン（2.3.2 など）。

- 必須

### `target-version`

ターゲットバージョン（2.4.5 など）。

- 必須

### `--help`, `-h`

指定したコマンドのヘルプを表示します。 コマンドが指定されていない場合は、 &lt;info>リスト&lt;/info> command

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

ANSI 出力を強制（または無効 —no-ansi）にします

- 値を受け入れない

### `--no-ansi`

「 —ansi」オプションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `graphql:compare`

GraphQLスキーマの互換性の検証

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```


### `schema1`

最初のGraphQLスキーマを指すエンドポイント URL。

- 必須

### `schema2`

2 番目のGraphQLスキーマを指すエンドポイント URL。

- 必須

### `--output`, `-o`

出力を書き出すファイルのパス（JSON 形式）

- 値を受け入れる

### `--help`, `-h`

指定したコマンドのヘルプを表示します。 コマンドが指定されていない場合は、 &lt;info>リスト&lt;/info> command

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

ANSI 出力を強制（または無効 —no-ansi）にします

- 値を受け入れない

### `--no-ansi`

「 —ansi」オプションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない


## `upgrade:check`

アップグレード互換性ツールは、Adobe Commerceカスタマイズ済みのインスタンスを特定のバージョンと照合するために、その中にインストールされているすべてのモジュールを分析するコマンドラインツールです。 最新バージョンのAdobe Commerceにアップグレードする前に対処する必要があるエラーと警告のリストを返します。

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```


### `dir`

Adobe Commerceインストールディレクトリ。

- 必須

### `--current-version`, `-a`

省略した場合は、現在のAdobe CommerceバージョンのAdobe Commerceインストールのバージョンが使用されます。

- 値を受け入れる

### `--coming-version`, `-c`

省略した場合、Target Adobe Commerceバージョン、最新リリースバージョンのAdobe Commerceが使用されます。 使用可能なAdobe Commerceバージョン：2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3.3\| 2.3.3.3-p1 \| 2.3.3.4-p1 \| 2.3.4-p2 \| 2.3.5\| 2.3.5-p1 \| 2.3.5-p2\| 2.3.6 \| 2.3.6-p1 \| 2.3.7\| 2.3.7-p1 \| 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1 -p1 \|2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.2.2-p2 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4\| 2.4.4-p1 \| 2.4.4-p2 \| 2.4.4.4-p24.5-p1 \| 2.4.4-p3 \| 2.4.5-p2 \| 2.4.6

- 値を受け入れる

### `--json-output-path`

出力を JSON 形式で書き出すファイルのパス

- 値を受け入れる

### `--html-output-path`

出力を書き出すファイルのパスをHTML形式で指定

- 値を受け入れる

### `--min-issue-level`

レポートに表示する最小の問題レベル（警告、エラーまたは重大）。

- デフォルト： `warning`
- 値を受け入れる

### `--ignore-current-version-compatibility-issues`, `-i`

現在および今後のバージョンで一般的な問題を無視する

- デフォルト： `false`
- 値を受け入れない

### `--context`

実行コンテキスト。 このオプションは統合の目的で使用され、実行結果には影響しません。

- 値が必要です

### `--help`, `-h`

指定したコマンドのヘルプを表示します。 コマンドが指定されていない場合は、 &lt;info>リスト&lt;/info> command

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

ANSI 出力を強制（または無効 —no-ansi）にします

- 値を受け入れない

### `--no-ansi`

「 —ansi」オプションを無効にする

- デフォルト： `false`
- 値を受け入れない

### `--no-interaction`, `-n`

インタラクティブな質問をしない

- デフォルト： `false`
- 値を受け入れない
