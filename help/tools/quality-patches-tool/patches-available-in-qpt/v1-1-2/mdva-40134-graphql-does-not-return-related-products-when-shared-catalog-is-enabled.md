---
title: MDVA-40134：共有カタログが有効な場合、GraphQLが関連商品を返さない
description: MDVA-40134 パッチでは、共有カタログが有効な場合に、GraphQLが関連商品を返さない問題が修正されています。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.2 がインストールされている場合に利用できます。 パッチ ID は MDVA-40134。 この問題はAdobe Commerce 2.4.3 で修正されました。
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
exl-id: 5d31e042-4396-40ce-8bf1-63ad9a55214d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-40134：共有カタログが有効な場合、GraphQLが関連商品を返さない

MDVA-40134 パッチでは、共有カタログが有効な場合に、GraphQLが関連商品を返さない問題が修正されています。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.2 がインストールされている場合に使用できます。 パッチ ID は MDVA-40134。 この問題はAdobe Commerce 2.4.3 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

共有カタログが有効になっている場合、GraphQLが関連商品を返さない。

<u> 前提条件 </u>:

B2B モジュールをインストールする必要があります。
インスタンスは、サンプルデータのみでクリーンアップする必要があります。

<u> 再現手順 </u>:

1. **ストア**/**設定**/**一般**/**B2B 機能** に移動し、「**会社および共有カタログ**」を有効にします。
1. **カタログ**/**共有カタログ** に移動し、すべての製品を **一般カタログ** に追加します。
1. サンプルデータを使用して、Jourst Duffle Bag （SKU 24-MB01）を変更します。
1. **関連製品** の下に、2 つのダッフルバッグ（ID 7 と 13）を追加します。
1. **Post** リクエストを送信します。

<pre>&lbrace;
  製品（フィルター：{sku: {eq: "24-MB01"}}、並べ替え：{name: ASC}） &lbrace;
    項目 &lbrace;
      related_products &lbrace;
        uid
        名前
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;</pre>

<u> 期待される結果 </u>:

関連する商品はGraphQLの応答に表示されます。

<u> 実際の結果 </u>:

ユーザーに次のエラーが表示されます。

<pre>Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId （）の戻り値は int 型にする必要があり、null は &lbrace;"exception":"[object] （GraphQL\\Error\\Error （code: 0）:Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId （）の戻り値は int 型にする必要があり、null が返されます </pre>

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
