---
title: 'ACSD-66434: [!UICONTROL Customer ID]が会社 [!DNL GraphQL]  クエリにありません'
description: ACSD-66434 パッチを適用して、[!UICONTROL Customer ID]が会社 [!DNL GraphQL] のクエリに見つからないAdobe Commerceの問題を修正します。
feature: B2B, GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: cd83c868-29d8-4d7c-9067-af7597056d35
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# ACSD-66434: [!UICONTROL Customer ID]が会社[!DNL GraphQL] クエリにありません

ACSD-66434 パッチは、会社[!DNL GraphQL]のクエリに&#x200B;**[!UICONTROL Customer ID]**&#x200B;が見つからない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67がインストールされている場合に利用できます。 パッチ IDはACSD-66434です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.6-p10 - 2.4.6-p11、2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL GraphQL]会社クエリは、会社構造内の&#x200B;**[!UICONTROL Customer ID]**&#x200B;に対して`null`を返します。

<u>複製する手順</u>:

1. B2Bおよびインベントリモジュールを使用してAdobe Commerce 2.4-developをインストールします。
1. Commerce管理者から、B2B機能を有効にして、テスト会社を作成します。
1. 次の[!DNL GraphQL]の突然変異を使用して、会社管理者のベアラートークンを生成します。

```graphql
mutation {
  generateCustomerToken(email: "admin_email@example.com", password: "admin_password") {
    token
  }
}
```

1. 生成されたトークンを使用して、次の[!DNL GraphQL] クエリを含む顧客の会社構造を取得します。

```graphql
query {
  company {
    id
    name
    legal_name
    structure {
      items {
        entity {
          __typename
          ... on Customer {
            firstname
            lastname
            email
            job_title
            id
          }
        }
      }
    }
  }
}
```

<u>期待される結果</u>:

会社[!DNL GraphQL] クエリで&#x200B;**[!UICONTROL Customer ID]**&#x200B;を返す必要があります。

<u>実際の結果</u>:

**[!UICONTROL Customer ID]**&#x200B;は、会社[!DNL GraphQL] クエリで`null`として返されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
