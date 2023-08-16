---
title: 共通コマンド
description: 一般的な Commerce CLI コマンドと使用方法のサンプリングを表示します。
exl-id: d35a1dd9-10b3-4364-b6f4-b1e259a04e3d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# 共通コマンド

次に、使用可能なコマンドの一部をまとめます。

**コマンドの完全なリストを表示するには**:

```bash
bin/magento list
```

ヘルプコマンドの例：

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

コマンドは概要形式でのみ表示されます。コマンドの詳細については、[ コマンド ] 列のリンクをクリックします。

| コマンド | 説明 |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | キャッシュの管理 |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | インデクサーを管理します |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | コマース cron ジョブを実行します |
| [`magento setup:di:compile`](../cli/code-compiler.md) | 存在しないプロキシとファクトリをすべてコンパイルし、1 つのストアと Web サイトのクラス定義、継承情報、プラグイン定義を事前にコンパイルします。 |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | モジュールの依存関係、循環依存関係、およびコマースフレームワークの依存関係。 |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | 翻訳辞書または翻訳パッケージを作成します |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | 静的ビューファイルをデプロイします |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | LESS から CSS を作成 |
| [`magento dev:tests:run`](../cli/unit-tests.md) | 自動テストの実行 |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | レイアウト XML ファイルを更新して、新しい XSLT(Extensible Stylesheet Language Transformations) スタイルシートに一致させる |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | パフォーマンステストに使用するデータを生成します。 |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | コマースアプリケーションをインストールした後に、オプションのサンプルデータをインストールします。<br><br>サンプルデータについて詳しくは、 [オプションのサンプルデータ](../../installation/sample-data/overview.md). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | バックエンド設定の管理 |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | 管理者ユーザーを作成/編集/ロック解除します。 |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | 開発者テンプレートのヒントを有効または無効にします。 |

## 共通の引数

次の引数は、すべてのコマンドに共通です。 次のコマンドは、Commerce ソフトウェアのインストール前またはインストール後に実行できます。

| 長いバージョン | 短いバージョン | 意味 |
|--- |--- |--- |
| `--help` | `-h` | 任意のコマンドに関するヘルプを取得します。 例： `./magento help setup:install` または `./magento help setup:config:set`. |
| `--quiet` | `-q` | クワイエットモード。出力なし。 |
| `--no-interaction` | `-n` | インタラクティブな質問はありません。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 詳細レベル。 例： `--verbose=3` または `-vvv` は、最も詳細な出力である debug verbosity を表示します。 デフォルトはです。 `--verbose=1` または `-v`. |
| `--version` | `-V` | このアプリケーションバージョンを表示 |
| `--ansi` | 該当なし | ANSI 出力を強制 |
| `--no-ansi` | 該当なし | ANSI 出力を無効にする |
