---
title: MDVA-44505：報酬ポイントを適用するカートのGraphQL クエリが総計を更新しません
description: MDVA-44505 パッチは、報酬ポイントを適用するカートに対するGraphQL クエリが報酬ポイントを考慮せず、誤った総計を返す問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.14がインストールされている場合に利用できます。 パッチ IDはMDVA-44505です。 この問題は、Adobe Commerce 2.4.3で修正されています。
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
exl-id: 543698d8-8963-4bf7-af82-11c2498e882e
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-44505：報酬ポイントを適用するカートのGraphQL クエリが総計を更新しません

MDVA-44505 パッチは、報酬ポイントを適用するカートに対するGraphQL クエリが報酬ポイントを考慮せず、誤った総計を返す問題を解決します。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.14がインストールされている場合に使用できます。 パッチ IDはMDVA-44505です。 この問題は、Adobe Commerce 2.4.3で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

報酬ポイントを適用するカートのGraphQL クエリは、報酬ポイントを考慮せず、誤った総計を返します。

<u>複製する手順</u>:

1. 報酬ポイントの設定。
1. カートを作成し、いくつかリワードポイントを適用します。
1. `GraphQL` エンドポイントから`GetCart` クエリを呼び出して、買い物かごを取得します。

   ```GraphQL
   query {
     cart(cart_id: "{CART_ID}") {
       prices {
         discounts {
           amount {
             value
           }
         }
         grand_total {
           value
         }
       }
     }
   }
   ```

1. 総入場者数をチェック。
1. 次に、REST API （`/rest/V1/carts/mine/totals`）を使用して顧客のカート合計を確認します。

<u>期待される結果</u>:

買い物かごのGraphQL クエリは、報酬ポイントを考慮した正しい合計金額を返します。

<u>実際の結果</u>:

GraphQL クエリは、報酬ポイントを考慮せず、誤った総計を返します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
