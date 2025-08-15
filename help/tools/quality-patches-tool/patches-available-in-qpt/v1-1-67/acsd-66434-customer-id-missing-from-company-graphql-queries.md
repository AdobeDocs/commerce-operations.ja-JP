---
title: ACSD-66434:company[!UICONTROL Customer ID]queries に  [!DNL GraphQL]  がありません
description: ACSD-66434 パッチを適用して、company[!UICONTROL Customer ID]queries に  [!DNL GraphQL]  が見つからないAdobe Commerceの問題を修正します。
feature: B2B, GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: cd83c868-29d8-4d7c-9067-af7597056d35
source-git-commit: e60194341bf79ca3ecdc505cf30f226b8f1b6c7f
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# ACSD-66434：会社 [!UICONTROL Customer ID] クエリに [!DNL GraphQL] がありません

ACSD-66434 パッチは、会社の **[!UICONTROL Customer ID]** クエリに [!DNL GraphQL] が見つからない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 がインストールされている場合に使用できます。 パッチ ID は ACSD-66434 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p10 - 2.4.6-p11、2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL GraphQL] の会社クエリは、会社構造内の `null` の **[!UICONTROL Customer ID]** を返します。

<u> 再現手順 </u>:

1. Adobe Commerce 2.4-develop を B2B および Inventory モジュールと共にインストールします。
1. Commerceの「管理者」で、「B2B 機能」を有効化し、テスト会社を作成します。
1. 次の [!DNL GraphQL] のバリエーションを使用して、会社管理者のベアラートークンを生成します。

```
mutation {
  generateCustomerToken(email: "admin_email@example.com", password: "admin_password") {
    token
  }
}
```

1. 生成されたトークンを使用して、次の [!DNL GraphQL] クエリで顧客の会社構造を取得します。

```
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

<u> 期待される結果 </u>:

**[!UICONTROL Customer ID]** は、会社 [!DNL GraphQL] クエリで返される必要があります。

<u> 実際の結果 </u>:

**[!UICONTROL Customer ID]** は、会社 `null` クエリで [!DNL GraphQL] として返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
