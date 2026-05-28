---
title: MDVA-42950：製品ページでビデオが再生されない
description: MDVA-42950 パッチは、製品ページでビデオが再生されない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.12がインストールされている場合に利用できます。 パッチ IDはMDVA-42950です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Products
role: Admin
exl-id: 61c36dc5-0015-431d-84c1-0726bb310cd6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-42950：製品ページでビデオが再生されない

MDVA-42950 パッチは、製品ページでビデオが再生されない問題を解決します。 このパッチは、[品質パッチツール（QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12がインストールされている場合に使用できます。 パッチ IDはMDVA-42950です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品ページでビデオが再生されていません。

<u>複製する手順</u>:

1. **Stores** > **Configuration** > **Catalog** > **Product Video**&#x200B;に移動して、YouTube API キーを設定します。
1. YouTubeのビデオを、親が設定可能な任意のシンプルな製品に追加します。
1. コンテンツ > **デザイン** > **設定** > **HTML ヘッド** > **スクリプトおよびスタイルシート**&#x200B;にHEADER HTMLを追加します。

   ```HTML
   <script async="" src="https://www.youtube.com/iframe_api"></script>`
   ```

1. PDPに移動し、「製品設定」を選択して、写真とビデオのリストにビデオを表示します。
1. ビデオを再生してみてください。

<u>期待される結果</u>:

ビデオを再生しています。

<u>実際の結果</u>:

ビデオが再生されない。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
