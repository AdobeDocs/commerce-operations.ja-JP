---
title: ACSD-58008：終了日を*empty*として編集すると、スケジュールの更新が消える
description: ACSD-58008 パッチを適用して、終了日を*empty*として編集するとスケジュール更新が消えるAdobe Commerceの問題を修正します。
feature: Staging, Page Content
role: Admin, Developer
exl-id: 6d2279e5-6580-4325-b0a8-ed62a95da3c2
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-58008：終了日を&#x200B;*empty*&#x200B;として編集すると、スケジュールの更新が消える

ACSD-58008 パッチでは、終了日を&#x200B;*empty*&#x200B;として編集すると、スケジュールの更新が消える問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.48がインストールされている場合に利用できます。 パッチ IDはACSD-58008です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

終了日を&#x200B;*empty*&#x200B;として編集すると、スケジュールの更新が消えます

<u>複製する手順</u>:

1. [!UICONTROL Admin]としてログインします。
1. **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**&#x200B;に移動し、ページを作成します。
1. 作成したページを選択し、**[!UICONTROL Schedule New Update]**&#x200B;をクリックします。 *（ページの右上隅に移動）*。
1. 4つのアップデートを作成。 *（例：* 2 *分の増分）*。
1. *更新プログラム 2*&#x200B;を更新し、時間を前回の&#x200B;*更新プログラム 4*&#x200B;より前の時間に変更します。
1. 更新を保存します。

<u>期待される結果</u>:

スケジュールの更新には、*更新3*&#x200B;が表示されます。

<u>実際の結果</u>:

スケジュールの更新に&#x200B;*更新3*&#x200B;が表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
