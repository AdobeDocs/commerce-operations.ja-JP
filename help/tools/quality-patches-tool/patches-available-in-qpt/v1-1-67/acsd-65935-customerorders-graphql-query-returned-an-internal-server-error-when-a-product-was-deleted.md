---
title: 'ACSD-65935: ''customerOrders'' GraphQL クエリは、商品が削除されたときに内部サーバーエラーを返しました'
description: ACSD-65935 パッチを適用すると、商品が削除されたときに「customerOrders」GraphQL クエリが内部サーバーエラーを返したAdobe Commerceの問題を修正できます。
feature: Orders, GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: fd0b7043770bbbd12fbb9aad8cddaa2434d2ea5b
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---


# ACSD-65935：商品 `customerOrders` 削除すると、GraphQL クエリが内部サーバーエラーを返しました

ACSD-65935 パッチは、商品が削除されたときに `customerOrders` GraphQL クエリが内部サーバーエラーを返した問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 がインストールされている場合に使用できます。 パッチ ID は ACSD-65935 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

商品が削除されると、`customerOrders` GraphQL クエリが内部サーバーエラーを返します。

<u> 再現手順 </u>:

1. 2 つのシンプルな製品の作成
1. 顧客を作成し、フロントエンドから 2 つの製品を注文します。
1. バックエンドに移動し、1 つの製品を削除します。
1. 顧客トークンを作成します。

```
https://localhost/pub/graphql
mutation {
  generateCustomerToken(email: "test@test.com", password: "123123qA") {
    token
  }
}
```

1. `eligible_for_return` フィルター（顧客注文を取得するためにPWAで使用）を使用して注文のリストを取得します。

```
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

<u> 期待される結果 </u>:

注文リストはエラーなしで収集されます。

<u> 実際の結果 </u>:

例外：*内部サーバーエラー*

```
[2025-05-16T23:42:15.174025+00:00] report.ERROR: Call to a member function getIsReturnable() on null

{"exception":"[object] (GraphQL\\Error\\Error(code: 0): Call to a member function getIsReturnable() on null at /var/www/html/localhost/vendor/webonyx/graphql-php/src/Error/Error.php:170) [previous exception] [object] (Error(code: 0): Call to a member function getIsReturnable() on null at /var/www/html/localhost/magento2ee/app/code/Magento/Rma/Helper/Data.php:644)"}

[]
```


## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
