---
title: 共通コマンド
description: 一般的なAdobe Commerce CLI コマンドとその使用例について説明します。 開発と管理に必要なコマンドラインツールを確認します。
exl-id: d35a1dd9-10b3-4364-b6f4-b1e259a04e3d
source-git-commit: f9a135fc63574ccbecd3f564a87fc5c4ac03f009
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# 共通コマンド

次に、使用可能なコマンドの一部を示します。

**コマンドの完全なリストを表示するには**:

```shell
bin/magento list
```

help コマンドの例：

```shell
bin/magento help <command>
```

```shell
bin/magento help cache:enable
```

コマンドは概要フォームでのみ表示されます。コマンドの詳細については、「コマンド」列のリンクをクリックしてください。

| コマンド | 説明 |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | キャッシュを管理します |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | インデクサーの管理 |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Commerce cron ジョブを実行します |
| [`magento setup:di:compile`](../cli/code-compiler.md) | 存在しないすべてのプロキシとファクトリをコンパイルし、1つのストアとweb サイトのクラス定義、継承情報、プラグイン定義を事前にコンパイルします。 |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | Module dependencies、circular dependencies、およびCommerce framework dependencies。 |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | 翻訳辞書または翻訳パッケージを作成します |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | 静的ビューファイルをデプロイ |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | LESSからCSSを作成します |
| [`magento dev:tests:run`](../cli/unit-tests.md) | 自動テストの実行 |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | レイアウト XML ファイルを、新しい拡張可能スタイルシート言語変換（XSLT）スタイルシートに合わせて更新します |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | パフォーマンステストに使用するデータを生成。 |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | Commerce アプリケーションのインストール後に、オプションのサンプルデータをインストールします。<br><br> サンプルデータについて詳しくは、[&#x200B; オプションのサンプルデータ &#x200B;](../../installation/sample-data/overview.md)を参照してください。 |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | バックエンド設定の管理 |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | 管理者ユーザーを作成/編集/ロック解除します。 |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug) | 開発者テンプレートヒントを有効/無効にします。 |

## 共通引数

次の引数は、[すべてのコマンド &#x200B;](/help/tools/reference/commerce-on-premises.md)に共通です。 これらのコマンドは、Commerce ソフトウェアのインストール前またはインストール後に実行できます。

| 長文 | 短いバージョン | 意味 |
|--- |--- |--- |
| `--help` | `-h` | 任意のコマンドのヘルプを表示します。 例：`./magento help setup:install`または`./magento help setup:config:set` |
| `--quiet` | `-q` | 静かなモード。出力なし。 |
| `--no-interaction` | `-n` | インタラクティブな質問なし。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 詳細レベル： 例えば、`--verbose=3`または`-vvv`は、最も冗長な出力であるデバッグの冗長性を表示します。 デフォルトは`--verbose=1`または`-v`です。 |
| `--version` | `-V` | このアプリケーションのバージョンを表示 |
| `--ansi` | なし | ANSI出力を強制 |
| `--no-ansi` | なし | ANSI出力を無効にする |
