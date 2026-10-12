---
title: ACSD-52095:CSVの書き出し中に在庫値の管理が間違っている
description: CSVの書き出し中に商品管理の在庫値が間違っているAdobe Commerceの問題を修正するには、ACSD-52095 パッチを適用します。
feature: Inventory, Products
role: Admin, Developer
exl-id: 1f8415aa-23c6-480a-b54d-37b2b2d3199a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '400'
ht-degree: 0%
---
# CSVの書き出し中にACSD-52095: [!UICONTROL Manage Stock]値が間違っています

ACSD-52095 パッチは、CSVの書き出し中に製品`manage_stock`値が間違っている問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35がインストールされている場合に利用できます。 パッチ IDはACSD-52095です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品の書き出し後に、CSV ファイルで`manage_stock`値が0に誤って設定されます。

<u>複製する手順</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]**&#x200B;に移動し、**[!UICONTROL Manage Stock]** = *[!UICONTROL No]*&#x200B;と設定します。
1. 新しい商品を作成して保存します。
1. **[!UICONTROL System]** > **[!UICONTROL Export]**&#x200B;に移動します。
1. *[!UICONTROL Entity Type]* = *[!UICONTROL Products]*&#x200B;を選択し、製品を書き出します。
1. 生成されたCSV ファイルを確認してください：`manage_stock` = 0、`use_config_manage_stock` = 1。
1. もう一度&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]**&#x200B;に移動し、**[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*&#x200B;と設定します。
1. **システム** > **書き出し**に移動します。
*[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*&#x200B;を選択します。
1. 生成されたCSV ファイルを確認してください：`manage_stock` = 0、`use_config_manage_stock` = 1。
1. 管理者で製品を開き、**[!UICONTROL Advanced Inventory]**&#x200B;に移動して&#x200B;**[!UICONTROL Manage Stock]**&#x200B;値を確認します。

<u>期待される結果</u>

製品に対して有効になっている場合、**[!UICONTROL Manage Stock]**&#x200B;の値は&#x200B;*1*&#x200B;です。

<u>実際の結果</u>

製品に対して有効になっている場合、**[!UICONTROL Manage Stock]**&#x200B;の値は&#x200B;*0*&#x200B;です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
