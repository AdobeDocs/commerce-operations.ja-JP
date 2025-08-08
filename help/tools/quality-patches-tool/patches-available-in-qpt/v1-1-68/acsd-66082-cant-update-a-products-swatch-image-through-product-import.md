---
title: ACSD-66082：製品の読み込みから製品のスウォッチ画像を更新できない
description: ACSD-66082 パッチを適用すると、swatch_image フィールドが EMPTY_VALUE に設定された CSV ファイルをアップロードしてスウォッチ画像の設定を解除すると、読み込みプロセスがエラーで失敗するAdobe Commerceの問題が修正されます。
feature: Products, Data Import/Export, Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: bdd15514c6b6ece6c7f33a41267357b4a24261f1
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# ACSD-66082：製品の読み込みから製品のスウォッチ画像を更新できない

ACSD-66082 パッチは、製品の読み込みを通じて製品のスウォッチ画像を更新できなかった問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 がインストールされている場合に使用できます。 パッチ ID は ACSD-66082 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`swatch_image` フィールドを `EMPTY_VALUE` に設定した CSV ファイルをアップロードしてスウォッチ画像の設定を解除すると、読み込みプロセスがエラーで失敗します。

<u> 再現手順 </u>:

1. シンプルな製品を作成します。 **[!UICONTROL Catalog]**/**[!UICONTROL Products]** に移動します。 「**[!UICONTROL Add Product]**」ボタンの横にある下矢印をクリックし、「**[!UICONTROL Simple Product]**」を選択します。 **[!UICONTROL SKU]** を *ABC* に設定します。
1. *testing.png* という名前の PNG 画像を `var/import/images/` にアップロードします。
1. 次の内容の CSV ファイルを作成します。

   ```
   sku,swatch_image,swatch_image_label
   ABC,testing.png,testing
   ```

1. **[!UICONTROL System]** / **[!UICONTROL Import]** に移動し、次の設定を調整してファイルを読み込みます。
   * **[!UICONTROL Entity type]**: *Products*
   * **[!UICONTROL Import Behavior]**: *追加/更新*
   * 「**[!UICONTROL Choose File]**」をクリックして、前の手順で作成した CSV ファイルを選択して読み込みます。 読み込みが正常に完了し、スウォッチが追加されます。
1. 次の内容で CSV を更新します。

   ```
   sku,swatch_image,swatch_image_label
   ABC,__EMPTY__VALUE__,__EMPTY__VALUE__
   ```

1. 読み込みプロセスを繰り返します。

<u> 期待される結果 </u>:

スウォッチ画像が未設定になります。

<u> 実際の結果 </u>:

読み込みプロセスでエラーがスローされる。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
