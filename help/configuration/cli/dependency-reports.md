---
title: 依存関係レポート
description: モジュール、循環、フレームワークの依存関係の合計を示すレポートを作成します。
exl-id: b7a32fe1-71c5-495f-8276-242503fb50ae
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# 依存関係レポート

{{file-system-owner}}

次のタイプのレポートを実行できます。

- **モジュールの依存関係**：モジュール間の依存関係の合計数と、依存関係がハードかソフトかを表示します。
- **循環依存関係**：依存関係チェーンの合計数、および各モジュールの循環依存関係の数とリストを表示します。
- **フレームワークの依存関係**：モジュール別のコマースフレームワークへの依存関係の合計数を表示します（各ライブラリのフレームワークエントリの合計数を含む）。

コメント内の依存関係も依存関係です。

## 依存関係レポートの実行

コマンドオプション：

```bash
bin/magento info:dependencies:{show-modules|show-modules-circular|show-framework} [-d|--directory="<path>"] [-o|--output="<path and filename"]
```

次の表で、このコマンドのオプション、パラメータ、値について説明します。

| パラメーター | 値 | 必須？ |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------- | --------- |
| `show-modules` | モジュールの依存関係レポート。 | はい |
| `show-modules-circular` | 循環依存関係レポート。 | はい |
| `show-framework` | フレームワークの依存関係レポート。 | はい |
| `-d --directory` | レポートデータの検索を開始するベースディレクトリのパス。 | いいえ |
| `-o --output` | レポートのコンマ区切り値 (csv) 出力ファイルの絶対ファイルシステムパスとファイル名を指定します。 | いいえ |

引数としてディレクトリまたはファイル名が渡されない場合、次のアプリケーションルートがデフォルトディレクトリとして使用され、次のデフォルトのファイル名が使用されます。

| コマンド | ファイル名 |
| ----------------------------------------------------- | ----------------------------------- |
| `bin/magento info:dependencies:show-modules` | `modules-dependencies.csv` |
| `bin/magento info:dependencies:show-modules-circular` | `modules-circular-dependencies.csv` |
| `bin/magento info:dependencies:show-framework` | `framework-dependencies.csv` |

### モジュールの依存関係レポートのサンプル

次に、サンプルモジュールの依存関係レポートの出力の一部を示します。

```terminal
"","All","Hard","Soft"
"Total number of dependencies","602","587","15"

"Dependencies for each module:","All","Hard","Soft"
"magento/module-cron","2","2","0"
" -- magento/module-config","","1","0"
" -- magento/module-store","","1","0"

"magento/module-catalog-rule","8","8","0"
" -- magento/module-store","","1","0"
" -- magento/module-rule","","1","0"
" -- magento/module-catalog","","1","0"
" -- magento/module-customer","","1","0"
" -- magento/module-backend","","1","0"
" -- magento/module-eav","","1","0"
" -- magento/module-indexer","","1","0"
" -- magento/module-import-export","","1","0"
```

### 循環依存関係レポートのサンプル

次に、循環依存関係のサンプルレポートの出力の一部を示します。

```terminal
"Circular dependencies:","Total number of chains"
"","848"

"Circular dependencies for each module:",""
"magento/module-config","70"
"magento/module-config->magento/module-store->magento/module-directory->magento/module-config"
"magento/module-config->magento/module-store->magento/module-config"
"magento/module-config->magento/module-cron->magento/module-config"
"magento/module-config->magento/module-email->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-theme->magento/module-customer->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-reports->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-theme->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-log->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-catalog-inventory->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-theme->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-payment->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-themeax->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-catalog-rule->magento/module-rule->magento/module-eav->magento/module-config"
```

### サンプルフレームワークの依存関係レポート

次に、サンプルフレームワークの依存関係レポートの出力の一部を示します。

```terminal
"Dependencies of framework:","Total number"
"","111"

"Dependencies for each module:",""
"Magento\Cron","1"
" -- Magento\Framework","143"

"Magento\CatalogRule","1"
" -- Magento\Framework","234"

"Magento\Webapi","2"
" -- Magento\Framework","347"
" -- Magento\Server","1"

"Magento\Checkout","1"
" -- Magento\Framework","759"

"Magento\Reports","1"
" -- Magento\Framework","553"
```
