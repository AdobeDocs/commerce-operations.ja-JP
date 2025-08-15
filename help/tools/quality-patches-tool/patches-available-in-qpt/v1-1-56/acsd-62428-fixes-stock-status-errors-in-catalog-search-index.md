---
title: ACSD-62428：カタログ検索インデックスの在庫ステータスエラー
description: SKU が検索可能な属性でない場合に、カタログ検索インデックスの「is_out_of_stock」値が正しく設定されない問題を修正するために、ACSD-62428 パッチを適用してください。
feature: Inventory, Catalog Management
role: Admin, Developer
exl-id: 4b9d7e4c-f522-4d75-8fc9-dcf14287d02a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62428：カタログ検索インデックスの在庫ステータスエラー

ACSD-62428 パッチでは、SKU 属性が検索可能 `is_out_of_stock` 設定されていない場合に、カタログ検索インデックスの値が誤った値に設定される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 で使用できます。パッチ ID は ACSD-62428 です。 この問題はAdobe Commerce 2.4.8 で修正される予定だったことに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

SKU が検索可能な属性として設定されていない場合、カタログ検索インデックスの `is_out_of_stock` の値が間違った値に設定され、在庫表示が不正確になります。

<u> 再現手順 </u>:

1. カスタム [!UICONTROL Source] とカスタム [!UICONTROL Stock] を作成します。
1. 3 つのシンプルな製品を作成し、その在庫をカスタム [!UICONTROL Source] に割り当てます。 これらの製品をカテゴリに割り当てます。
1. レプリケーションを容易にするために、*[!UICONTROL Inventory (MSI) Indexer]* を *[!UICONTROL Update on Save]* に設定します。
1. *[!UICONTROL Source Item Status]* を *[!UICONTROL In Stock]* に設定し、*[!UICONTROL Quantity]* を割り当てます。
1. 商品を保存します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Attributes]**/**[!UICONTROL Product]** に移動し、**[!UICONTROL SKU]** 属性を開きます。
1. *[!UICONTROL Use In]* を *[!UICONTROL No]* に設定します。
1. 製品数量を変更します（0 に設定していないことを確認します）。
1. 商品を保存します。

<u> 期待される結果 </u>:

`is_out_of_stock` 値は、SKU が検索可能な属性でない場合でも、製品の在庫ステータスを正確に反映します。

<u> 実際の結果 </u>:

`is_out_of_stock` の値が正しく 1 に設定されず、インデックス付きデータに SKU 属性がありません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
