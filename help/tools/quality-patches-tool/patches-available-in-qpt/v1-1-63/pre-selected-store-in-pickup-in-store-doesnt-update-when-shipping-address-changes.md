---
title: ACSD-64753：配送先住所が変更された場合、店舗の集荷で事前に選択された店舗が更新されない
description: ACSD-64753 パッチを適用すると、選択したストアのサービス半径外に新しい配送先住所が入力された場合に、事前に選択したストアが更新されなかったAdobe Commerceの問題を修正できます。
feature: Inventory
role: Admin, Developer
exl-id: 4efc99d6-88a3-43f9-88d4-dedb9d8a269e
type: Troubleshooting
source-git-commit: 036c1b81d9ec8f55f002446a8ea6078c6f8014d9
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-64753:「Pickup in Store」で事前に選択されたストアが、配送先住所が変更されても更新されない

ACSD-64753 パッチは、選択したストアのサービス半径外に新しい配送先住所が入力された場合に、事前に選択したストアが更新されなかった問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 がインストールされている場合に使用できます。 パッチ ID は ACSD-64753 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

選択したストアのサービス半径外に新しい配送先住所が入力された場合、事前に選択したストアは更新されませんでした。

<u> 再現手順 </u>:

1. **[!UICONTROL In-Store Delivery]**/**[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Delivery Methods]** に移動して、**[!UICONTROL In-Store Delivery]** を有効にします。
1. [!DNL Google] に有効な [!DNL Google Distance Provider] API キーを指定してください。 これを行うには、**[!UICONTROL Stores]** / **[!UICONTROL Configuration]** / **[!UICONTROL Catalog]** / **[!UICONTROL Inventory]** / **[!UICONTROL Google Distance Provider]** に移動します。
1. 新しいソース（**[!UICONTROL Stores]**/**[!UICONTROL Sources]**/**[!UICONTROL Add New Source]**）を追加し、次の値を設定します。
   * **[!UICONTROL Latitude]**: *-41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *はい*
   * **[!UICONTROL Country United]**: *States*
   * **[!UICONTROL State]**: *イリノイ州*
   * **[!UICONTROL City]**: *Carol ストリーム*
   * **[!UICONTROL Postcode]**: *60188*
1. 新しい在庫（**[!UICONTROL Stores]**/**[!UICONTROL Inventory]**/**[!UICONTROL Stock]**/**[!UICONTROL Add New Stock]**）を追加し、新しいソースとメイン web サイトをそれに割り当てます。
1. 任意の商品を編集し、商品を新しいSourceに割り当てます。在庫あり、数量 > *0*。
1. 再インデックスが完了するまで待ちます。
1. ストアフロントで新しい顧客を作成し、カリフォルニア州の住所をデフォルトの請求および配送として追加します。
1. この顧客に別のデフォルト以外のイリノイ州の住所を追加します。
1. 商品を買い物かごに追加し、チェックアウトに進みます。
1. カリフォルニア州の配送先住所を選択したままにし、配送方法 **[!UICONTROL Pick in Store]** 選択します。 「**[!UICONTROL Next]**」をクリックします。

<u> 期待される結果 </u>:

カリフォルニア州の住所は検索半径の上限（200 km）外なので、イリノイ州のSourceはお客様が利用できないはずです。

<u> 実際の結果 </u>:

イリノイ州のソースを選択でき、お客様はチェックアウトに進むことができます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
