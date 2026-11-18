---
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 63e52c8451f368e2d2a36096fc11c7ead62ee94e
workflow-type: tm+mt
source-wordcount: '704'
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

### `whatsnew_consolidated`

公開済みの新機能テーブルを、設定されたCommerce ドキュメントプロジェクトから`help/_includes/automated/whatsnew/consolidated.md`に統合します。

```sh
bundle exec rake whatsnew_consolidated
```

[`_config.yml`](_config.yml)の`whatsnew_consolidated.projects`のプロジェクトを設定します。 各エントリには、リポジトリ名、プロジェクトタイトル、絶対HTTP （S） web サイト URLが必要です。

```yaml
whatsnew_consolidated:
  projects:
    - repo: commerce-operations.en
      title: Adobe Commerce operational guides
      website: https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/home
    - repo: commerce-webapi
      title: Adobe Commerce web APIs
      website: https://developer.adobe.com/commerce/webapi/
    - repo: commerce.en
      title: Adobe Commerce
      website: https://experienceleague.adobe.com/en/docs/commerce
```

エントリを移動してセクションの順序を変更します。 両方のプラットフォームからプロジェクトを自由に切り替えることができます。 `.en`で終わるリポジトリ名は、ExL ソースパス `help/_includes/templated/whats-new.md`を使用します。 その他のすべてのリポジトリは、開発サイトのソース パス `src/pages/_includes/templated/whats-new.md`を使用しています。

タスクは、`AdobeDocs` GitHub組織からパブリック `main` ファイルを取得します。 各プロジェクトタイトルをプレーンテキストの見出しとして表示し、`website`で設定されたドキュメントのホームページにプロジェクトタイトルをリンクする文を含む各テーブルを新機能の更新のソースとして紹介します。 全体で`Description | Type | Date/source`個のテーブルヘッダーを使用します。 DevSite プロジェクトの場合のみ、エスケープされた`\<br/\>` タグは`<br/>`になります。 それ以外の場合、本文の行、重複、リンク、ソース行の順序は変更されません。 各ソースが独自の期間を定義します。

認識された更新なしメッセージを含むプロジェクトは省略されます。 すべてのプロジェクトにエントリがない場合、インクルードには、全体的な更新なしメッセージが1つ含まれます。 設定、取得、解析、または書き込みの失敗は、既存のインクルードを置き換えずにタスクに失敗します。

タスクは、生成をスケジュールしたり、消費ページを更新したりしません。

焦点を絞ったテストスイートには、`_jekyll` RakefileをロードしてBundlerを実行するRake エントリポイントテストが含まれています。 バンドラーと`_jekyll` バンドルを最初にインストールします。

```sh
cd _jekyll && bundle install
```

次に、リポジトリルートからテストを実行します。

```sh
ruby _jekyll/test/consolidated_whatsnew_test.rb
```

### `whatsnew_feedback`

既存のローカル `help/_includes/automated/whatsnew/consolidated.md`のインクルードをフィルタリングして`help/_includes/automated/whatsnew/consolidated-feedback.md`を作成します。

```sh
bundle exec rake whatsnew_feedback
```

タスクは、大文字と小文字を区別し、周囲の空白を無視して、コンマ区切りの完全なType値として`Feedback`と一致します。 `Feedback, technical`などの組み合わせ型が含まれます。 説明、ソースリンク、または部分的な型名のメンションは適用されません。

一致する行、重複、プレーンテキストのプロジェクト見出し、存在する場合はソース文、プロジェクトと行の順序は変更されません。 一致するエントリがないプロジェクトは省略されます。 何も一致しない場合、出力には1つの全体的なノーフィードバックメッセージが含まれます。

入力は既に存在している必要があります。 更新する場合は、`bundle exec rake whatsnew_consolidated`を個別に実行します。 フィードバックタスクは、リモートコンテンツの取得、プロジェクト設定の読み取り、入力の再生成を行いません。

入力が見つからないか、形式が正しくない場合は、既存のフィルターされたインクルードを置き換えずにタスクに失敗します。 入力ファイルは変更されず、フィルタリングされた出力はアトミックにパブリッシュされます。

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
