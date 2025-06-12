---
title: ACSD-60326：カスタマーエクスペリ [!UICONTROL Returns] ンスのステータスに関するGraphQL クエリでエラーが発生する
description: ACSD-60326 パッチを適用すると、カスタマーエクスペリ [!UICONTROL Returns] ンスステータスのGraphQL クエリでエラーが発生するAdobe Commerceの問題を修正できます。
feature: GraphQL, Returns, Customers
role: Admin, Developer
exl-id: 5cfd7e0d-8703-43a0-86d3-e69612347534
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# ACSD-60326：カスタマーエクスペリ [!UICONTROL Returns] ンスのステータスに関するGraphQL クエリでエラーが発生する

ACSD-60326 パッチでは、カスタマーエクスペリ [!UICONTROL Returns] ンスのステータスを求めるGraphQL クエリでエラーが発生する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 がインストールされている場合に使用できます。 パッチ ID は ACSD-60326 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

顧客 [!UICONTROL Returns] ーザーのステータスに関するGraphQL クエリでエラーが発生する。

<u> 再現手順 </u>:

1. サンプルデータを使用して新しいインスタンスを初期化します。
1. *[!UICONTROL Admin]* サイドバーで、**[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL RMA Settings]** に移動し、「**[!UICONTROL Enable RMA on Storefront]**」を *はい* に設定します。
1. **[!UICONTROL Sales]**/**[!UICONTROL Shipping Settings]**/**[!UICONTROL Origin]** に移動し、アドレスを入力します。
1. 顧客 `roni_cost@example.com` のパスワードを変更します。
1. 管理パネルにログインし、次の製品を使用して、顧客 `roni_cost@example.com` を注文します。
   * *WSH12-32-Red*
   * *WSH12-32-Purple*
   * *WSH12-32-Green*
1. この注文の *[!UICONTROL Invoice]* と *[!UICONTROL Shipment]* を作成します。
1. 「**[!UICONTROL Create Returns]**」を選択します。
1. **[!UICONTROL Return Items]**/**[!UICONTROL Add Items]** に移動し、次の操作を行います。
   * 「*WSH12-32-Red*」と「*WSH12-32-Purple*」を選択します。
   * **[!UICONTROL Add Selected Products to returns]** をクリックします。
      * Set **[!UICONTROL Requested]** = *1*
      * **[!UICONTROL Return Reason]** を *サービス停止* に設定
      * **[!UICONTROL Item Condition]** を *開封済み* に設定
      * **[!UICONTROL Resolution]** を *払戻* に設定します
   * 「**[!UICONTROL Submit Returns]**」をクリックします。
1. **[!UICONTROL Returns]** を開き、左側の「**[!UICONTROL Return Items]**」を選択します。
   * 両方の製品で **[!UICONTROL Authorized]** = *1* を設定します
   * *WSH12-32-Purple* に対して、**[!UICONTROL Status]** を *承認済み* に設定します
   * *WSH12-32-Red* の **[!UICONTROL Status]** を *拒否* に設定
   * **[!UICONTROL Save]** をクリック
1. 同じ商品で新しい注文を作成します。
1. 同じ製品の *[!UICONTROL Invoice]*、*[!UICONTROL Shipment]*、*[!UICONTROL Returns]* を作成します。 両方を承認して、[!UICONTROL Returns] のプロセスが終了するまで進みます。
1. 次のGraphQL クエリを使用してカスタマートークンを生成します。

   ```GraphQL
    mutation {
     generateCustomerToken(email: "roni_cost@example.com", password: "password") {
       token
      }
   }
   ```

1. 受信したトークンでを承認し、次のクエリを実行します。

   ```
   {
   customer {
       returns(pageSize: 20, currentPage: 1) {
        total_count
           items {
               uid
               number
               status
               created_at
           }
       }
   }
   }
   ```

<u> 期待される結果 </u>:

クエリにエラーは表示されません。 2 回目のリターンのステータスは *null* ではありません。

<u> 実際の結果 </u>:

クエリが内部サーバーエラーを返します。

```
    {
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 8,
                    "column": 5
                }
            ],
            "path": [
                "customer",
                "returns",
                "items",
                1,
                "status"
            ]
        }
    ],
    "data": {
        "customer": {
            "returns": {
                "total_count": 2,
                "items": [
                    {
                        "uid": "MQ==",
                        "number": "000000001",
                        "status": "PARTIALLY_AUTHORIZED",
                        "created_at": "2024-07-09 10:35:55"
                    },
                    {
                        "uid": "Mg==",
                        "number": "000000002",
                        "status": null,
                        "created_at": "2024-07-09 10:50:02"
                    }
                ]
            }
        }
    }
    } 
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
