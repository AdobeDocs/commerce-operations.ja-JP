---
source-git-commit: ca9e04d50e69b8a51ec4a6fbcf1d35f0fb363fab
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---
# 概要

このプロジェクトには、ニュースダイジェストのデータ生成、テンプレートファイルのレンダリング、画像の最適化、マップの生成など、ワークフローの様々な側面を自動化するためのいくつかの Rake タスクが含まれています。 Rakefile で定義された各 Rake タスクの説明と使用ガイドラインを以下に示します。

## タスクのレイク

### `render`

`_jekyll/_data/` のデータを使用して、`_jekyll/templates` ディレクトリのテンプレート化されたファイルをレンダリングします。 結果は、`help/includes/templated` ディレクトリにあります。

**使用方法：**

```sh
rake render
```

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

## 前提条件

- Ruby と Bundler がインストールされました。
- Gemfile で指定されている必須の gems。
- `azure_regions` タスクの Python、[PyGMT](https://www.pygmt.org/latest/install.html) および [pdf2svg](https://formulae.brew.sh/formula/pdf2svg)。

## 設定

1. 必要な gem をインストールします。

   ```sh
   bundle install
   ```

2. `azure_regions` タスクに Python、PyGMT、pdf2svg がインストールされていることを確認します。 設定について詳しくは、[_scripts/azure_regions.py](_scripts/azure_regions.py) のコメントにあるドキュメントを参照してください。
