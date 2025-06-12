---
title: MDVA-44505：報酬ポイントを適用する買い物かごに対するGraphQL クエリで総計が更新されない
description: MDVA-44505 パッチは、報酬ポイントを適用する買い物かごに対するGraphQL クエリが報酬ポイントを考慮せず、誤った総計を返す問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.14 がインストールされている場合に利用できます。 パッチ ID は MDVA-44505。 この問題はAdobe Commerce 2.4.3 で修正されました。
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
exl-id: 543698d8-8963-4bf7-af82-11c2498e882e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-44505：報酬ポイントを適用する買い物かごに対するGraphQL クエリで総計が更新されない

MDVA-44505 パッチは、報酬ポイントを適用する買い物かごに対するGraphQL クエリが報酬ポイントを考慮せず、誤った総計を返す問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.14 がインストールされている場合に使用できます。 パッチ ID は MDVA-44505。 この問題はAdobe Commerce 2.4.3 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 ～ 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

報酬ポイントを適用する買い物かごに対するGraphQL クエリは報酬ポイントを考慮せず、誤った総計を返します。

<u> 再現手順 </u>:

1. 報酬ポイントを設定します。
1. 買い物かごを作成して、報酬ポイントを適用します。
1. `GraphQL` エンドポイントから `GetCart` クエリを呼び出し、買い物かごを取得します。

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

1. 総計のエントリを確認します。
1. 次に、REST API を使用して、顧客の買い物かごの合計を確認します（`/rest/V1/carts/mine/totals`）。

<u> 期待される結果 </u>:

買い物かごに対するGraphQL クエリは、報酬ポイントを考慮した正しい総計を返します。

<u> 実際の結果 </u>:

GraphQLのクエリで報酬ポイントが考慮されず、誤った総計が返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
