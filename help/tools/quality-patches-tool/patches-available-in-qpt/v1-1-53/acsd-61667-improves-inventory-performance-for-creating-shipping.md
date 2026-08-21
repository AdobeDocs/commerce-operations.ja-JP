---
title: ACSD-61667：配送を作成するための在庫パフォーマンスを向上させる
description: ACSD-60584 パッチを適用して、実店舗での受け取りに関する多くのソースの場合に出荷を作成するための在庫パフォーマンスを向上させます。
feature: Customers, Shipping/Delivery
role: Admin, Developer
exl-id: 47682daf-9117-45f1-ab09-a66c13132ff3
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-61667：配送を作成するための在庫パフォーマンスを向上させる

ACSD-61667 パッチは、複数のソースで[[!DNL Inventory Management for Commerce]](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) （旧MSI）受け取りストアが有効になっている場合に、加盟店が注文を配送できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53がインストールされている場合に利用できます。 パッチ IDはACSD-61667です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

複数のソースを含むMSI ピックアップストアが有効になっている場合、注文を配送できません。 このパッチは、実店舗での受け取りに多くのソースが該当する場合に出荷を作成するために、在庫のパフォーマンスを向上させます。

<u>前提条件：</u>:

Adobe Commerce Inventory モジュールがインストールされ、有効になります。

<u>複製する手順</u>:

1. *10*&#x200B;以上のソースを作成し、それらの受け取り場所を有効にします。
1. ピックアップストアは、**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**&#x200B;の下で有効になっています。
1. 大量の受け取り注文の作成。
1. **[!UICONTROL Admin login]**&#x200B;に移動し、**[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL View]**&#x200B;を選択します。
1. 保留中の注文をフィルタリングして確認します。
1. **[!UICONTROL Ship]**&#x200B;をクリックします。

<u>期待される結果</u>:

発送ページが期待どおりに読み込まれます。

<u>実際の結果</u>:

「*503 Maximum execution time out*」エラーが発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
