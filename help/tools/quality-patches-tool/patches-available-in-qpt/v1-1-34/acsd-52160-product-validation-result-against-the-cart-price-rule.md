---
title: ACSD-52160：買い物かご価格ルールに対する製品検証結果
description: ACSD-52160 パッチを適用すると、買い物かごの価格ルールに対する商品の検証結果がルール条件*[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*に基づいて適切に評価されないAdobe Commerceの問題を修正できます。
exl-id: 8f8799c9-850a-4c8f-bde4-68df64e46c85
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52160：買い物かごの価格ルールに対する製品検証結果が適切に評価されていない

ACSD-52160 パッチでは、買い物かごの価格ルールに対する製品検証結果が、ルール条件 *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]* に基づいて適切に評価されない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34 がインストールされている場合に使用できます。 パッチ ID は ACSD-52160 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

買い物かご価格ルールに対する製品検証結果が、ルール条件 *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]* に基づいて適切に評価されていません。

<u> 再現手順 </u>:

1. 2 つの異なるカテゴリに割り当てられた 2 つの製品を作成します。
1. 次のような条件を持つ **[!UICONTROL Cart Price Rule]** を作成します。

   * *[!UICONTROL FOUND]* パラメーターの **SKU 1**
   * *[!UICONTROL NOT FOUND]* パラメーターの **SKU 2**

1. 両方の商品を買い物かごに追加します。
1. クーポンコードを適用します。

<u> 期待される結果 </u>

買い物かごには、制限されたカテゴリの製品が含まれているので、クーポンコードは適用されません。

<u> 実績 </u>

クーポンコードが適用されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)」を参照してください。
