---
title: 'Managed alerts on Adobe Commerce: [!DNL Redis] memory warning アラート'
description: この記事では、 [!DNL New Relic] でAdobe Commerceの警告アラートを受け取った場合のトラブルシュ  [!DNL Redis]  ティング手順を説明します。 早急な対応が必要です。
feature: Categories, Marketing Tools, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: e91ed9e95677790001fcfa3acca75a709c003c39
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---


# Adobe Commerceの管理アラート：[!DNL Redis] memory warning アラート

この記事では、[!DNL New Relic] でAdobe Commerceの [!DNL Redis] 警告アラートが表示された場合のトラブルシューティング手順を説明します。 この問題を解決するには、早急な対応が必要です。 選択したアラート通知チャネルに応じて、アラートは次のようになります。

![new_relic_redis_memory_warning.png](../../assets/managed-alerts/new_relic_redis_memory_warning.png)

## 影響を受ける製品とバージョン

クラウドインフラストラクチャー上のAdobe Commerce Pro のすべてのバージョンは、アーキテクチャを計画します。

## 問題

[Adobe Commerceの Managed アラート ](managed-alerts-for-magento-commerce.md) にサインアップし、1 つ以上のアラートしきい値を超えた場合、[!DNL New Relic] でアラートが届きます。 これらのアラートは、Adobeが、サポートとエンジニアリングのインサイトを使用して、マーチャントに標準のアラートセットを提供するために開発しました。

**<u>動け！</u>**

* このアラートがクリアされるまで、スケジュールされているデプロイメントを中止することをお勧めします。
* サイトが完全に応答しなくなった場合、または完全に応答しなくなった場合は、直ちにサイトをメンテナンスモードにします。 手順については、『Commerce インストールガイド』の [ メンテナンスモードの有効化または無効化 ](https://experienceleague.adobe.com/ja/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) を参照してください。
* トラブルシューティングのためにサイトに引き続きアクセスできるように、IP を除外 IP アドレスリストに追加してください。 手順については、『Commerce インストールガイド』の [ 除外 IP アドレスのリストの管理 ](https://experienceleague.adobe.com/ja/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) を参照してください。

**<u>やめて！</u>**

* 追加のマーケティングキャンペーンを開始すると、サイトに追加のページビューが表示される場合があります。
* インデクサーや追加の Cron を実行すると、CPUやディスクにさらに負荷がかかる場合があります。
* 主要な管理タスク（データの読み込み/書き出し、メディアのフラッシュ、多数の割り当てられた商品を含むカテゴリの保存、一括更新など、Commerce管理者での主要なアクション）を実行します。
* キャッシュをクリアします。

## 解決策

原因の特定とトラブルシューティングを行うには、次の手順に従います。

1. [one.newrelic.com](https://login.newrelic.com/login)/**インフラストラクチャ**/**サードパーティのサービス** ページに移動して、[!DNL Redis] 使用メモリが増加しているか減少しているかを確認し、[!DNL Redis] のダッシュボードを選択します。 安定しているか増加している場合は、[ サポートチケットを送信 ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) して、クラスターをアップサイズするか、`maxmemory` 限を次のレベルに上げます。
1. [!DNL Redis] メモリ消費が増加した原因を特定できない場合は、最近の傾向を確認して、最近のコードのデプロイメントまたは設定の変更に関する問題（新しい顧客グループやカタログの大幅な変更など）を特定します。 コードのデプロイメントまたは変更における相関関係について、過去 7 日間のアクティビティを確認することをお勧めします。
1. サードパーティの拡張機能の動作が正しくないことを確認します。
   * 最近インストールしたサードパーティの拡張機能と、問題が発生した時刻との相関関係を確認します。
   * Adobe Commerceのキャッシュに影響を与え、キャッシュが急速に大きくなる可能性がある拡張機能を確認します。 例えば、カスタムレイアウトブロック、キャッシュ機能の上書き、キャッシュへの大量データの保存などです。
1. 拡張機能の動作に誤りがある証拠がない場合は、[ クラウドインフラストラクチャ上のAdobe Commerceの問題を修正する  [!DNL Redis]  ための最新のパッチをインストールする ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues) を参照してください。 上記の手順で問題の原因を特定またはトラブルシューティングできない場合は、L2 キャッシュを有効にして、アプリと [!DNL Redis] の間のネットワークトラフィックを減らすことを検討してください。 L2 キャッシュの概要については、『Commerce設定ガイド』の「Adobe Commerce アプリケーションの [L2 キャッシュ ](https://experienceleague.adobe.com/ja/docs/commerce-operations/configuration-guide/cache/level-two-cache)」を参照してください。 クラウドインフラストラクチャの L2 キャッシュを有効にするには、次の操作を試します。
   * 2002.1.2 バージョン未満の場合は、ECE ツールをアップグレードします。
   * [REDIS\_BACKEND 変数を使用 ](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend) を使用し、ファイルを更新して、L2 キャッシュ `.magento.env.yaml` 設定します。

   ```yaml
   stage:
      deploy:
          REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
