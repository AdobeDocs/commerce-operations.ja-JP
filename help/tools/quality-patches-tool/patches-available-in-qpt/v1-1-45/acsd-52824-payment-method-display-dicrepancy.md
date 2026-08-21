---
title: ACSD-52824：企業のお客様に対して無効な支払い方法が表示される
description: 会社の設定で無効になっていても、 [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] 支払い方法が会社のお客様に表示されるAdobe Commerceの問題を修正するには、ACSD-52824 パッチを適用します。
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 39d67de6-1796-4067-ae7a-ef17fcf794e5
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# ACSD-52824：企業のお客様に対して無効な支払い方法が表示される

ACSD-52824 パッチは、会社の設定で無効になっているにもかかわらず、[!DNL PayPal Express]、[!DNL Google Pay]および[!DNL Apple Pay]の支払い方法が会社のお客様に表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.45がインストールされている場合に利用できます。 パッチ IDはACSD-52824です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

会社のお客様向けに、無効な支払い方法が表示されます。

<u>複製する手順</u>:

1. [!DNL PayPal Express Checkout]を設定して有効にします。 **[!UICONTROL Basic Settings]**/選択&#x200B;**[!DNL PayPal Express Checkout]**&#x200B;に移動し、**[!UICONTROL Display on Shopping Cart]**&#x200B;のオプションを&#x200B;*はい*&#x200B;に設定します。
1. [!DNL Braintree]を設定し、[!DNL Apple Pay]と[!DNL Google Pay]から[!DNL Braintree]を有効にします。
1. **[!UICONTROL Customers]** > **[!UICONTROL Companies]**&#x200B;に移動して、新しい会社を作成します。
1. **[!UICONTROL Advanced Settings]**&#x200B;をクリックし、**[!UICONTROL Applicable Payment Methods]**&#x200B;を見つけて、**[!UICONTROL Selected Payment Methods]**&#x200B;を選択します。
1. **[!UICONTROL Selected Payment Methods]**&#x200B;で、有効で、*[!DNL PayPal Express Checkout]*、*[!DNL Apple Pay]*、または&#x200B;*[!DNL Google Pay]*&#x200B;に関連付けられていない支払い方法を選択します。 例えば、**[!UICONTROL Check/Money Order]**&#x200B;を選択します。
1. 適切な支払い方法を選択したら、新しい顧客を作成し、作成した会社に関連付けます。
1. 会社に関連付けられている顧客アカウントでログインし、商品をカートに追加します。
1. チェックアウトプロセスでは、ミニカート、ショッピングカート、支払い手順に注意を払う必要があります。

<u>期待される結果</u>:

[!DNL PayPal]と[!DNL Braintree]の支払いオプションは、ミニカートとショッピングカートには表示されません。

<u>実際の結果</u>:

[!DNL PayPal]と[!DNL Braintree]の支払いオプションは、ミニカートとショッピングカートに引き続き表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
