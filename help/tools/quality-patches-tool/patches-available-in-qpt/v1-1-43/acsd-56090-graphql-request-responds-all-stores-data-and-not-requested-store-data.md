---
title: 'ACSD-56090: GraphQLの応答がストア固有ではない'
description: ACSD-56090 パッチを適用して、GraphQLのレスポンスにストア固有のデータではなく、すべてのストアデータが含まれているAdobe Commerceの問題を修正します。
feature: GraphQL
role: Admin, Developer
exl-id: 0909c09c-3260-43d2-8eac-0e5d7639f24b
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# ACSD-56090: GraphQLの応答がストア固有ではない

ACSD-56090 パッチでは、GraphQLの応答に、ストア固有のデータではなく、すべてのストアデータが含まれている問題が修正されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43がインストールされている場合に利用できます。 パッチ IDはACSD-56090です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQLの応答には、ストア固有のデータではなく、すべてのストアデータが含まれます。

<u>複製する手順</u>:

1. **[!UICONTROL Admin panel]** > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**&#x200B;にログインし、2つのルート カテゴリを作成します。
1. 各ルートカテゴリには、1つのサブカテゴリが必要です。
1. **[!UICONTROL Stores]** > **[!UICONTROL All stores]** >それぞれに異なるルート カテゴリを持つ2つのストアが存在します。 （各ストアには、少なくとも1つのストアビューが必要です）
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]** >製品の作成に移動します

* 割り当てられたすべてのルートおよびサブカテゴリ
* すべてのウェブサイトが割り当てられました。

1. GraphqQL クエリを実行します（add header — store = &#39;storename）。

```graphql
   query {
     products(filter: { url_key: { eq: "abc" } }) {
       items {
         categories {
           name
           id
           url_path
           breadcrumbs {
             category_id
             category_name
             category_level
           }
         }
       }
     }
   }
```

1. GraphqQL クエリを実行した後、応答を確認します。

<u>期待される結果</u>:

ストア固有のデータが返されます

<u>実際の結果</u>:

返されたデータはストア固有ではありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
