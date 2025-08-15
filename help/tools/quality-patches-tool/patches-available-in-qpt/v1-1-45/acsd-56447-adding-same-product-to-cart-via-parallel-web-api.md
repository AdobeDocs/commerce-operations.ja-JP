---
title: ACSD-56447：並列 web REST API を使用して同じ製品を買い物かごに追加すると、買い物かごに 2 つの異なる項目が表示される
description: ACSD-56447 パッチを適用すると、Adobe Commerceの問題を修正できます。この問題では、並行する web REST API リクエストを使用して同じ商品を買い物かごに追加すると、買い物かごに 2 つの異なる商品が表示されます。
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: ef0b2ce7-74f5-47b6-a44c-bda898c444b2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56447：並列 web REST API を使用して同じ製品を買い物かごに追加すると、買い物かごに 2 つの異なる項目が表示される

ACSD-56447 パッチでは、並行する web REST API リクエストを介して同じ製品を買い物かごに追加すると、買い物かごに 2 つの異なる項目が表示される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45 がインストールされている場合に使用できます。 パッチ ID は ACSD-56447 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

並行する web REST API リクエストを使用して同じ製品を買い物かごに追加すると、買い物かごに 2 つの異なる項目が表示されます。

<u> 再現手順 </u>:

1. [!DNL Postman] を使用して REST API 呼び出しリクエストを行うための顧客トークンを生成します。
1. 顧客の買い物かごを作成します。
1. 上記で生成したトークンを使用して、顧客用の空の買い物かごを作成します。
1. CURL を使用すると、並行して実行される 2 つの `AddProductsToCart` リクエストを作成できます。 開発者向けドキュメントの [ 注文処理のチュートリアル ](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) の手順に従います。

<u> 期待される結果 </u>:

複数の数量を持つ品目が 1 行に表示されます。

<u> 実際の結果 </u>:

複数の行項目で同じ SKU が表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
