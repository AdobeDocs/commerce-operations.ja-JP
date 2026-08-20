---
title: ACSD-48164：制限付き管理者がweb サイトレベルの値を保存できない
description: 制限付き管理者がweb サイトレベルの値を保存できないAdobe Commerceの問題を修正するには、ACSD-48164 パッチを適用します。
feature: Admin Workspace
role: Admin
exl-id: 1ad4758e-7ecc-48d0-8313-1163188cbe73
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-48164：制限付き管理者がweb サイトレベルの値を保存できない

ACSD-48164 パッチは、制限付き管理者がweb サイトレベルの値を保存できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.27がインストールされている場合に利用できます。 パッチ IDはACSD-48164です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

制限付き管理者は、web サイトレベルの値を保存できません。

<u>複製する手順</u>:

1. [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**&#x200B;に新しいweb サイト、ストア、ストア ビューを作成します。
1. [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**&#x200B;に新しい管理者ロールを作成します。

   * **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**&#x200B;に移動し、新しいweb サイトを選択して、この役割を任意の管理者ユーザーに割り当てます。

1. 任意の商品を選択し、新しいweb サイトのみを割り当てます。 デフォルトのweb サイトは選択しないでください。
1. 手順2で割り当てられた管理者ユーザーとしてログインし、*[!UICONTROL Status]*、*[!UICONTROL Tax Class]*&#x200B;などのweb サイトレベルの属性を変更して、**[!UICONTROL All Store View]** スコープの下で製品を編集し、製品を新規として設定します。
1. 製品を保存します。

<u>期待される結果</u>:

1つのweb サイトの役割スコープに関連付けられている管理者ユーザーは、*[!UICONTROL All Store View]* スコープを使用してWeb サイト レベルの製品属性を保存できます。

<u>実際の結果</u>:

製品が保存されたという成功メッセージが表示されますが、製品属性値は変更されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
