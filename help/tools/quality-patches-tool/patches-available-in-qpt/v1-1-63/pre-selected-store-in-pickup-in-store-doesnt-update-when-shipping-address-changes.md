---
title: ACSD-64753：配送先住所が変更された場合、実店舗での受け取り時に選択した実店舗が更新されない
description: ACSD-64753 パッチを適用して、選択したストアのサービス半径の外側に新しい配送先住所が入力されたときに、事前に選択したストアが更新されなかったAdobe Commerceの問題を修正します。
feature: Inventory
role: Admin, Developer
exl-id: 4efc99d6-88a3-43f9-88d4-dedb9d8a269e
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# ACSD-64753：配送先住所の変更時に「実店舗での受け取り」で選択した店舗が更新されない

ACSD-64753 パッチは、選択したストアのサービス半径の外側に新しい配送先住所が入力されたときに、事前に選択したストアが更新されなかった問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63がインストールされている場合に利用できます。 パッチ IDはACSD-64753です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

選択したストアのサービス半径の外側に新しい配送先住所が入力された場合、選択したストアは更新されませんでした。

<u>複製する手順</u>:

1. **[!UICONTROL In-Store Delivery]**&#x200B;を有効にするには、**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**&#x200B;に移動します。
1. [!DNL Google Distance Provider]に有効な[!DNL Google] API キーを指定してください。 これを行うには、**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**&#x200B;に移動します。
1. 新しいソース （**[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]**）を追加し、次の値を設定します。
   * **[!UICONTROL Latitude]**: *-41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *はい*
   * **[!UICONTROL Country United]**: *状態*
   * **[!UICONTROL State]**: *イリノイ州*
   * **[!UICONTROL City]**: *キャロル ストリーム*
   * **[!UICONTROL Postcode]**: *60188*
1. 新しい在庫（**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** > **[!UICONTROL Add New Stock]**）を追加し、新しいソースとメイン web サイトをそれに割り当てます。
1. 任意の商品を編集し、新しいSourceに商品を割り当てます（在庫あり、数量> *0*）。
1. 再インデックスが完了するまで待ちます。
1. ストアフロントで、新しい顧客を作成し、カリフォルニアの住所をデフォルトの請求および配送として追加します。
1. デフォルト以外のイリノイ州のアドレスをこの顧客に追加します。
1. 商品をカートに追加し、チェックアウトに進みます。
1. カリフォルニアの配送先住所を選択したままにして、**[!UICONTROL Pick in Store]**&#x200B;の配送方法を選択します。 **[!UICONTROL Next]**&#x200B;をクリックします。

<u>期待される結果</u>:

カリフォルニア州の住所が最大検索半径（200 km）を超えているため、イリノイ州のSourceはお客様が利用できないようになっています。

<u>実際の結果</u>:

イリノイ州のソースを選択し、チェックアウトに進むことができます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
