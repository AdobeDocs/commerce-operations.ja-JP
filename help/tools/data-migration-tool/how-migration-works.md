---
title: データ移行の仕組み
description: 用語、ワークフロー図、手順など、Magento 1 とMagento 2 間のデータ移行プロセスについて説明します。
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---

# データ移行の仕組み

ここでは、[!DNL Data Migration Tool] を使用してMagento1 からMagento2 にデータを移行する方法の概要について説明します。

[!DNL Data Migration Tool] は、Magento1 からMagento2 にデータを転送するために使用される CLI （コマンド・ライン・インタフェース）ツールです。 このツールは、Magento1 と 2 のデータベース構造（テーブルとフィールド）間の整合性の確認、データ転送の進行状況のトラッキング、ログの作成、データ検証テストの実行を行います。

## 用語

* **モード** - Magento 1.x からMagento 2.x へデータを移行する一連の操作を順序よく記述したもの。
* **手順** – 移行するデータの種類を定義するモードのタスク。
* **ステージ** - データの検証、転送、検証を行う手順のタスクです。
* **マップファイル** - Magento 1.x とMagento 2.x の間の規則と接続を、各段階を完了するためのデータ構造として定義する XML ファイル。

## モード

この [!DNL Data Migration Tool] では、Magento 1.x からMagento 2.x にデータを転送して適応させるために、移行プロセスを 3 つのフェーズまたは *モード* に分割します。3 つのモードがここに一覧表示され、この順序で実行する必要があります。

1. **設定モード**: システム設定と web サイト関連の設定を移行します。
1. **データモード**：データベースアセットを一括移行します。
1. **差分モード**：新規顧客や注文など、増分変更（前回の実行以降に加えられた変更）を移行します。

![ 移行モード ](../../assets/data-migration/MigrationModes2.png)

## 手順

[!DNL Data Migration Tool] では、各モード内で一連の *手順* を使用して、特定のタイプのデータを移行します。 例えば、設定モードでは、すべての設定データを移行する手順として、ストア手順と設定手順の 2 つの手順が使用されます。 これらの各手順（およびその他のモードの手順）で移行される特定のデータについて詳しくは、[[!DNL Data Migration Tool]  技術仕様 ](technical-specification.md) を参照してください。

![ 移行の概要 ](../../assets/data-migration/MigrationOverview2.png)

## ステージ

各ステップには 3 つの *ステージ* があり、データが適切に移行されるように、これらのステージは常に次の順序で実行されます。

1. **整合性チェック**：テーブルフィールド名、型、その他の情報を比較して、Magento 1 と 2 のデータ構造の間の適合性を検証します。
1. **データ転送**:Magento 1 および 2 からテーブルごとにデータテーブルを転送します。
1. **ボリュームチェック**：テーブル間のレコード数を比較して、転送が成功したことを確認します。

![ 移行ステージ ](../../assets/data-migration/MigrationSteps2.png)

## ファイルのマッピング

移行プロセスの最下位レベルには、XML *マップファイル* があります。 この [!DNL Data Migration Tool] では、ステップの各段階でマップファイルを使用して、Magento 1.x テーブルと 2.x テーブルの間で異なるデータ構造を変換します。

たとえば、Magento Open Source 1.8.0.0 のデータベースからMagento Open Source 2.x.x にデータを変換する場合、マップ ファイルはテーブルの名前が変更されたことを考慮して、変換先データベースでテーブルの名前を変更します。 データ構造やデータ形式に違いがない場合、[!DNL Data Migration Tool] は、拡張機能によって作成されたテーブルのデータを含め、そのままMagento2 データベースに転送します。

マップファイルで相違が宣言されない場合、[!DNL Data Migration Tool] はエラーを表示し、開始しません。

マッピングファイルの詳細については、[[!DNL Data Migration Tool] 技術仕様 ] を参照してください。

## 移行フロー図

![ 移行フロー ](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] 技術仕様](technical-specification.md)

世界の#1 コマースプラットフォームであるMagento 1.x から、未来のプラットフォームであるMagento 2 への移行を検討してくださっていることを嬉しく思います。 移行と呼ばれるこのプロセスの詳細をお知らせします。

## 移行コンポーネント

Magento 2 の移行には、データ、拡張機能、カスタムコード、テーマ、カスタマイズの 4 つのコンポーネントが含まれます。

### データ

すべての商品、顧客、注文データ、店舗の構成、プロモーションなどをMagento2 に効率的に移行するのに役立つ **Magento2[!DNL Data Migration Tool]** を開発しました。 このガイドでは、データ移行に使用するツールとベストプラクティスに関する情報を提供します。

### 拡張機能とカスタムコード

アドビでは、Magento 2 でMagento 1 の拡張機能を使用できるように、開発コミュニティと協力して取り組んでいます。 お気に入りの拡張機能の最新バージョンをダウンロードまたは購入できる [Commerce Marketplace](https://marketplace.magento.com/) を紹介します。

Magento 2 の拡張モジュール開発の詳細については、「[PHP 開発者ガイド ](https://developer.adobe.com/commerce/php/development/)」を参照してください。

### テーマとカスタマイズ

Magento2 は、新しいアプローチとテクノロジーを使用して、マーチャントに革新的なショッピングエクスペリエンスを生み出し、新しいレベルに拡張する比類のない能力を提供します。 これらの高度な機能を活用するには、開発者はテーマやカスタマイズを変更する必要があります。 Magento 2 [ テーマ ](https://developer.adobe.com/commerce/frontend-core/guide/themes/)、[ レイアウト ](https://developer.adobe.com/commerce/frontend-core/guide/layouts/)、[ カスタマイズ ](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/) の作成に関するドキュメントがオンラインで利用できます。

## 移行の努力

バージョン 1.x 間（v1.12 から v1.14 など）のアップグレードと同様に、Magento 1 からMagento 2 への移行に必要な労力のレベルは、サイトの構築方法とそのカスタマイズのレベルによって異なります。
しかし、私たちは常に [!DNL Data Migration Tool] を改善しています（詳しくは [ 変更ログ ](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) を参照）。そのため、移行の取り組みは減少し続けています。
