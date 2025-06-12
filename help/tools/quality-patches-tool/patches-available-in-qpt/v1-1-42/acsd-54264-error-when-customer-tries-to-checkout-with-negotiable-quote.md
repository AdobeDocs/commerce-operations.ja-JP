---
title: ACSD-54264：お客様が交渉可能な見積もりでチェックアウトしようとするとエラーが発生する
description: Adobe Commerce ACSD-54264 パッチを適用すると、「リクエストされた属性を更新できません。 Row ID:store_id」は、顧客が別のストアビューから交渉可能な見積もりでチェックアウトしようとすると表示されます。
feature: B2B, Checkout
role: Admin, Developer
exl-id: b1696228-b2ed-44eb-9e75-bf25ccf2f1cd
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-54264：お客様が交渉可能な見積もりでチェックアウトしようとすると、エラーが表示される

ACSD-54264 パッチでは、エラーメッセージ *要求された属性を更新できません。 行 ID:store_id* は、顧客が別のストアビューから交渉可能な見積もりでチェックアウトしようとすると表示されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42 がインストールされている場合に使用できます。 パッチ ID は ACSD-54264 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

エラーメッセージ *リクエストされた属性を更新できません。 行 ID:store_id* は、顧客が別のストアビューから交渉可能な見積もりでチェックアウトしようとすると表示されます。

<u> 前提条件 </u>:

Adobe Commerce B2B モジュールがインストールされ、有効になっています。

<u> 再現手順 </u>:

1. デフォルトの web サイト用に、追加のストア表示を作成します。
1. 設定で *[!UICONTROL B2B Quote]* を有効にします。
1. ストア表示のいずれかで会社の顧客としてログインします。
1. *[!UICONTROL Shopping Cart]* に製品を追加します。
1. 見積をレビュー用に発行します。
1. 管理者ユーザーとして、**[!UICONTROL Sales]** / **[!UICONTROL Quotes]** に移動し、承認済みの見積もりを送信します。
1. 会社の顧客として、ストア表示を別のストア表示に変更します。
1. チェックアウトしてみてください。

<u> 期待される結果 </u>:

顧客はこの見積もりで注文を行います。

<u> 実際の結果 </u>:

* エラーは、配送情報の保存中に発生します。

  `You cannot update the request attribute. Row ID: store_id =#`

* 次のエラーがログに記録されます。

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
