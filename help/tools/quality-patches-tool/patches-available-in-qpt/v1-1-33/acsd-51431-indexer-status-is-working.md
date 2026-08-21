---
title: ACSD-51431：変更ログにエントリがないにもかかわらず、インデクサーのステータスが*[!UICONTROL Working]*です
description: 変更ログにエントリがないにもかかわらず、インデクサーステータスが*[!UICONTROL Working]*であるAdobe Commerceの問題を修正するには、ACSD-51431 パッチを適用します。
feature: Logs, Price Indexer
role: Admin
exl-id: c87c059b-f435-468d-a7fe-e6786fdba1f8
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-51431：変更ログにエントリがないにもかかわらず、インデクサーのステータスが&#x200B;*[!UICONTROL Working]*&#x200B;です

変更ログにエントリがないにもかかわらず、インデクサーのステータスが&#x200B;*[!UICONTROL Working]*&#x200B;であるパフォーマンスの問題がACSD-51431 パッチによって修正されます。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-51431です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

変更ログにエントリがないにもかかわらず、インデクサーのステータスは&#x200B;*[!UICONTROL Working]*&#x200B;です。

<u>複製する手順</u>:

1. **[!UICONTROL indexers]**&#x200B;を[!UICONTROL Update on Schedule]に設定します。
1. 毎分実行するようにcron ジョブを設定します。
1. 異なる製品への変更を同時に保存します。
1. 数分で`bin/magento indexer:status`を実行します。

<u>期待される結果</u>:

変更は処理され、インデクサーのステータスは&#x200B;*[!UICONTROL Ready]*&#x200B;です。 *[!UICONTROL Schedule]* ステータスは&#x200B;*[!UICONTROL idle (0 in the backlog)]*&#x200B;です。

<u>実際の結果</u>:

変更は処理され、インデクサーのステータスは&#x200B;*[!UICONTROL Ready]*&#x200B;です。 ただし、*[!UICONTROL Schedule]* ステータスには&#x200B;*[!UICONTROL working (0 in the backlog)]*&#x200B;が表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
