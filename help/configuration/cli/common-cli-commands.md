---
title: 一般的なコマンド
description: 一般的なAdobe Commerce CLI コマンドとその使用例について説明します。 開発および管理に不可欠なコマンドラインツールについて説明します。
exl-id: d35a1dd9-10b3-4364-b6f4-b1e259a04e3d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# 一般的なコマンド

次に、使用可能なコマンドの一部を要約します。

**コマンドの完全なリストを表示するには**:

```bash
bin/magento list
```

help コマンドの例：

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

コマンドは概要形式でのみ表示されます。コマンドの詳細については、[ コマンド ] 列のリンクをクリックしてください。

| コマンド | 説明 |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | キャッシュを管理 |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | インデクサーを管理します。 |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Commerce cron ジョブを実行 |
| [`magento setup:di:compile`](../cli/code-compiler.md) | 存在しないすべてのプロキシおよびファクトリをコンパイルし、1 つのストアおよび web サイトのクラス定義、継承情報およびプラグイン定義を事前にコンパイルします。 |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | モジュールの依存関係、循環依存関係およびCommerce フレームワークの依存関係。 |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | 翻訳ディクショナリまたは翻訳パッケージを作成します |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | 静的ビューファイルをデプロイ |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | LESS から CSS を作成する |
| [`magento dev:tests:run`](../cli/unit-tests.md) | 自動化されたテストの実行 |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | 新しい XSLT （Extensible Stylesheet Language Transformations） スタイルシートに一致するように、レイアウト XML ファイルを更新します |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | パフォーマンステストに使用するデータを生成します。 |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | Commerce アプリケーションのインストール後に、オプションのサンプルデータをインストールします。<br><br> サンプルデータについて詳しくは、「[&#x200B; サンプルデータのオプション &#x200B;](../../installation/sample-data/overview.md)」を参照してください。 |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | バックエンド設定を管理 |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | 管理者ユーザーを作成/編集/ロック解除します。 |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | 開発者テンプレートのヒントを有効または無効にします。 |

## 一般的な引数

次の引数は [&#x200B; すべてのコマンド &#x200B;](/help/tools/reference/commerce-on-premises.md) に共通です。 これらのコマンドは、Commerce ソフトウェアのインストールの前または後に実行できます。

| ロングバージョン | ショートバージョン | 意味 |
|--- |--- |--- |
| `--help` | `-h` | 任意のコマンドのヘルプを表示します。 例えば、`./magento help setup:install` や `./magento help setup:config:set` です。 |
| `--quiet` | `-q` | クワイエットモード。出力なし。 |
| `--no-interaction` | `-n` | インタラクティブな質問はありません。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 詳細レベル。 例えば、`--verbose=3` または `-vvv` は、デバッグの詳細を表示します。これは最も詳細な出力です。 デフォルトは `--verbose=1` または `-v` です。 |
| `--version` | `-V` | このアプリケーションのバージョンを表示 |
| `--ansi` | 該当なし | ANSI 出力を強制 |
| `--no-ansi` | 該当なし | ANSI 出力を無効にする |
