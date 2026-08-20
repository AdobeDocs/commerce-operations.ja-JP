---
title: ACSD-56447：並列web REST APIを介して同じ商品をカートに追加すると、カート内に2つの別々のアイテムが表示される
description: ACSD-56447 パッチを適用して、同じ商品を並行するweb REST API リクエストを介してカートに追加すると、カート内に2つの別の商品が発生するというAdobe Commerceの問題を修正します。
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: ef0b2ce7-74f5-47b6-a44c-bda898c444b2
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# ACSD-56447：並列web REST APIを介して同じ商品をカートに追加すると、カート内に2つの別々のアイテムが表示される

ACSD-56447 パッチでは、同じ製品を並行するweb REST API リクエストを介してカートに追加すると、カート内に2つの別々のアイテムが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.45がインストールされている場合に利用できます。 パッチ IDはACSD-56447です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

並行してweb REST API リクエストを使用して同じ商品をカートに追加すると、カートに2つの別々のアイテムが表示されます。

<u>複製する手順</u>:

1. [!DNL Postman]を使用してREST API呼び出し要求を行うための顧客トークンを生成します。
1. 顧客向けのショッピングカートの作成。
1. 上記で生成したトークンを使用して、顧客用の空のカートを作成します。
1. CURLを使用して、2つの`AddProductsToCart` リクエストを並行して実行します。 開発者ドキュメントの[注文処理チュートリアル &#x200B;](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/)の手順に従います。

<u>期待される結果</u>:

複数の数量を持つ品目は、1行に表示されます。

<u>実際の結果</u>:

同じSKUが複数の行アイテムに表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
