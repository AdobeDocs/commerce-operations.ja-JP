---
title: ACSD-60326：お客様[!UICONTROL Returns] ステータスのGraphQL クエリでエラーが発生する
description: ACSD-60326 パッチを適用して、お客様[!UICONTROL Returns] ステータスのGraphQL クエリでエラーが発生したAdobe Commerceの問題を修正します。
feature: GraphQL, Returns, Customers
role: Admin, Developer
exl-id: 5cfd7e0d-8703-43a0-86d3-e69612347534
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# ACSD-60326：お客様[!UICONTROL Returns] ステータスのGraphQL クエリでエラーが発生する

ACSD-60326 パッチは、お客様[!UICONTROL Returns]のステータスに関するGraphQL クエリでエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51がインストールされている場合に利用できます。 パッチ IDはACSD-60326です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

お客様[!UICONTROL Returns]のステータスに対するGraphQL クエリでエラーが発生する。

<u>複製する手順</u>:

1. サンプルデータを使用して新しいインスタンスを初期化します。
1. *[!UICONTROL Admin]* サイドバーで、**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]**&#x200B;に移動し、**[!UICONTROL Enable RMA on Storefront]**&#x200B;を&#x200B;*はい*&#x200B;に設定します。
1. **[!UICONTROL Sales]** > **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]**&#x200B;に移動し、アドレスを入力します。
1. お客様`roni_cost@example.com`のパスワードを変更します。
1. 管理パネルにログインし、顧客`roni_cost@example.com`に対して次の製品を注文します。
   * *WSH12-32-Red*
   * *WSH12-32-Purple*
   * *WSH12-32-Green*
1. この注文の&#x200B;*[!UICONTROL Invoice]*&#x200B;と&#x200B;*[!UICONTROL Shipment]*&#x200B;を作成します。
1. **[!UICONTROL Create Returns]**&#x200B;を選択します。
1. **[!UICONTROL Return Items]** > **[!UICONTROL Add Items]**&#x200B;に移動し、次の操作を行います。
   * *WSH12-32-Red*&#x200B;と&#x200B;*WSH12-32-Purple*&#x200B;を選択
   * **[!UICONTROL Add Selected Products to returns]**&#x200B;をクリックします。
      * Set **[!UICONTROL Requested]** = *1*
      * **[!UICONTROL Return Reason]**&#x200B;を&#x200B;*サービス外*&#x200B;に設定
      * **[!UICONTROL Item Condition]**&#x200B;を&#x200B;*開封*&#x200B;に設定
      * **[!UICONTROL Resolution]**&#x200B;を&#x200B;*返金*&#x200B;に設定
   * **[!UICONTROL Submit Returns]**&#x200B;をクリックします。
1. **[!UICONTROL Returns]**&#x200B;を開き、左側の&#x200B;**[!UICONTROL Return Items]**&#x200B;を選択します。
   * 両方の製品に&#x200B;**[!UICONTROL Authorized]** = *1*&#x200B;を設定します
   * **[!UICONTROL Status]**&#x200B;を&#x200B;*WSH12-32-Purple*&#x200B;の&#x200B;*Authorized*&#x200B;として設定
   * **[!UICONTROL Status]**&#x200B;を&#x200B;*WSH12-32-Red*&#x200B;の&#x200B;*拒否*&#x200B;として設定
   * **[!UICONTROL Save]**&#x200B;をクリック
1. 同じ商品で新しい注文を作成します。
1. 同じ製品に&#x200B;*[!UICONTROL Invoice]*、*[!UICONTROL Shipment]*&#x200B;および&#x200B;*[!UICONTROL Returns]*&#x200B;を作成します。 両方を承認し、[!UICONTROL Returns] プロセスの最後まで続行します。
1. 次のGraphQL クエリを使用して、顧客トークンを生成します。

   ```GraphQL
    mutation {
     generateCustomerToken(email: "roni_cost@example.com", password: "password") {
       token
      }
   }
   ```

1. 受信したトークンで認証し、次のクエリを実行します。

   ```graphql
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

<u>期待される結果</u>:

クエリにエラーは表示されません。 2回目のリターンのステータスが&#x200B;*null*&#x200B;ではありません。

<u>実際の結果</u>:

クエリは、内部サーバーエラーを返します。

```json
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

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
