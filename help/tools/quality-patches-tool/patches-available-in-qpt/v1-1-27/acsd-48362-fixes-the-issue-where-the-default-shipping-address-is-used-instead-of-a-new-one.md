---
title: ACSD-48362：新しい住所の代わりに、デフォルトの配送先住所が使用されます。
description: ACSD-48362 パッチを適用して、交渉可能な見積もりを使用して注文を行う際に、デフォルトの配送先住所ではなく新しい配送先住所が使用されるAdobe Commerceの問題を修正します。
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
exl-id: 6f0717a6-1e29-4059-9640-5b92586c36e4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%

---

# ACSD-48362：新しい住所の代わりにデフォルトの配送先住所が使用される

ACSD-48362 パッチは、交渉可能な見積もりを使用して注文を行う際に、新しく追加された住所の代わりにデフォルトの配送先住所が使用される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27がインストールされている場合に利用できます。 パッチ IDはACSD-48362です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

交渉可能な見積を使用して注文を行う場合、新しく追加された配送先住所の代わりに、デフォルトの配送先住所が使用されます。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**&#x200B;に移動して、B2B見積もりを有効にします。
1. 会社ユーザーとしてログインします。
1. 商品をカートに追加する。
1. カートページに移動し、見積もりを依頼します。
1. お客様の&#x200B;**[!UICONTROL My Quotes]** ページに移動し、作成したばかりの見積もりを選択します。
1. お客様の見積もりページの&#x200B;**[!UICONTROL Shipping Information]** セクションに移動します。
   * **[!UICONTROL Add New Address]**&#x200B;をクリックしてフォームに入力し、アドレスを保存します（**[!UICONTROL Use as my default billing address]**&#x200B;または&#x200B;**[!UICONTROL Use as my default shipping address]**&#x200B;は選択しないでください）。
1. お客様の見積もりページで「**[!UICONTROL Send for Review]**」をクリックします。
1. Adobe Commerce Admin as an admin userに移動し、作成したばかりの見積もりを開いて、**[!UICONTROL Send]**&#x200B;をクリックします。
1. お客様の見積もりページに移動し、ページを更新して、**[!UICONTROL Proceed to Checkout]**&#x200B;をクリックします。
1. チェックアウトページでは、新しい配送先住所が選択されている場合でも、データにデフォルトの配送先住所が表示されます。
1. **[!UICONTROL Continue]**&#x200B;をクリックして注文します。

<u>期待される結果</u>:

注文は、チェックアウトページでデフォルトの配送先住所を再選択することなく、新しい住所を使用する必要があります。

<u>実際の結果</u>:

注文はデフォルトの配送先住所で行われます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。 

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
