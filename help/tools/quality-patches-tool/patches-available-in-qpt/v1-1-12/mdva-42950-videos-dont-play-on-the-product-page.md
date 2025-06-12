---
title: MDVA-42950：製品ページでビデオが再生されない
description: MDVA-42950 パッチを使用すると、製品ページでビデオが再生されない問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.12 がインストールされている場合に利用できます。 パッチ ID は MDVA-42950。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: Products
role: Admin
exl-id: 61c36dc5-0015-431d-84c1-0726bb310cd6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-42950：製品ページでビデオが再生されない

MDVA-42950 パッチを使用すると、製品ページでビデオが再生されない問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.12 がインストールされている場合に使用できます。 パッチ ID は MDVA-42950。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 ～ 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

製品ページでビデオが再生されない。

<u> 再現手順 </u>:

1. **Stores**/**Configuration**/**Catalog**/**Product Video** に移動して、YouTube API キーを設定します。
1. YouTubeのビデオを、親が設定可能な任意のシンプルな商品に追加します。
1. コンテンツ / **デザイン** / **設定** / **HTML Head** / **スクリプトとスタイルシート** でヘッダーHTMLを追加します。

   ```HTML
   <script async="" src="https://www.youtube.com/iframe_api"></script>`
   ```

1. PDP に移動し、「製品設定」を選択して、写真とビデオのリストでビデオを表示します。
1. ビデオを再生してみます。

<u> 期待される結果 </u>:

ビデオが再生中です。

<u> 実際の結果 </u>:

ビデオが再生されない。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
