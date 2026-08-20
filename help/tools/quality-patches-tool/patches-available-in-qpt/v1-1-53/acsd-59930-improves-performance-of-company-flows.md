---
title: ACSD-59930：会社のフローのパフォーマンスを向上させる
description: アドレス帳に*1000+*のアドレスを持つ管理者を持つ会社を作成、保存または削除する際に、管理パネルに*タイムアウト*エラーが表示されるAdobe Commerceの問題を解決するには、ACSD-59930 パッチを適用します。
feature: Customers, B2B
role: Admin, Developer
exl-id: eaa6c78d-13e3-439d-90f7-70c1c96c3197
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-59930：会社のフローのパフォーマンスを向上させる

ACSD-59930 パッチは、アドレスブックに&#x200B;*1000+*&#x200B;個のアドレスを持つ管理者を持つ会社を作成、保存、または削除する際に、管理パネルに&#x200B;*タイムアウト* エラーが表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53がインストールされている場合に利用できます。 パッチ IDはACSD-59930です。 この問題は、Adobe Commerce B2B-1.5.0で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

会社の作成、保存、削除フローのパフォーマンスを向上させます。

<u>前提条件：</u>:

Adobe Commerce B2B モジュールをインストールして有効にする。

<u>複製する手順</u>:

1. *[!UICONTROL Address Book]*&#x200B;に&#x200B;*1000+*&#x200B;個のアドレスを持つ顧客を作成します。
1. 会社を作成し、上記の顧客を管理者として使用します。
1. 会社を救う。

<u>期待される結果</u>:

会社はタイムアウトエラーを表示せずに正常に作成されました。

<u>実際の結果</u>:

タイムアウトエラーが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
