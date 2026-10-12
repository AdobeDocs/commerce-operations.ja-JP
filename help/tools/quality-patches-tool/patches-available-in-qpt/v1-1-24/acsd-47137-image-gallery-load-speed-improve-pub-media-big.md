---
title: ACSD-47137：画像ギャラリーの読み込み速度「pub/media」フォルダーを大きく改善
description: 「pub/media」フォルダーが非常に大きい場合に、画像ギャラリーの読み込み速度を向上させるには、ACSD-47137 パッチを適用します。
feature: Cache, Catalog Management, Categories, Media
role: Admin
exl-id: 8a5dd930-1940-486e-96db-ee1b166cf312
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
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
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

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
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
