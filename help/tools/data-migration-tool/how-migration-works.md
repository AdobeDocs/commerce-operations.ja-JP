---
title: データ移行の仕組み
description: 用語、ワークフロー図、手順など、Magento 1 とMagento 2 間のデータ移行プロセスについて説明します。
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# データ移行の仕組み

ここでは、[!DNL Data Migration Tool] を使用してMagento 1 からMagento 2 にデータを移行する方法について概要を説明します。

[!DNL Data Migration Tool] は、Magento 1 からMagento 2 にデータを転送するために使用されるコマンドラインインターフェイス（CLI）ツールです。 このツールは、Magento 1 と 2 のデータベース構造（テーブルとフィールド）の一貫性を検証し、データ転送の進行状況を追跡し、ログを作成して、データ検証テストを実行します。

## 用語

* **モード** - Magento 1.x からMagento 2.x にデータを移行する際の一連の順序付き操作。
* **手順** – 移行するデータの種類を定義するモードのタスク。
* **ステージ** - データの検証、転送、検証を行う手順のタスクです。
* **マップファイル** - Magento 1.x とMagento 2.x の間の規則と接続を、各段階を完了するためのデータ構造として定義する XML ファイル。

## モード

この [!DNL Data Migration Tool] では、Magento 1.x からMagento 2.x にデータを転送して適応させるために、移行プロセスを 3 つのフェーズまたは *モード* に分割します。3 つのモードがここに一覧表示され、この順序で実行する必要があります。

1. **設定モード**: システム設定と web サイト関連の設定を移行します。
1. **データモード**：データベースアセットを一括移行します。
1. **差分モード**：新規顧客や注文など、増分変更（前回の実行以降に加えられた変更）を移行します。

![&#x200B; 移行モード &#x200B;](../../assets/data-migration/MigrationModes2.png)

## 手順

[!DNL Data Migration Tool] では、各モード内で一連の *手順* を使用して、特定のタイプのデータを移行します。 例えば、設定モードでは、すべての設定データを移行する手順として、ストア手順と設定手順の 2 つの手順が使用されます。 これらの各手順（およびその他のモードの手順）で移行される特定のデータについて詳しくは、[[!DNL Data Migration Tool]  技術仕様 &#x200B;](technical-specification.md) を参照してください。

![&#x200B; 移行の概要 &#x200B;](../../assets/data-migration/MigrationOverview2.png)

## ステージ

各ステップには 3 つの *ステージ* があり、データが適切に移行されるように、これらのステージは常に次の順序で実行されます。

1. **整合性チェック**：テーブルフィールド名、タイプ、その他の情報を比較して、Magento 1 と 2 のデータ構造の間の互換性を確認します。
1. **データ転送**:Magento 1 および 2 からテーブルごとにデータテーブルを転送します。
1. **ボリュームチェック**：テーブル間のレコード数を比較して、転送が成功したことを確認します。

![&#x200B; 移行ステージ &#x200B;](../../assets/data-migration/MigrationSteps2.png)

## ファイルのマッピング

移行プロセスの最下位レベルには、XML *マップファイル* があります。 この [!DNL Data Migration Tool] では、手順の各段階でマップファイルを使用して、Magento 1.x テーブルと 2.x テーブル間の異なるデータ構造を変換します。

例えば、データをMagento Open Source 1.8.0.0 データベースからMagento Open Source 2.x.x に変換する場合、マップファイルは、テーブルの名前が変更されたことを考慮して、変換先データベースでその名前を変更します。 データ構造やデータ形式に違いがない場合、[!DNL Data Migration Tool] は、拡張機能で作成されたテーブルのデータを含め、データをそのままの状態でMagento 2 データベースに転送します。

マップファイルで相違が宣言されない場合、[!DNL Data Migration Tool] はエラーを表示し、開始しません。

マッピングファイルの詳細については、[[!DNL Data Migration Tool] 技術仕様 ] を参照してください。

## 移行フロー図

![&#x200B; 移行フロー &#x200B;](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] 技術仕様](technical-specification.md)

世界の#1 コマース基盤であるMagento 1.x から、未来のプラットフォームであるMagento 2 への移行を検討してくださっていることを嬉しく思います。 移行と呼ばれるこのプロセスの詳細をお知らせします。

## 移行コンポーネント

Magento 2 の移行には、データ、拡張機能、カスタムコード、テーマ、カスタマイズの 4 つのコンポーネントが含まれます。

### データ

**Magento 2[!DNL Data Migration Tool]** は、すべての商品、顧客、注文データ、店舗構成、プロモーションなどをMagento 2 に効率的に移行するのに役立ちます。 このガイドでは、データ移行に使用するツールとベストプラクティスに関する情報を提供します。

### 拡張機能とカスタムコード

アドビでは、Magento 2 でMagento 1 拡張機能を使用するお客様を支援するために、開発コミュニティと協力して取り組んでいます。 お気に入りの拡張機能の最新版をダウンロードまたは購入できる [Commerce Marketplace](https://marketplace.magento.com/) を紹介します。

Magento 2 用の拡張機能の開発について詳しくは、「[PHP 開発者ガイド &#x200B;](https://developer.adobe.com/commerce/php/development/)」を参照してください。

### テーマとカスタマイズ

Magento 2 は、マーチャントが革新的なショッピングエクスペリエンスを創出し、新しいレベルに拡張するための比類のない機能を提供する新しいアプローチとテクノロジーを使用しています。 これらの高度な機能を活用するには、開発者はテーマやカスタマイズを変更する必要があります。 Magento 2[&#x200B; テーマ &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/themes/)、[&#x200B; レイアウト &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) および [&#x200B; カスタマイズ &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/) を作成するためのドキュメントがオンラインで利用できます。

## 移行の努力

1.x バージョン間（v1.12 から v1.14 など）のアップグレードと同様に、Magento 1 からMagento 2 への移行に必要な作業レベルは、サイトの構築方法とそのカスタマイズレベルによって異なります。
しかし、私たちは常に [!DNL Data Migration Tool] を改善しています（詳しくは [&#x200B; 変更ログ &#x200B;](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) を参照）。そのため、移行の取り組みは減少し続けています。
