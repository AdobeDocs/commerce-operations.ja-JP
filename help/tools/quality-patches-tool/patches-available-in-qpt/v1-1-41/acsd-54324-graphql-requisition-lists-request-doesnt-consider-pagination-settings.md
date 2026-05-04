---
title: 'ACSD-54324: GraphQL requisition_lists リクエストでページネーション設定が考慮されない'
description: ACSD-54324 パッチを適用して、GraphQLの「requisition_lists」リクエストでページネーション設定が考慮されず、すべての結果が返されるAdobe Commerceの問題を修正します。
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 60f82602-1cfc-4523-a50d-46af5d5f10d9
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# ACSD-54324: GraphQL `requisition_lists` リクエストでページネーション設定が考慮されない

ACSD-54324 パッチは、GraphQL `requisition_lists` リクエストでページネーション設定が考慮されず、すべての結果が返される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.41がインストールされている場合に利用できます。 パッチ IDはACSD-54324です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQL `requisition_lists` リクエストでは、ページネーション設定は考慮されず、すべての結果が返されます。

<u>複製する手順</u>:

1. 管理者にログインし、**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**&#x200B;に移動します。

   * *[!UICONTROL Enable Requisition List]*&#x200B;を&#x200B;*はい*&#x200B;に設定します。

1. フロントエンドにログインし、上部メニューまたは&#x200B;**[!UICONTROL My Account]**&#x200B;から&#x200B;**[!UICONTROL My Requisition Lists]**&#x200B;に移動し、複数の購買依頼を作成します（例：7）。
1. お客様トークンを生成したら、お客様に対して以下のGraphQL `requisition_lists` クエリを実行します。

   * ページのサイズが、作成した購買リストの合計数を下回っていることを確認します（例：4）。

   ```graphql
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

1. `total_count` フィールドの値が、4を表示する必要がある場合は7を示していることを確認します。

   項目の数は、*ページサイズ*&#x200B;と同じにする必要がある場合も7と表示されます。

<u>期待される結果</u>:

* *ページサイズ*&#x200B;としてリストされている数値は、`total_count`の下に返され、レコードの合計数ではありません。
* 項目数は&#x200B;*ページサイズ*&#x200B;と同じです。

<u>実際の結果</u>:

*ページサイズ*&#x200B;が指定されている場合でも、レコードの合計数は`total_count`に基づいて返されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
