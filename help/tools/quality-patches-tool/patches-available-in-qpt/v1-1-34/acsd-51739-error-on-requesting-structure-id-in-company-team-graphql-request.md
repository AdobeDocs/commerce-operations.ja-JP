---
title: 'ACSD-51739: 「CompanyTeam」GraphQL リクエストの「structure_id」をリクエスト中にエラーが発生しました'
description: ACSD-51739 パッチを適用すると、「CompanyTeam」GraphQL リクエストで「structure_id」がリクエストされた場合にエラーが返されるAdobe Commerceの問題を修正できます。
exl-id: 74c78278-779d-4fb6-ba10-501b25b9f1fe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739:GraphQL リクエストで `structure_id` をリクエスト中にエラー `CompanyTeam` 発生しました

ACSD-51739 パッチは、`CompanyTeam` GraphQL リクエストで `structure_id` がリクエストされた場合にエラーが返される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34 がインストールされている場合に使用できます。 パッチ ID は ACSD-51739 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 ～ 2.4.7

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`CompanyTeam` GraphQL リクエストで `structure_id` がリクエストされると、エラーが返されます。

<u> 再現手順 </u>

1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL General]**/**[!UICONTROL B2B Features]** に移動し、*[!UICONTROL Enable Company]* を *はい* に設定します。
1. 会社を会社管理者ユーザーと共に作成します。
1. 新しい顧客（*customer1*）を作成し、会社（上記で作成）をこの顧客に割り当てます。
1. フロントエンドで、会社の管理者ユーザーとしてログインします。
1. 会社チームを作成し、ドラッグ&amp;ドロップでチームに *customer1* を割り当てます。
1. `structure_id` を含む `CompanyTeam` を含む、次の会社の GraphQl クエリを実行します。

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. GraphQLの応答を確認します。

<u> 期待される結果 </u>:

エラーは返されず、リクエストされたすべてのデータがGraphQL応答に存在します。

<u> 実際の結果 </u>:

* 応答に *内部サーバーエラー* が含まれています。
* `var/log/exception.log` には次が含まれます。

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
