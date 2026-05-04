---
source-git-commit: ef3abc83e2c699ebfbb53ad367aaceb9ecb92491
workflow-type: tm+mt
source-wordcount: '1155'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->
**バージョン**: 3.0.26

このリファレンスには、`bin/uct` コマンドラインツールで利用できる9つのコマンドが含まれています。
最初のリストは、Adobe Commerceの`bin/uct list` コマンドを使用して自動生成されます。

## 一般

このツールについて詳しくは、[概要](/help/upgrade/upgrade-compatibility-tool/overview.md)を参照してください。

>[!NOTE]
>
>`composer update` コマンドは、このツールのアップグレードに使用できません。最新バージョンを[&#x200B; ダウンロードしてインストールする必要があります](/help/upgrade/upgrade-compatibility-tool/run.md)。

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

- 値を受け付けません

#### `--no-interaction`, `-n`

インタラクティブな質問は避けてください

- 既定：`false`
- 値を受け付けません


## `_complete`

```shell
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
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

```shell
bin/uct completion [--debug] [--] [<shell>]
```

シェル完了スクリプトをダンプします

```text
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    ./uct/bin/uct completion  | sudo tee /etc/bash_completion.d/uct

Or dump the script to a local file and source it:

    ./uct/bin/uct completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/apps/uct/bin/uct completion )"
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

```shell
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```

コマンドのヘルプの表示

```text
The help command displays help for a given command:

  ./uct/bin/uct help list

You can also output the help in other formats by using the --format option:

  ./uct/bin/uct help --format=xml list

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

```shell
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

リストコマンド

```text
The list command lists all commands:

  ./uct/bin/uct list

You can also display the commands for a specific namespace:

  ./uct/bin/uct list test

You can also output the information in other formats by using the --format option:

  ./uct/bin/uct list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  ./uct/bin/uct list --raw
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


## `refactor`

```shell
bin/uct refactor <path>
```

自動的に修正できる問題を解決します。 指定されたパスのコードが更新されます。

### 引数

#### `path`

で問題を解決するためのパス。

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `core:code:changes`

```shell
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```

Upgrade Compatibility Toolは、インストールされているすべてのAdobe Commerce以外のモジュールを分析することで、Adobe Commerce インスタンスを特定のバージョンに照らし合わせてチェックするコマンドラインツールです。 新しいバージョンのAdobe Commerce コードにアップグレードする前に対処する必要があるエラーと警告のリストを返します。

### 引数

#### `dir`

Adobe Commerceのインストールディレクトリ。

- 必須


#### `vanilla-dir`

Adobe Commerce Vanilla インストールディレクトリ。

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--output`, `-o`

出力が書き出されるファイルのパス（Json形式）

- 値を受け入れる


## `dbschema:diff`

```shell
bin/uct dbschema:diff <current-version> <target-version>
```

選択した2つのバージョン間のAdobe Commerce DB スキーマの違いを一覧表示できます。 利用可能なバージョン：2.3.0 | 2.3.1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4 | 2.3.5 | 2.3.5 | 2.3.5-p1 | 2.3.5-p2 | 2.3.6 | 2.3.7 | 2.3-p2 | 2.3.7-p2 | 2.3-p3 | 2.3 2.4.0 | 2.4.0-p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2-p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4-p1 | 2.4.5 | 2.4.4-p2 | 2.4.4-p3 | 2.4-p3 | 2.4.4-p5 | 2.4.5-p2 | 2.4.5-p3 | 2.4.5-p4 | 2.4.6 | 2.4.6-p1 | 2.4.6-p2 | 2.4.7-beta1 | 2.4.4-p6 | 2.4.5-p5 | 2.4.6-p3 | 2.4.7-beta2 | 2.4.4-p7 | 2.4.5-p6 | 2.4-p4 | 2.4-p4 2.4.5-p7 | 2.4.4-p8 | 2.4.4-p9 | 2.4.5-p8 | 2.4.6-p6 | 2.4.7-p1 | 2.4.4-p10 | 2.4.5-p9 | 2.4.6-p7 | 2.4.7-p2 | 2.4.4-p11 | 2.4.5-p10 | 2.4.6-p8 | 2.4.7-p3 | 2.4.8 beta1 | 2.4.4-p12 | 2.4.5-p11 | 2.4.6-p9 | 2.4.7-p4 | 2.4.8-beta2 | 2.4.4-p13 | 2.4.5-p12 | 2.4.6-p10 | 2.4.7-p5 | 2.4.8 | 2.4.9-alpha2 | 2.4.8-p2 | 2.4.7-p7 | 2.4-p12 | p.4 2.4.4-p15 | 2.4.9-alpha1 | 2.4.8-p1 | 2.4.7-p6 | 2.4.6-p11 | 2.4.4-p14 | 2.4.9-alpha3 | 2.4.8-p3 | 2.4.7-p8 | 2.4.6-p13 | 2.4.5-p15 | 2.4.4-p16 | 2.4-beta1 | 2.4.8-p4 | 2.4.7-p9 | 2.4.6-p14 | 2.4.5-p16 | 2.4.4-p17

