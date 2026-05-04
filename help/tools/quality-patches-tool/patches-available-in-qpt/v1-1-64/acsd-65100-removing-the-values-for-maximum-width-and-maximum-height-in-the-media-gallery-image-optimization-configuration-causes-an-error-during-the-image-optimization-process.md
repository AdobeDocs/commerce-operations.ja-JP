---
title: 'ACSD-65100: [!UICONTROL Media Gallery Image Optimization]設定の[!UICONTROL Maximum Width]と[!UICONTROL Maximum Height]の値を削除すると、エラーが発生する'
description: ACSD-65100 パッチを適用して、[!UICONTROL Media Gallery Image Optimization]設定の[!UICONTROL Maximum Width]と[!UICONTROL Maximum Height]の値を削除すると、画像の最適化プロセス中にエラーが発生するAdobe Commerceの問題を修正します。
feature: Media
role: Admin, Developer
exl-id: 86197602-19a1-41c2-b129-1f695f303ce5
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-65100: [!UICONTROL Media Gallery Image Optimization]設定の[!UICONTROL Maximum Width]と[!UICONTROL Maximum Height]の値を削除すると、エラーが発生する

ACSD-65100 パッチは、**[!UICONTROL Media Gallery Image Optimization]**&#x200B;設定の&#x200B;**[!UICONTROL Maximum Width]**&#x200B;と&#x200B;**[!UICONTROL Maximum Height]**&#x200B;の値を削除すると、画像最適化プロセス中にエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64がインストールされている場合に利用できます。 パッチ IDはACSD-65100です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-P5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Maximum Width]**&#x200B;と&#x200B;**[!UICONTROL Maximum Height]**&#x200B;の値が&#x200B;**[!UICONTROL Media Gallery Image Optimization]**&#x200B;設定で削除されると、画像最適化プロセス中にエラーが発生します。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery Image Optimization]**&#x200B;に移動します。
1. **[!UICONTROL Maximum Width]**&#x200B;と&#x200B;**[!UICONTROL Maximum Height]**&#x200B;の値を削除します。
1. 設定キャッシュをクリーニングします。
1. **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**&#x200B;に移動します。
1. 任意のページを開いて編集します。
1. コンテンツ領域：
   1. **[!UICONTROL Add Layout]** > **[!UICONTROL Row]**&#x200B;を選択します。
   1. **[!UICONTROL Add Elements]** > **[!UICONTROL Text]**&#x200B;を選択します。
   1. WYSIWYG エディターで、**[!UICONTROL Add Image]**&#x200B;をクリックします。
   1. 画像をアップロードし、**[!UICONTROL Add Selected]**&#x200B;を選択します。
1. `var/log/exception.log` ファイルを確認してください。

<u>期待される結果</u>:

エラーがありません。

<u>実際の結果</u>:

次のようなエラーがログに記録されます。

```text
report.ERROR: InvalidArgumentException: Invalid image dimensions. in /var/www/html/vendor/magento/framework/Image/Adapter/AbstractAdapter.php:630
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
