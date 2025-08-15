---
title: ACSD-50234：を使用して注文した場合に、確認メールに記載されている顧客名が正しくない  [!DNL PayPal]
description: ACSD-50234 パッチを適用すると、 [!DNL PayPal] を使用して注文した場合に、確認メールにお客様の名前が正しく表示されないAdobe Commerceの問題を修正できます。
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 9a8a7cef-0166-4b4b-96a0-87fd4f1a0ef3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-50234:[!DNL PayPal] を使用して注文した場合に、確認メールに記載されている顧客名が正しくない

ACSD-50234 パッチは、[!DNL PayPal] を使用して注文した場合に、確認メールに顧客名が正しく表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 がインストールされている場合に使用できます。 パッチ ID は ACSD-50234 です。 この問題はAdobe Commerce 2.4.5 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.4-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL PayPal] を使用して注文した場合の確認メールに、間違った顧客名が表示される。

<u> 再現手順 </u>

1. **[!UICONTROL PayPal Express Checkout]** を有効にします。
1. ゲストとしてフロントエンドに移動します。
1. 商品を買い物かごに追加します。
1. **[!UICONTROL PayPal Express Checkout]** を支払い方法として使用してチェックアウトします。
1. 注文確認メールを確認します。

<u> 期待される結果 </u>

注文確認メール、請求書メール、およびすべての出荷関連メールは、顧客名を宛先としています。

<u> 実績 </u>

注文確認メール、請求書メールおよびすべての出荷関連メールは、*ゲスト* 宛てです。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
