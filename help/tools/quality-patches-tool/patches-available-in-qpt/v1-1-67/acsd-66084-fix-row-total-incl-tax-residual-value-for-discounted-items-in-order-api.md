---
title: 'ACSD-66084: ''row_total_incl_tax''は、注文 API で完全に割引された項目に対して 0.00 ではなく、ゼロに近い値を返します'
description: ACSD-66084 パッチを適用すると、注文 API 応答で「row_total_incl_tax」が 0.00 ではなく、ゼロに近い残差値として返されるAdobe Commerceの問題が修正されます。
feature: Orders, REST, Taxes, Payments, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 421c6fe6-b6b1-4f33-acb6-fbd4306bcc4c
source-git-commit: 951738a4c671ed6fcc47b2a928d2110c78763d26
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# ACSD-66084:`row_total_incl_tax` は、注文 API で完全に割引された項目に対して 0.00 ではなく、ゼロに近い値を返します

ACSD-66084 パッチは、完全に割引された項目に対して 0.00 ではなく、`row_total_incl_tax` が注文 API 応答のゼロに近い残差値として返される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 がインストールされている場合に使用できます。 パッチ ID は ACSD-66084 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`row_total_incl_tax` は、完全に割引された項目に対して 0.00 ではなく、ゼロに近い残差値として注文 API 応答で返されます。

<u> 再現手順 </u>:

1. 価格と特別な価格で製品を作成してください。 **[!UICONTROL Catalog]**/**[!UICONTROL Products]** に移動し、**[!UICONTROL Add Product]**/をクリックして、**[!UICONTROL Price]** を$25 に設定し、**[!UICONTROL Special Price]** の下で **[!UICONTROL Advanced Pricing]** を$16.99 に設定します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Taxes]**/**[!UICONTROL Tax Zones and Rates]** に移動して、20% の料金を追加します。 次に、**[!UICONTROL Tax Rules]** に移動してルールを作成し、割り当てます
   製品税区分として **[!UICONTROL Taxable Goods]** 定します。
1. 100% 割引とクーポンを使用して販売ルールを作成します。 **[!UICONTROL Marketing]**/**[!UICONTROL Promotions]**/**[!UICONTROL Cart Price Rules]** に移動し、100% 割引のルールを追加してから、**[!UICONTROL Specific Coupon]** を使用してコードを入力します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Tax]** に移動し、税金設定を構成します。
1. 送料無料を有効にします。 **[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Delivery Methods]**/**[!UICONTROL Free Shipping]** に移動します。 **[!UICONTROL Enabled]** を **[!UICONTROL Yes]** に設定し、設定を調整します。
1. 製品ページに移動し、「**[!UICONTROL Add to Cart]**」を選択します。 買い物かごに移動し、クーポンコードを適用します。
1. 該当する税ゾーンを注文します。
1. REST API を使用して管理トークン（API）を生成します。
1. REST API を使用して注文の詳細を取得します。
1. 応答の `row_total_incl_tax` を確認します。

<u> 期待される結果 </u>:

項目 `row_total_incl_tax` 完全に割引されている場合は、`0.00` のように、通貨に適した値を返す必要があります。

<u> 実際の結果 </u>:

`row_total_incl_tax` は `3.5527136788005e-15` のようなゼロに近い浮動小数点値を返します。これは通貨表示には適していません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
