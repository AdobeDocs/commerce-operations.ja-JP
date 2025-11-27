---
source-git-commit: 48dfdd81992a82bf984c3e7b0f30f8e5a69ee735
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 1%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->
**バージョン**:3.0.25

このリファレンスには、`bin/uct` のコマンド ライン ツールで使用できる 9 つのコマンドが含まれています。
最初のリストは、Adobe Commerceで `bin/uct list` コマンドを使用して自動生成されます。

## 一般

ツールについて詳しくは、[&#x200B; 概要 &#x200B;](/help/upgrade/upgrade-compatibility-tool/overview.md) を参照してください。

>[!NOTE]
>
>`composer update` コマンドはこのツールのアップグレードには機能しません。[&#x200B; 最新バージョンをダウンロードしてインストール &#x200B;](/help/upgrade/upgrade-compatibility-tool/run.md) する必要があります。

このリファレンスドキュメントは、アプリケーションソースコードから生成されます。 ドキュメントを変更するには、を開きます。
関連する [&#x200B; コードベース &#x200B;](https://github.com/magento) リポジトリ内の対応するコマンドのプルリクエスト。 参照：
[&#x200B; コードの投稿 &#x200B;](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) を参照してください。

### グローバルオプション

#### `--help`, `-h`

指定されたコマンドのヘルプを表示します。 コマンドが指定されていない場合は、list コマンドの表示ヘルプが表示されます

- デフォルト：`false`
- 値を受け入れません

#### `--quiet`, `-q`

メッセージを出力しない

- デフォルト：`false`
- 値を受け入れません

#### `--verbose`, `-v|-vv|-vvv`

メッセージの冗長さを増やします。通常の出力の場合は 1、詳細な出力の場合は 2、デバッグの場合は 3 です。

- デフォルト：`false`
- 値を受け入れません

#### `--version`, `-V`

このアプリケーションのバージョンを表示

- デフォルト：`false`
- 値を受け入れません

#### `--ansi`

ANSI 出力を強制（または無効化 – no-ansi）

- 値を受け入れません

#### `--no-ansi`

「– ansi」オプションを否定します

- デフォルト：`false`
- 値を受け入れません

#### `--no-interaction`, `-n`

対話型の質問をしない

- デフォルト：`false`
- 値を受け入れません


## `_complete`

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

シェル補完の候補を提供する内部コマンド

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options) を参照してください。

#### `--shell`, `-s`

シェル型（「bash」、「fish」、「zsh」）

- 値が必要です

#### `--input`, `-i`

入力トークンの配列（例：COMP_WORDS または argv）

- デフォルト：`[]`
- 値が必要です

#### `--current`, `-c`

カーソルがある「入力」配列のインデックス （例：COMP_CWORD）

- 値が必要です

#### `--api-version`, `-a`

完了スクリプトの API バージョン

- 値が必要です

#### `--symfony`, `-S`

非推奨

- 値が必要です


## `completion`

```bash
bin/uct completion [--debug] [--] [<shell>]
```

シェル完了スクリプトをダンプ

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    uct/bin/uct completion  | sudo tee /etc/bash_completion.d/uct

Or dump the script to a local file and source it:

    uct/bin/uct completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/jenkins/workspace/gendocs-uct-cli/uct/bin/uct completion )"
```

### 引数

#### `shell`

シェルの型（例：&#39;&#39;bash&#39;&#39;）は、&#39;&#39;$SHELL&#39;&#39;環境変数の値が指定されていない場合に使用されます

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options) を参照してください。

#### `--debug`

完了デバッグログのテール

- デフォルト：`false`
- 値を受け入れません


## `help`

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```

コマンドのヘルプを表示する

```
The help command displays help for a given command:

  uct/bin/uct help list

You can also output the help in other formats by using the --format option:

  uct/bin/uct help --format=xml list

To display the list of available commands, please use the list command.
```

### 引数

#### `command_name`

コマンド名

- デフォルト：`help`

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options) を参照してください。

#### `--format`

出力形式（txt、xml、json、md）

- デフォルト：`txt`
- 値が必要です

#### `--raw`

生のコマンド ヘルプを出力するには

- デフォルト：`false`
- 値を受け入れません


## `list`

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

コマンドのリスト

```
The list command lists all commands:

  uct/bin/uct list

You can also display the commands for a specific namespace:

  uct/bin/uct list test

You can also output the information in other formats by using the --format option:

  uct/bin/uct list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  uct/bin/uct list --raw
```

### 引数

#### `namespace`

名前空間名

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options) を参照してください。

