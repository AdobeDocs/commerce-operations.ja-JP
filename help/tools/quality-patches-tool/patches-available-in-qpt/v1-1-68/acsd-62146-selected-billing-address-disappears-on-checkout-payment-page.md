---
title: ACSD-62146：選択した請求先住所がチェックアウト支払いページに表示されない
description: ACSD-62146 パッチを適用して、アドレス検索が有効になり、お客様のアドレス数の制限が1に設定されている場合に、選択した請求先住所がチェックアウト支払いページに表示されなくなるAdobe Commerceの問題を修正します。
feature: Customers, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 2a2f1afe-8a48-4beb-b78d-a894b685717d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
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
source-wordcount: '401'
ht-degree: 0%
---
# ACSD-62146：選択した請求先住所がチェックアウト支払いページに表示されない

ACSD-62146 パッチは、アドレス検索が有効で[!UICONTROL Number of Customer Addresses Limit]が1に設定されている場合に、選択した請求先住所がチェックアウト支払いページに表示されなくなる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68がインストールされている場合に利用できます。 パッチ IDはACSD-62146です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

アドレス検索が有効で&#x200B;**[!UICONTROL Number of Customer Addresses Limit]**&#x200B;が1に設定されている場合、選択した請求先住所がチェックアウト支払いページに表示されなくなります。

<u>複製する手順</u>:

1. アドレス検索を有効にするには、**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**&#x200B;に移動します。
1. **[!UICONTROL Number of Customer Addresses Limit]**&#x200B;を1に設定します。
1. 顧客を作成し、2つの異なるアドレスを追加します。
1. 商品をカートに追加し、チェックアウトに進みます。
1. **[!UICONTROL Change Address]**&#x200B;をクリックし、ポップアップを使用してアドレスを変更します。
1. 配送先住所として「住所2」を選択します。
1. **[!UICONTROL Next]**&#x200B;をクリックして支払い手順に進みます。
1. 請求先住所と配送先住所が同じであることを確認します。
1. 支払いを行わずにページを更新します。

<u>期待される結果</u>:

請求先住所と配送先住所が同じ場合、配送先住所が表示されます。

<u>実際の結果</u>:

デフォルトの請求先住所と選択した配送先住所は表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
