---
title: 自己ホスト型Adobe Commerceのセキュリティ概念
description: 自己ホスト型のセキュリティに関するアイデアと概念、および考慮すべきベストプラクティスについて説明します。 読み取り専用ファイルシステム、マルウェアスキャン、その他多くのトピックなど、adobe コマースをホストする際の考慮事項に関する概念について説明します。
landing-page-description: Adobe Commerceを独自にホストする際に考慮すべきセキュリティ概念と事項をいくつか説明します。
short-description: 自分でAdobe Commerceをホストするための戦略とセキュリティの概念について説明します。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: cca195c20ddcba634a8fc39c0867e0ae28f43683
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---


# セキュリティ概念

セキュリティは、常に e コマースプロジェクトに関連するあらゆるものに対して強く考慮する必要があります。 強いセキュリティスタンスがなければ、攻撃可能な表面積は急激に大きくなります。 提示された概念とアイデアは、一般的に悪用される一般的な脆弱性を減らす方法を提供します。

以下の概念は特定の順序ではありません。 これは、考慮すべきアイデアや概念を提供するためのものです。 多くは無料で、または最小限の設定と設定、その後の監視が必要です。 このチュートリアル以外でこれらのトピックを調べ、ここで紹介する概念を十分に理解していることを確認します。

## 読み取り専用ファイル・システム

