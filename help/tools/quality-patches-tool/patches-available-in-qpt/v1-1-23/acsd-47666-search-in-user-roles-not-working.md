---
title: 「ACSD-47666:[!UICONTROL User Roles] の検索が機能しない」
description: ACSD-47666 パッチを適用すると、[!UICONTROL User Roles] のフィルター関数が期待どおりに動作しないAdobe Commerceの問題を修正できます。
feature: Roles/Permissions, Search
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-47666:**[!UICONTROL User Roles]** の検索が機能しない

ACSD-47666 パッチを使用すると、**[!UICONTROL User Roles]** の検索が機能しない問題を解決できます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 がインストールされている場合に使用できます。 パッチ ID は ACSD-47666 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**[!UICONTROL User Roles]** のフィルター関数が期待どおりに動作しません。

<u> 再現手順 </u>:

1. Adobe Commerce管理者/ **[!UICONTROL System]** / **[!UICONTROL Permissions]** / **[!UICONTROL User Roles]** にログインします。
1. リストから既存の役割を開きます。
1. 「**[!UICONTROL Role Users]**」タブを開きます。
1. 列にクエリを入力します。
1. Enter キーを押します。

<u> 期待される結果 </u>:

**[!UICONTROL User Roles]** のフィルター関数では、クエリに基づいて結果がフィルタリングされます。

<u> 実際の結果 </u>:

コンソールエラー _（インデックス）:9 を含む無限読み込みがキャッチされない TypeError : null のプロパティを読み取れません（「down」を読み取ります）_。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。 

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
