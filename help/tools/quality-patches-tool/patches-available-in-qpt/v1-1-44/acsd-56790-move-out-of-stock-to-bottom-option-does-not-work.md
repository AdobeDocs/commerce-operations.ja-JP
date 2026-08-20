---
title: 'ACSD-56790: **[!UICONTROL move out of stock to bottom]** オプションは、 [!DNL Visual Merchandiser]内の商品を並べ替える際に機能しません'
description: Visual Merchandiserで商品を並べ替える際に、「在庫切れ」オプションが機能しないAdobe Commerceの問題を修正するには、ACSD-56790 パッチを適用します。
feature: Products, Categories
role: Admin, Developer
exl-id: a5e5f208-793d-45a5-a000-f8ff1c31d049
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# ACSD-56790: **[!UICONTROL move out of stock to bottom]** オプションは、[!DNL Visual Merchandiser]で製品を並べ替える際に機能しません

ACSD-56790 パッチは、[!DNL Visual Merchandiser]内の商品を並べ替える際に「在庫切れから一番下へ」オプションが機能しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.44がインストールされている場合に利用できます。 パッチ IDはACSD-56790です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL move out of stock to bottom]** オプションは、[!DNL Visual Merchandiser]内の商品を並べ替える際に機能しません

<u>複製する手順</u>:

1. Adobe Commerceをインストールします。
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;に移動し、次の属性を作成します。
1. 新しいweb サイトを作成します：**非メイン**。
1. この新しいweb サイトに&#x200B;**Non-main Store**&#x200B;を作成します。
1. 2つのストアを作成します。

   * 最初に&#x200B;**メイン web サイト ストア**&#x200B;にアクセスします。
   * **非メインストア**&#x200B;の2番目。

1. 2つのソースを作成します。
   * レター：
   * データを。

1. 2つのストックを作成します。
   * 最初のメイン – 販売チャネル：メイン Web サイト – 割り当てられたソース：レター。
   * 2番目の非メイン – 販売チャネル：非メイン – 割り当てられたソース：数値。

1. 両方のweb サイトで3つのシンプルな商品を作成し、すべてデフォルトカテゴリに配置し、両方のソースに割り当てます。

   * ProductA - Qty *10* in Letters, Qty *0* in Numbers.
   * Product1 - Qty *0* in Letters, Qty *10* in Numbers.
   * ProductA1 - Qty *10* in Letters, Qty *10* in Numbers.

1. **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**&#x200B;に移動し、**[!UICONTROL Default category]**&#x200B;を選択します。
1. 範囲を&#x200B;**First**&#x200B;に変更します。
1. 「カテゴリ」セクションの「製品」を展開します。
1. 並べ替え順序を&#x200B;**[!UICONTROL move out of stock to bottom]**&#x200B;として選択します

<u>期待される結果</u>:

**在庫切れ**&#x200B;商品の商品リストが一番下に移動しました。

<u>実際の結果</u>:

製品の読み込みに失敗しました。 ページが管理者ダッシュボードにリダイレクトされ、エラーメッセージが表示されます：`Invalid security or form key. Please refresh the page`

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
