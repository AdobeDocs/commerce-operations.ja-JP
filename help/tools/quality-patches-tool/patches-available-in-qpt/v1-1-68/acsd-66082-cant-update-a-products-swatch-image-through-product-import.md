---
title: ACSD-66082：製品の読み込みによって製品のスウォッチ画像を更新できない
description: swatch_image フィールドがEMPTY_VALUEに設定されたCSV ファイルをスウォッチ画像のセット解除にアップロードすると、インポートプロセスがエラーで失敗するAdobe Commerceの問題を修正するには、ACSD-66082 パッチを適用します。
feature: Products, Data Import/Export, Media
role: Admin, Developer
type: Troubleshooting
exl-id: 0bfff90e-5f1f-4c87-8a99-efc5bb0d814b
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-66082：製品の読み込みによって製品のスウォッチ画像を更新できない

ACSD-66082 パッチは、製品の読み込みによって製品のスウォッチ画像を更新できなかった問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68がインストールされている場合に利用できます。 パッチ IDはACSD-66082です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`swatch_image` フィールドが`EMPTY_VALUE`に設定されたCSV ファイルをアップロードしてスウォッチ画像の設定を解除すると、インポートプロセスがエラーで失敗します。

<u>複製する手順</u>:

1. シンプルな商品の作成。 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動します。 **[!UICONTROL Add Product]** ボタンの横にある下向き矢印をクリックし、**[!UICONTROL Simple Product]**&#x200B;を選択します。 **[!UICONTROL SKU]**&#x200B;を&#x200B;*ABC*&#x200B;に設定します。
1. *testing.png*&#x200B;という名前のPNG画像を`var/import/images/`にアップロードします。
1. 次の内容のCSV ファイルを作成します。

   ```text
   sku,swatch_image,swatch_image_label
   ABC,testing.png,testing
   ```

1. 次の設定を調整して、**[!UICONTROL System]** > **[!UICONTROL Import]**&#x200B;に移動し、ファイルを読み込みます。
   * **[!UICONTROL Entity type]**: *製品*
   * **[!UICONTROL Import Behavior]**: *追加/更新*
   * **[!UICONTROL Choose File]**&#x200B;をクリックして、前の手順で作成したCSV ファイルを選択して読み込みます。 読み込みが成功し、スウォッチが追加されます。
1. 次の内容でCSVを更新します。

   ```text
   sku,swatch_image,swatch_image_label
   ABC,__EMPTY__VALUE__,__EMPTY__VALUE__
   ```

1. 読み込みプロセスを繰り返します。

<u>期待される結果</u>:

スウォッチ画像の設定が解除されます。

<u>実際の結果</u>:

読み込みプロセスでエラーが発生する。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
