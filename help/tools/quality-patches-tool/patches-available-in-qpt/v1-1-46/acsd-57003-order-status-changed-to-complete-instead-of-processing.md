---
title: ACSD-57003：注文のステータスが、*処理中*に変わるのではなく、*完了*に変わります
description: ACSD-57003 パッチを適用すると、注文のステータスが「処理中」ではなく「完了」に変わるAdobe Commerceの問題が修正されます。
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: a28ecc35-5c9a-4bba-b0b9-67fbe37ed8c3
source-git-commit: 128107310416e97edca3b122e97456138d04073f
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-57003：注文のステータスが *処理中* ではなく *完了* に変わる

ACSD-57003 パッチでは、注文のステータスが *処理中* ではなく *完了* に変更される問題が修正されています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.46 がインストールされている場合に使用できます。 パッチ ID は ACSD-57003 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3、2.4.6-p8、2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 ～ 2.4.6-p9、2.4.7-p2 ～ 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

注文が部分的に返金され、部分的に出荷された場合、注文のステータスは *処理中* に変わるのではなく、*完了* に変わります。

<u> 再現手順 </u>:

1. 2 つの設定可能な製品を使用して注文を作成します。
1. すべての品目の請求書を発行します。
1. 最初の品目のみを出荷します。
1. 出荷済品目のみ（*最初の品目*）のクレジット・メモを払戻または作成します。
1. 注文ステータスを確認します。

<u> 期待される結果 </u>:

注文のステータスは _処理中_ 状態にする必要があります。

<u> 実際の結果 </u>:

一部出荷済品目のクレジット・メモを作成すると、受注ステータスが *完了* に変わります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
