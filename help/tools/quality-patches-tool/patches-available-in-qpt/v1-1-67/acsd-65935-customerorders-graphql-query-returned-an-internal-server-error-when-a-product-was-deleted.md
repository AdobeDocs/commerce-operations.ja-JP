---
title: 'ACSD-65935: ''customerOrders'' GraphQL クエリは、製品が削除されたときに内部サーバーエラーを返しました'
description: ACSD-65935 パッチを適用して、製品が削除されたときに「customerOrders」GraphQL クエリが内部サーバーエラーを返したAdobe Commerceの問題を修正します。
feature: Orders, GraphQL
role: Admin, Developer
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%
---

# ACSD-65935: `customerOrders` GraphQL クエリで、製品が削除されたときに内部サーバーエラーが返されました

ACSD-65935 パッチは、製品が削除されたときに`customerOrders` GraphQL クエリが内部サーバーエラーを返した問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67がインストールされている場合に利用できます。 パッチ IDはACSD-65935です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品が削除されると、`customerOrders` GraphQL クエリは内部サーバーエラーを返します。

<u>複製する手順</u>:

1. 2つのシンプルな商品を作成
1. 顧客を作成し、フロントエンドから2つの商品を注文します。
1. バックエンドに移動し、1つの製品を削除します。
1. 顧客トークンの作成：

```text
https://localhost/pub/graphql
mutation {
  generateCustomerToken(email: "test@test.com", password: "123123qA") {
    token
  }
}
```

1. `eligible_for_return` フィルターを使用して注文のリストを取得します（PWAでお客様の注文を取得するために使用）。

```text
https://localhost/pub/graphql
{
  customerOrders {
    items {
      order_number
      id
      created_at
      grand_total
      status
        items{
          eligible_for_return
        }
    }
  }
}
```

<u>期待される結果</u>:

注文リストはエラーなく収集されます。

<u>実際の結果</u>:

例外：*内部サーバーエラー*

```graphql
[2025-05-16T23:42:15.174025+00:00] report.ERROR: Call to a member function getIsReturnable() on null

{"exception":"[object] (GraphQL\\Error\\Error(code: 0): Call to a member function getIsReturnable() on null at /var/www/html/localhost/vendor/webonyx/graphql-php/src/Error/Error.php:170) [previous exception] [object] (Error(code: 0): Call to a member function getIsReturnable() on null at /var/www/html/localhost/magento2ee/app/code/Magento/Rma/Helper/Data.php:644)"}

[]
```


## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
