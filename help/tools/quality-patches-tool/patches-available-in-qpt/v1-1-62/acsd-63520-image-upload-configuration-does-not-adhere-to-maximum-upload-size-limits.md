---
title: ACSD-63520：画像アップロード設定を通じてアップロードされた画像が、設定されたサイズ制限を超えている
description: ACSD-63520 パッチを適用して、Admin パネルのImages Upload Configurationを介してアップロードされた画像が、設定された最大アップロードサイズ制限に準拠しないAdobe Commerceの問題を修正します。
feature: Media, Products
role: Admin, Developer
exl-id: 5132bfa9-813a-4623-8e02-a8801f6396e8
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-63520: [!UICONTROL Image Upload Configuration]を通じてアップロードされた画像が、設定されたサイズ制限を超えています

ACSD-63520 パッチは、[!UICONTROL Images Upload Configuration]を通じてアップロードされた画像が、設定された最大アップロードサイズ制限に準拠しない問題を解決します。 これに対処するには、[!UICONTROL Admin] パネルで[!UICONTROL Images Upload Configuration]設定を構成します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62がインストールされている場合に利用できます。 パッチ IDはACSD-63520です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.7

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチが[!DNL Adobe Commerce] バージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!UICONTROL Admin] パネルの[!UICONTROL Images Upload Configuration]を通じてアップロードされた画像は、最大アップロードサイズ制限に準拠していません。

<u>複製する手順</u>:

1. **[!UICONTROL Admin]** パネルにログインします。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Images Upload Configuration]**&#x200B;に移動して、次を設定します。
   * クォリティ：100
   * フロントエンドのサイズ変更を有効にする：はい
   * 最大幅：800
   * 最大高さ：600
1. **[!UICONTROL Media Gallery Image Optimization]**&#x200B;を展開して設定：
   * 画像の最適化を有効にする：はい
   * 最大幅：1000
   * 最大高さ：1000
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Configurable Product]**&#x200B;に移動します。
   1. **[!UICONTROL Product Name]**、**[!UICONTROL SKU]**、**[!UICONTROL Price]**&#x200B;を追加します。
   1. **[!UICONTROL Create Configurations]**&#x200B;をクリックし、**[!UICONTROL Attributes]**&#x200B;を選択して、**[!UICONTROL Next]**&#x200B;をクリックします。
   1. サイズ （S、M、L、XL）を選択し、**[!UICONTROL Next]**&#x200B;をクリックします。
   1. **[!UICONTROL Images]**&#x200B;で、**[!UICONTROL Apply single set of images to all SKUs]**&#x200B;を選択します。
   1. 画像をアップロードします（最小1024x1024）。「**[!UICONTROL Next]**」をクリックします。
   1. **[!UICONTROL Generate Product]**&#x200B;をクリックします。
1. **[!UICONTROL Save]**&#x200B;をクリックします。

<u>期待される結果</u>:

画像は、設定されたアップロードサイズとサイズ変更の制限に従う必要があります。

<u>実際の結果</u>:

画像のサイズは変更されず、設定されたアップロードサイズの制限を超えています。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
