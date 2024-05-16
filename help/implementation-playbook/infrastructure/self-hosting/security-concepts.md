---
title: 自己ホスト型Adobe Commerce セキュリティの概念
description: 自己ホスト型のセキュリティに関するアイデアと概念、および考慮すべきベストプラクティスについて説明します。 Adobe commerce をホストする際に考慮すべき読み取り専用ファイルシステム、マルウェアのスキャン、その他多くのトピックなどの概念について説明します。
landing-page-description: セキュリティの概念と、Adobe Commerceを自分でホストする際に考慮すべき事項について説明します。
short-description: Adobe Commerceを自分でホストするための戦略とセキュリティの概念について説明します。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: f76a8906-af31-4a61-be68-f5dad87161e2
feature: Install, Security
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1546'
ht-degree: 0%

---

# セキュリティの概念

セキュリティは、e コマースプロジェクトに関連するあらゆることに対して常に強力に考慮する必要があります。 強力なセキュリティ対策がなければ、攻撃可能な表面積は指数関数的に大きくなります。 提示される概念とアイデアは、典型的に悪用される一般的な脆弱性を減らすことが証明されている方法を提供します。

以下の概念は特定の順序ではありません。 考慮すべきアイデアや概念を提供することを目的としています。 多くは無料であるか、最小限のセットアップと設定、およびその後の監視が必要になります。 ここに示す概念を十分に理解できるように、このチュートリアル以外でこれらのトピックを調べます。

## 読み取り専用ファイルシステム

