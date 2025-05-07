---
title: ACSD-63520：画像アップロード設定を使用してアップロードされた画像が、設定されたサイズ制限を超えています
description: 管理パネルの画像アップロード設定を使用してアップロードされた画像が、設定された最大アップロードサイズの制限に従わないAdobe Commerceの問題を修正するために、ACSD-63520 パッチを適用してください。
feature: Media, Products
role: Admin, Developer
source-git-commit: 987d335f03d552763f75adb73890787abf235e66
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---


# ACSD-63520:[!UICONTROL Image Upload Configuration] 経由でアップロードされた画像が、設定されたサイズ制限を超えています

ACSD-63520 パッチは、[!UICONTROL Images Upload Configuration] を介してアップロードされた画像が、設定された最大アップロードサイズの制限に従わない問題を解決します。 この問題に対処するには、[!UICONTROL Admin] ントロールパネルで [!UICONTROL Images Upload Configuration] の設定を行います。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 がインストールされている場合に使用できます。 パッチ ID は ACSD-63520 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.7

**Adobe Commerce バージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがお使いの [!DNL Adobe Commerce] バージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: パッチを検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!UICONTROL Admin] パネルの [!UICONTROL Images Upload Configuration] を使用してアップロードされた画像は、最大アップロードサイズの制限に従いません。

<u> 再現手順 </u>:

1. パネルにログイ **[!UICONTROL Admin]** します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Advanced]**/**[!UICONTROL System]**/**[!UICONTROL Images Upload Configuration]** に移動し、以下を設定します。
   * 画質：100
   * フロントエンドのサイズ変更を有効にする：はい
   * 幅の最大値：800
   * 最大の高さ：600
1. **[!UICONTROL Media Gallery Image Optimization]** を展開して設定します。
   * 画像の最適化を有効にする：はい
   * 幅の最大値：1000
   * 最大の高さ：1000
1. **[!UICONTROL Catalog]**/**[!UICONTROL Products]**/**[!UICONTROL Add Configurable Product]** に移動します。
   1. **[!UICONTROL Product Name]**、**[!UICONTROL SKU]**、**[!UICONTROL Price]** を追加します。
   1. 「**[!UICONTROL Create Configurations]**」をクリックし、「**[!UICONTROL Attributes]**」を選択して「**[!UICONTROL Next]**」をクリックします。
   1. サイズ（S、M、L、XL）を選択し、[**[!UICONTROL Next]**] をクリックします。
   1. 「**[!UICONTROL Images]**」で、「**[!UICONTROL Apply single set of images to all SKUs]**」を選択します。
   1. 画像（1024 x 1024 以上）をアップロードし、「**[!UICONTROL Next]**」をクリックします。
   1. 「**[!UICONTROL Generate Product]**」をクリックします。
1. 「**[!UICONTROL Save]**」をクリックします。

<u> 期待される結果 </u>:

画像は、設定されたアップロードサイズおよびサイズ変更制限に従う必要があります。

<u> 実際の結果 </u>:

画像のサイズは変更されず、設定されたアップロードサイズ制限を超えることもありません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
