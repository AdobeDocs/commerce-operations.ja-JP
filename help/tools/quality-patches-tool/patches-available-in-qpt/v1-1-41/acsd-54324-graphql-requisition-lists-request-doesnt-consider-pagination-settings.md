---
title: ACSD-54324:GraphQL requisition_lists リクエストでページネーションの設定が考慮されない
description: ACSD-54324 パッチを適用すると、Adobe Commerceの「requisition_lists」リクエストでページネーションの設定が考慮されず、すべての結果が返されるGraphQLの問題を修正できます。
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 60f82602-1cfc-4523-a50d-46af5d5f10d9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-54324:GraphQL `requisition_lists` リクエストでページネーションの設定が考慮されない

ACSD-54324 パッチでは、GraphQL `requisition_lists` リクエストがページネーションの設定を考慮せず、すべての結果を返す問題を修正しています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.41 がインストールされている場合に使用できます。 パッチ ID は ACSD-54324 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

GraphQL `requisition_lists` リクエストは、ページネーションの設定を考慮せず、すべての結果を返します。

<u> 再現手順 </u>:

1. 管理者にログインし、**[!UICONTROL Admin]** / **[!UICONTROL Store]** / **[!UICONTROL Configuration]** / **[!UICONTROL General]** / **[!UICONTROL B2B Features]** に移動します。

   * *[!UICONTROL Enable Requisition List]* を *はい* に設定します。

1. フロントエンドにログインし、トップメニューまたは **[!UICONTROL My Account]** から **[!UICONTROL My Requisition Lists]** に移動し、複数の購買依頼を作成します（例：7）。
1. カスタマートークンを生成した後、以下のGraphQL `requisition_lists` クエリを実行して、カスタマーを検索します。

   * ページ・サイズが、作成した購買依頼リストの合計数より少ないことを確認します（例：4）

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. `total_count` フィールドの値が 7 を示し、4 を示す必要があることを確認します。

   また、項目数が *ページサイズ* と同じである必要がある場合は、7 と表示されます。

<u> 期待される結果 </u>:

* *ページサイズ* としてリストされた数は、レコードの合計数ではなく、`total_count` の下に返されます。
* 項目数は *ページサイズ* と同じです。

<u> 実際の結果 </u>:

*ページサイズ* が記載されている場合でも、レコードの合計数は `total_count` 下に返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
