---
title: 'ACSD-65254: updateCustomerEmail [!DNL GraphQL] mutationを使用して顧客の電子メールを更新した後、電子メール通知が送信されない'
description: updateCustomerEmail [!DNL GraphQL] mutationを使用してアカウントのメールアドレスを正常に更新した後、メール通知がお客様に送信されなかったAdobe Commerceの問題を修正するには、ACSD-65254 パッチを適用します。
feature: GraphQL, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: a97daceb-98f6-4bb8-9847-692af700c0fd
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-65254: `updateCustomerEmail` [!DNL GraphQL]の突然変異を介して顧客の電子メールを更新した後、電子メール通知が送信されない

ACSD-65254 パッチは、`updateCustomerEmail` [!DNL GraphQL]の変異を使用してアカウントのメールアドレスを更新した後にメール通知が顧客に送信されなかった問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65がインストールされている場合に利用できます。 パッチ IDはACSD-65254です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`updateCustomerEmail` [!DNL GraphQL]の変異を使用してメールアドレスを更新した後、メール通知が顧客に送信されませんでした。

<u>複製する手順</u>:

1. 以下のミューテーションを使用してユーザーを作成：

   ```
   mutation {
       createCustomer(
           input: {
               firstname: "Test"
               lastname: "User"
               email: "test@test.com"
               password: "Admin@123"
               is_subscribed: true
           }
       ) {
           customer {
               created_at
           }
       }
   }
   ```

1. 以前に作成したユーザーのトークンを生成し、ベアラートークンとして使用します。

   ```
   mutation {
   generateCustomerToken(email: "test@test.com", password: "Admin@123") {
       token
   }
   }
   ```

1. 最後に作成されたベアラートークンを使用して、以前に作成したユーザーのメールを更新してみてください。

   ```
   mutation {
       updateCustomerEmail(email: "test+updated@test.com", password: "Admin@123") {
           customer {
               email
           }
       }
   }
   ```

<u>期待される結果</u>:

顧客は、アカウントのメールアドレスを更新した後、メール通知を受け取る必要があります。

<u>実際の結果</u>:

新しいアドレスには購読メールのみが送信されます。メールアドレスの変更の確認メールは送信されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
