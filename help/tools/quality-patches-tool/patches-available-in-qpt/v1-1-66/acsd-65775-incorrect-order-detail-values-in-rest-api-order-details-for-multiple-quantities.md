---
title: ACSD-65775：複数の数量に対する REST API 注文詳細の「base_row_total」と「row_total」の値が正しくありません
description: ACSD-65775 パッチを適用すると、同じ商品が複数注文された場合に、REST API の注文詳細で誤った「base_row_total」と「row_total」の値が返されるAdobe Commerceの問題を修正できます。
feature: REST
role: Admin, Developer
type: Troubleshooting
exl-id: c2a8f4ef-3998-4e73-af9e-69b17a10d684
source-git-commit: ce5a136dd59c52d5fa5b555b3ee74fe14d7e53a4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-65775：複数の数量に対する REST API 注文の詳細の `base_row_total` と `row_total` の値が正しくない

ACSD-65775 パッチでは、同じ項目を複数個並べ替えた場合に、REST API の注文詳細で誤った `base_row_total` と `row_total` の値が返される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 がインストールされている場合に使用できます。 パッチ ID は ACSD-65775 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

注文詳細の REST API 応答の `base_row_total` と `row_total` には、同じ品目の複数の数量が注文された場合、合計価格ではなく単価が表示されます。

<u> 再現手順 </u>:

1. 2 つのシンプルな製品を作成します。10 ドルの価格の simple1 と 15 ドルの価格の simple2 です。
1. 新しい顧客アカウントを作成します。
1. simple1 を数量 2 の買い物かごに追加し、simple2 を数量 3 の買い物かごに追加します。
1. 顧客アカウントを使用して注文します。
1. 次のペイロードを持つ POST リクエストを `/rest/V1/integration/admin/token` に送信して、管理トークンを取得します。

   ```
   {
     "username": "admin",
     "password": "password"
   }
   ```

1. `/rest/default/V1/orders/1` へのGET リクエストを使用して、注文の詳細を取得します。

<u> 期待される結果 </u>:

`base_row_total` と `row_total` は、数量に品目価格を乗算して計算された合計価格を反映する必要があります（例：simple1 の場合、2×$10 = $20）。

<u> 実際の結果 </u>:

`base_row_total` と `row_total` は、単価のみを返します（例えば、simple1 の場合は$20 ではなく$10）。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
