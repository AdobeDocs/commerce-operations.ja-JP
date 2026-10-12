---
title: MDVA-40134：共有カタログが有効になっている場合にGraphQLが関連商品を返さない
description: MDVA-40134 パッチは、共有カタログが有効になっている場合にGraphQLが関連商品を返さない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.2がインストールされている場合に利用できます。 パッチ IDはMDVA-40134です。 この問題は、Adobe Commerce 2.4.3で修正されています。
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
exl-id: 5d31e042-4396-40ce-8bf1-63ad9a55214d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%
---
# MDVA-40134：共有カタログが有効になっている場合にGraphQLが関連商品を返さない

MDVA-40134 パッチは、共有カタログが有効になっている場合にGraphQLが関連商品を返さない問題を修正します。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2がインストールされている場合に使用できます。 パッチ IDはMDVA-40134です。 この問題は、Adobe Commerce 2.4.3で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

共有カタログが有効になっている場合、GraphQLは関連商品を返しません。

<u>前提条件</u>:

B2B モジュールをインストールする必要があります。
インスタンスは、サンプルデータのみでクリーンである必要があります。

<u>複製する手順</u>:

1. **ストア** > **設定** > **一般** > **B2B機能**&#x200B;に移動し、**会社と共有カタログ**&#x200B;を有効にします。
1. **カタログ** > **共有カタログ**&#x200B;に移動し、すべての製品を&#x200B;**一般カタログ**&#x200B;に追加します。
1. サンプルデータを使用して、Joust Duffle Bag （SKU 24-MB01）を変更します。
1. **関連製品**&#x200B;の下に、2つのDuffle バッグ （ID 7と13）を追加します。
1. **Post** リクエストを送信します。

<pre>{
  products （filter: {sku: {eq: "24-MB01"}}, sort: {name: ASC}） {
    items {
      related_products {
        uid
        name
      }
    }
  }
}</pre>

<u>期待される結果</u>:

関連商品は、GraphQLの回答に記載されています。

<u>実際の結果</u>:

ユーザーに次のエラーが表示されます。

<pre>Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId （）の戻り値はint型である必要があり、nullは{"exception":"[object] （GraphQL\\Error\\Error （コード：0）:Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId （）の戻り値はint型である必要があり、nullが返されます </pre>

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
