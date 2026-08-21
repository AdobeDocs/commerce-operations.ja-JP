---
title: ACSD-62056:MSIがインストールされている場合、設定可能な製品の画像アップロードが失敗する
description: ACSD-62056 パッチを適用して、MSIがインストールされている場合に設定可能な製品の画像が追加されないAdobe Commerceの問題を修正します。
feature: Products, Media
role: Admin, Developer
exl-id: bab8e617-d80c-4456-8ade-bdc6b4294d26
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# ACSD-62056:MSIがインストールされている場合、設定可能な製品の画像アップロードが失敗する

ACSD-62056 パッチは、MSIがインストールされている場合に設定可能な製品の画像が追加されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54がインストールされている場合に利用できます。 パッチ IDはACSD-62056です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!UICONTROL Inventory Management/MSI]が有効になっている設定可能な製品を編集する場合、画像を追加するオプションが機能しません。 これは、[!UICONTROL Apply a single set of images to all SKUs]と[!UICONTROL Apply unique images by attribute to each SKU]の両方のオプションに影響します。

<u>前提条件</u>:

[!UICONTROL Inventory Management/MSI]個のモジュールがインストールされ、有効になっています。

<u>複製する手順</u>:

1. 新しいソースを作成します。
1. 新しい在庫を作成し、新しいソースを割り当てます。
1. 設定可能な製品を編集します。
1. **[!UICONTROL Edit Configurations]** > **[!UICONTROL Next]** > **[!UICONTROL Next]**&#x200B;をクリックします。
1. 次のいずれかを選択して画像を追加します。

   * [!UICONTROL Apply a single set of images to all SKUs]
   * [!UICONTROL Apply unique images by attribute to each SKU]

<u>期待される結果</u>:

画像が追加されます。

<u>実際の結果</u>:

画像は追加されていません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
