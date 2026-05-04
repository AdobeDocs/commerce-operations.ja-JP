---
title: ACSD-58131:0 バイトの画像ファイルが原因で、古いメディアギャラリーが画像を読み込めない
description: ディレクトリに0 バイトの画像が存在する場合に古いメディアギャラリーが画像をレンダリングできないAdobe Commerceの問題を修正するには、ACSD-58131 パッチを適用します。
feature: Media
role: Admin, Developer
type: Troubleshooting
exl-id: 8fdca43d-b79f-4036-8694-de6fa1417a52
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-58131:0 バイトの画像ファイルが原因で、古いメディアギャラリーが画像を読み込めない

ACSD-58131 パッチは、0 バイトの画像がディレクトリに存在する場合に、古いメディアギャラリーが画像をレンダリングできない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68がインストールされている場合に利用できます。 パッチ IDはACSD-58131です。 この問題は、Adobe Commerce 2.5.0で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

0 バイトの画像をメディアギャラリーディレクトリに配置すると、古いメディアギャラリーは画像をレンダリングできません。 更新されたシステムは、無効な0 バイトファイルをスキップし、期待どおりに有効な画像を表示し、無効なファイルごとに警告を記録するようになりました。

```text
[2024-05-02T14:00:39.616459+00:00] report.WARNING: The image empty2.jpg is invalid and cannot be displayed in the gallery. [] []
```

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]**&#x200B;に移動します。
1. **[!UICONTROL Enable Old Media Gallery]**&#x200B;を&#x200B;*はい*&#x200B;に設定します。
1. `pub/media/wysiwyg` ディレクトリにいくつかの画像を配置します。
1. `touch pub/media/wysiwyg/empty_image.png`を使用して、同じディレクトリに0 バイトの画像を作成します。
1. 任意のコンテンツ（例：CMS ブロック）の下にPage Builderを使用して、`wysiwyg` ディレクトリから画像を追加します。
   1. 新しいブロックを作成します。 **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Blocks]**&#x200B;に移動し、**[!UICONTROL Add New Block]**&#x200B;をクリックします。
   1. ページビルダーを使用してコンテンツセクションを編集します。
   1. **[!UICONTROL Layout]**&#x200B;の下で、新しい&#x200B;**[!UICONTROL Row]**&#x200B;をステージにドラッグします。
   1. **[!UICONTROL Media]**&#x200B;を展開し、**[!UICONTROL Image]** プレースホルダーを行にドラッグします。
   1. **[!UICONTROL Select from Gallery]**&#x200B;をクリックします。
   1. デフォルトで選択されていない場合は、`wysiwyg` ディレクトリを選択します。

<u>期待される結果</u>:

0 バイトの画像（またはその他のファイル）が存在する場合でも、メディアギャラリーは機能し続けます。

<u>実際の結果</u>:

`var/log/system.log`に重大なエラーが記録されたため、メディアギャラリーが`wysiwyg` ディレクトリから画像を読み込めません。

```text
[2024-03-22T05:00:55.100934+00:00] report.CRITICAL: Exception: Notice: getimagesizefromstring(): Error reading from ! in /app/project/vendor/magento/module-cms/Model/Wysiwyg/Images/Storage.php on line 426 in /app/project/vendor/magento/framework/App/ErrorHandler.php:62
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
