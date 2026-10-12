---
title: 'ACSD-61528: GraphQLを使用してロールを取得すると、結果が返されない'
description: ACSD-61528 パッチを適用して、GraphQLを使用して会社の管理者からロールを取得すると常にnull結果が返されるAdobe Commerceの問題を解決します。
feature: GraphQL, B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 81d78746-e723-4b18-860c-d973158b469c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: e439352c-5b67-587d-b34e-d2a0aa5a0242
    internal-label: Roles/Permissions
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%
---
# ACSD-61528: GraphQLを使用してロールを取得すると、結果が返されない

ACSD-61258 パッチでは、GraphQLを使用して会社の管理者からロールを取得すると、常にnull結果が返される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53がインストールされている場合に利用できます。 パッチ IDはACSD-61528です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQLを使用して会社の管理者からロールを取得する場合、ロールの結果は常にnullでした。

<u>前提条件：</u>:

Adobe Commerce B2B モジュールをインストールして有効にする。

<u>複製する手順</u>:

1. 会社を作成する。
1. 以下のミューテーションを持つGraphQLの会社管理者としてログインします。

   ```GraphQL
      mutation {
          generateCustomerToken(email: "company@admin.com", password: "PASSWORD") {
      token
      }
   }
   ```

1. 結果のトークンを&#x200B;**Authorization** リクエストヘッダーに`Bearer` トークンとして追加し、GraphQL クエリの下で実行します。

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

<u>期待される結果</u>:

GraphQL クエリは、ロールを返します。

<u>実際の結果</u>:

会社の役割はnullです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
