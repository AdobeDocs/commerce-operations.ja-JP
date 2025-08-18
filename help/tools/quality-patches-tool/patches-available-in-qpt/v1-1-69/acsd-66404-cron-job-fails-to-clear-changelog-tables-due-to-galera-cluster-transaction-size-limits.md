---
title: ACSD-66404：トランザクションサイズの制限により、Cron ジョブで変更ログテーブル  [!DNL Galera Cluster]  クリアに失敗する
description: ACSD-66404 パッチを適用すると、cron ジョブで変更ログテーブルがクリアされず、これらのテーブルに大量のデータが含まれている場合に問題が発生する  [!DNL Galera Cluster] Adobe Commerceの問題を修正できます。
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 42bd5934782ca65b891a36f61102083356c92e59
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ACSD-66404：トランザクションサイズの制限により、Cron ジョブで変更ログテーブル [!DNL Galera Cluster] クリアできない

ACSD-66404 パッチを適用すると、cron ジョブが変更ログテーブルをクリアできず、大量のデータを処理する際に [!DNL Galera Cluster] の問題が発生する問題が修正されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACSD-66404 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p6、2.4.7-p6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

Cron ジョブで変更ログテーブルがクリアされず、これらのテーブルに大量のデータがある場合に [!DNL Galera Cluster] の問題が発生する。

<u> 再現手順 </u>:

1. パフォーマンスプロファイルを使用して多くの製品を生成する。
1. システム内のすべての製品に対して一括更新を実行すると、DB テーブルに多数のエントリ `inventory_cl` 表示されます。
1. `indexer_clean_all_changelogs` cron ジョブを実行します。

<u> 期待される結果 </u>:

`indexer_clean_all_changelogs` cron ジョブは、複数の削除クエリで大きな変更ログ（10 GB 以上）に対して変更ログのクリーンアップを実行できます。[!DNL Galera Cluster] の問題は発生しません。

<u> 実際の結果 </u>:

`indexer_clean_all_changelogs` cron ジョブは、1 つの削除クエリで大きな変更ログ（10 GB 以上）に対して変更ログのクリーンアップを実行するので、[!DNL Galera Cluster] の問題が発生します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドの
* クラウドインフラストラクチャー上のAdobe Commerce:[ アップグレードとパッチ適用 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) クラウドインフラストラクチャー上のCommerce ガイド

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]：品質向上パッチを適用するためのセルフサービス ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) ツール（『ツールガイド』）
