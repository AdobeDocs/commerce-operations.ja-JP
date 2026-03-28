---
title: ACSD-52095:CSVの書き出し中に在庫値の管理が間違っている
description: CSVの書き出し中に商品管理の在庫値が間違っているAdobe Commerceの問題を修正するには、ACSD-52095 パッチを適用します。
feature: Inventory, Products
role: Admin, Developer
exl-id: 1f8415aa-23c6-480a-b54d-37b2b2d3199a
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '366'
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

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [ [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
