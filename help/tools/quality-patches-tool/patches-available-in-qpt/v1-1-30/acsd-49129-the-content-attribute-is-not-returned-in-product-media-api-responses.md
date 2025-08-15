---
title: ACSD-49129：製品メディア API 応答で「Content」属性が返されない
description: ACSD-49129 パッチを適用すると、「rest/V1/products/sku/media」 product media API 応答で*content*属性（*base64 image code*）が返されないAdobe Commerceの問題が修正されます。
feature: REST, Attributes, Media, Page Content, Products
role: Admin
exl-id: 5235b7d1-4ebf-4cfb-8605-47614306a122
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-49129：製品メディア API 応答で「Content」属性が返されない

ACSD-49129 パッチでは、*製品メディア API 応答で* content *[!UICONTROL base64 image code]* 属性（`rest/V1/products/sku/media`）が返されない問題を修正しています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.30 がインストールされている場合に使用できます。 パッチ ID は ACSD-49129 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.5-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

*content* 属性（*[!UICONTROL base64 image code]*）が、`rest/V1/products/sku/media` 製品メディア API 応答で返されません。

<u> 再現手順 </u>:

1. 画像付きの製品を作成します。
1. *GET REST API* リクエストを `rest/V1/products/<sku>/media` と `rest/V1/products/<sku>/media/<entryId>` に送信します。
1. API の応答を確認します。

<u> 期待される結果 </u>

データを含む *content* 属性は、REST API を介して使用できます。

<u> 実績 </u>

*content* 属性が API 応答に存在しません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