読み取り専用ファイルシステムの概念は、 [Adobe Commerce an cloud infrastructure](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. これにより、悪役の使用する 1 つの主要な領域が完全に削除されます。 多くの悪用は、検出を避けるために、Commerce アプリケーションに存在すると想定されるファイルを変更することを利用しています。 不良アクターは、作成する代わりに、既存のファイルの内容を変更して、予期しないアクションを実行します。 ファイルシステムを読み取り専用にすると、この攻撃ベクトルが大幅に減少します。

## TWO Factor 認証およびパスワードマネージャを使用

パスワードは共有しないでください。 各管理者ユーザーは、適切な ACL を持つ独自のアカウントを持つ必要があります。 2 つの要因の識別が無効になったり削除されたりしないようにします。 サードパーティへの管理者アクセス権を提供する場合は、パスワードがパスワードマネージャーによって生成され、再利用されないようにしてください。

## マルウェアスキャン

マルウェアスキャンは、通常、Adobe Commerceを専門としようとするホスティングプロバイダーから見つかります。 新しい脅威が検出され、トリアージされ、診断されると、この既知のマルウェアや悪用例のライブラリは、ますます増え続けています。 ホスティングプロバイダーがそのようなサービスを持っているかどうか、および自動で実行できるか、またはリクエストに応じてのみ実行できるかどうかを確認します。 また、独自の既知の弱点を悪用したライブラリを使用して、コマースアプリケーションの悪用を常に確認できる、購読できるサービスもあります。 一部は外部のみで、一部はインフラストラクチャに追加して、すべてのフォルダー、ファイル、さらにはデータベースの内部ディープスキャンを提供できます。 このアリーナでは、Sansec.io から Sucuri、もちろん MageReport まで、長年の経験を持つプロバイダーがいくつか存在します。 無料のものもあれば、関連する費用も伴うものもあります。 これを理解し、Adobe Commerceのアーキテクトや DevOps チームと深く話し合うことで、適切なソリューションを見つけることができます。

## コマース用サイト全体分析ツール

この [サイト全体分析ツール](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} は、Adobe Commerceインストールのセキュリティと操作性を確保するための詳細なシステムインサイトと推奨事項を含む、プロアクティブなセルフサービスツールおよび中央リポジトリです。 リアルタイムで24/7るパフォーマンスの監視、レポート、アドバイスを提供し、潜在的な問題を特定し、サイトの正常性、安全性、およびアプリケーション設定をより適切に表示できるようにします。 解決時間を短縮し、サイトの安定性とパフォーマンスを向上させます。

## 管理アクションログの設定を有効にして検証します

これは、Adobe Commerce管理者にログインし、ストア/設定/詳細設定/管理者/管理アクションログに移動した後に表示されます。 これは、監視および記録されるイベントのリストを提供します。 疑いがコマース管理者にアクセスできた場合、搾取されたサイトで法医学的分析を行う際に役立ちます。 このログとレポートは、不良アクターが実行したイベントを確認するのに役立ちます。 管理アクションのログが無効になっている場合は、特定のアクションを実行したときに、誰かが隠しアクションのためにログを無効にした可能性がある場合は、ログを削除します。

## SSH アクセス用の Bastion Server

この操作は、「セキュリティ概念」チュートリアルのほとんどのトピックを説明するのが難しくなります。 この基本的な考え方は、ssh アクセスの仲介者として機能するサーバを提供することです。 このようにして、実稼動サーバーで外部の SSH 接続が許可されることはありません。 このベースションサーバーを作成し、ローカル IP マスクを使用して、指定されたサーバーのみが SSH で接続できるようにすることができます。

## ACL の役割と権限の確認

Adobe Commerceのすべての管理者ユーザーに ACL の役割が割り当てられます。 この役割は、ジョブを実行する必要がある機能のみを提供するために作成する必要があります。 ACL ロールは、必要以上の権限を提供しないように、頻繁に評価する必要があります。 必要に応じて、多くの ACL ロールと責務を作成します。 何らかの理由でサードパーティにアクセス権が付与された場合は、できるだけ早く非アクティブ化する必要があります。 管理者ユーザーを作成する際に、アクセスと自動有効期限の設定が必要な期間について尋ねます。

## 頻繁に管理者ユーザーと SSH ユーザーアクセスを監査する

不要な管理者ユーザーや権限のない管理者ユーザーの作成を検出するには、頻繁に監査する必要があります。 経験則として、Adobe Commerceアプリケーションに毎月 SSH と管理者アクセス権を持つユーザーを確認することが推奨されます。 新しいユーザーが検出された場合は、そのユーザーのアカウントを無効にし、そのようなインシデントに関する会社のポリシーおよび手順に従います。 ユーザーのアクセス権を回復する方が、利用から回復するよりも簡単です。

## データベースクレンジング

本番データへのアクセスを制限します。 指定されたチームメイトは、本番データベースをプルダウンし、実際のデータをクレンジングする能力を持っている必要があります。 データを削除することがオプションの場合、注文件数、引用符、顧客数などの適切なテーブルを切り捨てます。 ただし、完全なデータセットが必要な場合もありますが、値は匿名化できます。 これは、通常、ステージング環境でも同じです。 また、アップグレード前に便利です。 匿名化された実際のデータ量を持つことで、デプロイメントを適切に実行してアップグレードする時間をテストし、検証することができます。 限られたデータセットがある場合、アップグレードプロセスとアップグレードのタイミングを過小評価する可能性があります。

+++顧客情報のランダム化の例次に、Adobe Commerceでデータを格納する一部の標準テーブルで、ランダムな文字列とすべての名と姓のフィールドを使用して顧客の電子メールアドレスを変更する方法の例を示します。 **すべてのテーブルで機密データを確認することを忘れないでください。このリストは、顧客データを格納するテーブルを含むものではありません**

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


+++匿名化を試みる代わりに、テーブルを切り詰めることもできます

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

+++情報を完全に削除する例以下に、すべての注文、見積もり、クレジットメモなどを起動前または低い開発環境で削除する例を示します

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

[!BADGE Adobe Commerce Only]{type=Informative}

環境変数を使用すると、各環境で変更できる値と変更する必要がある値を設定できます。 例えば、環境ごとに異なる管理 URL を使用できます。 この値を環境変数として設定すると、これを設定し、必要に応じて Cloud UI からすばやくこの値を参照することができます。

このトピックの詳細については、Experience Leagueを参照してください [クラウドインフラストラクチャ環境変数でのコマース](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## ソフトウェア脆弱性スキャンツール

CI/CD パイプラインは、いくつかのタスクを自動化する強力なツールになります。 特に、開発者が利用可能なコードをコミットする機会は、常に真の可能性です。 ピアコードレビューは、通常、このようなアイテムを取得しますが、それは人間であるため、誤りが発生します。 自動コードスキャンにより、新しく導入された機能で予期しない脆弱性が発生する機会を減らすことができます。 これらのツールは、コードをライブコードベースに結合するのを防ぐためのものです。 コードセキュリティと品質スキャンを自動化する方法とツールは多数あります。 堅牢なカスタム開発ツールが存在する可能性がありますが、常に更新と調整が必要です。 代わりに、synk.io やAmazonのコードインスペクターなど、事前に更新されたツールを適用する方法もあります。

## Web アプリケーションファイアウォール

DevOps やホスティングプロバイダーとの通信時によく使用される Web アプリケーションファイアウォールまたは WAF。

Web アプリケーションファイアウォール (WAF) は、一連のセキュリティルールに従ってトラフィックをフィルタリングすることで、悪意のあるトラフィックがサイトやネットワークに入るのを防ぎます。 ルールのいずれかをトリガーするトラフィックは、サイトやネットワークに損害を与える前にブロックされます。

Adobe Commerceのクラウド WAF は、Adobe Commerce Web アプリケーションを様々な攻撃から保護するためのルールセットを備えた WAF ポリシーを提供します。 自己ホストオプションを選択し、WAF を検索し、ルールを設定する必要があります。 ホスティングプロバイダーや WAF プロバイダーの中には、好ましいスタートを切る一般的なルールセットがあるものの、一部の作業がプロジェクトに適していると考えられるものもあります。

WAF は、疑わしいアクティビティを識別するために、Web および管理トラフィックを調べます。 GETとPOSTトラフィック（HTTP API 呼び出し）を評価し、ルールセットを適用してブロックするトラフィックを決定します。 WAF は、SQL インジェクション攻撃、クロスサイトスクリプティング攻撃、データ抽出攻撃、HTTP プロトコル違反など、様々な攻撃をブロックする可能性があります。

クラウドベースのサービスである WAF では、インストールや保守を行うためのハードウェアやソフトウェアは必要ありません。 既存のテクノロジー・パートナーである Fastly は、ソフトウェアと専門知識を提供します。 Fastly のグローバル配信ネットワーク全体の各キャッシュノードに、常時稼働する高パフォーマンスの WAF を配置します。

Fastly が提供するクラウド上のAdobe Commerceの WAF について詳しくは、 [Adobe Commerce Knowledge Base FAQ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
