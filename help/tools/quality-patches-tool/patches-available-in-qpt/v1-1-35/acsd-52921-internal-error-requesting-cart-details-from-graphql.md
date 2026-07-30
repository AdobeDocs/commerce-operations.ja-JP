---
title: ACSD-52921：在庫切れ設定可能な商品について、GraphQLからカートの詳細を要求する際にエラーが発生する
description: 在庫切れの設定可能な商品について、GraphQLからカートの詳細をリクエストする際に内部エラーが発生するAdobe Commerceの問題を修正するには、ACSD-52921 パッチを適用します。
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 7790718a-6b86-497e-b1a1-88ba22c3e8ff
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# ACSD-52921：在庫切れ設定可能な商品について、GraphQLからカートの詳細を要求する際にエラーが発生する

ACSD-52921 パッチは、在庫切れの設定可能な商品について、GraphQLからカートの詳細をリクエストする際に内部エラーが発生する問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35がインストールされている場合に利用できます。 パッチ IDはACSD-52921です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

在庫切れ設定可能な商品について、GraphQLからカートの詳細をリクエストすると、内部エラーが発生します。

<u>複製する手順</u>:

1. いくつかのオプションを含む、設定可能な製品を作成します。
1. 上記の設定可能な製品のオプションをフロントエンドからカートに追加します（ゲストチェックアウト）。
1. 上記の作成された見積もりに対して、`[ quote_id_mask ]` db テーブルから`[ masked_id ]`を取得します。
1. 上記のゲストカートの詳細を取得するには、次のGraphQL クエリを実行します。

   手順3から受け取った`[ masked_id ]`をクエリに追加します。

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
1. バックエンドに移動し、設定可能な製品の&#x200B;*[!UICONTROL Stock Status]*&#x200B;を&#x200B;*[!UICONTROL Out of Stock]*&#x200B;に更新します。
1. 手順4と同じGraphQL クエリを実行します。

<u>期待される結果</u>:

エラーメッセージは、応答で正しく送信/処理されます。

<u>実際の結果</u>:

GraphQL クエリに応答して&#x200B;*500 Internal Server* エラーがスローされます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」ガイド

## 関連トピックス

* [[!DNL Quality Patches Tool]  リリース：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します
* [Commerce実装プレイブックのデータベーステーブルを修正するためのベストプラクティス &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
