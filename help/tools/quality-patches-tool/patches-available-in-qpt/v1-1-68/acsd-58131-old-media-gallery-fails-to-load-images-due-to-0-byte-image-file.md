---
title: ACSD-58131:0 バイトの画像ファイルが原因で、古いメディアギャラリーが画像の読み込みに失敗する
description: ACSD-58131 パッチを適用すると、ディレクトリに 0 バイトの画像が存在する場合に、古い Media Gallery で画像をレンダリングできないAdobe Commerceの問題を修正できます。
feature: Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: b09749a1e56ab6a7b613135ca252fd69757669d0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-58131:0 バイトの画像ファイルが原因で、古いメディアギャラリーが画像の読み込みに失敗する

ACSD-58131 パッチは、0 バイトの画像がディレクトリに存在する場合に、古いメディアギャラリーが画像のレンダリングに失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 がインストールされている場合に使用できます。 パッチ ID は ACSD-58131 です。 この問題はAdobe Commerce 2.5.0 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

0 バイトの画像がメディアギャラリーディレクトリに配置されると、古いメディアギャラリーは画像のレンダリングに失敗します。 更新されたシステムは、無効な 0 バイトのファイルをスキップし、有効な画像を期待どおりに表示して、無効な各ファイルに対して警告をログに記録するようになりました。

```
[2024-05-02T14:00:39.616459+00:00] report.WARNING: The image empty2.jpg is invalid and cannot be displayed in the gallery. [] []
```

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Advanced]**/**[!UICONTROL System]**/**[!UICONTROL Media Gallery]** に移動します。
1. **[!UICONTROL Enable Old Media Gallery]** を *はい* に設定します。
1. `pub/media/wysiwyg` ディレクトリにいくつかの画像を配置します。
1. `touch pub/media/wysiwyg/empty_image.png` を使用して、同じディレクトリに 0 バイトの画像を作成します。
1. ページビルダーを使用して、`wysiwyg` ディレクトリの画像を任意のコンテンツの下に追加します（例：CMS ブロック）。
   1. 新しいブロックを作成します。 **[!UICONTROL Content]**/*[!UICONTROL Elements]*/**[!UICONTROL Blocks]** に移動し、「**[!UICONTROL Add New Block]**」をクリックします。
   1. ページビルダーを使用して、「コンテンツ」セクションを編集します。
   1. 「**[!UICONTROL Layout]**」の下で、新しい **[!UICONTROL Row]** をステージにドラッグします。
   1. **[!UICONTROL Media]** を展開し、**[!UICONTROL Image]** プレースホルダーを行にドラッグします。
   1. 「**[!UICONTROL Select from Gallery]**」をクリックします。
   1. `wysiwyg` ディレクトリがデフォルトで選択されていない場合は、選択します。

<u> 期待される結果 </u>:

0 バイトの画像（またはその他のファイル）が存在する場合でも、メディアギャラリーは引き続き機能します。

<u> 実際の結果 </u>:

`wysiwyg` にログインした重大なエラーが原因で、`var/log/system.log` ディレクトリからの画像の読み込みに失敗しました。

```
[2024-03-22T05:00:55.100934+00:00] report.CRITICAL: Exception: Notice: getimagesizefromstring(): Error reading from ! in /app/project/vendor/magento/module-cms/Model/Wysiwyg/Images/Storage.php on line 426 in /app/project/vendor/magento/framework/App/ErrorHandler.php:62
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
