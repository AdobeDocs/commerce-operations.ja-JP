---
title: パッチステータスレポートの生成
description: ' [!DNL Commerce Version Tool] を使用して、JSONまたはCSV形式でAdobe Commerce パッチステータスレポートを生成する方法を説明します。'
TQID: 'https://experienceleague.adobe.com/-lC-20YMpbTM3tTZjbBO5zD5gb9n7cRah5Ycy8wQoyw'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: cb0391ae368b53a795535f3adb636628a339b963
workflow-type: tm+mt
source-wordcount: 590
ht-degree: 2%

---

# パッチステータスレポートの生成

[!DNL Commerce Version Tool] （[!DNL CVT]）を使用して、Adobe Commerce インストールのパッチ ステータス レポートを生成します。 このレポートは、適用された、欠落している、不明な毎月のセキュリティパッチを特定し、デフォルトでJSON出力を返します。

## 前提条件

[!DNL CVT]を実行する前に、次のことを確認してください：

- ターゲットインストールでは、サポートされているAdobe Commerceのバージョンとエディションが使用されます。
- `composer.lock`が存在し、検査する環境と一致します。
- PHPとシステム `patch` バイナリが使用可能です。
- コマンドを実行する環境からプロジェクトファイルを読み取ることができます。
- キャッシュファイルと監査ログエントリが必要な場合、ツールは`var/patch_metadata/`と`var/log/`に書き込むことができます。
- 資格情報は、使用権限が付与されたパッチがインストールに適用される場合、`COMPOSER_AUTH`または`auth.json`を通じて利用できます。

[!DNL CVT] ツールは、`COMPOSER_AUTH`、Adobe Commerce プロジェクト `auth.json`、およびグローバルコンポーザー`auth.json`に対して、使用権限が付与されたパッチ資格情報を確認します。

## レポートの生成

Adobe Commerce プロジェクトのルートから、次を実行します。

```bash
php vendor/bin/patch-status
```

別のAdobe Commerce インストールを確認するには、`--root` オプションを使用します。

```bash
php vendor/bin/patch-status --root=/path/to/commerce
```

## コマンドオプション

JSONはデフォルトの出力形式です。 CSV出力は、スキャナー、ダッシュボード、コンプライアンスレポートでサポートされています。

| オプション | 説明 |
| --- | --- |
| `--root=PATH` | Adobe Commerce インストール ルートへのパスを指定します。 デフォルトは現在のディレクトリです。 |
| `--format=json\|csv` | 出力形式を設定します。 デフォルトは`json`です。 |
| `--no-cache` | レジストリおよびpatch-diff キャッシュをバイパスし、新しいリモートフェッチを強制し、リモートレジストリが使用できない場合はエラーで終了します。 |
| `--version`, `-V` | ツールバージョンを印刷します。 |
| `--help`, `-h` | ヘルプメッセージを印刷します。 |

{style="table-layout:auto"}

## JSONおよびCSV出力の確認

次のサンプルは、デフォルトのJSON出力を示しています。

```bash
php vendor/bin/patch-status
```

```json
{
  "base_version": "2.4.7-p9",
  "installed_components": {
    "CE": "2.4.7-p9",
    "EE": "2.4.7-p9",
    "B2B": "1.5.2-p5"
  },
  "applied_patches": [
    "247p9-2026-05-001-CE",
    "247p9-2026-05-001-EE"
  ],
  "missing_patches": [
    "247p9-2026-06-001-CE",
    "247p9-2026-06-001-EE"
  ],
  "unknown_patches": [],
  "vulnerability_status": {
    "CVE-2026-12354": { "status": "PROTECTED" },
    "CVE-2026-67890": { "status": "VULNERABLE" }
  },
  "registry_source": "remote",
  "warnings": []
}
```

CSV出力を生成するには、`--format=csv` オプションを使用します。

```bash
php vendor/bin/patch-status --format=csv
```

CSV出力はCVEごとに1行を生成し、スプレッドシート、スキャナー、ダッシュボード、コンプライアンスツールに適しています。

## レポート結果の理解

セキュリティステータスの主張をする前に、欠けているパッチや未知のパッチを確認しましょう。

### パッチステータス値

パッチステータスレポートは、パッチの結果を次の値でグループ化します。

| パッチステータス | 意味 |
| --- | --- |
| 適用 | [!DNL CVT] ツールは、Adobe Commerce コードベースの毎月のセキュリティ パッチを検出します。 |
| 環境なし | パッチは、インストールされたAdobe Commerce バージョンまたはコンポーネントに適用されますが、[!DNL CVT] ツールでは検出されません。 |
| 不明 | ツールは、使用可能なレジストリ、パッチの差分、または検出結果からパッチのステータスを確認できません。 |

{style="table-layout:auto"}

### CVE ステータス値

JSON出力では、CVE ステータス値が大文字でレポートされます。

| CVE ステータス | 意味 |
| --- | --- |
| `PROTECTED` | 該当するパッチがCVEまたはコンポーネントに対して検出されます。 |
| `VULNERABLE` | CVEまたはコンポーネントに該当するパッチがありません。 |
| `UNKNOWN` | [!DNL CVT] ツールは、使用可能なレジストリと検出データからCVE ステータスを判断できません。 |
| `NOT_APPLICABLE` | CVEは、Adobe Commerce Business-to-Business （B2B）、Adobe Commerce Page Builder、Adobe Commerce Inventoryなど、インストールされていないコンポーネントに適用されます。 |

{style="table-layout:auto"}

### キー出力フィールド

レポートには、次の情報を含めることができます。

- **基本Adobe Commerce バージョン** - インストールされている基本バージョンが`composer.lock`から検出されました。
- **レジストリ ソース** - パッチ メタデータが`remote`、`cache`、または`stale_cache`のいずれかから取得されたかどうか。
- **インストール済みのコンポーネント** - `composer.lock`からAdobe Commerce パッケージ領域が検出されました。
- **適用されたパッチ** - Adobe Commerce コードベースで毎月のセキュリティパッチが検出されました。
- **パッチが見つかりません** – 適用される毎月のセキュリティパッチが適用されますが、検出されません。
- **不明なパッチ** - [!DNL CVT] ツールで分類できないパッチ。
- **CVEによる脆弱性ステータス** - CVE カバレッジは、保護された状態、脆弱な状態、該当しない状態、または不明な状態にマッピングされています。
- **警告** - レポートの信頼性または完全性に影響を与える可能性のある条件。

## パッチレジストリとキャッシュ

パッチレジストリファイルには、[!DNL CVT] ツールが、インストールされているバージョンに適用されるパッチを決定するために使用するパッチメタデータが含まれています。 このツールは、利用可能な場合は新しいレジストリキャッシュを使用し、必要に応じてリモートレジストリを取得し、ネットワークが利用できない場合は警告を表示して古いキャッシュを使用できます。 `--no-cache`は、新しいリモートフェッチが必要な場合にのみ使用してください。

## 関連トピック

- [概要](intro.md)
- [トラブルシューティング](troubleshooting.md)
- [リリースノート](release-notes.md)
