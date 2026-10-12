---
title: MDVA-37234：複数回カートにアイテムを追加すると、重複した行アイテムが作成される
description: MDVA-37234 パッチでは、同じSKUに対してカートにアイテムを複数回追加すると（並列リクエスト）、同じカート IDに対して重複したラインアイテムが作成される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.3がインストールされている場合に利用できます。 パッチ IDはMDVA-37234です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Orders, Shopping Cart
role: Admin
exl-id: d4e9fca1-7fba-4a33-9c5e-c9695cbfc61c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%
---
# MDVA-37234：複数回カートにアイテムを追加すると、重複した行アイテムが作成される

MDVA-37234 パッチでは、同じSKUに対してカートにアイテムを複数回追加すると（並列リクエスト）、同じカート IDに対して重複したラインアイテムが作成される問題を修正します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.3がインストールされている場合に使用できます。 パッチ IDはMDVA-37234です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.3.6、2.4.1、および2.4.2

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方式） 2.3.5 - 2.3.7-p1および2.4.1 - 2.4.2-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

同じSKUに対してアイテムをカートに複数回追加すると（並列リクエスト）、同じカート IDに対して重複した行アイテムが作成されます。

<u>複製する手順</u>:

1. SKU = simple1でシンプルな商品を作成します。
1. 顧客の構築：
1. GraphQL リクエストを行うための顧客トークンを生成します。

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
        generateCustomerToken(
            email: "customer email"
            password: "customer password"
        )
        &lbrace;
            token
        &rbrace;
    &rbrace;
    </code>
    </pre>

1. 手順3で説明したトークンを使用して、顧客用の空のカートを作成します。

   <pre>
    <code class="language-graphql">
    mutation&lbrace;
     createEmptyCart
    &rbrace;
    </code>
    </pre>

1. 2つの`addSimpleProductsToCart` リクエストを並行して実行するスクリプトを作成します。 例：

   <pre>
    <YOUR_ACCESS_TOKEN><YOUR_CART_ID><YOUR_ACCESS_TOKEN><YOUR_CART_ID>
    </pre>

1. スクリプトを実行します。

<u>期待される結果</u>:

合計数量を持つ1つの製品ライン （この場合は3つ）のみがショッピングカートに作成されます。

<u>実際の結果</u>:

同じ商品に対して2つの別々の行がショッピングカートに作成されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメントタイプに応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

Adobe Commerceの高品質なパッチについて詳しくは、次を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で使用可能な パッチ」セクションを参照してください。
