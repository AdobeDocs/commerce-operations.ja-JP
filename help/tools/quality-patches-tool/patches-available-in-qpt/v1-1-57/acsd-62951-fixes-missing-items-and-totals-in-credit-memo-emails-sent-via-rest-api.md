---
title: ACSD-62951:REST API を介して送信されたメールに含まれ [!UICONTROL Credit Memo] 欠落している項目と合計を修正
description: ACSD-62951 パッチを適用すると、注文項目と合計を含めずに [!UICONTROL Credit Memo] メールが送信されるAdobe Commerceの問題を修正できます。
feature: REST
role: Admin, Developer
exl-id: e0c6d4c1-ecaf-46e7-af2d-05a148970d71
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-62951:REST API を介して送信されたメールに含まれ *[!UICONTROL Credit Memo]* 欠落している項目と合計を修正

ACSD-62951 パッチは、注文項目と合計を含めずに [!UICONTROL Credit Memo] メールが送信される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-62951 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p10

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

REST API でクレジットメモを作成する際に送信される *[!UICONTROL Credit Memo]* メール `POST V1/order/:orderId/refund`、注文項目と合計は含まれません。

<u> 再現手順 </u>:

1. 任意の製品で注文を作成します。
1. 注文を出荷して請求します。 請求書のメールが送信され、製品の詳細が含まれていることを確認します。
1. API クライアントを使用して管理トークンを生成します。
1. トークンを使用して、REST API を介してクレジットメモを作成します。
   1. エンドポイント：`POST V1/order/:orderId/refund`
   1. リクエストペイロード :

      ```
      {  
          "notify": true,  
          "items": [  
              {  
                  "order_item_id": 1,  
                  "qty": 1  
              }  
          ]  
      }  
      ```

<u> 期待される結果 </u>:

*[!UICONTROL Credit Memo]* のメールには、返金された項目と合計が含まれている必要があります

<u> 実際の結果 </u>:

*[!UICONTROL Credit Memo]* のメールには、項目や合計が含まれていないので、情報が不完全になります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
