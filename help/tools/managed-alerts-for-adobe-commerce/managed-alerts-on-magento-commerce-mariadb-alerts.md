---
title: Adobe Commerceの管理アラート：MariaDB アラート
description: この記事では、 [!DNL New Relic] でAdobe Commerceの MariaDB アラートを受信した場合のトラブルシューティング手順を説明します。 MariaDB アラートは、高いクエリ負荷と過剰なデータ操作言語（DML）クエリを監視します。 どちらも、ユーザーエクスペリエンスの低下やダウンタイムにつながる可能性があります。 2 種類のアラートを受信できます。
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: ccf8b7c5ad1fbef2cfba05f65f05ab8af0375b4c
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---


# Adobe Commerceの管理アラート：MariaDB アラート

この記事では、[!DNL New Relic] でAdobe Commerceの MariaDB アラートを受信した場合のトラブルシューティング手順を説明します。 MariaDB アラートは、高いクエリ負荷と過剰なデータ操作言語（DML）クエリを監視します。 どちらも、ユーザーエクスペリエンスの低下やダウンタイムにつながる可能性があります。 次の 2 種類のアラートを受信できます。

* DML 問合せの警告
* DML 問合せクリティカル

## 影響を受ける製品とバージョン

Adobe Commerce on cloud infrastructure Pro プランアーキテクチャ

## 問題

[Adobe Commerceの Managed アラート ](managed-alerts-for-magento-commerce.md) にサインアップし、1 つ以上のアラートしきい値を超えた場合、[!DNL New Relic] で管理アラートを受け取ります。 これらのアラートは、サポートおよびエンジニアリングのインサイトを使用して、標準セットをお客様に提供するために、Adobeで開発されました。

**動け！**

* このアラートがクリアされるまで、スケジュールされている展開を中止します。
* サイトが応答しない、または完全に応答しなくなった場合は、すぐにサイトをメンテナンスモードにします。 手順については、『Commerce インストールガイド』の [ メンテナンスモードの有効化または無効化 ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) を参照してください。 トラブルシューティングのためにサイトに引き続きアクセスできるように、IP を除外 IP アドレスリストに追加してください。 手順については、「[ 除外 IP アドレスのリストの管理 ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)」を参照してください。
* サイトパフォーマンスに影響が出ている場合は、読み込みなどのスクリプトを終了し、アラートの原因を特定してください。

**やめて！**

* MariaDB に追加の負荷がかかる可能性のあるインデクサーや追加のクローンを実行します。
* 主要な管理タスク（Commerce管理者、データのインポート/エクスポートなど）を実行します。
* キャッシュをクリアします。

## 解決策

**DML 問合せ（UPDATE、INSERT およびDELETEを使用してデータベースを変更する問合せ）**

DML クエリ・クリティカル・アラートを受け取った場合は、手順 1 から開始します。 DML クエリの警告アラートを受け取った場合は、手順 2 から開始します。

1. Adobe Commerce サポートチケットが存在するかどうかを確認します。 手順については、ナレッジベース [ サポートチケットの追跡 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) を参照してください。 サポートがしきい値アラートを受け取り、チケッ [!DNL New Relic] を作成して、問題の処理を開始した可能性があります。 チケットが存在しない場合は、作成します。 チケットには、次の情報が含まれている必要があります。
   * 連絡先の理由：「**[!UICONTROL New Relic MariaDB alert received]**」を選択します。
   * アラートの説明。
   * [[!DNL New Relic]  インシデント リンク ](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). これは、[Adobe Commerceの Managed アラート ](managed-alerts-for-magento-commerce.md) に含まれています。
1. 問題の原因を特定するには、DML 問合せを特定します。
   1. New Relic[ データベースページ ](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) の手順を使用して、データベース操作を確認します。
   1. **[!UICONTROL CALL COUNT]** で並べ替え、次に **[!UICONTROL OPERATION]** で並べ替えます。 `INSERT`、`DELETE`、`UPDATE` の操作を確認します。
   1. 高い AVG を探します。
   1. クリックスルーしてデータベース操作呼び出し元を検索します。 これにより、そのクエリを使用しているトランザクションが時間別に識別されます。
   1. コードの最適化または運用の最適化を探します。
      * コードの最適化：一括挿入/更新、インデックス使用の最小化、コードのスロットルなどを使用してクエリを最適化する場合を想定しています。
      * 運用の最適化：リソースを大量に消費するデータ変更の負荷を軽減し、トラフィック時間を短縮します。
      * その他の最適化：ECE-Tools の最新バージョンを使用していることを確認してください。 手順については、Cloud ガイドのCommerceの [ece-tools バージョンを更新 ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) を参照してください。
