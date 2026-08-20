---
title: 'ACSD-66404:  [!DNL Galera Cluster]  トランザクションサイズの制限により、Cron ジョブで変更ログテーブルをクリアできない'
description: ACSD-66404 パッチを適用して、cron ジョブで変更ログテーブルがクリアされず、これらのテーブル内の大量のデータが発生した場合に [!DNL Galera Cluster] 問題が発生するAdobe Commerceの問題を修正します。
feature: System
role: Admin, Developer
type: Troubleshooting
exl-id: d7ad3b11-aee6-4a26-8892-369fbfe6932e
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '380'
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
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

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
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」ガイド

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール
