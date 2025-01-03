---
title: ACSD-62758：設定可能な製品ページでのビデオレンダリングの問題を解決
description: ACSD-62758 パッチを適用すると、Adobe Commerceの問題を修正できます。この問題では、事前に選択されたスウォッチオプションが URL に含まれている場合、設定可能な製品詳細ページの製品ビデオが正しくレンダリングされません。
feature: Catalog Management
role: Admin, Developer
source-git-commit: 313709361ee86e39b89c416f71a92b078318f4fb
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# ACSD-62758：設定可能な製品ページでのビデオレンダリングの問題を解決

ACSD-62758 パッチでは、URL に事前に選択されたスウォッチオプションが含まれている場合、設定可能な製品詳細ページの製品ビデオが正しくレンダリングされない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-62758 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

URL に事前に選択されたスウォッチオプションが含まれている場合、設定可能な製品詳細ページで製品ビデオが正しくレンダリングされず、ビデオの代わりに静的画像が表示されます。

<u> 再現手順 </u>:

1. [!UICONTROL Stores]/[!UICONTROL Attributes]/[!UICONTROL Product] に移動します。
1. **[!UICONTROL Color]** 属性を選択し、編集します。
1. 次の設定を更新します。
   1. [!UICONTROL Catalog Input Type for Store Owner] を [!UICONTROL Visual Swatch] に設定します。
   1. **[!UICONTROL Update Product Preview Image]** を **[!UICONTROL Yes]** に設定します。
1. この属性にはいくつかのオプションを作成します。
1. 新しいカテゴリを作成し、**[!UICONTROL Color]** 属性を使用して新しい設定可能な製品をそれに追加します。
1. 親製品に 1 つのランダム画像を追加します。
1. 新しく作成された設定可能な子製品を編集し、メディアギャラリーにビデオを追加します。
   1. 「**[!UICONTROL Add Video]**」をクリックし、テストビデオの URL （https://vimeo.com/12860646）を使用します。
1. 製品を保存し、キャッシュをクリアして、ストアを再インデックスします。
1. ストアフロントで新しく作成した製品を開き、スウォッチオプションの 1 つを選択し、プレーヤーボタンが表示された状態でビデオが正しく読み込まれていることを確認します。
1. ビデオが期待どおりに読み込まれ、プレーヤーボタンが表示されます。
1. 次に、スウォッチオプションの 1 つを右クリックし、「**[!UICONTROL Inspect]**」を選択して、属性 id およびオプション id を探します。 製品 URL をコピーし、その末尾に次の内容を追加します。`www.product-url.com/producit-test#attribute_id=option_id`。 スウォッチオプションが事前選択されます。 更新された URL を新しいウィンドウで開きます。

<u> 期待される結果 </u>:

スウォッチオプションを手動で選択した場合と同様に、ビデオは正しく読み込まれます。

<u> 実際の結果 </u>:

ビデオの代わりに静的画像が表示されます。 コンソールエラーがログに記録され、ビデオの初期化が失敗したことを示します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
