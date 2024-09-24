---
title: '''ACSD-47137：画像ギャラリーの読み込み速度の向上''pub/media'' フォルダーが大きい'''
description: 「pub/media」フォルダーが非常に大きい場合は、画像ギャラリーの読み込み速度を向上させるために ACSD-47137 パッチを適用します。
feature: Cache, Catalog Management, Categories, Media
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-47137：フォルダーが大きい場合の画像ギャラリーの読み込み速度 `pub/media` 向上

`pub/media` フォルダーが非常に大きい場合、ACSD-47137 パッチにより画像ギャラリーの読み込み速度が向上します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 がインストールされている場合に使用できます。 パッチ ID は ACSD-47137 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`pub/media` フォルダーが非常に大きい場合、画像ギャラリーの読み込み速度が遅くなります。

<u> 再現手順 </u>:

1. Adobe Commerce管理者/ **[!UICONTROL STORES]** / **[!UICONTROL Settings]** / **[!UICONTROL Configuration]** / **[!UICONTROL Advanced]** / **[!UICONTROL System]** / **[!UICONTROL Media Gallery]** / **[!UICONTROL Enable Old Media Gallery]** に移動します _いいえ_。
1. 設定キャッシュをクリーンアップします。
1. ログアウトして、管理者ユーザーとして再度ログインします。
1. 管理者サイドバーで、**[!UICONTROL Catalog]**/**[!UICONTROL Categories]** に移動し、ルートカテゴリを選択します。
1. **[!UICONTROL Content]** セクションを展開し、**[!UICONTROL Select from Gallery]** をクリックします。

ページを読み込む際、Adobe Commerceはメディアフォルダーツリー `media_gallery/directories/gettree` 読み込むためのリクエストを送信します。

<u> 期待される結果 </u>:

`media_gallery/directories/gettree` リクエストでは、`pub/media/` フォルダーからパスリスト全体をループする以外に、必要なディレクトリからのみコンテンツを読み込む必要があります。

<u> 実際の結果 </u>:

`pub/media/` フォルダーに多数のコンテンツがある場合、`media_gallery/directories/gettree` リクエストの読み込みに時間がかかる。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
