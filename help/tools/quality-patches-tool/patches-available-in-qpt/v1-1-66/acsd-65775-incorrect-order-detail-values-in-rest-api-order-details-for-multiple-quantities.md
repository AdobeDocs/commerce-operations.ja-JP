---
title: ACSD-65775：複数の量のREST API順序の詳細で、「base_row_total」と「row_total」の値が正しくありません
description: ACSD-65775 パッチを適用して、同じ項目の複数の数量が注文されたときにREST APIの注文の詳細が誤った「base_row_total」値と「row_total」値を返すAdobe Commerceの問題を修正します。
feature: REST
role: Admin, Developer
type: Troubleshooting
exl-id: c2a8f4ef-3998-4e73-af9e-69b17a10d684
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-65775：複数の量のREST API順序の詳細で`base_row_total`と`row_total`の値が正しくありません

ACSD-65775 パッチは、同じ項目の複数の数量が注文されたときに、REST APIの注文の詳細が誤った`base_row_total`値と`row_total`値を返す問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66がインストールされている場合に利用できます。 パッチ IDはACSD-65775です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

注文の詳細REST API応答の`base_row_total`と`row_total`は、同じ項目の複数の数量を注文した場合の合計価格ではなく、単価を表示します。

<u>複製する手順</u>:

1. シンプルな商品を2つ作成しましょう。simple1は10 ドル、simple2は15 ドルです。
1. 新しい顧客アカウントを作成します。
1. 数量2の買い物かごにsimple1を追加し、数量3のsimple2を追加します。
1. 顧客アカウントを使用して注文します。
1. 次のペイロードを使用して`/rest/V1/integration/admin/token`にPOST リクエストを送信して、管理トークンを取得します。

   ```json
   {
     "username": "admin",
     "password": "password"
   }
   ```

1. GET リクエストを使用して注文の詳細を`/rest/default/V1/orders/1`に取得します。

<u>期待される結果</u>:

`base_row_total`と`row_total`は、数量に品目価格を掛けた合計価格を反映する必要があります（例：simple1の場合は2 × $10 = $20）。

<u>実際の結果</u>:

`base_row_total`と`row_total`は、単価のみを返します（例：$20ではなくsimple1の場合は$10）。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
