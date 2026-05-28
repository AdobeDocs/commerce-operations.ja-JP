---
title: 'ACSD-62951: REST API経由で送信された[!UICONTROL Credit Memo]通のメールの欠落アイテムと合計を修正します'
description: ACSD-62951 パッチを適用して、注文項目と合計を含めずに[!UICONTROL Credit Memo]電子メールが送信されるAdobe Commerceの問題を修正します。
feature: REST
role: Admin, Developer
exl-id: e0c6d4c1-ecaf-46e7-af2d-05a148970d71
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-62951: REST API経由で送信された&#x200B;*[!UICONTROL Credit Memo]*&#x200B;通のメールの欠落アイテムと合計を修正します

ACSD-62951 パッチは、注文項目と合計を含めずに[!UICONTROL Credit Memo]電子メールが送信される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-62951です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p10

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

REST API `POST V1/order/:orderId/refund`を介してクレジットメモを作成したときに送信される&#x200B;*[!UICONTROL Credit Memo]*&#x200B;電子メールには、注文項目と合計が含まれていません。

<u>複製する手順</u>:

1. 任意の商品で注文を作成します。
1. 配送および請求書の発行： 請求書の電子メールが送信され、製品の詳細が含まれていることを確認します。
1. API クライアントを使用して管理トークンを生成します。
1. トークンを使用して、REST APIを介してクレジットメモを作成します。
   1. エンドポイント：`POST V1/order/:orderId/refund`
   1. リクエストペイロード：

      ```json
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

<u>期待される結果</u>:

*[!UICONTROL Credit Memo]*&#x200B;の電子メールには、返金済みの項目と合計が含まれている必要があります

<u>実際の結果</u>:

*[!UICONTROL Credit Memo]*&#x200B;の電子メールに項目または合計が含まれていないため、情報が不完全です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
