---
title: 'MDVA-39229: カタログ ルール ステージングの更新開始時刻を更新した後にエラーが発生する'
description: MDVA-39229 パッチは、ユーザーがカタログルールのステージング更新の開始時間を更新した後にエラーが発生する問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.5がインストールされている場合に利用できます。 パッチ IDはMDVA-39229です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Catalog Management, Staging
role: Admin
exl-id: 633123bc-634c-4943-a2f1-9a48999774f4
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39229: カタログ ルール ステージングの更新開始時刻を更新した後にエラーが発生する

MDVA-39229 パッチは、ユーザーがカタログルールのステージング更新の開始時間を更新した後にエラーが発生する問題を修正します。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.5がインストールされている場合に使用できます。 パッチ IDはMDVA-39229です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.3.4-p2

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ユーザーは、カタログルールのステージング更新の開始時刻を更新すると、エラーが発生します。

<u>複製する手順</u>:

1. カタログ価格ルールを作成します。
1. ステージング更新を作成して実行します。
1. クエリを実行し、ステージングフラグが作成されたことを確認します。


   `select * from flag;`


1. 5分後に開始する新しいステージング更新プログラムを作成します。
1. **コンテンツ** > **ステージング** > **ダッシュボード** > **新しい更新**&#x200B;を開き、開始時間を1分遅らせます。
1. 6分間待ってください。
1. cronを実行します。

<u>期待される結果</u>:

更新開始時間が変更され、更新が適用されます。 古い更新は`staging_update` テーブルから削除されます。

<u>実際の結果</u>:

ユーザーに次のエラーが表示されます。

*report.ERROR: Cron Job staging_synchronize_entities_periodにエラーがあります：アクティブな更新を削除できません。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で使用可能な[ パッチ」セクションを参照してください。
