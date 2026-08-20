---
title: 'ACSD-52786: カタログ ルール *[!UICONTROL SKU is]*は、SKUで始まるすべての製品に適用されます'
description: ACSD-52786 パッチを適用して、指定されたSKUで始まるすべての商品にカタログルール条件*[!UICONTROL SKU is]*が適用されるAdobe Commerceの問題を修正します。
feature: Price Rules
role: Admin
exl-id: 668d5f16-18a9-4054-aa6e-1fb8fa211373
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-52786: カタログ ルール「*[!UICONTROL SKU is]*」は、SKUで始まるすべての製品に適用されます

ACSD-52786 パッチは、指定されたSKUで始まるすべての製品にカタログルール条件&#x200B;*[!UICONTROL SKU is]*&#x200B;が適用される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35がインストールされている場合に利用できます。 パッチ IDはACSD-52786です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カタログ ルール条件&#x200B;*[!UICONTROL SKU is]*&#x200B;は、指定されたSKUで始まるすべての製品に適用されます。

<u>複製する手順</u>:

1. SKU 「24」の商品とSKU 「24-MB01」の商品を2つ作成します。
1. **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**&#x200B;に移動します。
1. 次の条件を適用します。
   * これらの条件のうち&#x200B;*[!UICONTROL If ** ALL **は** TRUE **]*: *[!UICONTROL SKU is 24]*です
1. 割引額を設定します。
1. **[!UICONTROL Save and Apply]**&#x200B;をクリックします。
1. キャッシュをフラッシュします。
1. ストアフロントに行き、24 MB01の価格を確認してください。

<u>期待される結果</u>:

カタログルールは、SKUが24に等しい1つの製品にのみ適用されます。

<u>実際の結果</u>:

カタログ ルール条件&#x200B;*[!UICONTROL SKU is]*&#x200B;は、指定されたSKUで始まるすべての製品に適用されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
