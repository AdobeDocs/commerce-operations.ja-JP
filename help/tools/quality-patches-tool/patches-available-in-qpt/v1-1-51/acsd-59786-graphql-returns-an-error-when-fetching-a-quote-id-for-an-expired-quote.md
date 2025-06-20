---
title: ACSD-59786：有効期限切れの引用符に対して「quote_id」を取得すると、GraphQLがエラーを返す
description: ACSD-59786 パッチを適用すると、有効期限切れの見積もりの「quote_id」を取得する際にGraphQL クエリがエラーを返すAdobe Commerceの問題を修正できます。
feature: GraphQL, Quotes, Companies
role: Admin, Developer
exl-id: 3c7aaa99-a2e0-44fe-9426-b24095615915
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-59786：有効期限切れの引用符の `quote_id` を取得すると、GraphQLがエラーを返す

ACSD-59786 パッチでは、有効期限切れの見積書の `quote_id` を取得する際に、GraphQL クエリがエラーを返す問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 がインストールされている場合に使用できます。 パッチ ID は ACSD-59786 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

有効期限切れの見積書の `quote_id` を取得すると、GraphQL クエリがエラーを返します。

<u> 再現手順 </u>:

1. **[!UICONTROL Companies]** と **[!UICONTROL Purchase Orders]** を有効にします。
   * **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL General]**/**[!UICONTROL B2B Features]** を選択し、**[!UICONTROL Enable Company]** を *はい* に設定します。
   * **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL General]**/**[!UICONTROL B2B Features]**/**[!UICONTROL Order Approval Configuration]** を選択し、**[!UICONTROL Enable Purchase Orders]** を *はい* に設定します。
1. 新しい会社を作成し、同じ **[!UICONTROL Enable Purchase Orders]** めに *はい* に設定します。
1. シンプルな製品を作成してカテゴリに割り当てます。
1. 会社の管理者アカウントを使用して Storefront にログインし、**[!UICONTROL Purchase Order]** を支払い方法として使用して新しい注文を作成します。
1. **[!UICONTROL Quote Lifetime (days)]** を変更します。
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Shopping Cart]** > **[!UICONTROL Quote Lifetime (days)]** = *0*。
1. コマンド `bin/magento c:f` を実行します。
1. DB `quote_table` に移動して、`created_at` と `updated_at` の値を過去の 1 日に変更します。
1. コマンド `bin/magento cron:run --group="sales_clean_quotes` を実行します。
1. **[!UICONTROL Purchase Order]** を作成する管理者用の承認済みトークンを使用して、以下のGraphQL リクエストを実行します。

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

<u> 期待される結果 </u>:

GraphQL クエリは、`quote_id` を返します。

<u> 実際の結果 </u>:

GraphQL クエリが内部サーバーエラーを返します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
