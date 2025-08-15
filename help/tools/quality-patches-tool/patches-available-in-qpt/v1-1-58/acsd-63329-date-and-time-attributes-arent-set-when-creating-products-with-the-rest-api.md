---
title: ACSD-63329:REST API で商品を作成する際に、日時属性が設定されない
description: REST API で商品を作成する際に、日付と時間のフィールドにデフォルト値が設定されないAdobe Commerceの問題を修正するために、ACSD-63329 パッチを適用してください。
feature: REST
Role: Admin, Developers
exl-id: d8e7917b-07a5-465b-944b-fd6168dea63c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63329:REST API で商品を作成する際に、日付フィールドと時間フィールドのデフォルト値が設定されない

ACSD-63329 パッチでは、REST API を使用して新しい製品を作成する際に、日付と時間のフィールドにデフォルト値が設定されなかった問題を修正しています（例：`/rest/default/V1/products`）。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 がインストールされている場合に使用できます。 パッチ ID は ACSD-63329 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

REST API を使用して商品を作成する場合、日時フィールドにデフォルト値が設定されない：`/rest/default/V1/products`

<u> 再現手順 </u>:

1. **[!UICONTROL Product]** 属性を作成し、そのデフォルト値を `12/31/2020` に設定して、**[!UICONTROL Catalog Input Type for Store Owner]** を ***[!UICONTROL Date]*** または&#x200B;***[!UICONTROL Date and Time]***&#x200B;に設定します。
1. 別のテキストタイプ属性を作成し、デフォルト値を ***テスト値*** に設定します。
1. `/rest/all/V1/products/` への REST API POST リクエストを使用して、新しい製品を作成します。

   ```
       {
           "product": {
               "sku": "testsku2",
               "name": "Test Api Product 2",
               "attribute_set_id": 4,
               "price": 100,
               "status": 1,
               "visibility": 4,
               "type_id": "simple",
               "weight": 20,
               "extension_attributes": {
                   "website_ids": [
                       1
                   ]
               }
           }
       }
   ```

1. 上記の属性に保存された値を確認します。

<u> 期待される結果 </u>:

API を使用して製品を作成する場合は、デフォルト値を **[!UICONTROL Date/Datetime]** type 属性に保存する必要があります。

<u> 実際の結果 </u>:

**[!UICONTROL Text]** 属性のデフォルト値は保存されますが、**[!UICONTROL Date type]** 属性のデフォルト値は保存されません。 **[!UICONTROL Date]** 属性の値が空です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
