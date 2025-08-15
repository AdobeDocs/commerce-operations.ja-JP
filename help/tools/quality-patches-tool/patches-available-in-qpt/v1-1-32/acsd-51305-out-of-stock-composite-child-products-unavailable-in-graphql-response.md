---
title: ACSD-51305:GraphQL応答で使用できない在庫切れの複合子製品
description: ACSD-51305 パッチを適用して、Adobe Commerceの応答で在庫切れの複合子製品を使用できないGraphQLの問題を修正してください。
feature: Categories, GraphQL, Orders, Products
role: Admin
exl-id: 110bb332-2032-4aaf-b95e-971fc3382262
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-51305:GraphQL応答で使用できない在庫切れの複合子製品

ACSD-51305 パッチでは、在庫切れの複合子製品がGraphQL応答で使用できない問題を修正しています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32 がインストールされている場合に使用できます。 パッチ ID は ACSD-51305 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

在庫切れの複合子製品は、GraphQL応答では使用できません。

<u> 再現手順 </u>:

1. 管理者 Web サイトにログインします。
1. カテゴリ（cat1、id=3）を作成します。
1. *simple1* 製品（在庫切れ、個別に表示されない、*cat1*）に割り当てを作成します。
1. *cat1* に割り当てられた、*simple2* 製品（在庫あり、個別には表示されない）を作成します。
1. *simple1* と *simple2* 子製品を持つ *bundle1* 製品をラジオボタン *option1* 製品として作成して、*cat1* カテゴリに割り当てます。
1. **[!UICONTROL Admin]**/**[!UICONTROL System]**/**[!UICONTROL Configuration]**/**[!UICONTROL Catalog]**/**[!UICONTROL Inventory]** に移動します。

   * **[!UICONTROL Display Out of Stock Products]** を *はい* に設定します。

1. ストアフロントで *bundle1* 製品を開き、*simple1* 子製品と *simple2* 子製品の両方が内部に表示されていることを確認します。
1. 次のGraphQL クエリを実行します。

   ```GraphQL
   {
       categoryList(filters: { ids: { in: ["3"] } }) {
           id
           name
           products(pageSize: 8, sort: { position: ASC }) {
               total_count
               items {
                   id
                   sku
                   name
                   ... on BundleProduct {
                       url_key
                       items {
                           title
                           sku
                           options {
                               quantity
                               position
                               is_default
                               product {
                                   id
                                   name
                                   sku
                               }
                           }
                       }
                   }
               }
           }
       }
   }
   ```

<u> 期待される結果 </u>:

**[!UICONTROL Product]** ブロック内の **[!UICONTROL Options]** セクションが空ではありません。

<u> 実際の結果 </u>:

**[!UICONTROL Product]** ブロック内の **[!UICONTROL Options]** セクションが空です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
