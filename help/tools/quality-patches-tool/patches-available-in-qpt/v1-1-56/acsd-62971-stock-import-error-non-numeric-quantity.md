---
title: ACSD-62971：在庫ソースを数値以外の数量値でインポートすると、数量が 0 に設定される
description: ACSD-62971 パッチを適用すると、「quantity」列に数値以外の値を含む在庫ソースを読み込むと、数量が 0 に設定されるAdobe Commerceの問題が修正されます。
feature: Data Import/Export, Inventory
role: Admin, Developer
exl-id: ece23153-4932-4ac5-b46e-49327a8e84a1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-62971：在庫ソースを数値以外の数量値でインポートすると、数量が 0 に設定される

ACSD-62971 パッチでは、「quantity」列に数値以外の値を含む在庫ソースをインポートすると、数量が 0 に設定される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 がインストールされている場合に使用できます。 パッチ ID は ACSD-62971 です。 この問題はAdobe Commerce 2.4.8 で修正される予定だったことに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**[!UICONTROL Quantity]** 列に数値以外の値がある在庫ソースを読み込むと、数量が 0 に設定される問題を修正しました。

<u> 再現手順 </u>:

1. 数量=100 の **[!UICONTROL Simple Product]** を作成
1. 数量が正しくない（「abc」）ファイルを使用して **[!UICONTROL Stock Sources]** インポートを実行します

   ```table
   source_code    sku    status    quantity
     default     simple    1         abc
   ```

1. インポート後の数量を確認します。

<u> 期待される結果 </u>:
データの読み込みの検証は失敗します。

<u> 実際の結果 </u>:
シンプルな商品の数量が 0 になり、商品は [!UICONTROL Out of Stock] のように更新されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
