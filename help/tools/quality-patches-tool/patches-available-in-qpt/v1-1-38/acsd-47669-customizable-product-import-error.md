---
title: ACSD-47669：カスタマイズ可能なオプションを含む製品をインポートする際に内部サーバーエラーが発生する
description: カスタマイズ可能なオプションを使用して製品を読み込む際に内部サーバーエラーが発生するAdobe Commerceの問題を修正するには、ACSD-47669 パッチを適用します。
feature: Products
role: Admin, Developer
exl-id: e1a3b3b4-0392-4325-9766-a83276c1a593
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-47669：カスタマイズ可能なオプションを含む製品をインポートする際に内部サーバーエラーが発生する

ACSD-47669 パッチは、製品のインポート中に内部サーバーエラーが発生する問題を修正し、カスタマイズ可能なオプションを提供します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.38がインストールされている場合に利用できます。 パッチ IDはACSD-47669です。 この問題は、Adobe Commerce 2.4.6で既に修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カスタマイズ可能なオプションを含む製品を読み込むと、内部サーバーエラーが発生します。

<u>複製する手順</u>:

1. 追加のストアビューを作成する。 en、UKなど、2つのストアビューがあることを確認します。
1. 2つのシンプルな製品（例：prod1とprod2）を作成します。
1. 各ストアビューと&#x200B;**すべてのストアビュー** スコープの両方の製品のカスタムオプションを追加するcsv ファイルを準備します。 このcsv ファイルを読み込みます。
1. 2つのレコードを含む別のcsv ファイルを準備します。 最初のレコードは、英国のストアビューのスコープに特化した「prod1」のカスタムオプションを更新し、2番目のレコードは、**すべてのストアビュー**&#x200B;のスコープの「prod2」のカスタムオプションを更新する必要があります。 この2番目のcsv ファイルを読み込みます。

<u>期待される結果</u>:

オプションはエラーなくカスタマイズできるはずです。

<u>実際の結果</u>:

整合性制約の違反エラーが発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
