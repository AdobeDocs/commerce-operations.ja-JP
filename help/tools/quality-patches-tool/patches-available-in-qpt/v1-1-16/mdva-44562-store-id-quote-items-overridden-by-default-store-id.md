---
title: MDVA-44562：既定のストア IDで上書きされる見積もり項目のストア ID
description: MDVA-44562 パッチでは、デフォルトのストア IDがGraphQL リクエストの見積もり項目のストア IDを上書きする問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.16がインストールされている場合に利用できます。 パッチ IDはMDVA-44562です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。
feature: Quotes
role: Admin
exl-id: 007a82f7-4bc9-4a51-8b18-05f6c0867ea7
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# MDVA-44562：既定のストア IDで上書きされる見積もり項目のストア ID

MDVA-44562 パッチでは、デフォルトのストア IDがGraphQL リクエストの見積もり項目のストア IDを上書きする問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.16がインストールされている場合に使用できます。 パッチ IDはMDVA-44562です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

見積もり項目のストア IDは、GraphQL リクエストのデフォルトのストア IDによって上書きされます。

<u>複製する手順</u>:

1. 新しいストアビューを作成します。
1. ストアビューごとに異なる名前の新しいシンプルな商品を作成します。
1. 新規顧客の作成：
1. 顧客認証トークンを取得します。

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. 認証トークンを使用して、顧客の新しい見積もりを作成します。

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. 商品をカートに追加する。

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. デフォルトのストアビューのカートコンテンツを取得します。

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. 新しいストアビューのカートコンテンツを取得します。

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>期待される結果</u>:

新しいストアビューからの応答には、新しいストアビューからの製品名が表示されます。

<u>実際の結果</u>:

新しいストアビューからの応答には、デフォルトのストアビューで設定された製品名が表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