読み取り専用のファイルシステムの概念は、次の場所から借用されました。 [クラウドインフラストラクチャー上のAdobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. これにより、悪い俳優が使用する 1 つの主要な領域が完全に削除されます。 悪用の多くは、検出されないように、Commerce アプリケーション内にあると想定されるファイルを変更することを利用しています。 不正なアクターは、ファイルを作成する代わりに、既存のファイルの内容を変更して、予期しないアクションを実行します。 ファイルシステムを読み取り専用にすると、この攻撃ベクトルが大幅に減少します。

## 2 要素認証とパスワードマネージャーの使用

決してパスワードを共有しないでください。 各管理者ユーザーには、適切な ACL を持つ独自のアカウントが必要です。 2 要素の識別が無効になったり削除されたりしていないことを確認します。 サードパーティに管理者アクセス権を付与する場合は、パスワードがパスワードマネージャーによって生成され、再利用されないようにしてください。

## マルウェア スキャン

マルウェアのスキャンは、通常、Adobe Commerceでの特殊化を試みるホスティングプロバイダーから検出されます。 新しい脅威が発見、分類、診断されるにつれ、既知のマルウェアや攻撃のライブラリは増え続けています。 ホスティングプロバイダーにそのようなサービスがあるかどうか、また、ホスティングプロバイダーが自動的に実行できるか、またはリクエストに応じてのみ実行できるかを問い合わせてください。 また、既知の悪用の独自のライブラリを使用して、コマースアプリケーションの悪用を絶えず確認できる購読サービスもあります。 これらの一部は外部のみですが、インフラストラクチャに追加して、すべてのフォルダー、ファイル、さらにはデータベースに対する内部のディープスキャンを提供することもできます。 Sansec.io から Sucuri、そしてもちろん MageReport まで、この分野で長年の経験を持つプロバイダーがいくつかあります。 無料のものもあれば、付随する費用が発生するものもあります。 この情報を入手し、Adobe Commerce アーキテクトや DevOps チームと十分に話し合うことで、適切なソリューションを確実に見つけることができます。

## Commerce用 Site-Wide Analysis Tool

この [サイト全体分析ツール](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} は、プロアクティブなセルフサービスツールで、Adobe Commerce インストールのセキュリティと操作性を確保するための詳細なシステムインサイトおよびレコメンデーションが含まれている中央リポジトリです。 24 時間 365 日、パフォーマンスの監視、レポート、アドバイスをリアルタイムで行うことで、潜在的な問題を特定し、サイトの正常性、安全性、アプリケーションの設定をより明確に把握します。 これにより、解決時間が短縮され、サイトの安定性とパフォーマンスが向上します。

## 管理アクションのログ記録の設定を有効にして確認する

これは、Adobe Commerce管理者にログインし、ストア /設定/詳細/管理者/管理者アクションのログに移動すると見つかります。 監視および記録されるイベントのリストが表示されます。 悪用されたサイトでフォレンジック分析を行う際に、疑わしいユーザーがCommerce管理者にアクセスできると便利です。 このログとレポートは、不正なアクターが実行したイベントを確認するのに役立ちます。 管理者アクションのログが無効になっている場合、誰かがカバーするために管理者アクションを無効にした可能性があることを示すサインです。特定のアクションを実行するときは、ログを削除してください。

## SSH アクセス用の Bastion サーバー

これは、「セキュリティの概念」チュートリアルのほとんどのトピックでは説明が困難です。 この基本的な考え方は、ssh アクセスの仲介者として機能するサーバを提供することです。 この方法では、実稼動サーバーは外部の ssh 接続を許可しません。 このバスティングサーバーを作成し、ローカル IP マスクを使用して、指定されたサーバーのみが SSH で接続できるようにすることができます。

## ACL の役割と権限の確認

Adobe Commerceのすべての管理者ユーザーには、ACL ロールが割り当てられます。 この役割は、ジョブを実行する必要がある機能のみを提供するために作成する必要があります。 ACL の役割は必要以上の権限を与えないように、頻繁に評価する必要があります。 必要に応じて、責任を持つ多くの ACL 役割を作成します。 何らかの理由でサードパーティへのアクセスが許可された場合は、できるだけ早くアクティベートを解除する必要があります。 管理者ユーザーを作成する際に、アクセスが絶対に必要な期間を尋ね、自動有効期限を設定します。

## 管理者ユーザーと SSH ユーザーアクセスを頻繁に監査する

管理者ユーザーの望ましくない作成や不正な作成を検出するために、管理者ユーザーリストは頻繁に監査される必要があります。 経験則として、Adobe Commerce アプリケーションに対する SSH および管理者アクセス権を持つユーザーを毎月確認することをお勧めします。 新しいユーザーが検出された場合は、そのユーザーのアカウントを無効にし、そのようなインシデントに対する会社のポリシーと手順に従ってください。 エクスプロイトから回復するよりも、ユーザーアクセスを回復する方が簡単です。

## データベースクレンジング

実稼動データへのアクセスを制限します。 指定されたチームメイトは、実稼動データベースを取り込み、実際のデータをクレンジングできる必要があります。 データの削除がオプションの場合は、受注、見積、顧客などの適切な表を切り捨てます。 ただし、データの完全なセットが必要でも、値を匿名化できる場合もあります。 これは通常、ステージング環境で発生します。 アップグレードの前にも役立ちます。 リアルタイムのデータ量を匿名化することで、アップグレード用のデプロイメントを適切に実行するための時間をテストおよび検証できます。 データのセットが限られている場合、アップグレードプロセスとタイミングを過小評価する可能性があります。

+++ランダム化顧客情報の例Adobe Commerceがデータを保存する一部の標準テーブルで、ランダムな文字列とすべての名フィールドと姓フィールドを使用して顧客のメールアドレスを変更する方法の例を以下に示します。 **すべてのテーブルの機密データを確認してください。このリストは、顧客データを保存する可能性のあるテーブルを含むものではありません**

```SQL
SET FOREIGN_KEY_CHECKS=0;
UPDATE customer_entity SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE email_contact SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE sales_invoice_grid SET customer_email = 'customer@example.com', customer_name  = 'Jack Smith';
UPDATE sales_order SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Smith', remote_ip = '127.0.0.1';
UPDATE sales_order_address SET region = 'Ohio', postcode = '12345-1234', lastname = 'Smith', street = '123 Main street', region_id = 44, city = 'Phoenix', telephone = NULL, firstname = 'Jane', company = NULL;
UPDATE sales_order_grid SET customer_email = 'customer@example.com', shipping_name = 'Jack', billing_name = 'Jack Smith', billing_address = '123 Main Street', shipping_address = '321 Pine Street', customer_name = 'Jane Smith';
UPDATE sales_shipment_grid SET customer_email = 'customer@example.com', customer_name = 'Jane Smith', billing_address = '123 Main street', billing_name = 'Jack Doe', shipping_name = 'Susie Smith';
UPDATE quote SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Jones', customer_dob = NULL, remote_ip = '127.0.0.1';
UPDATE quote_address SET email = 'customer@example.com', firstname = 'Jack', lastname = 'Smith', company = NULL, street = '123 Main st', city = 'AnyCity', region = 'Some State', region_id = 44, postcode = '12345-1234', telephone = NULL;
UPDATE magento_rma SET customer_custom_email = 'customer@example.com' WHERE customer_custom_email IS NOT NULL;
UPDATE customer_address_entity SET firstname = 'Jack', lastname = 'Smith', telephone = '909-555-1212', postcode = NULL,  region = NULL, street = '123 Main street', city = 'Anycity', company = NULL;
UPDATE customer_grid_flat SET name = 'Jane Doe', email = 'customer@example.com', dob = NULL, gender = NULL, taxvat = NULL, shipping_full = '', billing_full = '', billing_firstname = 'Jack', billing_lastname = 'Smith', billing_telephone = NULL, billing_postcode = NULL, billing_country_id = NULL, billing_region = NULL, billing_street = '123 Main street', billing_city = 'Anycity', billing_fax = NULL, billing_vat_id = NULL, billing_company = NULL;
UPDATE sales_creditmemo_grid SET billing_name = 'Sally', billing_address = '123 Main Street', customer_name = 'Jack Smith', customer_email = 'customer@example.com';
    
UPDATE magento_rma_grid SET customer_name = 'Jack Smith';
SET FOREIGN_KEY_CHECKS=1;
```

+++


+++匿名化を試みる代わりに、テーブルを切り捨てることもできます

```SQL
SET FOREIGN_KEY_CHECKS=0;
TRUNCATE customer_log;  
TRUNCATE customer_visitor;  
TRUNCATE magento_logging_event;
TRUNCATE oauth_consumer;
TRUNCATE oauth_nonce;
TRUNCATE oauth_token;
TRUNCATE password_reset_request_event;
TRUNCATE acknowledgement;
TRUNCATE acknowledgement_report;
TRUNCATE avatax_log;
TRUNCATE avatax_queue;
TRUNCATE cron_schedule;
SET FOREIGN_KEY_CHECKS=1;
```

+++

+++情報を完全に削除する例ローンチ前または低い開発環境のためにすべての注文、見積もり、クレジットメモなどを削除する例を以下に示します

```SQL
DELETE FROM `gift_message`;
DELETE FROM `inventory_reservation`;
DELETE FROM `quote`;
DELETE FROM `quote_address`;
DELETE FROM `quote_address_item`;
DELETE FROM `quote_id_mask`;
DELETE FROM `quote_item`;
DELETE FROM `quote_item_option`;
DELETE FROM `quote_payment`;
DELETE FROM `quote_shipping_rate`;
DELETE FROM `reporting_orders`;
DELETE FROM `sales_bestsellers_aggregated_daily`;
DELETE FROM `sales_bestsellers_aggregated_monthly`;
DELETE FROM `sales_bestsellers_aggregated_yearly`;
DELETE FROM `sales_creditmemo`;
DELETE FROM `sales_creditmemo_comment`;
DELETE FROM `sales_creditmemo_grid`;
DELETE FROM `sales_creditmemo_item`;
DELETE FROM `sales_invoice`;
DELETE FROM `sales_invoiced_aggregated`;
DELETE FROM `sales_invoiced_aggregated_order`;
DELETE FROM `sales_invoice_comment`;
DELETE FROM `sales_invoice_grid`;
DELETE FROM `sales_invoice_item`;
DELETE FROM `sales_order`;
DELETE FROM `sales_order_address`;
DELETE FROM `sales_order_aggregated_created`;
DELETE FROM `sales_order_aggregated_updated`;
DELETE FROM `sales_order_grid`;
DELETE FROM `sales_order_item`;
DELETE FROM `sales_order_payment`;
DELETE FROM `sales_order_status_history`;
DELETE FROM `sales_order_tax`;
DELETE FROM `sales_order_tax_item`;
DELETE FROM `sales_payment_transaction`;
DELETE FROM `sales_refunded_aggregated`;
DELETE FROM `sales_refunded_aggregated_order`;
DELETE FROM `sales_shipment`;
DELETE FROM `sales_shipment_comment`;
DELETE FROM `sales_shipment_grid`;
DELETE FROM `sales_shipment_item`;
DELETE FROM `sales_shipment_track`;
DELETE FROM `sales_shipping_aggregated`;
DELETE FROM `sales_shipping_aggregated_order`;
DELETE FROM `tax_order_aggregated_created`;
DELETE FROM `tax_order_aggregated_updated`;
DELETE FROM `magento_rma`;
DELETE FROM `magento_rma_grid`;
DELETE FROM `magento_rma_item_entity`;
DELETE FROM `magento_rma_status_history`;
DELETE FROM `magento_sales_creditmemo_grid_archive`;
DELETE FROM `magento_sales_invoice_grid_archive`;
DELETE FROM `magento_sales_order_grid_archive`;
DELETE FROM `magento_sales_shipment_grid_archive`;
DELETE FROM `sequence_creditmemo_0`;
DELETE FROM `sequence_creditmemo_1`;
DELETE FROM `sequence_creditmemo_2`;
DELETE FROM `sequence_creditmemo_7`;
DELETE FROM `sequence_invoice_0`;
DELETE FROM `sequence_invoice_1`;
DELETE FROM `sequence_invoice_2`;
DELETE FROM `sequence_invoice_7`;
DELETE FROM `sequence_order_0`;
DELETE FROM `sequence_order_1`;
DELETE FROM `sequence_order_2`;
DELETE FROM `sequence_order_7`;
DELETE FROM `sequence_rma_item_0`;
DELETE FROM `sequence_rma_item_1`;
DELETE FROM `sequence_rma_item_2`;
DELETE FROM `sequence_rma_item_7`;
DELETE FROM `sequence_shipment_0`;
DELETE FROM `sequence_shipment_1`;
DELETE FROM `sequence_shipment_2`;
DELETE FROM `sequence_shipment_7`;

## USE THE FOLLOWING WITH CAUTION - CAN CAUSE ISSUES WITH TAX/PAYMENT PROCESSORS IF YOU REUSE ORDER NUMBERS, ETC.

ALTER TABLE sequence_creditmemo_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_7 AUTO_INCREMENT=1;
```

+++

## 環境変数の使用

[!BADGE Adobe Commerce on cloud のみ]{type=Informative}

環境変数を使用すると、環境ごとに変更できる値と変更する必要がある値を設定できます。 例えば、環境ごとに異なる管理者 URL を使用したい場合があります。 この値を環境変数として設定すると、これを設定できるほか、必要に応じて Cloud UI からこの値をすばやく参照することもできます。

このトピックの詳細については、Experience Leagueを参照してください [クラウドインフラストラクチャー上のCommerceの環境変数](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## ソフトウェア脆弱性スキャンツール

CI/CD パイプラインは強力なツールとなり、一部のタスクを自動化するのに役立ちます。 特に、悪用できる可能性のあるコードを開発者がコミットする機会は、常に真の可能性です。 ピアコードレビューは通常、そのようなアイテムをキャッチしますが、それは人間であるため、間違いが発生します。 自動コードスキャンは、新しく導入された機能で予期しない脆弱性が発生する機会を減らすのに役立ちます。 これらのツールは、コードをライブコードベースに結合するのをブロックする場所に配置することもできます。 自動コードセキュリティと品質スキャンを提供する方法やツールは多数あります。 堅牢なカスタム開発ツールもありますが、定期的な更新と調整が必要です。 別の方法として、synk.io やAmazonのコードインスペクターなど、事前に更新されたツールを適用することもできます。

## Web アプリケーションファイアウォール

DevOps やホスティングプロバイダーと話すときによく使用される web アプリケーションファイアウォールまたは WAF。

Web アプリケーションファイアウォール（WAF）は、一連のセキュリティルールに対してトラフィックをフィルタリングすることで、悪意のあるトラフィックがサイトやネットワークに侵入するのを防ぎます。 いずれかの規則をトリガーするトラフィックは、サイトやネットワークに損害を与える前にブロックされます。

Adobe Commerceの Cloud WAF は、Adobe Commerce web アプリケーションを様々な攻撃から保護するように設計されたルールセットを含む WAF ポリシーを提供します。 セルフホスティングオプションを選択する場合、WAF の検索とルールの設定はユーザーの責任です。 一部のホスティングプロバイダーや WAF プロバイダーには、開始に適した一般的なルールのセットがありますが、一部の作業ではプロジェクトに適した結果が得られることを期待しています。

WAF は、Web および管理トラフィックを調べて、疑わしいアクティビティを特定します。 GETとPOSTトラフィック（HTTP API 呼び出し）を評価し、ルールセットを適用して、ブロックするトラフィックを決定します。 WAF は、SQL インジェクション攻撃、クロスサイトスクリプティング攻撃、データ除外攻撃、HTTP プロトコル違反など、様々な攻撃をブロックできます。

WAF はクラウドベースのサービスで、インストールや保守にハードウェアやソフトウェアを必要としません。 既存のテクノロジーパートナーである Fastly は、ソフトウェアと専門知識を提供します。 その高パフォーマンスで常時稼動の WAF は、Fastly のグローバル配信ネットワーク全体の各キャッシュノードに存在します。

Fastly が提供するAdobe Commerce on cloud の WAF について詳しくは、 [Adobe Commerce ナレッジベース FAQ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
