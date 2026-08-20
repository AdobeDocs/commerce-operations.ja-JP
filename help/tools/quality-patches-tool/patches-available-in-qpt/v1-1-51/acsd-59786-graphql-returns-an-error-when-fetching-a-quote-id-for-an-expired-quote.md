---
title: ACSD-59786：期限切れの見積もりに対して「quote_id」を取得する際に、GraphQLがエラーを返す
description: ACSD-59786 パッチを適用して、期限切れの見積もりに対して「quote_id」を取得する際にGraphQL クエリがエラーを返すAdobe Commerceの問題を修正します。
feature: GraphQL, Quotes, Companies
role: Admin, Developer
exl-id: 3c7aaa99-a2e0-44fe-9426-b24095615915
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# ACSD-59786：期限切れの見積もりに対して`quote_id`を取得する際にGraphQLがエラーを返す

ACSD-59786 パッチは、期限切れの見積もりに対して`quote_id`を取得する際にGraphQL クエリがエラーを返す問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.51がインストールされている場合に利用できます。 パッチ IDはACSD-59786です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQL クエリは、期限切れの見積もりに対して`quote_id`を取得する際にエラーを返します。

<u>複製する手順</u>:

1. **[!UICONTROL Companies]**&#x200B;と&#x200B;**[!UICONTROL Purchase Orders]**&#x200B;を有効にします。
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**&#x200B;と&#x200B;**[!UICONTROL Enable Company]**&#x200B;を&#x200B;*Yes*&#x200B;に設定します。
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** > **[!UICONTROL Order Approval Configuration]**&#x200B;で、**[!UICONTROL Enable Purchase Orders]**&#x200B;を&#x200B;*はい*&#x200B;に設定します。
1. 新しい会社を作成し、同じ会社に&#x200B;**[!UICONTROL Enable Purchase Orders]**&#x200B;を&#x200B;*はい*&#x200B;に設定します。
1. シンプルな商品を作成し、カテゴリーに割り当てる：
1. 会社の管理者アカウントを使用してStorefrontにログインし、支払い方法として&#x200B;**[!UICONTROL Purchase Order]**&#x200B;を使用して新しい注文を作成します。
1. **[!UICONTROL Quote Lifetime (days)]**&#x200B;を変更します。
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Shopping Cart]** > **[!UICONTROL Quote Lifetime (days)]** = *0*.
1. コマンド `bin/magento c:f`を実行します。
1. DB `quote_table`に移動し、`created_at`と`updated_at`の値を1日前の日付に変更します。
1. コマンド `bin/magento cron:run --group="sales_clean_quotes`を実行します。
1. **[!UICONTROL Purchase Order]**&#x200B;を作成する管理者の承認されたトークンを使用して、以下に示すGraphQL リクエストを実行します。

   ```GraphQL
   {
       customer {
           purchase_order(uid: "MQ==") {
               quote {
                   id
               }
           }
       }
   } 
   ```

<u>期待される結果</u>:

GraphQL クエリは`quote_id`を返します。

<u>実際の結果</u>:

GraphQL クエリは、内部サーバーエラーを返します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
