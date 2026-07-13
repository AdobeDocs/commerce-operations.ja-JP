---
title: Adobe Commerceの管理アラート：ディスクの警告アラート
description: この記事では、 [!DNL New Relic]でAdobe Commerceに関する警告ディスクアラートを受け取った場合のトラブルシューティング手順について説明します。 この問題を解決するには早急な行動が必要だ。
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 90ea4384-97aa-499d-93c1-b40c3a4eed42
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---

# Adobe Commerceの管理アラート：ディスクの警告アラート

この記事では、[!DNL New Relic]でAdobe Commerceに関する警告ディスクアラートを受け取った場合のトラブルシューティング手順について説明します。 この問題を解決するには早急な行動が必要だ。 選択したアラート通知チャネルに応じて、アラートは次のようになります。

ストレージ使用量のしきい値を超えたことを示す![&#x200B; ディスク容量警告アラート通知](../../assets/managed-alerts/disk-warning-magento-managed.png){width="500"}

## 影響を受ける製品とバージョン

* Adobe Commerceオンクラウドインフラストラクチャ、プロプランアーキテクチャ。

## イシュー

Adobe Commerce[&#128279;](managed-alerts-for-magento-commerce.md)の管理対象アラートにサインアップし、1つ以上のアラートしきい値を超えた場合、[!DNL New Relic]にアラートが届きます。 これらのアラートは、サポートとエンジニアリングからのインサイトを使用して、お客様に標準セットを提供するためにAdobeによって開発されました。

<u> **実行！** </u>

* このアラートがクリアされるまでスケジュールされたデプロイメントをすべて中止します。
* サイトが完全に応答しない、または応答しなくなった場合は、すぐにメンテナンスモードにします。 手順については、『Commerce インストールガイド』の「[&#x200B; メンテナンスモードを有効または無効にする](https://experienceleague.adobe.com/ja/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)」を参照してください。 トラブルシューティングのためにサイトにアクセスできるように、IPを免除IP アドレスリストに追加してください。 手順については、Commerce インストールガイドの「[除外IP アドレスのリストを管理する](https://experienceleague.adobe.com/ja/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)」を参照してください。

<u> **実行しない！** </u>

* 追加のページビューをサイトに呼び込む可能性のある、追加のマーケティング施策を開始します。
* CPUまたはディスクに負荷がかかる可能性があるインデクサーまたは別のクローンを実行します。
* 主要な管理作業（Commerce管理者、データの読み込み/書き出しなど）を行います。
* キャッシュをクリアします。 アラートの原因を調査して解決する前に「実行しない」アクションのいずれかを実行すると、サイトが応答しなくなる可能性があります（サイトの停止がまだ発生していない場合）。

## Solution

以下の手順に従って、原因を特定し、トラブルシューティングします。

1. [!DNL New Relic]で、最も使用頻度の高いディスクを確認します。 手順については、[[!DNL New Relic]  インフラストラクチャ監視ホストページの&#x200B;**[!UICONTROL Storage]** タブを参照してください：[!UICONTROL Storage] タブ &#x200B;](https://docs.newrelic.com/docs/infrastructure/infrastructure-data/infrastructure-ui-pages/infra-hosts-ui-page/#storage):
   * [!DNL New Relic]でディスク使用量の増加が遅い場合は、次のオプションを試してください。
      * スペース配分を調整してディスク容量を最適化する。 手順については、Commerce on Cloud ガイドの「[&#x200B; ディスク領域を管理](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space)」を参照してください。 また、追加のディスク容量をリクエストする必要がある場合もあります（Adobeのアカウントチームにお問い合わせください）。
      * MySQL用のディスク領域をクリアします。 手順については、[MySQLのディスク容量が少ない](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud)を参照してください。
      * [!DNL New Relic]でディスク使用量が急速に増加している場合は、ディレクトリ内でファイルが非常に急速に増加している問題があることを示している可能性があります。 次のチェックを実行します。
         1. CLI/ターミナルで次のコマンドを実行して、全体的なディスク容量を確認し、問題を特定します：`df -h`
         1. 予期せず大きくなり、ディスク使用量が増加するディレクトリを特定したら、影響を受けるファイルシステムを確認する必要があります。 次の例は、ファイルディレクトリ `pub/media/`を確認する方法を示しています。 これは、Adobe Commerceがログとビッグメディアファイルを保存するために使用するディレクトリです。 ただし、予期しないディスク使用量を示すディレクトリに対しては、このコマンドを実行する必要があります：`du -sch ~/pub/media/*`。

ターミナルからの出力で、これらのディレクトリのいずれかにファイルが表示され、ディスク使用量が急速に増加し、ファイルの内容が必要でないことがわかっている場合は、ファイルの削除を検討してください。 この操作に慣れていない場合は、[Adobe Commerce サポートチケットを送信](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case)してください。
