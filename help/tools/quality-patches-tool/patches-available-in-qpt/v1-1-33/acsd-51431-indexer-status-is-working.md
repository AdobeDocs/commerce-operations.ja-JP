---
title: 「ACSD-51431：変更ログにエントリがない場合でも、インデクサーのステータスは*[!UICONTROL Working]*です」
description: 変更ログにエントリがない場合でも、インデクサーのステータスが*[!UICONTROL Working]*であるAdobe Commerceの問題を修正するために、ACSD-51431 パッチを適用してください。
feature: Logs, Price Indexer
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-51431：変更ログにエントリがない場合でも、インデクサーのステータスが *[!UICONTROL Working]* になる

ACSD-51431 パッチは、変更ログにエントリがない場合でもインデクサーのステータスが *[!UICONTROL Working]* になるパフォーマンスの問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.33 がインストールされている場合に使用できます。 パッチ ID は ACSD-51431 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

変更ログにエントリがない場合でも、インデクサーのステータスは *[!UICONTROL Working]* です。

<u> 再現手順 </u>:

1. **[!UICONTROL indexers]** を [!UICONTROL Update on Schedule] に設定します。
1. cron ジョブを毎分実行するように設定します。
1. 異なる製品への変更を同時に保存します。
1. 数分で `bin/magento indexer:status` を実行します。

<u> 期待される結果 </u>:

変更が処理され、インデクサーが *[!UICONTROL Ready]* ステータスになります。 *[!UICONTROL Schedule]* の状態は *[!UICONTROL idle (0 in the backlog)]* です。

<u> 実際の結果 </u>:

変更が処理され、インデクサーが *[!UICONTROL Ready]* ステータスになります。 ただし、*[!UICONTROL Schedule]* のステータスは *[!UICONTROL working (0 in the backlog)]* と表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
