---
title: ACSD-52921：設定可能な在庫切れの商品について、GraphQLにカートの詳細をリクエスト中にエラーが発生しました
description: ACSD-52921 パッチを適用すると、設定可能な在庫切れの商品についてGraphQLに買い物かごの詳細をリクエストしたときに内部エラーが発生するAdobe Commerceの問題を修正できます。
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 7790718a-6b86-497e-b1a1-88ba22c3e8ff
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-52921：設定可能な在庫切れの商品について、GraphQLにカートの詳細をリクエスト中にエラーが発生しました

ACSD-52921 パッチでは、設定可能な在庫切れの商品について、GraphQLに買い物かごの詳細をリクエストすると内部エラーが発生する問題を修正しました。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35 がインストールされている場合に使用できます。 パッチ ID は ACSD-52921 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

在庫切れの設定可能な商品の買い物かごの詳細をGraphQLにリクエストすると、内部エラーが発生します。

<u> 再現手順 </u>:

1. いくつかのオプションを使用して設定可能な製品を作成します。
1. 上記の設定可能な製品のオプションをフロントエンド（ゲストのチェックアウト）から買い物かごに追加します。
1. 上記で作成した引用の `[ masked_id ]` を `[ quote_id_mask ]` db テーブルから取得します。
1. 次のGraphQL クエリを実行して、上記のゲストの買い物かごの詳細を取得します。

   手順 3 で取得した `[ masked_id ]` をクエリに追加します。

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. これにより、問題なく見積もりの詳細が返されます。
1. バックエンドに移動し、設定可能な製品の *[!UICONTROL Stock Status]* を *[!UICONTROL Out of Stock]* に更新します。
1. 手順 4 と同じGraphQL クエリを実行します。

<u> 期待される結果 </u>:

このエラーメッセージは、応答で正しく送信または処理されます。

<u> 実際の結果 </u>:

*500 内部サーバー* GraphQL クエリへの応答でエラーがスローされる。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドの
* クラウドインフラストラクチャー上のAdobe Commerce:[ アップグレードとパッチ適用 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) クラウドインフラストラクチャー上のCommerce ガイド

## 関連資料

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースに追加しました
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）
* Commerce実装プレイブックの [ データベーステーブルを変更する際のベストプラクティス ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
