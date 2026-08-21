---
title: MDVA-38799：ステージング更新を作成した後、ダウンロード可能な製品が保存されない
description: MDVA-38799 パッチは、ステージング更新を作成した後にダウンロード可能な製品が保存されない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.0がインストールされている場合に利用できます。 パッチ IDはMDVA-38799です。 この問題は、Adobe Commerce バージョン 2.4.3で修正されています。
feature: Products, Staging
role: Admin
exl-id: 0ae665a8-cda2-4340-91e7-5b9b969a6607
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# MDVA-38799：ステージング更新を作成した後、ダウンロード可能な製品が保存されない

MDVA-38799 パッチは、ステージング更新を作成した後にダウンロード可能な製品が保存されない問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.0がインストールされている場合に使用できます。 パッチ IDはMDVA-38799です。 この問題は、Adobe Commerce バージョン 2.4.3で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce on cloud infrastructure 2.4.1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0-2.4.2-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ステージング更新を作成した後、ダウンロード可能な製品は保存されません。 ユーザーにエラーメッセージが表示されます：*ダウンロード可能なサンプルが製品に関連していません。 リンクを確認して、もう一度やり直してください*。

<u>複製する手順</u>:

1. **カタログ** > **製品**&#x200B;に移動します。
1. 「製品を追加」の横にあるドロップダウンをクリックし、「ダウンロード可能な製品」を選択します。
   * 商品の名前、SKU、価格、数量を入力します。
1. ダウンロード可能な情報ページまでスクロールします。
1. 「サンプル」で、「**リンクを追加**」をクリックします。
   * タイトルを入力し、ファイルをアップロードします（ファイルの種類は関係ありません）。
1. **保存**&#x200B;をクリックします。 次のメッセージが表示されます。*製品を保存しました*。
1. ページの上部にある「**新しい更新をスケジュール**」をクリックします。
   * 更新名と、有効な開始日と終了日を入力します。
1. ステージング更新で「**保存**」をクリックします。
1. 製品の&#x200B;**保存**&#x200B;をクリックします。

<u>期待される結果</u>:

製品はエラーなく保存されます。

<u>実際の結果</u>:

次のエラーメッセージが表示されます：*ダウンロード可能なサンプルが製品に関連していません。 リンクを確認して、もう一度やり直してください*。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
