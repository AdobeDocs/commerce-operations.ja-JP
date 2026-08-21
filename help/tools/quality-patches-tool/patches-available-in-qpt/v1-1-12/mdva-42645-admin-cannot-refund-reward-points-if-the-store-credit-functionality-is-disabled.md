---
title: MDVA-42645：管理者は、無効なストアクレジットに対する報酬ポイントを返金できません
description: MDVA-42645 パッチは、ストアクレジット機能が無効になっている場合に管理者が報酬ポイントを返金できない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.12がインストールされている場合に利用できます。 パッチ IDはMDVA-42645です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
exl-id: 8053fcc7-d30c-424a-9494-df6e8630b095
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# MDVA-42645：管理者は、無効なストアクレジットに対する報酬ポイントを返金できません

MDVA-42645 パッチは、ストアクレジット機能が無効になっている場合に管理者が報酬ポイントを返金できない問題を解決します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12がインストールされている場合に使用できます。 パッチ IDはMDVA-42645です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ストアクレジット機能が無効になっている場合、管理者は報酬ポイントを返金できません。

<u>複製する手順</u>:

1. シンプルな商品の作成。
1. 新しい顧客アカウントを作成し、いくつかリワードポイントを追加します。
1. ストア クレジット機能を無効にするには、**ストア** >設定> **設定** > **顧客** > **顧客設定** > **ストア クレジット オプション**&#x200B;に移動します。
1. 報酬ポイントが割り当てられている顧客としてログインします。
1. 商品をカートに追加し、「チェックアウト」に移動します。
1. 支払いセクションで報酬ポイントを使用して、注文します。
1. 管理画面で注文を開き、注文を請求書で請求します。
1. 「**クレジットメモ**」リンクをクリックして、新しいクレジットメモを作成します。
1. 下部の「ポイントの払い戻し」オプションをクリックし、「**オフラインの払い戻し**」をクリックします。

<u>期待される結果</u>:

* クレジットメモが正常に作成されました。
* 報酬ポイントは正常に返金されます。

<u>実際の結果</u>:

次のエラーメッセージが表示されます。*注文金額より多くの店舗クレジットを使用することはできません。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
