---
source-git-commit: 4589c405bab743001e967a9825d578ee1a03c216
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---
# 概要

このプロジェクトには、ニュースダイジェストのデータ生成、テンプレートファイルのレンダリング、画像の最適化、マップの生成など、ワークフローの様々な側面を自動化するためのいくつかの Rake タスクが含まれています。 Rakefile で定義された各 Rake タスクの説明と使用ガイドラインを以下に示します。

## タスクのレイク

### `render`

`_jekyll/templates` のデータを使用して、`_jekyll/_data/` ディレクトリのテンプレート化されたファイルをレンダリングします。 結果は、`help/includes/templated` ディレクトリにあります。 このタスクは、レンダリング後、インクルードの関係とタイムスタンプを自動的に維持します。

**使用方法：**

```sh
rake render
```

**機能：**
- レンダリングスクリプトを実行して、テンプレートファイルを生成します
- `includes:maintain_all` を実行して関係とタイムスタンプを更新する
- すべてのインクルードメタデータがレンダリング後に最新であることを確認

### `image_optim`

変更されたコミットされていないファイルのイメージを最適化します。 その他の画像の場合は、`path` 引数を使用してディレクトリまたはファイルを指定します。

**使用方法：**

```sh
rake image_optim
```

**引数 `path` 使用：**

```sh
rake image_optim path=../path/to/dir/or/file
```

### `whatsnew`

ニュースダイジェストのデータを生成します。 デフォルトの期間は前回の更新以降の期間です。 `since` 引数を使用して、別の期間を指定できます。

**使用方法：**

```sh
rake whatsnew
```

**引数 `since` 使用：**

```sh
rake whatsnew since="jul 4"
```

### `whatsnew_bp`

ベストプラクティスでニュースダイジェストのデータを生成します。 デフォルトの期間は前回の更新以降の期間です。 `since` 引数を使用して、別の期間を指定できます。

**使用方法：**

```sh
rake whatsnew_bp
```

**引数 `since` 使用：**

```sh
rake whatsnew_bp since="jul 4"
```

### `azure_regions`

