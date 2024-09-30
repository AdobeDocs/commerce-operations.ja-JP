---
title: 「ACSD-53414：制限付き管理者ユーザーが、権限適用範囲外のCMS ページを表示できる」
description: ACSD-53414 パッチを適用すると、制限付き管理者ユーザーが権限適用範囲外のCMS ページを表示できるAdobe Commerceの問題を修正できます。
feature: CMS
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-53414：制限付き管理者ユーザーが、権限適用範囲外のCMS ページを表示できる

ACSD-53414 パッチでは、制限付き管理者ユーザーが、自身の権限適用範囲外にあるCMS ページを表示できる問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 がインストールされている場合に使用できます。 パッチ ID は ACSD-53414 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

制限付き管理者ユーザーには、権限適用範囲外のCMS ページも表示されます。

<u> 再現手順 </u>:

1. 新しい web サイト（sub_website）、ストア（sub_store）、ストレビュー（sub_storeview）を作成します。
1. sub_expert ロールを作成して、sub_website および sub_store の範囲を許可します。 [!UICONTROL Dashboard] および [!UICONTROL Pages] の権限のみを割り当てます。
1. 新しい管理者ユーザーを作成して、sub_expert ロールに割り当てます。
1. 以下の CSM ページを sub_storereview と default storereview に割り当てます。

   * [!UICONTROL 404 Not Found] > サブストアの確認
   * [!UICONTROL 503 Service Unavailable] > デフォルトの storereview

1. 手順 3 で作成した管理者ユーザーを使用して管理者にログインします。
1. CMS ページグリッドを確認します。

<u> 期待される結果 </u>:

*[!UICONTROL 503 Service Unavailable]* ページは、web 管理者には表示されません。

<u> 実際の結果 </u>:

*[!UICONTROL 503 Service Unavailable]* は、web 管理者に表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
