---
title: ACSD-53414：制限付き管理者ユーザーが、権限の範囲外のCMS ページを表示する
description: ACSD-53414 パッチを適用して、制限付き管理者ユーザーが権限範囲外のCMS ページを表示できるAdobe Commerceの問題を修正します。
feature: CMS
role: Admin, Developer
exl-id: 86658336-679b-4fe0-9d26-56064ff0c604
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-53414：制限付き管理者ユーザーが、権限の範囲外のCMS ページを表示する

ACSD-53414 パッチでは、制限付き管理者ユーザーが権限範囲外のCMS ページを表示できる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.40がインストールされている場合に利用できます。 パッチ IDはACSD-53414です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

制限付き管理者ユーザーは、権限の範囲を超えてCMS ページを表示できます。

<u>複製する手順</u>:

1. 新しいweb サイト（sub_website）、ストア（sub_store）、およびストアビュー（sub_storeview）を作成します。
1. sub_expertの役割を作成し、sub_websiteとsub_storeの範囲を許可します。 次の権限のみを割り当てます：[!UICONTROL Dashboard]および[!UICONTROL Pages]。
1. 新しい管理者ユーザーを作成し、sub_expertの役割に割り当てます。
1. 次のCSM ページをsub_storeviewとデフォルトのstoreviewに割り当てます。

   * [!UICONTROL 404 Not Found] > サブストアビュー
   * [!UICONTROL 503 Service Unavailable] > デフォルトのストアビュー

1. 手順3で作成した管理者ユーザーを使用して、管理者にログインします。
1. CMSのページグリッドを確認します。

<u>期待される結果</u>:

*[!UICONTROL 503 Service Unavailable]* ページはweb管理者には表示されません。

<u>実際の結果</u>:

*[!UICONTROL 503 Service Unavailable]*&#x200B;はweb管理者に表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
