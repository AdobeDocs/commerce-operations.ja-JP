---
title: 'ACSD-66084: ''row_total_incl_tax''は、注文APIで完全に割引された商品の0.00ではなく、ほぼゼロを返します'
description: ACSD-66084 パッチを適用して、注文API応答で完全に割引された商品に対して、「row_total_incl_tax」がほぼゼロの残存値として返されるAdobe Commerceの問題を修正します。
feature: Orders, REST, Taxes, Payments, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 421c6fe6-b6b1-4f33-acb6-fbd4306bcc4c
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-66084: `row_total_incl_tax`は、注文APIで完全に割引されたアイテムに対して0.00ではなく、ほぼ0を返します

ACSD-66084 パッチでは、完全に割引された項目に対して0.00ではなく、注文API応答で`row_total_incl_tax`がほぼゼロの残存値として返される問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67がインストールされている場合に利用できます。 パッチ IDはACSD-66084です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`row_total_incl_tax`は、完全に割引された商品の場合は0.00ではなく、注文API応答でほぼゼロの残存値として返されます。

<u>複製する手順</u>:

1. 価格と特別な価格で商品を作成します。 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動し、**[!UICONTROL Add Product]**&#x200B;をクリックして、**[!UICONTROL Price]**&#x200B;を$25に、**[!UICONTROL Special Price]**&#x200B;を$16.99を&#x200B;**[!UICONTROL Advanced Pricing]**&#x200B;の下に設定します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Taxes]** > **[!UICONTROL Tax Zones and Rates]**&#x200B;に移動し、20%のレートを追加します。 次に、**[!UICONTROL Tax Rules]**&#x200B;に移動し、ルールを作成して割り当てます
   製品税区分として&#x200B;**[!UICONTROL Taxable Goods]**&#x200B;を指定します。
1. 100%割引とクーポン付きのセールスルールを作成する。 **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]**&#x200B;に移動し、100%割引のルールを追加してから、**[!UICONTROL Specific Coupon]**&#x200B;を使用してコードを入力してください。
1. **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** >に移動し、税金設定を構成します。
1. 送料無料を有効にする。 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL Free Shipping]**&#x200B;に移動します。 **[!UICONTROL Enabled]**&#x200B;を&#x200B;**[!UICONTROL Yes]**&#x200B;に設定し、設定を調整します。
1. 製品ページに移動し、**[!UICONTROL Add to Cart]**&#x200B;を選択します。 ショッピングカートに移動し、クーポンコードを適用します。
1. 該当する税区間で注文します。
1. REST API経由で管理トークン（API）を生成します。
1. REST APIを使用して注文の詳細を取得します。
1. 応答の`row_total_incl_tax`を確認してください。

<u>期待される結果</u>:

項目が完全に割引された場合、`row_total_incl_tax`は`0.00`のように通貨に適した値を返す必要があります。

<u>実際の結果</u>:

`row_total_incl_tax`は、`3.5527136788005e-15`のように、ほぼゼロの浮動小数点値を返します。これは、通貨表示には適していません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
