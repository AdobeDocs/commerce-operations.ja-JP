---
title: 'ACSD-66963: ''estimateTotals''の突然変異で、バーチャル製品の割引に対してnullが返される'
description: ACSD-66963 パッチを適用して、バーチャル商品のみのカートに割引コードが適用された場合、「estimateTotals」が割引の*null*を返すAdobe Commerceの問題を修正します。
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: b62e48f5-a9d6-456a-97e7-96f740d8e927
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# ACSD-66963: `estimateTotals`の突然変異が仮想製品の割引に対してnullを返します

ACSD-66963 パッチは、仮想製品のみを含むカートに割引コードが適用された場合、`estimateTotals`が&#x200B;*null*&#x200B;を割引として返す問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68がインストールされている場合に利用できます。 パッチ IDはACSD-66963です。 この問題は、Adobe Commerce 2.4.8で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

仮想商品のみを含むカートに割引コードが適用された場合、`estimateTotals`の変異は&#x200B;*null*&#x200B;を割引として返します。

<u>複製する手順</u>:

1. バーチャル商品のみを含むカートを作成します。
1. 割引コードを適用する：

   ```
   mutation {
     estimateTotals(
       input: {
         cart_id: "cart_id",
         address: {
           country_code: US,
           postcode: "78732",
           region: {
             region_code: "TX"
           }
         },
         shipping_method: {
           carrier_code: "{$shipping}",
           method_code: "{$shipping}"
         }
       }
     ) {
       cart {
         prices {
           discounts {
             amount {
               value
               currency
             }
             label
             coupon {
               code
             }
             applied_to
             type
           }
         }
       }
     }
   }
   ```

<u>期待される結果</u>:

バーチャル商品のみを含むカートには、割引情報が含まれています。

```
    {
      "data": {
        "estimateTotals": {
          "cart": {
            "prices": {
              "discounts": [
                {
                  "amount": {
                    "value": 100.5,
                    "currency": "USD"
                  },
                  "label": "A second discount code for testing",
                  "coupon": {
                    "code": "z3r0c00l"
                  },
                  "applied_to": "ITEM",
                  "type": null
                }
              ]
            }
          }
        }
      },
      "extensions": {}
    }
```

<u>実際の結果</u>:

仮想商品のみのカートの割引情報は&#x200B;*null*&#x200B;として返されます。

```
    {
      "data": {
        "estimateTotals": {
          "cart": {
            "prices": {
              "discounts": null
            }
          }
        }
      },
      "extensions": {}
    }
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
