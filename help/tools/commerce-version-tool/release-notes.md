---
title: '[!DNL Commerce Version Tool] リリースノート'
description: 新しいパッチステータスレポート、CVE保護ステータス、CSV出力、キャッシュ動作など、 [!DNL Commerce Version Tool]  リリースについて説明します。
feature: Release Notes
TQID: 'https://experienceleague.adobe.com/38I3U5y9rmurP5gVhalfUq7DlcUb-JpF5eUam1nwEyk'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 180
ht-degree: 2%

---

# [!DNL Commerce Version Tool] リリースノート

これらのリリースノートでは、[!DNL Commerce Version Tool] （[!DNL CVT]）の更新について説明しています。

## バージョン 1.0.0 - 2026年6月 {#version-1-0-0}

### 新機能

- **パッチステータスレポート** - Adobe Commerce インストールに対して、Adobe Commerceの毎月のセキュリティパッチが適用されている、欠落している、または分類できない状況をレポートします。
- **CVE保護ステータス** - パッチの結果をCVEごとの保護ステータス値`PROTECTED`、`VULNERABLE`、`UNKNOWN`および`NOT_APPLICABLE`にマッピングします。
- **マルチコンポーネントのサポート** - Adobe Commerce Business-to-Business （B2B）、Adobe Commerce Page Builder、Adobe Commerce Inventory、およびパッチレジストリファイルに表示されるその他のコンポーネントを含む、`composer.lock`からインストールされたAdobe Commerce コンポーネントを検出します。
- **JSONおよびCSV出力** - プログラマティックな使用のためにデフォルトでJSON出力を提供し、スプレッドシート、スキャナー、ダッシュボード、およびコンプライアンスツール用にCSV出力を提供します。
- **オフラインフレンドリーなキャッシュ動作** - フェッチが成功するたびに、パッチレジストリファイルをローカルにキャッシュします。 リモート レジストリが利用できない場合、[!DNL CVT] ツールは警告を表示してキャッシュ レジストリを使用できます。
- **バンドル配信** – 毎月のAdobe Commerce セキュリティパッチファイル内に出荷されます。 パッチを適用すると、[!DNL CVT]が`vendor/bin/patch-status`にインストールされ、個別のインストール手順は実行されません。

## 関連トピック

- [概要](intro.md)
- [パッチステータスレポートの生成](generate-report.md)
- [トラブルシューティング](troubleshooting.md)
