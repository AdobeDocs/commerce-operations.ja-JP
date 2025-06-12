---
title: ACSD-49392：一部払い戻し後に注文ステータスがクローズに変更される
description: ACSD-49392 パッチを適用すると、バンドルされた製品の部分払い戻し後に注文ステータスがクローズに変わるAdobe Commerceの問題を修正できます。
feature: Orders
role: Admin
exl-id: e12cbf2d-219e-4cb5-a226-6c7ae4929549
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49392：一部払い戻し後に注文ステータスがクローズに変更される

>[!NOTE]
>
>パッチ ACSD-49392 は、バージョン 2.4.6-p7 から 2.4.6-p10 のパッチ [ACSD-57003](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-57003-order-status-changed-to-complete-instead-of-processing) に置き換えられました。

ACSD-49392 パッチは、バンドルされた製品の部分払い戻し後に注文ステータスがクローズに変更される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.31 がインストールされている場合に使用できます。 パッチ ID は ACSD-49392 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.3.7-p4 および 2.4.1 ～ 2.4.6-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

バンドルされた製品の一部払い戻し後、注文ステータスが「クローズ」に変更される。

<u> 再現手順 </u>:

1. Adobe Commerceにログインしてバンドル製品を作成するか、既存のバンドル製品を使用します。
1. このバンドル製品を 1 より多い数量で注文します。
1. 管理者に移動し、手順 2 で作成した注文を **[!UICONTROL Sales]** / **[!UICONTROL Order]** から開き、請求書を作成します。 注文ステータスを確認します。 処理中です。
1. 一部のクレジットメモを作成します（バンドル内のすべての製品に対して払い戻しを行わないでください）。
1. 注文ステータスを確認します。

<u> 期待される結果 </u>

バンドルされた製品の一部のクレジットメモを作成した後、注文ステータスは「処理中」になります。

<u> 実績 </u>

バンドル製品の一部のクレジット・メモを作成すると、受注ステータスは「完了」になります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
