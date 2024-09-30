---
title: 「ACSD-53204：ギャラリーに画像を追加する同時リクエストで「製品を保存できません」エラーが発生する」
description: ACSD-53204 パッチを適用すると、Adobe Commerceの問題を修正できます。rest/V1/products/&lt;sku&gt;/media エンドポイントを使用して商品ギャラリーに画像を追加するリクエストを同時に行うと、「The product cannot be saved （商品は保存できません）」エラーがスローされます。
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53204：ギャラリーに画像を追加する同時リクエストで「*製品を保存できません*」エラーが発生する

ACSD-53204 パッチでは、`rest/V1/products/<sku>/media` エンドポイントを使用して製品ギャラリーに画像を追加する同時リクエストを行うと、「*製品を保存できません*」エラーがスローされる問題を修正しています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.39 がインストールされている場合に使用できます。 パッチ ID は ACSD-53204 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`rest/V1/products/<sku>/media` エンドポイントを使用して製品ギャラリーに画像を追加するリクエストを同時に実行すると *「* 製品を保存できません」エラーがスローされる。

<u> 再現手順 </u>:

1. 管理パネルにログインします。
1. SKU p1 で製品を作成します。
1. `rest/V1/products/<sku>/media` エンドポイントに対して複数の同時リクエストを実行し、複数の画像を同時にアップロードします。

<u> 期待される結果 </u>:

画像はエラーなしで保存されます。

<u> 実際の結果 </u>:

「*製品を保存できません*」エラーが時々返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。