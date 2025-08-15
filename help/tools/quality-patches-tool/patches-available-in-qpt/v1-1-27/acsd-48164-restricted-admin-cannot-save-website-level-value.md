---
title: ACSD-48164：制限付き管理者は、web サイトレベルの値を保存できません
description: ACSD-48164 パッチを適用して、制限付き管理者が web サイトレベルの値を保存できないAdobe Commerceの問題を修正してください。
feature: Admin Workspace
role: Admin
exl-id: 1ad4758e-7ecc-48d0-8313-1163188cbe73
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48164：制限付き管理者は、web サイトレベルの値を保存できません

ACSD-48164 パッチは、制限付き管理者が web サイトレベルの値を保存できない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 がインストールされている場合に使用できます。 パッチ ID は ACSD-48164 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

制限付き管理者は、web サイトレベルの値を保存できません。

<u> 再現手順 </u>:

1. [!UICONTROL Admin]/**[!UICONTROL Store]**/**[!UICONTROL All Stores]** で、新しい web サイト、ストア、ストア表示を作成します。
1. [!UICONTROL Admin]/**[!UICONTROL System]**/**[!UICONTROL User Roles]** で新しい管理者ロールを作成します。

   * **[!UICONTROL Role Resources]**/**[!UICONTROL Role Scopes]** に移動して、新しい web サイトを選択し、この役割を任意の管理者ユーザーに割り当てます。

1. 任意の製品を選択し、新しい web サイトのみを割り当てます。 デフォルトの web サイトは選択しないでください。
1. 手順 2 で割り当てられた管理者ユーザーとしてログインし、**[!UICONTROL All Store View]**、*[!UICONTROL Status]* などの web サイトレベルの属性を変更して *[!UICONTROL Tax Class]* の範囲の製品を編集し、製品を新規として設定します。
1. 商品を保存します。

<u> 期待される結果 </u>:

ある web サイトへの役割スコープに関連付けられている管理者ユーザーは、*[!UICONTROL All Store View]* スコープを使用して web サイトレベルの製品属性を保存できます。

<u> 実際の結果 </u>:

製品が保存されたという成功メッセージが表示されますが、製品属性値は変更されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
