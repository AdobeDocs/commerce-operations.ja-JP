---
title: ACSD-58375：ストアビューレベルでビデオを追加する際に、YouTube API キーが正しく設定されていないとエラーが発生する
description: ACSD-58375 パッチを適用して、ストアビューレベルでYouTube ビデオを追加する際に間違ったYouTube API キー設定が発生するAdobe Commerceの問題を修正します。
feature: Catalog Management, Configuration
role: Admin, Developer
exl-id: 24187308-d9dc-4ce2-9cfa-70ccb7726a5b
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-58735：ストアビューレベルでビデオを追加する際に、YouTube API キーが正しく設定されていないとエラーが発生する

ACSD-58735 パッチは、ストアビューレベルでYouTube ビデオを追加する際に、YouTube API キーの設定が間違ってエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.49がインストールされている場合に利用できます。 パッチ IDはACSD-58735です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

YouTube API キーの設定が正しくないと、ストアビューレベルでYouTube ビデオを追加する際にエラーが発生します。

<u>複製する手順</u>:

1. 管理者/**[!UICONTROL Stores]** / **[!UICONTROL Configuration]** / **[!UICONTROL Catalog]** / **[!UICONTROL Product Video]**&#x200B;に移動します。
1. *スコープ*&#x200B;を&#x200B;*[!UICONTROL Main Website]* レベルに変更します。
1. YouTube API キーを追加します。
1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動します。
1. 任意の商品を選択し、*[!UICONTROL Images and Video]*&#x200B;までスクロールします。 **[!UICONTROL Add Video]**&#x200B;をクリックします。
1. YouTube ビデオリンクをコピーし、ビデオリンクフィールドに貼り付けます。 フィールドから移動します。

<u>期待される結果</u>:

YouTube API キーにはグローバルなスコープがあり、web サイトレベルで非表示になっています。

<u>実際の結果</u>:

次のエラーがスローされます：*次の理由により、ビデオが表示されません：API キーが無効です。 有効なAPI キー*&#x200B;を渡してください。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
