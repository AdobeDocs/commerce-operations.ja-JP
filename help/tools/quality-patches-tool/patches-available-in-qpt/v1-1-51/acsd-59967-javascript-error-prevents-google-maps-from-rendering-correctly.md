---
title: 'ACSD-59967: JavaScript エラーにより、 [!DNL Google Maps] が正しくレンダリングされない'
description: ACSD-59967 パッチを適用して、JavaScript エラーによって [!DNL Google Maps] が正しくレンダリングされないAdobe Commerceの問題を修正します。
feature: Admin Workspace, Page Builder, CMS
role: Admin, Developer
exl-id: 2982857a-7adb-4163-be18-4d2caf0d645c
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-59967: JavaScript エラーにより、[!DNL Google Maps]が正しくレンダリングされない

ACSD-59967 パッチは、JavaScript エラーによって[!DNL Google Maps]が正しくレンダリングされない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.51がインストールされている場合に利用できます。 パッチ IDはACSD-59967です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p3

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

JavaScript エラーにより、[!DNL Google Maps]が正しくレンダリングされません。

<u>複製する手順</u>:

1. 有効な[!DNL Google Maps] キーを生成します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Content Management]**&#x200B;の下で[!DNL Google Maps] API キーを設定します。
1. [!DNL Google API Key] フィールドを&#x200B;**[!UICONTROL Google Maps API Key]** フィールドに追加し、設定を保存します。
1. **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Create New Page]**&#x200B;に移動します。
1. **[!UICONTROL Row]**&#x200B;要素と&#x200B;**[!UICONTROL Maps]**&#x200B;要素を追加します。

<u>期待される結果</u>:

コンソールにJavaScript エラーはなく、マップは&#x200B;*Storefront*&#x200B;および&#x200B;*Admin*&#x200B;で正しくレンダリングされます。

<u>実際の結果</u>:

JavaScript エラーがコンソールに表示され、マップが正しくレンダリングされません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
