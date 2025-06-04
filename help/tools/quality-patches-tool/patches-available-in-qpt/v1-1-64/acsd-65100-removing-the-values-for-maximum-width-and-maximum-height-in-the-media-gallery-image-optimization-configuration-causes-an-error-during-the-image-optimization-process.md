---
title: ACSD-65100:[!UICONTROL Media Gallery Image Optimization] 設定で [!UICONTROL Maximum Width] と [!UICONTROL Maximum Height] の値を削除すると、エラーが発生する
description: '[!UICONTROL Media Gallery Image Optimization] 設定の [!UICONTROL Maximum Width] と [!UICONTROL Maximum Height] の値を削除すると、画像の最適化プロセス中にエラーが発生するAdobe Commerceの問題を修正するために、ACSD-65100 パッチを適用してください。'
feature: Media
role: Admin, Developer
source-git-commit: 97ffcd84b760962e1ad7290343f81860ca6568c7
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# ACSD-65100:[!UICONTROL Media Gallery Image Optimization] 設定で [!UICONTROL Maximum Width] と [!UICONTROL Maximum Height] の値を削除すると、エラーが発生する

ACSD-65100 パッチでは、**[!UICONTROL Media Gallery Image Optimization]** 設定の **[!UICONTROL Maximum Width]** と **[!UICONTROL Maximum Height]** の値を削除すると、画像の最適化プロセス中にエラーが発生する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 がインストールされている場合に使用できます。 パッチ ID は ACSD-65100 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-P5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**[!UICONTROL Media Gallery Image Optimization]** 設定で **[!UICONTROL Maximum Width]** と **[!UICONTROL Maximum Height]** の値が削除されると、画像の最適化プロセス中にエラーが発生します。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/*[!UICONTROL Settings]*/**[!UICONTROL Configuration]**/**[!UICONTROL Advanced]**/**[!UICONTROL System]**/**[!UICONTROL Media Gallery Image Optimization]** に移動します。
1. **[!UICONTROL Maximum Width]** と **[!UICONTROL Maximum Height]** の値を削除します。
1. 設定キャッシュをクリーンアップします。
1. **[!UICONTROL Content]**/*[!UICONTROL Elements]*/**[!UICONTROL Pages]** に移動します。
1. 任意のページを編集用に開きます。
1. コンテンツ領域で以下を行います。
   1. **[!UICONTROL Add Layout]**/**[!UICONTROL Row]** を選択します。
   1. **[!UICONTROL Add Elements]**/**[!UICONTROL Text]** を選択します。
   1. WYSIWYG エディターで、「**[!UICONTROL Add Image]**」をクリックします。
   1. 画像をアップロードして選択 **[!UICONTROL Add Selected]** ます。
1. `var/log/exception.log` ファイルを確認します。

<u> 期待される結果 </u>:

エラーはありません。

<u> 実際の結果 </u>:

次のようなエラーがログに記録されます。

```
report.ERROR: InvalidArgumentException: Invalid image dimensions. in /var/www/html/vendor/magento/framework/Image/Adapter/AbstractAdapter.php:630
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