Azure リージョン マップを生成します。 入力データファイルは `_jekyll/tmp/azure-regions.json` に配置する必要があります。 結果は `_jekyll/tmp/azure-regions.svg` にあります。 Python、[PyGMT](https://www.pygmt.org/latest/install.html)、および [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) がインストールされている必要があります。

**使用方法：**

```sh
rake azure_regions
```

### `get_released_versions`

最新の 10 リリース済みバージョンを `magento/magento2` リポジトリから取得します。 [GitHub CLI](https://cli.github.com/) がインストールされ、認証されている必要があります。

**使用方法：**

```sh
rake get_released_versions
```

**出力：** リリースタグの名前と日付を使用して `tmp/core-release.txt` を生成します。

### `first_merge_date`

指定した分岐への最初の結合の日付を取得します。 [GitHub CLI](https://cli.github.com/) がインストールされ、認証されている必要があります。

**使用方法：**

```sh
rake first_merge_date base=develop
```

**引数：**

- `base` （必須）：結合を確認するターゲット分岐名。

### `includes:maintain_relationships`

`include-relationships.yml` ディレクトリ内のすべてのマークダウンファイルをスキャンし、パターン `help` を使用してインクルードステートメントを検索することで、`{{$include /help/_includes/filename.md}}` ファイルを検出および更新します。 このタスクでは、メイン コンテンツ ファイルとインクルード ファイルとの関係が自動的に維持されます。

**使用方法：**

```sh
rake includes:maintain_relationships
```

**機能：**
- 既存のインクルードファイルのリストを `help/_includes` ディレクトリから読み取ります
- すべての主要な Markdown ファイルを検索して、各インクルードを参照するファイルを見つけます。
- `{{$include /help/_includes/filename.md}}` パターンを使用して参照を識別します
- 検出された関係で `include-relationships.yml` ファイルを更新します
- 行われた変更の概要を提供し、参照されていないインクルードを特定します

### `includes:maintain_timestamps`

最新のインクルードファイル変更タイムスタンプをメインファイルに追加して、インクルードタイムスタンプを維持します。 このタスクでは、`include-relationships.yml` ファイルを読み取り、各インクルードファイルの Git 履歴を確認し、メインファイルの最後にタイムスタンプを追加または更新します。

**使用方法：**

```sh
rake includes:maintain_timestamps
```

**機能：**
- 負荷には `include-relationships.yml` からの関係が含まれます
- メインファイルごとに、インクルードファイル内の最新の Git コミット日を検索します
- メインファイルの末尾にタイムスタンプが付いたHTML コメントを追加または更新します
- 次の形式を使用します。`<!-- Last updated from includes: YYYY-MM-DD HH:MM:SS -->`
- チェックされたインクルードファイルとそのタイムスタンプを示す詳細出力を提供します

**出力例：**

```console
Processing installation/advanced.md...
  Latest include change: 2024-04-16 09:42:31
  Include files checked: help/_includes/cli-consumers.md (2022-09-12 09:38:25), help/_includes/secure-install.md (2022-09-08 11:33:05), help/_includes/sensitive-data.md (2024-04-16 09:42:31)
  Added new timestamp
```

### `includes:maintain_all`

`includes:maintain_relationships` と `includes:maintain_timestamps` の両方を順番に実行する便利なタスク。 インクルードの関係とタイムスタンプの両方を維持するには、この方法をお勧めします。

**使用方法：**

```sh
rake includes:maintain_all
```

### `unused_includes`

マークダウンファイルで参照されていないインクルードファイルを `help/_includes` ディレクトリで検索します。 これにより、安全に削除できる孤立したインクルードファイルを特定できます。

**使用方法：**

```sh
rake unused_includes
```

## 使用可能なタスクのリスト

使用可能なすべての Rake タスクとその説明を確認するには、次を使用します。

```sh
rake --tasks
```

特定のタスクについて詳しくは、以下を使用します。

```sh
rake -T [task_name]
```

## 管理タスクを含める

インクルード関連のすべてのタスクは、整理しやすくするために `includes` 名前空間の下に整理されています。

```sh
# Discover and maintain include relationships
rake includes:maintain_relationships

# Add/update timestamps based on include file changes
rake includes:maintain_timestamps

# Do both operations in sequence (recommended)
rake includes:maintain_all
```

## 関係ファイル形式を含める

`include-relationships.yml` ファイルは、メインコンテンツファイルとそれらに含まれるファイルとの関係を追跡します。 このファイルは、既存のインクルードファイルを読み取り、それらを参照するメインファイルを見つけることで関係を検出する `maintain_include_relationships` rake タスクによって自動的に管理されます。

**ファイル構造：**

```yaml
---
metadata:
  last_updated: '2025-08-22 14:04:37'
  description: 'Index of main files and their included files for automatic timestamp updates'
  total_relationships: 57
  auto_discovered: true
  discovery_date: '2025-08-22 14:04:37'
relationships:
  configuration/deployment/example-environment-variables.md:
    - "/help/_includes/config-save-config.md"
    - "/help/_includes/config-update-build-system.md"
    - "/help/_includes/config-update-prod-system.md"
  # ... more relationships
```

**フィールド：**
- `metadata.last_updated`：最終更新のタイムスタンプ
- `metadata.total_relationships`: インクルードを含むメインファイルの合計数
- `metadata.auto_discovered`：ファイルが自動的に生成されたことを示します
- `metadata.discovery_date`：関係が最初に検出された日付
- `relationships`：メインファイルとインクルードされるファイルとのマッピング

**Include ステートメントの形式：**
メインコンテンツファイルには、次の構文を使用して他のファイルが含まれます。

```markdown
{{$include /help/_includes/filename.md}}
```

## 前提条件

- Ruby と Bundler がインストールされました。
- Gemfile で指定されている必須の gem （コア依存関係は `adobe-comdox-exl-rake-tasks` で提供されます）。
- [ タスクと ](https://cli.github.com/) タスク用の `get_released_versions`GitHub CLI`first_merge_date`。
- [ タスクの Python、](https://www.pygmt.org/latest/install.html)PyGMT[ および ](https://formulae.brew.sh/formula/pdf2svg)pdf2svg`azure_regions`。

## 設定

1. 必要な gem をインストールします。

   ```sh
   bundle install
   ```

2. `azure_regions` タスクに Python、PyGMT、pdf2svg がインストールされていることを確認します。 設定について詳しくは、[_scripts/azure_regions.py](_scripts/azure_regions.py) のコメントにあるドキュメントを参照してください。
