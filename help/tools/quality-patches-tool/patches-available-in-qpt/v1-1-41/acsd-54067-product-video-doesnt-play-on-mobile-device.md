---
title: ACSD-54067：製品ビデオがモバイルデバイスで再生されない
description: モバイルデバイスで製品ビデオが再生されないAdobe Commerceの問題を修正するには、ACSD-54067 パッチを適用します。
feature: Media, Products
role: Admin, Developer
exl-id: 023e7cf7-c344-4e86-850d-741b85df87a9
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 2%

---

# ACSD-54067：製品ビデオがモバイルデバイスで再生されない

ACSD-54067 パッチは、モバイルデバイスで製品ビデオが再生されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.41がインストールされている場合に利用できます。 パッチ IDはACSD-54067です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品の動画がモバイルデバイスでは再生されない。

<u>複製する手順</u>:

1. Adobe Commerceをインストールします。
1. コマンドを実行します。
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. **[!UICONTROL Admin product list]** ページに移動し、*[!UICONTROL SKU product_dynamic_120]*&#x200B;で絞り込みます。
1. 製品ページを開き、**[!UICONTROL Images and Videos]**/ビデオを追加/URLを入力：https://vimeo.com/347119375に移動して保存します。
1. ストアフロントに移動し、*[!UICONTROL product_dynamic_120]*&#x200B;の製品ページを開きます。
1. ブラウザーを&#x200B;*モバイルデバイス*&#x200B;に設定し、幅を&#x200B;*320px*&#x200B;にして更新します。
1. ギャラリースライダーで、ビデオを選択し、クリックして再生します。

<u>期待される結果</u>:

製品のビデオが再生されます。

<u>実際の結果</u>:

製品動画が再生されない。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
