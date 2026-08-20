---
title: 'MDVA-43731: 「一致する最小条件」で値が追加された場合、検索類義語が機能しない'
description: MDVA-43731 パッチは、「一致する最小条件」に値が追加されたときに検索の類義語が機能しなくなる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.12がインストールされている場合に利用できます。 パッチ IDはMDVA-43731です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Cache, Marketing Tools, Search
role: Admin
exl-id: 1eada0cd-c0ab-4f0f-b6bf-7c10e1df07ce
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---

# MDVA-43731: 「一致する最小条件」で値が追加された場合、検索類義語が機能しない

MDVA-43731 パッチは、「一致する最小条件」に値が追加されたときに検索の類義語が機能しなくなる問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12がインストールされている場合に使用できます。 パッチ IDはMDVA-43731です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

「一致する最小条件」に値が追加されると、検索の類義語が機能しなくなります。

<u>複製する手順</u>:

1. サンプルデータを使用してAdobe Commerceをインストールします。
1. Elasticsearch7を検索エンジンとして設定します。
1. 「Jacket」という単語を検索します。 製品リストが表示されます。
1. パラメーター[4&lt;60%]を&#x200B;**設定** > **カタログ** > **カタログ検索** > **一致する最小条件**&#x200B;に追加します。
1. Config Cacheをクリアし、再インデックスを作成します。
1. もう一度「ジャケット」という単語を検索し、製品のリストが表示されることに注意してください。
1. **マーケティング** > **SEOと検索** > **同義語の検索**&#x200B;に移動します。
1. ジャケット、bagtecs、express plusの類義語を追加して、検索の類義語を作成します。
1. 再インデックスを作成します。
1. 類義語のいずれかを使用して商品検索を行います。 例えば、ジャケット。

<u>期待される結果</u>:

検索結果では、以前と同じ商品リストが表示されます。

<u>実際の結果</u>:

検索結果に商品は表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
