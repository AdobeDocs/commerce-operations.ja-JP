---
title: MDVA-41631：オプションの「電話機」値を使用せずに注文情報を取得中にエラーが発生しました
description: MDVA-41631 パッチでは、オプションの「電話番号」値を使用せずに注文情報を取得する際にユーザーがエラーを受け取る問題が [!DNL GraphQL]を通じて修正されます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.7がインストールされている場合に利用できます。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Orders
role: Admin
exl-id: e56cea59-ffc1-4520-85ca-136cda613884
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# MDVA-41631：オプションの「電話機」値を使用せずに注文情報を取得中にエラーが発生しました

MDVA-41631 パッチは、オプションの「telephone」値を指定せずに[!DNL GraphQL]経由で注文情報を取得する際にユーザーがエラーを受け取る問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7がインストールされている場合に利用できます。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

オプションの「電話番号」値を指定せずに[!DNL GraphQL]経由で注文情報を取得する際にエラーが発生します。

<u>複製する手順</u>:

1. **Store** > **Configuration** > **Customers** > **Customer Configuration** > **名前と住所のオプション** > **電話を表示**&#x200B;に移動し、電話番号をオプションとして設定します。
1. [!DNL GraphQL API]をログイン顧客として使用して注文します。
   * 請求先住所と配送先住所を設定する場合は、電話番号を設定しないでください。 開発者向けドキュメントの[[!DNL GraphQL]  チェックアウトチュートリアル ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/)に記載されている手順に従ってください。
1. [!DNL GraphQL] [`customerOrders` クエリ ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/orders/)を使用して注文を取得します。

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>期待される結果</u>:

利用者には注文情報が表示されます。

<u>実際の結果</u>:

ユーザーに次のエラーが表示されます：*&quot;message&quot;: &quot;内部サーバーエラー&quot;,*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
