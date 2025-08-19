---
title: ACSD-62146：選択した請求先住所がチェックアウトの支払いページに表示されない
description: 住所の検索が有効になっており、「Number of Customer Addresses Limit」が 1 に設定されている場合、選択した請求先住所がチェックアウトの支払いページに表示されなくなるAdobe Commerceの問題を修正するために、ACSD-62146 パッチを適用してください。
feature: Customers, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: 3de3de80383372d0e3bec5485fd65b9d70fe8860
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# ACSD-62146：選択した請求先住所がチェックアウトの支払いページに表示されない

ACSD-62146 パッチは、アドレス検索が有効で、[!UICONTROL Number of Customer Addresses Limit] が 1 に設定されている場合、選択した請求先住所がチェックアウトの支払いページに表示されなくなる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 がインストールされている場合に使用できます。 パッチ ID は ACSD-62146 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

住所検索が有効で、**[!UICONTROL Number of Customer Addresses Limit]** が 1 に設定されている場合、選択した請求先住所がチェックアウト支払いページに表示されなくなります。

<u> 再現手順 </u>:

1. アドレス検索を有効にするには、**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Checkout]**/**[!UICONTROL Checkout Options]** に移動します。
1. **[!UICONTROL Number of Customer Addresses Limit]** を 1 に設定します。
1. 顧客を作成し、2 つの異なるアドレスを追加します。
1. 商品を買い物かごに追加し、チェックアウトに進みます。
1. **[!UICONTROL Change Address]** をクリックし、ポップアップを使用してアドレスを変更します。
1. 住所 2 を配送先住所として選択します。
1. 「**[!UICONTROL Next]**」をクリックして、支払い手順に進みます。
1. 請求先と配送先住所が同じであることを確認します。
1. 支払いを行わずにページを更新します。

<u> 期待される結果 </u>:

請求先住所と出荷先住所が同じ場合は、出荷先住所が表示されます。

<u> 実際の結果 </u>:

デフォルトの請求先住所と選択した出荷先住所が表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
