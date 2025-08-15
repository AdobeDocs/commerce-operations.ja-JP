---
title: ACSD-48362：新しい配送先住所の代わりにデフォルトの配送先住所が使用されます。
description: ACSD-48362 パッチを適用すると、交渉可能な見積もりを使用して注文を行う際に、新しい配送先住所の代わりにデフォルトの配送先住所が使用されるAdobe Commerceの問題を修正できます。
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
exl-id: 6f0717a6-1e29-4059-9640-5b92586c36e4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# ACSD-48362：新しい配送先住所の代わりにデフォルトの配送先住所が使用される

ACSD-48362 パッチは、交渉可能な見積もりを使用して注文を行う際に、新しく追加されたアドレスの代わりにデフォルトの配送先住所が使用される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 がインストールされている場合に使用できます。 パッチ ID は ACSD-48362 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

交渉が可能な見積書を使用して注文を行う場合、新しく追加された配送先住所の代わりにデフォルトの配送先住所が使用されます。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL B2B features]**/**[!UICONTROL Enable company]**/**[!UICONTROL Enable B2B quote]** に移動して、B2B 見積もりを有効にします。
1. 会社のユーザーとしてログインします。
1. 商品を買い物かごに追加します。
1. 買い物かごページに移動し、見積もりを依頼します。
1. お客様の **[!UICONTROL My Quotes]** ページに移動し、作成した見積もりを選択します。
1. お客様の見積もりページの「**[!UICONTROL Shipping Information]**」セクションに移動します。
   * 「**[!UICONTROL Add New Address]**」をクリックし、フォームに入力して、アドレスを保存します（**[!UICONTROL Use as my default billing address]** または **[!UICONTROL Use as my default shipping address]** は選択しないでください）。
1. お客様の見積もりページで **[!UICONTROL Send for Review]** をクリックします。
1. Adobe Commerce管理者に管理者ユーザーとして移動し、作成した見積もりを開いて「**[!UICONTROL Send]**」をクリックします。
1. 次に、お客様の見積もりページに移動し、ページを更新して、「**[!UICONTROL Proceed to Checkout]**」をクリックします。
1. チェックアウトページでは、新しい配送先住所が選択されている場合でも、データにはデフォルトの配送先住所が表示されます。
1. 「**[!UICONTROL Continue]**」をクリックして、注文を行います。

<u> 期待される結果 </u>:

注文は、チェックアウトページでデフォルトの配送先住所を再選択せずに、新しい住所を使用する必要があります。

<u> 実際の結果 </u>:

注文はデフォルトの配送先住所で行われます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。 

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
