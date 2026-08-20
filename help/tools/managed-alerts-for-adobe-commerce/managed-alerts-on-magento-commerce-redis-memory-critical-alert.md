---
title: Adobe Commerceのアラートを管理： [!DNL Redis]  メモリ クリティカル アラート
description: この記事では、 [!DNL New Relic]でAdobe Commerceの [!DNL Redis] memory critical アラートを受け取った場合のトラブルシューティング手順について説明します。 この問題を解決するには、ただちに行動を起こす必要があります。
feature: Cache, Categories, Observability, Services, Support, Tools and External Services, Variables
role: Admin
exl-id: 1233889e-8c02-4ad6-b12c-683010b7bf35
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# Adobe Commerceで管理されたアラート：[!DNL Redis] メモリ クリティカル アラート

この記事では、[!DNL New Relic]でAdobe Commerceの[!DNL Redis] メモリ不足に関する警告を受け取った場合のトラブルシューティング手順について説明します。 この問題を解決するには、ただちに行動を起こす必要があります。 選択したアラート通知チャネルに応じて、アラートは次のようになります。

![new_relic_redis_memory_critical.png](../../assets/managed-alerts/new_relic_redis_memory_critical.png)

## 影響を受ける製品とバージョン

Adobe Commerce on cloud infrastructure Pro プランアーキテクチャのすべてのバージョン

## イシュー

Adobe Commerce[&#128279;](managed-alerts-for-magento-commerce.md)の管理対象アラートにサインアップし、1つ以上のアラートしきい値を超えた場合、[!DNL New Relic]にアラートが届きます。 これらのアラートは、Adobe Adobeが開発したもので、サポートとエンジニアリングから得たインサイトを活用して、標準的なアラートを顧客に提供します。

**<u>実行！</u>**

* このアラートがクリアされるまでスケジュールされたデプロイメントをすべて中止します。
* サイトが完全に応答しない、または応答しなくなった場合は、すぐにメンテナンスモードにします。 手順については、『Commerce インストールガイド』の「[&#x200B; メンテナンスモードを有効または無効にする](/help/installation/tutorials/maintenance-mode.md)」を参照してください。 トラブルシューティングのためにサイトにアクセスできるように、IPを免除IP アドレスリストに追加してください。 手順については、Commerce インストールガイドの「[除外IP アドレスのリストを管理する](/help/installation/tutorials/maintenance-mode.md#maintain-the-list-of-exempt-ip-addresses)」を参照してください。

**<u>やめて！</u>**

* 追加のページビューをサイトに呼び込む可能性のある、追加のマーケティング施策を開始します。
* CPUまたはディスクに負荷がかかる可能性があるインデクサーまたは別のクローンを実行します。
* 主要な管理タスクを実行します（例：データのインポート/エクスポート、メディアのフラッシュ、割り当てられた多数の製品を含むカテゴリの保存、一括更新など、Commerce管理者の主要なアクション）。
* キャッシュをクリアします。

## Solution

以下の手順に従って、原因を特定し、トラブルシューティングします。

**これは重大な警告であるため、問題のトラブルシューティングを試みる前に、手順1を完了することを強くお勧めします（手順2以降）。**

1. Adobe Commerce サポートチケットが存在するかどうかを確認します。 手順については、Commerce サポート サポート サポート サポート サポート技術情報の[&#x200B; サポートチケットの追跡](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#track-support-case)を参照してください。 サポートは、既に[!DNL New Relic]しきい値の通知を受け取り、チケットを作成し、問題に取り組み始めている可能性があります。 チケットが存在しない場合は、チケットを作成します。 チケットには次の情報が必要です。

   * 連絡先の理由：**[!UICONTROL New Relic CRITICAL alert received]**&#x200B;を選択してください。
   * アラートの説明。
   * [[!DNL New Relic]  インシデントリンク &#x200B;](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents/)。 これは、Adobe Commerce[&#128279;](managed-alerts-for-magento-commerce.md)の管理済みアラートに含まれています。

1. サポートチケットが存在しない場合は、[one.newrelic.com](https://login.newrelic.com) > **[!UICONTROL Infrastructure]** > **[!UICONTROL Third-party services]** ページに移動して、[!DNL Redis]使用済みメモリが増加または減少しているかどうかを確認し、[!DNL Redis] ダッシュボードを選択します。 安定または増加している場合は、[&#x200B; サポートチケット &#x200B;](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case)を送信してクラスターをアップグレードするか、`maxmemory`制限を次のレベルに増やします。
1. メモリ消費量が[!DNL Redis]増加する原因を特定できない場合は、最近の傾向を確認して、最近のコードのデプロイや設定の変更（新しい顧客グループやカタログの大規模な変更など）に関する問題を特定します。 コードのデプロイメントまたは変更の相関関係については、過去7日間のアクティビティを確認することをお勧めします。
1. サードパーティの拡張機能が正しく動作しないか確認してください：

   * 最近インストールされたサードパーティの拡張機能と問題が発生した時間との相関関係を確認してください。
   * Adobe Commerce キャッシュに影響を与え、キャッシュが迅速に拡張される可能性がある拡張機能を確認します。 たとえば、カスタムレイアウトブロック、キャッシュ機能の上書き、大量のデータのキャッシュへの保存などです。

1. 上記の手順で問題の原因を特定またはトラブルシューティングできない場合は、L2 キャッシュを有効にしてアプリと[!DNL Redis]間のネットワークトラフィックを削減することを検討してください。 L2 キャッシュの概要については、『Commerce Configuration Guide 』の「[L2 caching in the Adobe Commerce application](/help/configuration/cache/level-two-cache.md)」を参照してください。 クラウドインフラストラクチャのL2 キャッシュを有効にするには、次の手順を実行します。

   * 2002.1.2 バージョン未満の場合は、ECE ツールをアップグレードします。
   * [REDIS\_BACKEND変数](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend)を使用して`.magento.env.yaml` ファイルを更新して、L2 キャッシュを設定します。

   ```yaml
   stage:
       deploy:
           REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
