---
title: ACSD-63299：設定可能な製品の特別価格がストアフロントに表示されない
description: ACSD-63299 パッチを適用すると、特別価格属性が設定可能な商品の特別価格の表示に影響を与えなくなるAdobe Commerceの問題を修正できます。
feature: Catalog Management
Role: Admin, Developer
exl-id: cd1775c5-783e-4ed5-a148-1dae0b7542f8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-63299：設定可能な製品の特別価格がストアフロントに表示されない

ACSD-63299 パッチは、特別価格属性が設定可能な製品の特別価格の表示に影響を与えなくなる問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 がインストールされている場合に使用できます。 パッチ ID は ACSD-63299 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ま [!DNL Adobe Commerce]、特別価格属性の *製品リストで使用* 値を変更しても、設定可能な製品の特別価格の表示方法に影響しなくなりました。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/*[!UICONTROL Attributes]*/**[!UICONTROL Products]** に移動します。
1. ***[!UICONTROL special_price]*** 属性を見つけて、**[!UICONTROL Storefront Properties]** に移動します。
1. ***[!UICONTROL Used in Product Listing]*** を&#x200B;***[!UICONTROL No]***&#x200B;に変更します。
1. 1 つの子を持つ設定可能な製品を作成します。
   * 名前と SKU: テスト
   * 価格：159.00 ドル
   * 色に基づいてオプションを生成します。 新しい色を追加：青
   * 保存
1. 子製品を開いて、次の手順に従います。
   * **[!UICONTROL Advanced Pricing]** で特別価格を 99.90 ドルに設定する
   * [!UICONTROL Visibility] を **[!UICONTROL Catalog, Search]** に変更します。
1. シンプルな製品ページを開き、特別価格が表示されていることを確認します。
1. 設定可能な製品ページを開きます。
1. 青い商品を選択します。

<u> 期待される結果 </u>:

シンプルな商品と同じように特別価格が見えます。

<u> 実際の結果 </u>:

1. 設定可能な製品が選択されると、全価格が表示されます。
1. *99.90 ドル）と実際の価格（$99.90 + $59.10 = $159.00* のセクションの間に不一致があります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
