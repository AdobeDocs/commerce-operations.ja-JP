---
title: 'ACSD-51739: ''CompanyTeam'' GraphQL リクエストで''structure_id''をリクエスト中にエラーが発生しました'
description: ACSD-51739 パッチを適用して、「CompanyTeam」GraphQL リクエストで「structure_id」がリクエストされたときにエラーが返されるAdobe Commerceの問題を修正します。
exl-id: 74c78278-779d-4fb6-ba10-501b25b9f1fe
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# ACSD-51739: `CompanyTeam` GraphQL リクエストで`structure_id`をリクエスト中にエラーが発生しました

ACSD-51739 パッチは、`CompanyTeam` GraphQL リクエストで`structure_id`がリクエストされたときにエラーが返される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34がインストールされている場合に利用できます。 パッチ IDはACSD-51739です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`CompanyTeam` GraphQL リクエストで`structure_id`が要求されると、エラーが返されます。

<u>複製する手順</u>

1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**&#x200B;に移動し、*[!UICONTROL Enable Company]*&#x200B;を&#x200B;*Yes*&#x200B;に設定します。
1. 会社を会社管理者ユーザーと共に作成します。
1. 新しい顧客（*customer1*）を作成し、（上記で作成した）会社をこの顧客に割り当てます。
1. フロントエンドでは、会社管理者ユーザーとしてログインします。
1. 会社チームを作成し、ドラッグ&amp;ドロップを使用して&#x200B;*customer1*&#x200B;をチームに割り当てます。
1. `CompanyTeam`と`structure_id`を含む次の会社のGraphQl クエリを実行します。

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

<u>期待される結果</u>:

エラーは返されず、要求されたすべてのデータがGraphQL応答に存在します。

<u>実際の結果</u>:

* 応答に&#x200B;*内部サーバーエラー*&#x200B;が含まれています。
* `var/log/exception.log`の内容：

  ```yaml
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
