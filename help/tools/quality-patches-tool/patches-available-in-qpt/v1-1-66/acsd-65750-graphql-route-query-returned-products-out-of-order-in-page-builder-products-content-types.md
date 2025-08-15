---
title: 'ACSD-65750: [!DNL GraphQL] "route" クエリは、商品が順不同である in [!DNL Page Builder] Products コンテンツ タイプを返します'
description: ACSD-65750 パッチを適用すると、GraphQLの「ルート」クエリが商品を in [!DNL Page Builder] Products コンテンツタイプで順不同で返すAdobe Commerceの問題が修正されます。
feature: GraphQL, Page Builder, Products
role: Admin, Developer
type: Troubleshooting
exl-id: 3aee28e1-1293-42d0-a62c-5021e8f75518
source-git-commit: 2d6debf4d426a0473eb77919c2307afdc77bf937
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-65750:「route」クエリ [!DNL GraphQL]、製品コンテンツタイプで製品が順不同 [!DNL Page Builder] 返される

ACSD-65750 パッチでは、[!DNL GraphQL] の「ルート」クエリが製品コンテンツタイプで製品を順不同で返す問題 [!DNL Page Builder] 修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 がインストールされている場合に使用できます。 パッチ ID は ACSD-65750 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1 - 2.4.8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL GraphQL] Products コンテンツタイプを使用する際に、[!DNL Page Builder] の「ルート」クエリが、正しい並べ替え順で製品を返しません。

<u> 再現手順 </u>:

1. カタログに新しいカテゴリといくつかの製品を作成し、それらの製品をこのカテゴリにリンクします。
1. **[!UICONTROL Catalog]**/**[!UICONTROL Categories]** に移動し、作成したカテゴリを編集して「**[!UICONTROL Products in Category]**」タブを開きます。
1. このカテゴリの各製品にカスタム **[!UICONTROL Position]** を設定します。
1. カテゴリを保存し、再インデックスを実行します。
1. **[!UICONTROL Content]**/*[!UICONTROL Elements]*/**[!UICONTROL Pages]** に移動し、「**[!UICONTROL Add New Page]**」をクリックします。
1. **[!UICONTROL Content]** タブを展開し、「**[!UICONTROL Edit with Page Builder]**」をクリックします。
1. **[!UICONTROL Row]** 要素をコンテンツ領域にドラッグしてから、**[!UICONTROL Products]** 要素を行内にドラッグします。
1. Products 要素を次のように設定します。
   * **[!UICONTROL Select Products By]**: *カテゴリ*
   * **[!UICONTROL Category]**: *新しく作成したカテゴリを選択*
   * **[!UICONTROL Sort By]**: *位置*
1. **[!UICONTROL Search Engine Optimization]** タブに切り替え、**[!UICONTROL URL Key]** を *test-widget* に設定します。
1. ページを保存します
1. 次の [!DNL GraphQL] リクエストを実行します。

```
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

<u> 期待される結果 </u>:

システムは、カテゴリ位置で定義された順序で製品を返します。

<u> 実際の結果 </u>:

GraphQLの応答で、商品が商品のカテゴリ順位に一致しない順序で返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
