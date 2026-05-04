---
title: ACSD-63329:REST APIで製品を作成する際に、日付と時刻の属性が設定されない
description: REST APIを使用して製品を作成する際に、日付と時刻のフィールドにデフォルト値が設定されないAdobe Commerceの問題を修正するには、ACSD-63329 パッチを適用します。
feature: REST
Role: Admin, Developers
exl-id: d8e7917b-07a5-465b-944b-fd6168dea63c
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-63329:REST APIで製品を作成する際に、日付と時刻フィールドのデフォルト値が設定されない

ACSD-63329 パッチは、REST API `/rest/default/V1/products`を使用して新しい製品を作成する際に、日付と時刻のフィールドにデフォルト値が設定されなかった問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58がインストールされている場合に利用できます。 パッチ IDはACSD-63329です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

REST APIで製品を作成する場合、日付と時刻のフィールドにデフォルト値が設定されません：`/rest/default/V1/products`

<u>複製する手順</u>:

1. **[!UICONTROL Product]**&#x200B;属性を作成し、そのデフォルト値を`12/31/2020`に設定し、**[!UICONTROL Catalog Input Type for Store Owner]**&#x200B;を&#x200B;***[!UICONTROL Date]***&#x200B;または***[!UICONTROL Date and Time]***に設定します。
1. 別のテキストタイプ属性を作成し、デフォルト値を&#x200B;***テスト値***&#x200B;に設定します。
1. `/rest/all/V1/products/`へのREST API POST リクエストを使用して新しい製品を作成します。

   ```json
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

1. 上記の属性に保存されている値を確認します。

<u>期待される結果</u>:

APIを使用して製品を作成する場合、デフォルト値は&#x200B;**[!UICONTROL Date/Datetime]** タイプの属性に保存する必要があります。

<u>実際の結果</u>:

デフォルト値は&#x200B;**[!UICONTROL Text]**&#x200B;属性に保存されますが、**[!UICONTROL Date type]**&#x200B;属性には保存されません。 **[!UICONTROL Date]**&#x200B;属性の値が空です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
