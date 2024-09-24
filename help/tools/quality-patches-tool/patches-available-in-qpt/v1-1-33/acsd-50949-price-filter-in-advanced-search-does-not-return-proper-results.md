---
title: 「ACSD-50949：詳細検索の価格フィルターを SKU フィルターと一緒に使用すると、適切な結果が返されません」
description: ACSD-50949 パッチを適用すると、詳細検索で価格フィルターを SKU フィルターと一緒に使用した場合に、適切な結果が返されないAdobe Commerceの問題が修正されます。
feature: Orders, Search
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 1%

---

# ACSD-50949：詳細検索の価格フィルターを SKU フィルターと共に使用すると、適切な結果が返されない

ACSD-50949 パッチでは、SKU フィルターと一緒に使用した場合に、詳細検索で価格フィルターが適切な結果を返さない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 がインストールされている場合に使用できます。 パッチ ID は ACSD-50949 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) で互換性を確認します。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 問題

詳細検索の価格フィルターを SKU フィルターと一緒に使用すると、適切な結果が返されません。

<u> 再現手順 </u>:

1. 複数の製品を作成します。例：

   | SKU | 名前 | 価格 | 数量 |
   |-----|-----------|-------|----------|
   | MJ1 | 製品 1 | $10 | 10 |
   | MJ2 | 製品 2 | $15 | 10 |
   | MJ3 | 製品 3 | $21 | 10 |
   | MJ4 | 製品 4 | $32 | 10 |
   | MJ5 | 製品 5 | $33 | 10 |
   | MJ6 | 製品 6 | $34 | 10 |
   | MJ7 | 製品 7 | $44 | 10 |

1. ストアフロントで **[!UICONTROL Advanced Search]** を開き、SKU:&quot;MJ&quot;で検索します。
1. **[!UICONTROL Modify your search]** リンクをクリックします。
1. 条件に *1* ～ *21* の価格範囲を追加し、「**[!UICONTROL Search]**」ボタンをクリックします。

<u> 期待される結果 </u>:

定義された範囲内に価格がある製品のみが返されます。

<u> 実際の結果 </u>:

価格が 21 ** ドルを超える商品が返品されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)」を参照してください。
