---
title: 'ACSD-65750: [!DNL GraphQL] "route" クエリは、 [!DNL Page Builder] 製品コンテンツタイプで製品を注文せずに返します'
description: ACSD-65750 パッチを適用して、GraphQLの「route」クエリが [!DNL Page Builder] Products コンテンツタイプで製品を正しく返さないAdobe Commerceの問題を修正します。
feature: GraphQL, Page Builder, Products
role: Admin, Developer
type: Troubleshooting
exl-id: 3aee28e1-1293-42d0-a62c-5021e8f75518
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-65750: [!DNL GraphQL] 「route」クエリが[!DNL Page Builder]製品コンテンツタイプで製品を誤って返します

ACSD-65750 パッチは、[!DNL GraphQL] 「ルート」クエリが[!DNL Page Builder]製品コンテンツタイプで製品を誤って返す問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66がインストールされている場合に利用できます。 パッチ IDはACSD-65750です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1 - 2.4.8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL GraphQL] 「ルート」クエリは、[!DNL Page Builder]製品コンテンツタイプを使用する場合、正しい並べ替え順序で製品を返しません。

<u>複製する手順</u>:

1. カタログに新しいカテゴリと一部の製品を作成し、製品をこのカテゴリにリンクします。
1. **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**&#x200B;に移動し、作成したカテゴリを編集して、**[!UICONTROL Products in Category]** タブを開きます。
1. このカテゴリの各製品にカスタム **[!UICONTROL Position]**&#x200B;を設定します。
1. カテゴリを保存し、インデックス再作成を実行します。
1. **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**&#x200B;に移動し、**[!UICONTROL Add New Page]**&#x200B;をクリックします。
1. 「**[!UICONTROL Content]**」タブを展開し、「**[!UICONTROL Edit with Page Builder]**」をクリックします。
1. **[!UICONTROL Row]**&#x200B;要素をコンテンツ領域にドラッグしてから、行内の&#x200B;**[!UICONTROL Products]**&#x200B;要素をドラッグします。
1. Products要素を次のように設定します。
   * **[!UICONTROL Select Products By]**: *カテゴリ*
   * **[!UICONTROL Category]**: *新しく作成したカテゴリを選択*
   * **[!UICONTROL Sort By]**: *位置*
1. **[!UICONTROL Search Engine Optimization]** タブに切り替え、**[!UICONTROL URL Key]**&#x200B;を&#x200B;*test-widget*&#x200B;に設定します。
1. ページを保存します。
1. 次の[!DNL GraphQL] リクエストを行います。

```graphql
query {
  route(url: "/test-widget") {
    relative_url
    redirect_code
    type
    ... on CmsPage {
      identifier
      content
      __typename
    }
    ... on ProductInterface {
      uid
      __typename
    }
    ... on CategoryInterface {
      uid
      __typename
    }
    __typename
  }
}
```

<u>期待される結果</u>:

商品は、カテゴリ位置で定義された順序で返品されます。

<u>実際の結果</u>:

GraphQLのレスポンスのカテゴリ位置と一致しない順序で商品が返されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
