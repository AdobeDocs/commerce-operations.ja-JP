---
source-git-commit: 90e3f9cb6033c91be67947e84520d3e2537ca5d9
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---
# 概要

このプロジェクトでは、Rake タスクを使用して、ドキュメントワークフローの一部を自動化します。 ほとんどのタスクはExL Commerce ドキュメントリポジトリ間で共有され、[`adobe-comdox-exl-rake-tasks`](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks) gemから取得されます。 以下のいくつかのタスクは、このリポジトリに固有のものです。

**一般的なタスク（テンプレートのレンダリング、インクルードの管理、画像の最適化/監査、新機能ダイジェストの生成）については、[adobe-comdox-exl-rake-tasks README](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md)を参照してください。**

> GemfileとRakefileが存在するため、以下のすべての`bundle exec rake` コマンドは`_jekyll/` ディレクトリ内から実行する必要があります。

## リポジトリ固有のRake タスク

### `whatsnew_bp`

ベストプラクティスでニュースダイジェスト用のデータを生成します。 デフォルトの期間は、前回の更新以降です。 `since`引数を使用して別の期間を指定できます。

**使用状況：**

```sh
bundle exec rake whatsnew_bp
```

**引数`since`付き：**

```sh
bundle exec rake whatsnew_bp since="jul 4"
```

### `get_released_versions`

`magento/magento2` リポジトリから最新の10 リリース済みバージョンを取得します。 [GitHub CLI](https://cli.github.com/)をインストールして認証する必要があります。

**使用状況：**

```sh
bundle exec rake get_released_versions
```

**出力：** リリースタグ名と日付を含む`tmp/core-release.txt`が生成されます。

### `first_merge_date`

指定したブランチに最初に結合した日付を取得します。 [GitHub CLI](https://cli.github.com/)をインストールして認証する必要があります。

**使用状況：**

```sh
bundle exec rake first_merge_date base=develop
```

**引数：**

- `base` （必須）：結合を確認するターゲットブランチ名。

## 使用可能なタスクのリスト

使用可能なすべてのレイクタスクとその説明を表示するには、次を使用します。

```sh
bundle exec rake --tasks
```

特定のタスクの詳細については、次を使用してください。

```sh
bundle exec rake -T [task_name]
```

## 関係ファイル形式を含める

`include-relationships.yml` ファイルは、メインコンテンツ ファイルと含まれるファイルとの関係を追跡します。 このファイルは、`includes:maintain_relationships` タスクによって自動的に管理されます（タスクの使用状況については、[adobe-comdox-exl-rake-tasks README](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md)を参照）。このタスクは、既存のインクルードファイルを読み取り、それらを参照するメインファイルを見つけることで関係を検出します。

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
- `metadata.total_relationships`：次を含むメインファイルの合計数
- `metadata.auto_discovered`: ファイルが自動的に生成されたことを示します
- `metadata.discovery_date`：関係が最初に検出された日付
- `relationships`: メインファイルとインクルードされたファイルのマッピング

**ステートメント形式を含める：**
メインコンテンツファイルは、次の構文を使用して他のファイルを含めます。

```markdown
{{$include /help/_includes/filename.md}}
```

## 前提条件

- RubyとBundlerがインストールされています。
- Gemfileで指定されている必要な宝石（一般的なタスクは`adobe-comdox-exl-rake-tasks`によって提供されます。`whatsnew` タスクには`whatsup_github`が追加で必要です）。
- `get_released_versions`および`first_merge_date` タスクの[GitHub CLI](https://cli.github.com/)。

## 設定

必要な宝石を取り付けます。

```sh
bundle install
```
