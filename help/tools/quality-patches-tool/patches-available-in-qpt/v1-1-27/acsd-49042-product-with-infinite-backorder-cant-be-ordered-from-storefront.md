---
title: ACSD-49042：順不同の商品はストアフロントからは注文できません
description: ACSD-49042 パッチを適用すると、順不同の商品をストアフロントから注文できないAdobe Commerceの問題を修正できます。
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
exl-id: b94d06c0-806a-40be-bcd4-d6b8e5e474c3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-49042：順不同の商品はストアフロントからは注文できません

ACSD-49042 パッチでは、順不同の商品をストアフロントから注文できない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 がインストールされている場合に使用できます。 パッチ ID は ACSD-49042 です。 この問題はAdobe Commerce 2.4.5 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

このエラーは、順不同の商品をストアフロントから注文できない場合に発生します。

<u> 再現手順 </u>:

1. 次の設定を行います。
   * **[!UICONTROL Display Out of Stock Products]** を *[!UICONTROL Yes]* に設定します。
   * **[!UICONTROL Backorders]** を *[!UICONTROL Allow Qty Below 0]* に設定します。
1. 新しい **[!DNL custom stock]** と **[!DNL custom source]** を追加します。
1. **[!DNL custom source]** に製品を割り当て、その製品の在庫番号が設定されていることを確認してください（例：*10*）。
1. 製品の編集ページで、**[!UICONTROL Advanced Inventory]** を開きます。 カートに **[!UICONTROL minimum quantity]** を設定します（例：*160*）。 数量は在庫より上である必要があります。
1. 店頭に移動し、商品を購入して予約を作成します。
1. **[!UICONTROL product quantity]** を *0* に変更します。 重要なポイントは、予約がある場合に **[!DNL Admin panel]** から製品を保存することです。
1. ストアフロントで **[!UICONTROL product page]** を開き、商品をカートに追加してみてください。

<u> 期待される結果 </u>:

*0* 未満の数量のバックオーダーは許可されているので、買い物かごに製品を追加できます。

<u> 実際の結果 </u>:

商品が在庫切れと表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
