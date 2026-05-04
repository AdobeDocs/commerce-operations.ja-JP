---
title: 'ACSD-51846: [!DNL REST API]  ペイロードレベルとしての内部エラーが検証されません'
description: ' [!DNL REST API]  ペイロードのすべてのレベルが検証されないため、「内部エラー」が発生するAdobe Commerceの問題を修正するには、ACSD-51846 パッチを適用します。'
feature: REST
role: Developer
exl-id: 436b075c-d9df-4bf2-94a2-52f2e66e8a4c
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-51846: [!DNL REST API] ペイロードレベルが検証されていないため、内部エラーが発生する

ACSD-51846 パッチは、[!DNL REST API] ペイロードのすべてのレベルが検証されないため、「内部エラー」が発生する問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.36がインストールされている場合に利用できます。 パッチ IDはACSD-51846です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p2 - 2.4.5-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL REST API] ペイロードのすべてのレベルが検証されていないため、「内部エラー」が発生します。

<u>複製する手順</u>:

1. 顧客のカートに商品を追加する。
1. 間違った属性「_street._」を使用して[!DNL REST API] リクエストを`rest/V1/carts/mine/estimate-shipping-methods`に送信します 最後に点があります。

```json
 {
    "address": {
         "street.": [
             "\uc11c\uc6b8 \uac15\ubd81\uad6c \ud55c\ucc9c\ub85c166\uae38 2 (-\uc11c\uc6b8 \uac15\ubd81\uad6c \uc218\uc720\ub3d9 269-36)"
         ],
         "city": "pune",
         "region": null,
         "country_id": "IN",
         "postcode": "411015",
         "customer_id": "2",
         "firstname": "test",
         "lastname": "test",
         "middlename": null,
         "prefix": null,
         "suffix": null,
         "vat_id": null,
         "company": null,
         "telephone": "00000000000",
         "fax": null,
         "custom_attributes": []
     }
 }
```

<u>期待される結果</u>:

エンドポイントはパラメーターを検証し、特定のエラーメッセージを含む`400 status code`を返す必要があります。 例：

```text
report.CRITICAL: LogicException: Property "Street." does not have accessor method "getStreet." in class "Magento\Quote\Api\Data\AddressInterface". in vendor/magento/framework/Reflection/NameFinder.php:103
```

<u>実際の結果</u>:

エンドポイントは間違ったパラメーターを検証せず、`500 status code` エラーを返します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