#### `--raw`

生のコマンド リストを出力するには

- デフォルト：`false`
- 値を受け入れません

#### `--format`

出力形式（txt、xml、json、md）

- デフォルト：`txt`
- 値が必要です

#### `--short`

説明コマンドの引数をスキップするには

- デフォルト：`false`
- 値を受け入れません


## `refactor`

```bash
bin/uct refactor <path>
```

自動的に修正できる問題を解決します。 指定されたパスのコードが更新されます。

### 引数

#### `path`

で問題を解決するためのパスです。

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options) を参照してください。


## `core:code:changes`

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```

アップグレード互換性ツールは、Adobe Commerce インスタンスにインストールされているすべての非Adobe Commerce モジュールを分析して、そのインスタンスを特定のバージョンと照合するコマンドラインツールです。 新しいバージョンのAdobe Commerce コードにアップグレードする前に対処する必要があるエラーと警告のリストを返します。

### 引数

#### `dir`

Adobe Commerce インストールディレクトリ。

- 必須


#### `vanilla-dir`

Adobe Commerce vanilla インストールディレクトリ。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options) を参照してください。

#### `--output`, `-o`

出力の書き出し先となるファイルのパス（JSON 形式）

- 値を受け入れる


## `dbschema:diff`

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

選択した 2 つのバージョンにおけるAdobe Commerce DB スキーマの違いを一覧表示できます。 使用可能なバージョン：2.3.0 | 2.3.1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4-p1 | 2.3.4-p2 | 2.3.5 | 2.3.5-p1 | 2.3.5-p2 | 2.3.6 | 2.3.6-p1 | 2.3.7 | 2.3.7-p1 | 2.3.7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2.4.0 | 2.4.0-p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2-p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4-p1 | 2.4.5 | 2.4.4-p2 | 2.4.5-p1 | 2.4.4-p3 | 2.4.4-p4 | 2.4.4-p5 | 2.4.5-p2 | 2.4.5-p3 | 2.4.5-p4 | 2.4.6 | 2.4.6-p1 | 2.4.6-p2 | 2.4.7 – ベータ 1 | 2.4.4-p6 | 2.4.5-p5 | 2.4.6-p3 | 2.4.7-beta2 | 2.4.4-p7 | 2.4.5-p6 | 2.4.6-p4 | 2.4.7-beta3 | 2.4.7 | 2.4.6-p5 | 2.4.5-p7 | 2.4.4-p8 | 2.4.4-p9 | 2.4.5-p8 | 2.4.6-p6 | 2.4.7-p1 | 2.4.4-p10 | 2.4.5-p9 | 2.4.6-p7 | 2.4.7-p2 | 2.4.4-p11 | 2.4.5-p10 | 2.4.6-p8 | 2.4.7-p3 | 2.4.8-beta1 | 2.4.4-p12 | 2.4.5-p11 | 2.4.6-p9 | 2.4.7-p4 | 2.4.8-beta2 | 2.4.4-p13 | 2.4.5-p12 | 2.4.6-p10 | 2.4.7-p5 | 2.4.8 | 2.4.9-alpha2 | 2.4.8-p2 | 2.4.7-p7 | 2.4.6-p12 | 2.4.5-p14 | 2.4.4-p15 | 2.4.9-alpha1 | 2.4.8-p1 | 2.4.7-p6 | 2.4.6-p11 | 2.4.5-p13 | 2.4.4-p14 | 2.4.9-alpha3 | 2.4.8-p3 | 2.4.7-p8 | 2.4.6-p13 | 2.4.5-p15 | 2.4.4-p16

### 引数

#### `current-version`

現在のバージョン（例：2.3.2）。

- 必須


#### `target-version`

ターゲットバージョン（2.4.5 など）。

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options) を参照してください。


## `graphql:compare`

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```

GraphQL スキーマの互換性の検証

