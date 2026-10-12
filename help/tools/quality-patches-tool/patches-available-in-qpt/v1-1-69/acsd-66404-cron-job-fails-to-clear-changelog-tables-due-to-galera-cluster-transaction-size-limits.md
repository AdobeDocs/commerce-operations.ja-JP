---
title: 'ACSD-66404: [!DNL Galera Cluster]個のトランザクションサイズの制限により、Cron ジョブで変更ログテーブルをクリアできない'
description: ACSD-66404 パッチを適用して、cron ジョブで変更ログテーブルがクリアされず、これらのテーブル内の大量のデータが発生した場合に[!DNL Galera Cluster]件の問題が発生するAdobe Commerceの問題を修正します。
feature: System
role: Admin, Developer
type: Troubleshooting
exl-id: d7ad3b11-aee6-4a26-8892-369fbfe6932e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%
---
# ACSD-66404: [!DNL Galera Cluster]個のトランザクションサイズの制限により、Cron ジョブで変更ログテーブルをクリアできない

ACSD-66404 パッチは、cron ジョブが変更ログテーブルをクリアできない問題を修正し、大量のデータを処理する際に[!DNL Galera Cluster]の問題を引き起こします。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACSD-66404です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p6、2.4.7-p6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

Cron ジョブが変更ログ テーブルをクリアせず、これらのテーブル内の大量のデータが存在する場合、[!DNL Galera Cluster]件の問題が発生します。

<u>複製する手順</u>:

1. パフォーマンスプロファイルを使用して多くの商品を生み出す。
1. システム内のすべての製品に対して一括更新を実行します。そのため、`inventory_cl` DB テーブルには多くのエントリがあります。
1. `indexer_clean_all_changelogs` cron ジョブを実行します。

<u>期待される結果</u>:

`indexer_clean_all_changelogs` cron ジョブは、[!DNL Galera Cluster]の問題を引き起こさずに、複数の削除クエリで大きな変更ログ （10 GB以上）で変更ログのクリーンアップを実行できます。

<u>実際の結果</u>:

`indexer_clean_all_changelogs` cron ジョブは、1つの削除クエリで大きな変更ログ （10 GB以上）に対して変更ログのクリーンアップを実行し、[!DNL Galera Cluster]件の問題が発生しました。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」ガイド

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール
