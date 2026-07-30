---
title: MDVA-38666：管理者ユーザーが設定可能な製品オプションを変更できない
description: MDVA-38666 パッチは、管理者ユーザーが顧客のカート内の設定可能な製品オプションを変更できない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.9がインストールされている場合に利用できます。 パッチ IDはMDVA-38666です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Admin Workspace, Configuration, Products
role: Admin
exl-id: 8e72f6a4-b36f-4fe4-bc01-2254984dd512
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# MDVA-38666：管理者ユーザーが設定可能な製品オプションを変更できない

MDVA-38666 パッチは、管理者ユーザーが顧客のカート内の設定可能な製品オプションを変更できない問題を解決します。 このパッチは、[品質パッチツール （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9がインストールされている場合に使用できます。 パッチ IDはMDVA-38666です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.3.4-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者ユーザーは、お客様のカート内の設定可能な製品オプションを変更できません。

<u>複製する手順</u>:

1. 顧客アカウントの範囲をグローバルに設定。
1. 店舗を含む2つのweb サイトを作成する。
1. 設定可能な2つの製品を作成し、各web サイトに割り当てます。
1. フロントエンドで顧客アカウントを作成し、ログインします。
1. 商品をカートに追加してチェックアウトを行います（これは、各web サイトで見積もりIDを異ならせるために行います）。
1. 商品をカートに追加して残します。
1. 2番目のweb サイトに切り替えて、製品をカートに追加します（顧客アカウントの範囲がグローバルに設定されているので、同じログインが機能する必要があります）。
1. 管理者から顧客を開き、「買い物かご」タブに移動します。
1. ドロップダウンからストアを切り替えて、設定を変更してみてください。

<u>期待される結果</u>:

ユーザーは、設定可能なオプションを含むポップアップを取得します。

<u>実際の結果</u>:

ポップアップフォームが表示されません。 ユーザーは設定を変更できません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