### 引数

#### `schema1`

最初のGraphQL スキーマを指すエンドポイント URL。

- 必須


#### `schema2`

2 つ目のGraphQL スキーマを指すエンドポイント URL。

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options) を参照してください。

#### `--output`, `-o`

出力の書き出し先となるファイルのパス （JSON 形式）

- 値を受け入れる


## `upgrade:check`

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```

アップグレード互換性ツールは、Adobe Commerceのカスタマイズ済みインスタンスにインストールされているすべてのモジュールを分析し、そのインスタンスを特定のバージョンと照合するコマンドラインツールです。 最新バージョンのAdobe Commerceにアップグレードする前に対処する必要があるエラーと警告のリストを返します。

### 引数

#### `dir`

Adobe Commerce インストールディレクトリ。

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options) を参照してください。

#### `--current-version`, `-a`

現在のAdobe Commerceのバージョン。省略すると、Adobe Commerce インストールのバージョンが使用されます。

- 値を受け入れる

#### `--coming-version`, `-c`

Target のAdobe Commerceのバージョン。 省略した場合は、最新リリースの安定したAdobe Commerceが使用されます。 使用可能なAdobe Commerceのバージョン：2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3.3\| 2.3.3-p1 \| 2.3.4-p1 \| 2.3.4-p1 \| 2.3.5\| 2.3.5-p2 \| 2.3.6\| 2.3.6-p1 \| 2.3.7-p1 \| 2.3.7-p1 \| 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.2-p1 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4\| 2.4.4-p1 \| 2.4.4-p1 \| 2.4.4-p1 \| 2.4-p2 \| 2.4.4-p3 \| 2.4.4-p4 \| 2.4.4-p5 \| 2.4.4-p6 \| 2.4.4-p7 \| 2.4.4-p9 \| 2.4.4-p9 \| 2.4.4-p10 \| 2.4.4-p11 \| 2.4.4-p12 \| 2.4.4-p13 \| 2.4.4-p14 \| 2.4.4-p15 \| 2.4.4-p16 \| 2.4.5 \| 2.4.5-p1 \| 2.4.5-p2 \| 2.4.5-p3 \| 2.4.5-p5 \| 2.4.5-p5 \| 2.4.5-p6 \| 2.4.5-p7 \| 2.4.5-p8 \| 2.4.5-p9 \| 2.4.5-p10 \| 2.4.5-p11 \| 2.4.5-p12 2.4.5-p13 \| 2.4.5-p14 \| 2.4.5-p15 \| 2.4.6 \| 2.4.6-p1 \| 2.4.6-p2 \| 2.4.6-p3 \| 2.4.6-p4 \| 2.4.6-p5 \| 2.4.6-p7 \| 2.4.6-p8 \| 2.4.6-p9 \| 2.4.6-p10 \| 2.4.6-p11 \| 2.4.6-p12 \| 2.4.6-p13 \| 2.4.7-beta1 \| 2.4.7-beta2 \| 2.4.7-beta3 \| 2.4.7-p1 \| 2.4.7-p2 \| 2.4.7-p4 \| 2.4.7-p5 \| 2.4.7-p6 \| 2.4.7-p7\| 2.7-p7\| 2.4 2.4.8-beta1 \| 2.4.8-beta2 \| 2.4.8\| 2.4.8-p1 \| 2.4.8-p2 \| 2.4.8-p3 \| 2.4.9-alpha1 \| 2.4.9-alpha2 \| 2.4.9-alpha2 \| 2.4.9-alpha3

- 値を受け入れる

#### `--json-output-path`

出力が JSON 形式で書き出されるファイルのパス

- 値を受け入れる

#### `--html-output-path`

HTML形式で出力を書き出すファイルのパス

- 値を受け入れる

#### `--min-issue-level`

レポートに表示する最小限の問題レベル（警告、エラー、重大）。

- デフォルト：`warning`
- 値を受け入れる

#### `--ignore-current-version-compatibility-issues`, `-i`

現在および今後のバージョンでよくある問題を無視

- デフォルト：`false`
- 値を受け入れません

#### `--context`

実行コンテキスト。 このオプションは統合目的で、実行結果には影響しません。

- 値が必要です

