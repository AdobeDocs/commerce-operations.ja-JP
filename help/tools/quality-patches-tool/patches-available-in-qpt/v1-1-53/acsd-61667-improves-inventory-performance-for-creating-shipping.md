---
title: ACSD-61667：配送作成のための在庫パフォーマンスを向上
description: ACSD-60584 パッチを適用して、店舗内ピックアップを伴う多くのソースの場合に出荷を作成するための在庫パフォーマンスを向上させます。
feature: Customers, Shipping/Delivery
role: Admin, Developer
exl-id: 47682daf-9117-45f1-ab09-a66c13132ff3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-61667：配送作成のための在庫パフォーマンスを向上

ACSD-61667 パッチは、[[!DNL Inventory Management for Commerce]](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) （旧称 MSI）ピックアップストアが複数のソースで有効になっている場合に、マーチャントが注文を発送できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 がインストールされている場合に使用できます。 パッチ ID は ACSD-61667 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

複数のソースで MSI ピックアップ ストアが有効になっている場合、注文を出荷できません。 このパッチにより、在庫パフォーマンスが向上し、店舗での受け取りで多くのソースが発生した場合の出荷が可能になります。

<u> 前提条件：</u>:

Adobe Commerce インベントリモジュールがインストールされ、有効になっています。

<u> 再現手順 </u>:

1. *10* を超えるソースを作成し、ピックアップ場所を有効にします。
1. ピックアップ ストアは、**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** で有効になっています。
1. 大量の集荷注文を作成します。
1. **[!UICONTROL Admin login]** に移動し、**[!UICONTROL Sales]**/**[!UICONTROL Orders]**/**[!UICONTROL View]** を選択します。
1. 保留中の注文をフィルタリングして確認します。
1. 「**[!UICONTROL Ship]**」をクリックします。

<u> 期待される結果 </u>:

出荷ページが期待どおりに読み込まれます。

<u> 実際の結果 </u>:

*503 最大実行タイムアウト* エラーが発生します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
