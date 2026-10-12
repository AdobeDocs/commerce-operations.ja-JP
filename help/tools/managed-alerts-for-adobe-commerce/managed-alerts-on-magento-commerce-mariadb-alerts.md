---
title: Adobe Commerceでのアラートの管理：MariaDB アラート
description: この記事では、[!DNL New Relic]でAdobe CommerceのMariaDB アラートを受け取った場合のトラブルシューティング手順について説明します。 MariaDB アラートは、高いクエリロードと過剰なData Manipulation Language （DML）クエリを監視します。 どちらも、ユーザーエクスペリエンスの低下やダウンタイムにつながる可能性があります。 2種類のアラートを受け取ることができます。
feature: Cache, Observability, Support, Tools and External Services
role: Admin
exl-id: d85af2e1-090c-4ad7-a898-3a3c4a5efe3b
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: a59f76dc-e003-5617-951e-dffa5bd3de81
    internal-label: Support
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%
---
# Adobe Commerceでのアラートの管理：MariaDB アラート

この記事では、[!DNL New Relic]でAdobe CommerceのMariaDB アラートを受け取った場合のトラブルシューティング手順について説明します。 MariaDB アラートは、高いクエリロードと過剰なData Manipulation Language （DML）クエリを監視します。 どちらも、ユーザーエクスペリエンスの低下やダウンタイムにつながる可能性があります。 次の2種類のアラートを受け取ることができます。

* DML クエリの警告
* DML クエリが重要

## 影響を受ける製品とバージョン

Adobe Commerce on cloud infrastructure Pro プランアーキテクチャ

## イシュー

Adobe Commerce](managed-alerts-for-magento-commerce.md)の[管理対象アラートにサインアップし、1つ以上のアラートしきい値を超えた場合、[!DNL New Relic]に管理対象アラートが届きます。 これらのアラートは、サポートとエンジニアリングからのインサイトを使用して、お客様に標準セットを提供するためにAdobeによって開発されました。

**実行！**

* このアラートがクリアされるまでスケジュールされたデプロイメントをすべて中止します。
* サイトが完全に応答しない、または応答しなくなった場合は、すぐにメンテナンスモードにします。 手順については、『Commerce インストールガイド』の「[ メンテナンスモードを有効または無効にする](/help/installation/tutorials/maintenance-mode.md)」を参照してください。 トラブルシューティングのためにサイトにアクセスできるように、IPを免除IP アドレスリストに追加してください。 手順については、[除外IP アドレスのリストの管理](/help/installation/tutorials/maintenance-mode.md#maintain-the-list-of-exempt-ip-addresses)を参照してください。
* サイトパフォーマンスに影響がある場合は、アラートの原因となるインポートなどのスクリプトを終了します。

**やめて！**

* MariaDBに追加のストレスを与える可能性があるインデクサーまたは追加のcronを実行します。
* 主要な管理作業（Commerce管理者、データの読み込み/書き出しなど）を行います。
* キャッシュをクリアします。

## Solution

**DML クエリ （UPDATE、INSERT、およびDELETEを使用してデータベースを変更するクエリ）**

DML Queries Critical アラートを受け取った場合は、最初の手順から開始します。 DML クエリの警告アラートを受け取った場合は、手順2から開始します。

1. Adobe Commerce サポートチケットが存在するかどうかを確認します。 手順については、ナレッジベース [ サポートチケットの追跡](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#track-support-case)を参照してください。 サポートは、[!DNL New Relic]しきい値のアラートを受け取り、チケットを作成し、問題に取り組み始めた可能性があります。 チケットが存在しない場合は、チケットを作成します。 チケットには次の情報が必要です。
   * 連絡先の理由：**[!UICONTROL New Relic MariaDB alert received]**&#x200B;を選択してください。
   * アラートの説明。
   * [[!DNL New Relic]  インシデントリンク ](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents)。 これは、Adobe Commerce](managed-alerts-for-magento-commerce.md)の[管理済みアラートに含まれています。
1. 問題の原因を特定するには、DML クエリを特定してみてください。
   1. New Relic [ データベース ページ ](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time)の手順を使用して、データベース操作を確認します。
   1. **[!UICONTROL CALL COUNT]**、次に&#x200B;**[!UICONTROL OPERATION]**&#x200B;で並べ替えます。 `INSERT`、`DELETE`および`UPDATE`操作を確認してください。
   1. 高いAVGを探します。
   1. クリックして、データベース操作の呼び出し元を検索します。 これにより、クエリを使用しているトランザクションを時間ごとに特定できます。
   1. コードの最適化や運用上の最適化について調べます。
      * コードの最適化：一括挿入/更新、インデックスの使用を最小限に抑える、コードのスロットリングを使用して、クエリを最適化します。
      * 運用の最適化：リソースを大量に消費するデータの変更をオフロードして、トラフィック時間を短縮します。
      * 追加の最適化：最新バージョンのECE-Toolsを使用していることを確認します。 手順については、『Commerce on Cloud Guide 』の「[e-tools バージョンを更新](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package)」を参照してください。
