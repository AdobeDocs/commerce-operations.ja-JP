---
title: 'ACSD-52929: デフォルトのソース項目の再インデックスを実行する冗長リクエスト'
description: インベントリインデクサーが非同期モードで設定されている場合、デフォルトのソース項目を再インデックスする冗長なリクエストが発生するAdobe Commerceの問題を修正するために、ACSD-52929 パッチを適用してください。
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 904aed0e-a6cd-4a0f-949d-bb32fcd77356
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-52929: デフォルトのソース項目の再インデックスを実行する冗長リクエスト

ACSD-52929 パッチは、インベントリインデクサーが非同期モードで設定されている場合、デフォルトのソース項目を再インデックス化するリクエストの冗長性がある問題を修正しました。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.38 がインストールされている場合に使用できます。 パッチ ID は ACSD-52929 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

在庫インデクサーが非同期モードで設定されている場合、デフォルトのソース項目のインデックスを再作成するリクエストは冗長になります。

<u> 再現手順 </u>:

1. [!DNL RabbitMQ] の設定
1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Catalog]**/**[!UICONTROL Inventory]**/**[!UICONTROL Inventory Indexer Setting]** に移動して、**[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]** を設定し、非同期のインデックス再作成戦略を有効にします。
1. カスタム在庫ソースを作成します。
1. [!DNL RabbitMQ] ダッシュボードにログインし、「キュー」タブに移動します。
1. キュー `inventory.indexer.sourceItem` チェックし、メッセージがないことを確認します。
1. バックエンドから単純な製品を開き、カスタムソースに *[!UICONTROL stock only]* を追加して、製品を保存します。
1. `inventory.indexer.sourceItem` ダッシュボードで [!DNL RabbitMQ] キューを読み込み、メッセージを確認します。

<u> 期待される結果 </u>:

カスタムソースのキューにはメッセージが 1 つしかありません。

<u> 実際の結果 </u>:

キューには 2 つのメッセージが表示されます。1 つはデフォルトソース用で、もう 1 つはカスタムソース用です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