### 引数

#### `current-version`

現在のバージョン（例：2.3.2）。

- 必須


#### `target-version`

ターゲットバージョン（例：2.4.5）。

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。


## `graphql:compare`

```shell
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```

GraphQL スキーマの互換性の検証

### 引数

#### `schema1`

最初のGraphQL スキーマを指すエンドポイント URL。

- 必須


#### `schema2`

2番目のGraphQL スキーマを指すエンドポイント URL。

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--output`, `-o`

出力が書き出されるファイルのパス（JSON形式）

- 値を受け入れる


## `upgrade:check`

```shell
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```

Upgrade Compatibility Toolは、Adobe Commerceでカスタマイズしたインスタンスを、そのインスタンスにインストールされているすべてのモジュールを分析して特定のバージョンと照合するコマンドラインツールです。 最新バージョンのAdobe Commerceにアップグレードする前に対処する必要があるエラーと警告のリストを返します。

### 引数

#### `dir`

Adobe Commerceのインストールディレクトリ。

- 必須

### オプション

グローバルオプションについては、[&#x200B; グローバルオプション &#x200B;](#global-options)を参照してください。

#### `--current-version`, `-a`

現在のAdobe Commerceのバージョン、省略した場合はAdobe Commerceのバージョンが使用されます。

- 値を受け入れる

#### `--coming-version`, `-c`

Adobe Commerceのバージョンをターゲティングする。 省略した場合は、最新のリリース済み安定版のAdobe Commerceが使用されます。 使用可能なAdobe Commerce バージョン：2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5-p2 \| 2.3.6 \| 2.3-p1 \| 2.3.7 \| 2.3-p1 \| 2.3| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p2 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4-p3 \| 2.4-p1 \| 2.4-p2 \| 2.4.4-p3 \| 2.4.4-p4 \| 2.4.4-p5 \| 2.4.4-p7 \| 2.4.4-p8 \| 2.4.4-p9 \| 2.4.4-p10 \| 2.4.4-p10 \| 2.4.4-p11 \| 2.4.4-p12 \| 2.4.4-p13 \| 2.4.4-p14 \| 2.4-p15| 2.4.4-p16 \| 2.4.4-p17 \| 2.4.5 \| 2.4.5-p1 \| 2.4.5-p2 \| 2.4.5-p3 \| 2.4.5-p4 \| 2.4.5-p5 \| 2.4.5-p6 \| 2.4.5-p7 \| 2.4.5-p8 \| 2.4.5-p9 \| 2.4.5-p10 \| 2.4.5-p11| 2.4.5-p12 \| 2.4.5-p13 \| 2.4.5-p14 \| 2.4.5-p15 \| 2.4.6 \| 2.4.6-p1 \| 2.4.6-p1 \| 2.4.6-p2 \| 2.4.6-p3 \| 2.4.6-p4 \| 2.4.6-p5 \| 2.4.6-p6 \| 2.4.6-p7 \| p8| 2.4.6-p9 \| 2.4.6-p10 \| 2.4.6-p11 \| 2.4.6-p12 \| 2.4.6-p14 \| 2.4.7-beta1 \| 2.4.7-beta2 \| 2.4.7-beta3 \| 2.4.7 \| 2.4.7-p1 \| 2.4.7-p2 \| 2.4.7-p3 \| 2.4-p3 \| 2.4.7-p5 \| 2.4.7-p6 \| 2.4.7-p7 \| 2.4.7-p7 \| 2.4.7-p9 \| 2.4.8-beta1 \| 2.4.8-beta2 \| 2.4.8 \| 2.4.8-p1 \| 2.4.8-p2 \| 2.4.8-p3 \| 2.4.8-p4 \| 2.4.9-alpha1 \| 2.4.9-alpha2| \-alpha3 2.4.9-beta1

- 値を受け入れる

#### `--json-output-path`

出力がjson形式で書き出されるファイルのパス

- 値を受け入れる

#### `--html-output-path`

出力がHTML形式で書き出されるファイルのパス

- 値を受け入れる

#### `--min-issue-level`

レポートに表示する問題レベル（警告、エラー、または重大）は最小限です。

- 既定：`warning`
- 値を受け入れる

#### `--ignore-current-version-compatibility-issues`, `-i`

現在および今後のバージョンの一般的な問題を無視する

- 既定：`false`
- 値を受け付けません

#### `--context`

実行コンテキスト： このオプションは統合目的で、実行結果には影響しません。

- 値が必要です

