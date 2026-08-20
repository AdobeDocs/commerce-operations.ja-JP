---
title: ACSD-47137：画像ギャラリーの読み込み速度「pub/media」フォルダーを大きく改善
description: 「pub/media」フォルダーが非常に大きい場合に、画像ギャラリーの読み込み速度を向上させるには、ACSD-47137 パッチを適用します。
feature: Cache, Catalog Management, Categories, Media
role: Admin
exl-id: 8a5dd930-1940-486e-96db-ee1b166cf312
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-47137: `pub/media` フォルダーが大きいときに画像ギャラリーの読み込み速度を向上

ACSD-47137 パッチは、`pub/media` フォルダーが非常に大きい場合に、画像ギャラリーの読み込み速度を向上させます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24がインストールされている場合に利用できます。 パッチ IDはACSD-47137です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`pub/media` フォルダーが非常に大きい場合、画像ギャラリーの読み込み速度が遅くなります。

<u>複製する手順</u>:

1. Adobe Commerce Admin > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]**&#x200B;から&#x200B;_No_&#x200B;に移動します。
1. 設定キャッシュをクリーニングします。
1. ログアウトし、管理者ユーザーとして再度ログインします。
1. 管理サイドバーで、**[!UICONTROL Catalog]** > **[!UICONTROL Categories]**&#x200B;に移動し、ルートカテゴリを選択します。
1. **[!UICONTROL Content]** セクションを展開し、**[!UICONTROL Select from Gallery]**&#x200B;をクリックします。

ページを読み込む際、Adobe Commerceは`media_gallery/directories/gettree` リクエストを送信してメディアフォルダーツリーを読み込みます。

<u>期待される結果</u>:

`media_gallery/directories/gettree` リクエストは、必要なディレクトリからのみコンテンツを読み込む必要があります。ただし、`pub/media/` フォルダーからパス リスト全体をループする必要はありません。

<u>実際の結果</u>:

`pub/media/` フォルダーにコンテンツが多い場合、`media_gallery/directories/gettree` リクエストの読み込みに時間がかかります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
