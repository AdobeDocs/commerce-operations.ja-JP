---
title: ACSD-61528:GraphQLを使用してロールを取得しても、結果が返されない
description: ACSD-61528 パッチを適用すると、Adobe Commerceを使用して会社の管理者からロールを取得すると常に null 結果が返されるGraphQLの問題を解決できます。
feature: GraphQL, B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 81d78746-e723-4b18-860c-d973158b469c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61528:GraphQLを使用してロールを取得しても、結果が返されない

ACSD-61258 パッチでは、GraphQLを使用して会社の管理者からロールを取得すると、常に null 結果が返される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 がインストールされている場合に使用できます。 パッチ ID は ACSD-61528 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

GraphQLを使用して会社の管理者からロールを取得する場合、ロール結果は常に null でした。

<u> 前提条件：</u>:

Adobe Commerce B2B モジュールをインストールして有効にします。

<u> 再現手順 </u>:

1. 会社を作成します。
1. 以下のミューテーションを使用して、GraphQLに会社管理者としてログインします。

   ```GraphQL
      mutation {
          generateCustomerToken(email: "company@admin.com", password: "PASSWORD") {
      token
      }
   }
   ```

1. 結果のトークンを **トークンとして** Authorization`Bearer` リクエストヘッダーに追加し、GraphQL クエリの下で実行します。

   ```GraphQL
      {
      customer {
      email
      role{
       name
       id
      }
    }
   }
   ```

<u> 期待される結果 </u>:

GraphQL クエリは、ロールを返します。

<u> 実際の結果 </u>:

会社の役割が null です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
