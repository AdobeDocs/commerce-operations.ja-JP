---
title: ACSD-62056:MSI がインストールされている場合、設定可能な製品の画像アップロードに失敗する
description: ACSD-62056 パッチを適用すると、MSI がインストールされている場合に設定可能な商品の画像が追加されないAdobe Commerceの問題を修正できます。
feature: Products, Media
role: Admin, Developer
source-git-commit: 9c186e936492ebcab3903949f40d73745d2a28d3
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# ACSD-62056:MSI がインストールされている場合、設定可能な製品の画像アップロードに失敗する

ACSD-62056 パッチは、MSI がインストールされている場合に、設定可能な製品のイメージが追加されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 がインストールされている場合に使用できます。 パッチ ID は ACSD-62056 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!UICONTROL Inventory Management/MSI] を有効にして設定可能な製品を編集すると、画像を追加するオプションが機能しません。 これは、[!UICONTROL Apply a single set of images to all SKUs] オプションと [!UICONTROL Apply unique images by attribute to each SKU] オプションの両方に影響します。

<u> 前提条件 </u>:

[!UICONTROL Inventory Management/MSI] モジュールがインストールされ、有効になっています。

<u> 再現手順 </u>:

1. 新規ソースを作成します。
1. 新しい在庫を作成し、新しいソースを割り当てます。
1. 設定可能な商品を編集します。
1. **[!UICONTROL Edit Configurations]**/**[!UICONTROL Next]**/**[!UICONTROL Next]** をクリックします。
1. 次のいずれかを選択し、画像を追加します。

   * [!UICONTROL Apply a single set of images to all SKUs]
   * [!UICONTROL Apply unique images by attribute to each SKU]

<u> 期待される結果 </u>:

画像が追加されます。

<u> 実際の結果 </u>:

画像は追加されていません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
