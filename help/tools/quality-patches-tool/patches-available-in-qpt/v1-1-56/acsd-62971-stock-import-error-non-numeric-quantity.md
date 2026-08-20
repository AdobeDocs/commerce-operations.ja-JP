---
title: ACSD-62971：数値以外の数量の値を使用してストックソースを読み込むと、数量が0に設定される
description: ACSD-62971 パッチを適用して、「数量」列に数値以外の値を持つストックソースを読み込むと、数量が0に設定されるAdobe Commerceの問題を修正します。
feature: Data Import/Export, Inventory
role: Admin, Developer
exl-id: ece23153-4932-4ac5-b46e-49327a8e84a1
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-62971：数値以外の数量の値を使用してストックソースを読み込むと、数量が0に設定される

ACSD-62971 パッチでは、「数量」列に数値のない値を持つ在庫ソースを読み込むと、数量が0に設定される問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56がインストールされている場合に利用できます。 パッチ IDはACSD-62971です。 この問題は、Adobe Commerce 2.4.8で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Quantity]**&#x200B;列に数値以外の値を持つ在庫ソースを読み込むと、数量が0に設定される問題を修正します。

<u>複製する手順</u>:

1. qty=100で&#x200B;**[!UICONTROL Simple Product]**&#x200B;を作成
1. 誤った数量（「abc」）を持つファイルを使用して、**[!UICONTROL Stock Sources]**&#x200B;の読み込みを行います

   ```table
   source_code    sku    status    quantity
     default     simple    1         abc
   ```

1. インポート後の数量を確認してください。

<u>期待される結果</u>:
データの読み込みの検証は失敗します。

<u>実際の結果</u>:
簡易商品の数量が0になり、商品が[!UICONTROL Out of Stock]として更新されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
