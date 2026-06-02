---
title: ACSD-62758：設定可能な製品ページでのビデオレンダリングの問題を解決
description: ACSD-62758 パッチを適用して、設定可能な商品詳細ページの商品動画が、URLに選択済みのスウォッチオプションが含まれている場合に正しくレンダリングされないAdobe Commerceの問題を修正します。
feature: Catalog Management
role: Admin, Developer
exl-id: 084b497d-4471-4458-bc1d-2a452bfe2662
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# ACSD-62758：設定可能な製品ページでのビデオレンダリングの問題を解決

ACSD-62758 パッチは、設定可能な製品詳細ページの製品ビデオが、URLに事前選択されたスウォッチオプションが含まれている場合に正しくレンダリングされない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-62758です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

URLに事前に選択されたスウォッチオプションが含まれている場合、設定可能な製品詳細ページで製品ビデオが正しくレンダリングされず、その結果、ビデオではなく静止画像が表示されます。

<u>複製する手順</u>:

1. [!UICONTROL Stores] > [!UICONTROL Attributes] > [!UICONTROL Product]に移動します。
1. **[!UICONTROL Color]**&#x200B;属性を選択して編集します。
1. 次の設定を更新します。
   1. [!UICONTROL Catalog Input Type for Store Owner]を[!UICONTROL Visual Swatch]に設定します。
   1. **[!UICONTROL Update Product Preview Image]**&#x200B;を&#x200B;**[!UICONTROL Yes]**&#x200B;に設定します。
1. この属性に対していくつかのオプションを作成します。
1. **[!UICONTROL Color]**&#x200B;属性を使用して、新しいカテゴリを作成し、新しい設定可能な製品を追加します。
1. 親商品に1つのランダム画像を追加します。
1. 新しく作成した設定可能な子製品を編集し、メディアギャラリーにビデオを追加します。
   1. **[!UICONTROL Add Video]**&#x200B;をクリックし、テスト ビデオ URL https://vimeo.com/12860646を使用します。
1. 商品を保存し、キャッシュをクリアして、ストアのインデックスを再作成します。
1. 新しく作成した商品をストアフロントで開き、スウォッチオプションのいずれかを選択して、「プレーヤー」ボタンが表示された状態でビデオが正しく読み込まれることを確認します。
1. ビデオが期待どおりに読み込まれ、「プレーヤー」ボタンが表示されます。
1. 次に、スウォッチオプションのいずれかを右クリックし、**[!UICONTROL Inspect]**&#x200B;を選択して、属性IDとオプション IDを見つけます。 製品URLをコピーし、その末尾に以下を追加します：`www.product-url.com/producit-test#attribute_id=option_id`。 これにより、スウォッチ オプションが事前選択されます。 更新されたURLを新しいウィンドウで開きます。

<u>期待される結果</u>:

スウォッチオプションを手動で選択した場合と同様に、ビデオは正しく読み込まれます。

<u>実際の結果</u>:

ビデオの代わりに静止画像が表示されます。 コンソールエラーがログに記録され、ビデオ初期化の失敗を示します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。

