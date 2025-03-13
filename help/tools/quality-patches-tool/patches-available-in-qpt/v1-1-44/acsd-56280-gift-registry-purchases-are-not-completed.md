---
title: 'ACSD-56280: ギフト レジストリの購入が完了していません'
description: ACSD-56280 パッチを適用すると、ギフトレジストリの購入が完了しないAdobe Commerceの問題を修正できます
feature: Checkout
role: Admin
exl-id: a79f789f-999f-4d11-b7ee-2c065b681efb
source-git-commit: ab02be3396e68044e9356f89fba6b55aa880056f
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-56280: ギフト レジストリの購入が完了していません

>[!NOTE]
>
>このパッチは [ACSD-63283](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/acsd-63283-resolving-gift-registry-email-and-order-placement-issues-in-adobe-commerce.md) に置き換えられます。

ACSD-56280 パッチは、ギフトレジストリの購入が完了しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 がインストールされている場合に使用できます。 パッチ ID は ACSD-56280 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ギフト レジストリの購入が完了していません。

<u> 再現手順 </u>:

1. 顧客としてログインし、**[!UICONTROL product]** をギフト レジストリに追加します。
1. ギフト レジストリ リンクを共有します。
1. 別のブラウザー/匿名ウィンドウで、ギフトレジストリリンクを開きます。
1. 数量を追加し、品目を買い物かごに追加します。
1. **[!UICONTROL Checkout Page]** に移動し、「**[!UICONTROL shipping method]**」を選択します（登録者が提供する発送先住所は既に選択されています）。
1. 支払方法を選択します。
1. 「注文する」ボタンをクリックします。

<u> 期待される結果 </u>:

注文する必要があります。

<u> 実際の結果 </u>:

注文が行われず、表示されるエラーは `Call to a member function getUpdatedQty() on null` です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
