---
title: 'ACSD-62428: カタログ検索インデックスのストックステータスエラー'
description: ACSD-62428 パッチを適用して、SKUが検索可能な属性ではない場合に、カタログ検索インデックスの「is_out_of_stock」値が誤って設定される問題を修正します。
feature: Inventory, Catalog Management
role: Admin, Developer
exl-id: 4b9d7e4c-f522-4d75-8fc9-dcf14287d02a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%
---
# ACSD-62428: カタログ検索インデックスのストックステータスエラー

ACSD-62428 パッチでは、SKU属性が検索可能として設定されていない場合に、カタログ検索インデックスの`is_out_of_stock`値が正しくない値に設定される問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56で利用できます。 パッチ IDはACSD-62428です。 この問題は、Adobe Commerce 2.4.8で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カタログ検索インデックスの`is_out_of_stock`値は、SKUが検索可能な属性として設定されていない場合に誤った値に設定され、在庫表現が不正確になります。

<u>複製する手順</u>:

1. カスタム [!UICONTROL Source]とカスタム [!UICONTROL Stock]を作成します。
1. 3つのシンプルな商品を作成し、その在庫をカスタム [!UICONTROL Source]に割り当てます。 これらの製品をカテゴリに割り当てます。
1. レプリケーションを容易にするために&#x200B;*[!UICONTROL Inventory (MSI) Indexer]*&#x200B;を&#x200B;*[!UICONTROL Update on Save]*&#x200B;に設定します。
1. *[!UICONTROL Source Item Status]*&#x200B;を&#x200B;*[!UICONTROL In Stock]*&#x200B;に設定し、*[!UICONTROL Quantity]*&#x200B;を割り当てます。
1. 製品を保存します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;に移動し、**[!UICONTROL SKU]**&#x200B;属性を開きます。
1. *[!UICONTROL Use In]*&#x200B;を&#x200B;*[!UICONTROL No]*&#x200B;に設定します。
1. 製品数量を変更します（0に設定されていないことを確認してください）。
1. 製品を保存します。

<u>期待される結果</u>:

`is_out_of_stock`値は、SKUが検索可能な属性でない場合でも、商品の在庫状況を正確に反映します。

<u>実際の結果</u>:

`is_out_of_stock`値が1に誤って設定され、SKU属性がインデックス付きデータに含まれていません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
