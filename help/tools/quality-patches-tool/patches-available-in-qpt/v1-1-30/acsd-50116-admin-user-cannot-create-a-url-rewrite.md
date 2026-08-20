---
title: ACSD-50116：管理者ユーザーは、レベル 3以下のサブカテゴリのURL書き換えを作成できません
description: ACSD-50116 パッチを適用して、管理者ユーザーがレベル 3以下のサブカテゴリのURL書き換えを作成できないAdobe Commerceの問題を修正します。
feature: Admin Workspace, Categories
role: Admin
exl-id: b2a248eb-a6c4-4596-acac-04a52c5c2a61
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-50116：管理者ユーザーは、レベル 3以下のサブカテゴリのURL書き換えを作成できません

ACSD-50116 パッチは、管理者ユーザーがレベル 3以下のサブカテゴリのURL書き換えを作成できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.30がインストールされている場合に利用できます。 パッチ IDはACSD-50116です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者ユーザーは、レベル 3以下のサブカテゴリのURL書き換えを作成できません。

<u>複製する手順</u>:

1. 3つ以上のレベルのサブカテゴリを持つカテゴリツリーを作成します。
1. *[!UICONTROL For Product]*&#x200B;と&#x200B;*[!UICONTROL For Category]*&#x200B;の両方のオプションを使用して、レベル 4 カテゴリの&#x200B;*[!UICONTROL URL Rewrite]*&#x200B;を作成してみてください。

<u>期待される結果</u>:

カテゴリーツリーには、レベル 4以下までのサブカテゴリが表示されます。

<u>実際の結果</u>:

カテゴリーツリーには、最大レベル 3のサブカテゴリのみが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
