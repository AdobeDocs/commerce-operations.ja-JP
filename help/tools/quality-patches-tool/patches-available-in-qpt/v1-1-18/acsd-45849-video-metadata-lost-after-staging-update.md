---
title: ACSD-45849：ステージングの更新後にビデオメタデータが失われる
description: ACSD-45849 パッチは、ステージング更新が適用された後にビデオメタデータが失われる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.18がインストールされている場合に利用できます。 パッチ IDはACSD-45849です。 この問題はAdobe Commerce 2.4.4で修正されています。
feature: Staging, Page Content
role: Admin
exl-id: cbab0120-585a-47ef-8ed9-abb2da1ec3d6
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-45849：ステージングの更新後にビデオメタデータが失われる

ACSD-45849 パッチは、ステージング更新が適用された後にビデオメタデータが失われる問題を修正します。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.18がインストールされている場合に使用できます。 パッチ IDはACSD-45849です。 この問題はAdobe Commerce 2.4.4で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ステージング更新が適用されると、ビデオメタデータが失われます。

<u>複製する手順</u>:

1. **管理者** > **ストア** > **構成** > **カタログ** > **製品ビデオ**&#x200B;でYouTube API キーを設定します。
1. YouTubeの動画で商品を制作する。 URL、タイトル、説明が入力されていることに注意してください。
1. *画像とビデオ* セクションを変更せずに、任意のパラメーターを使用して、製品の新しいスケジュールされた更新を作成します。
1. スケジュールされた変更の&#x200B;**表示/編集**&#x200B;をクリックします。
1. **画像とビデオ**&#x200B;に移動し、ビデオをクリックします。

<u>期待される結果</u>:

URL、タイトル、説明には適切なデータが含まれています。

<u>実際の結果</u>:

URL、タイトル、および説明のフィールドが空です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
