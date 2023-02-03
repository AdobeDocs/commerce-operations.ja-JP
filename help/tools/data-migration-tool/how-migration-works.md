---
title: データ移行の仕組み
description: 用語、ワークフロー図、手順など、Magento1 とMagento2 の間のデータ移行プロセスについて説明します。
source-git-commit: 2e1a06b59fda7db4a9b32d000e1b2a3ca88926d3
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---


# データ移行の仕組み

このトピックでは、 [!DNL Data Migration Tool].

この [!DNL Data Migration Tool] は、Magento1 からMagento2 にデータを転送するために使用されるコマンドラインインターフェイス (CLI) ツールです。 ツールは、Magento1 と 2 のデータベース構造（テーブルとフィールド）間の整合性を検証し、データ転送の進行状況を追跡し、ログを作成し、データ検証テストを実行します。

## 用語

* **モード** -Magento1.x からMagento2.x へのデータ移行のための一連の操作が順序付けられています。
* **手順**  — 移行するデータの種類を定義するモードのタスク。
* **ステージ**  — データを検証、転送、検証する手順のタスク。
* **マップファイル**  — ステージを完了するための、Magento1.x とMagento2.x のデータ構造体の間のルールと接続を定義する XML ファイル。

## モード

この [!DNL Data Migration Tool] では、移行プロセスを 3 つの段階に分割するか、 *モード* データをMagento1.x からMagento2.x に転送して適応させるために使用します。3 つのモードがここに表示されます。この順序で実行する必要があります。

1. **設定モード**:はシステム設定と web サイト関連の設定を移行します。
1. **データモード**:データベースアセットを一括で移行します。
1. **差分モード**:は、新規顧客や注文など、増分的な変更（前回の実行以降の変更）を移行します。

![移行モード](../../assets/data-migration/MigrationModes2.png)

## 手順

この [!DNL Data Migration Tool] は、 *手順* を使用して、特定のタイプのデータを移行できます。 例えば、設定モードでは、すべての設定データを移行するために次の 2 つの手順を使用します。「保存」の手順と「設定」の手順 これらの各手順（および他のモードの手順）で移行される特定のデータの詳細は、 [[!DNL Data Migration Tool] 技術仕様](technical-specification.md).

![移行の概要](../../assets/data-migration/MigrationOverview2.png)

## ステージ

各ステップには、 *ステージ* データが適切に移行されるよう、常に次の順序で実行されます。

1. **整合性チェック**:テーブルのフィールド名、タイプ、その他の情報を比較して、Magento1 と 2 のデータ構造の互換性を検証します。
1. **データ転送**:データテーブルをMagento1 および 2 からテーブル別に転送します。
1. **ボリュームチェック**:テーブル間のレコード数を比較し、転送が成功したことを確認します。

![移行ステージ](../../assets/data-migration/MigrationSteps2.png)

## マップファイル

移行プロセスの最下位レベルには XML が存在します *マップファイル*. この [!DNL Data Migration Tool] は、ステップのステージ内でマップファイルを使用して、Magento1.x と 2.x のテーブル間で異なるデータ構造を変換します。

たとえば、Magento Open Source1.8.0.0 のデータベースからMagento Open Source2.x.x にデータを変換する場合、マップファイルはテーブルの名前が変更されたことを考慮し、その名前を宛先データベースで変更します。 データ構造やデータ形式に違いがない場合は、 [!DNL Data Migration Tool] は、拡張機能によって作成されたテーブルのデータを含め、そのままMagento2 データベースに転送します。

マップファイルで違いが宣言されていない場合、 [!DNL Data Migration Tool] はエラーを表示し、開始しません。

マッピングファイルについては、[[!DNL Data Migration Tool] 技術仕様 ]

## 移行フロー図

![移行フロー](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] 技術仕様 ]: technical-specification.md

Magento1.x という世界の#1コマースプラットフォームから未来のMagento2 への移行をご検討いただけたことをうれしく思います。 このプロセスの詳細を、移行と呼ばれる方法で共有できることをうれしく思います。

## 移行コンポーネント

Magento2 の移行には、次の 4 つのコンポーネントが含まれます。データ、拡張機能、カスタムコード、テーマ、およびカスタマイズ機能が含まれます。

### データ

我々は、 **Magento2[!DNL Data Migration Tool]** すべての製品、顧客、および注文データを効率的に移動するのに役立つように、設定、プロモーションなどをMagento2 に保存します。 このガイドでは、ツールと、それを使用してデータを移行する際のベストプラクティスに関する情報を提供します。

### 拡張機能とカスタムコード

アドビは、Magento2 のMagento1 拡張機能を使用するのに役立つよう、開発コミュニティと共に取り組んでいます。 これで、 [Commerce Marketplace](https://marketplace.magento.com/)：お気に入りの拡張機能の最新バージョンをダウンロードまたは購入できます。

Magento2 の拡張機能の開発について詳しくは、 [PHP 開発者ガイド](https://developer.adobe.com/commerce/php/development/).

### テーマとカスタマイズ

Magento2 は、新しいアプローチと技術を使用して、商人に革新的なショッピングエクスペリエンスを創出し、新しいレベルに拡張する卓越した能力を提供します。 これらの進歩を活用するには、開発者はテーマやカスタマイズを変更する必要があります。 Magento2 の作成に関するドキュメントは、オンラインで入手できます。 [テーマ](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [レイアウト](https://developer.adobe.com/commerce/frontend-core/guide/layouts/)、および [カスタマイズ](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## 移行の取り組み

1.x バージョン間のアップグレード（v1.12 から v1.14 など）と同様に、Magento1 からMagento2 へ移行する際の作業レベルは、サイトの構築方法とそのカスタマイズのレベルによって異なります。
しかし、常に [!DNL Data Migration Tool] ( [Changelog](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) 詳細は、したがって、移住努力は継続的に減少しています。
