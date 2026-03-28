---
title: 'ACSD-51358: スケジュールの更新が見つかりません'
description: ACSD-51358 パッチを適用して、終了日のないスケジュール済み更新の変更が、同じエンティティ上の他のスケジュール済み更新の削除につながるAdobe Commerceの問題を修正します。
feature: Staging
role: Admin, Developer
exl-id: 6e2e598b-72f1-4f00-a989-3f75bf65f8f0
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51358: スケジュールの更新が見つかりません

ACSD-51358 パッチでは、終了日のないスケジュール済み更新の変更が、同じエンティティ上の他のスケジュール済み更新の削除につながる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35がインストールされている場合に利用できます。 パッチ IDはACSD-51358です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

終了日のないスケジュールされた更新の変更は、同じエンティティ上の他のスケジュールされた更新の削除につながります。

<u>複製する手順</u>:

1. 終了日（**[!UICONTROL scheduled update]**&#x200B;更新1 *）なしで*&#x200B;を作成します。
1. 最初の更新と同じ開始日で新しい&#x200B;**[!UICONTROL scheduled update]**&#x200B;を作成しますが、次の日と終了日（*更新2*）を追加します。
1. 手順1 （**[!UICONTROL scheduled update]**&#x200B;更新1 *）で作成された*&#x200B;を編集し、変更を保存します。

<u>期待される結果</u>

（*更新2*）は、（**[!UICONTROL schedule update]**&#x200B;更新1 *）の編集時に* リストに残る必要があります。

<u>実際の結果</u>

（*更新1*）の編集時に、（**[!UICONTROL schedule update]**&#x200B;更新2 *）が* リストから削除されました。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [&#x200B; [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
