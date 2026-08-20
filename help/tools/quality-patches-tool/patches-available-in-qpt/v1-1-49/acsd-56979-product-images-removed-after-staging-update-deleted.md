---
title: ACSD-56979：ステージング更新が削除された後に製品画像が削除される
description: ステージング更新プログラムの削除後に製品画像が削除されるAdobe Commerceの問題を修正するには、ACSD-56979 パッチを適用します
feature: Products
role: Admin, Developer
exl-id: 1e0fbd5c-285b-408e-ba52-72619e29167b
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-56979：ステージング更新が削除された後に製品画像が削除される

ACSD-56979 パッチは、ステージング更新を削除した後に製品画像が削除される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.49がインストールされている場合に利用できます。 パッチ IDはACSD-56979です。 この問題は、Adobe Commerce 2.5.0で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe CommerceおよびMagento Open Sourceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ステージング更新プログラムを削除すると、製品画像が削除されます。

<u>複製する手順</u>:

1. Commerce管理サイドバーで、**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動し、商品を作成します。
1. **[!UICONTROL Images and Videos]**&#x200B;で、画像をアップロードして製品を保存します。
1. **[!UICONTROL Scheduled Changes]** ボックスで、**[!UICONTROL Schedule New Update]**&#x200B;を選択します。
   1. 開始日を数分先で選択します。
   1. 終了日は選択しないでください。
1. **[!UICONTROL Scheduled Changes]** ボックスで、**[!UICONTROL View/Edit]** リンクを選択します。
1. **[!UICONTROL Remove from Update]** > **[!UICONTROL Delete the Update]**&#x200B;に移動し、**[!UICONTROL Done]**&#x200B;を選択します。
1. ページを更新します。

<u>期待される結果</u>:

更新はスケジュールされた開始日より前に削除されるので、製品は同じままになります。

<u>実際の結果</u>:

画像コンテンツが失われ、ゼロ バイトが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
