---
title: 「ACSD-49737：カードの支払いに失敗した後、クーポンが誤って使用済みとしてマークされる」
description: ACSD-49737 パッチを適用すると、カード支払いが失敗した後にクーポンが誤って使用済みとしてマークされるAdobe Commerceの問題を修正できます。
feature: Orders, Payments
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49737：カードの支払いに失敗した後、クーポンが誤って *使用済み* とマークされる

ACSD-49737 パッチは、カード支払いが失敗した後、クーポンが誤って *使用中* とマークされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 がインストールされている場合に使用できます。 パッチ ID は ACSD-49737 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

カードの支払いに失敗した後、クーポンが誤って *使用中* とマークされます。

<u> 前提条件 </u>:

1. **[!UICONTROL Braintree sandbox payment]** メソッドを設定します。
1. [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en) consumer が設定され、実行されていることを確認します。

<u> 再現手順 </u>:

1. 自動生成されたクーポンコードを使用して **[!UICONTROL Cart Price Rule]** ールを作成します。
1. 顧客としてログインします。
1. 商品を買い物かごに追加します。
1. 自動生成されたクーポンコードを適用します。
1. 失敗した支払いで注文してみてください。
1. 「**[!UICONTROL Manage Coupon Codes]**」タブの **[!UICONTROL Cart Price Rule]** でクーポンの使用状況を確認します。

<u> 期待される結果 </u>:

支払いが失敗した場合、クーポンは *使用済み* としてフラグ付けしないでください。

<u> 実際の結果 </u>:

* クーポンコードに次のように表示 – 使用済み：*はい*、使用回数：*1*
* クーポンコードは 1 回限りの使用にのみ有効です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## パッチのインストール後に必要な追加手順

（この節はオプションです。問題を修正するためにパッチを適用した後に必要な手順が含まれる場合があります）。 

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
