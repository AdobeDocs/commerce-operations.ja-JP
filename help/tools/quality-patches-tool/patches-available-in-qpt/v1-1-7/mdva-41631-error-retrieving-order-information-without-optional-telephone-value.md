---
title: 'MDVA-41631: オプションの"telephone"値なしで注文情報を取得中にエラーが発生しました'
description: MDVA-41631 パッチでは、オプションの「telephone」値を使用せずに注文情報を取得する際にエラーが発生する問題  [!DNL GraphQL] 修正されています。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.7 がインストールされている場合に利用できます。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: Orders
role: Admin
exl-id: e56cea59-ffc1-4520-85ca-136cda613884
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-41631: オプションの&quot;telephone&quot;値なしで注文情報を取得中にエラーが発生しました

MDVA-41631 パッチでは、オプションの「telephone」値を使用せずに [!DNL GraphQL] から注文情報を取得する際にエラーが発生する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 がインストールされている場合に使用できます。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.1 ～ 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL GraphQL] を使用すると、オプションの「電話」値なしで注文情報を取得する際にエラーが発生します。

<u> 再現手順 </u>:

1. **ストア**/**設定**/**カスタマー**/**カスタマー設定**/**名前と住所のオプション**/**電話を表示** に移動し、電話番号をオプションとして設定します。
1. ログインしている顧客として [!DNL GraphQL API] を使用して注文します。
   * 請求先住所と配送先住所を設定する際は、電話番号を設定しないでください。 アドビの開発者向けドキュメントの [[!DNL GraphQL]  チェックアウトチュートリアル ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) に記載されている手順に従います。
1. [!DNL GraphQL] [`customerOrders` クエリ ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/orders/) を使用して注文を取得します。

<pre>
<code class="language-graphql">
&lbrace;
  customer &lbrace;
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}})&lbrace;
        items&lbrace;
          billing_address &lbrace;
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
&rbrace;
shipping_address &lbrace;
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
&rbrace;
        &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u> 期待される結果 </u>:

ユーザーは注文情報を取得します。

<u> 実際の結果 </u>:

ユーザーに次のエラーが表示されます。*&quot;message&quot;: &quot;Internal server error&quot;,*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
