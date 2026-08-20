---
title: 'MDVA-44887：管理パネルで「Uncaught SyntaxError: Unexpected token const」エラーが発生する'
description: 'MDVA-44887 パッチは、管理者ユーザーがメニューオプションをクリックできない問題を修正します。 管理パネルに「*Uncaught SyntaxError: Unexpected token const*」エラーが表示されます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.15がインストールされている場合に利用できます。 パッチ IDはMDVA-44887です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。'
feature: Admin Workspace, Orders
role: Admin
exl-id: d8cc03c3-35a0-4f00-8ec3-1ba3e100f7ca
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-44887：管理パネルで「Uncaught SyntaxError: Unexpected token const」エラーが発生する

MDVA-44887 パッチは、管理者ユーザーがメニューオプションをクリックできない問題を修正します。 *Uncaught SyntaxError: Unexpected token const* エラーが管理パネルに表示されます。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.15がインストールされている場合に使用できます。 パッチ IDはMDVA-44887です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者ユーザーはメニューオプションをクリックできません。 *Uncaught SyntaxError: Unexpected token const* エラーが管理パネルに表示されます。

<u>複製する手順</u>:

1. JS バンドルを有効にします。
1. JS ファイルを縮小します。
1. Commerce管理パネルにログインします。

<u>期待される結果</u>:

管理者ユーザーはメニューオプションをクリックできません。 ブラウザーコンソールにエラーがあります：*捕捉できない構文エラー：予期しないトークン数*。

<u>実際の結果</u>:

管理者パネルには、管理者ユーザーがアクセスできます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
