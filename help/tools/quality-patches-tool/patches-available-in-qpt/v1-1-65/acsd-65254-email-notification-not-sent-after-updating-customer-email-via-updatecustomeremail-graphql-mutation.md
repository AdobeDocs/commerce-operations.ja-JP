---
title: ACSD-65254:updateCustomerEmail [!DNL GraphQL] mutation を使用して顧客メールを更新した後、メール通知が送信されない
description: ACSD-65254 パッチを適用すると、updateCustomerEmail [!DNL GraphQL] mutation を使用してアカウントのメールアドレスを正常に更新した後に、メール通知が顧客に送信されないAdobe Commerceの問題を修正できます。
feature: GraphQL, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: a97daceb-98f6-4bb8-9847-692af700c0fd
source-git-commit: 7e9598e3ac0558706ef98ca81c19d27c37f7e860
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-65254:`updateCustomerEmail` ミューテーションを使用して顧客メールを更新した後、メール通知 [!DNL GraphQL] 送信されない

ACSD-65254 パッチは、`updateCustomerEmail` [!DNL GraphQL] のミューテーションを使用してアカウントのメールアドレスを更新した後、メール通知が顧客に送信されない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 がインストールされている場合に使用できます。 パッチ ID は ACSD-65254 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`updateCustomerEmail` [!DNL GraphQL] ミューテーションを使用してメールアドレスを更新した後、顧客にメール通知が送信されませんでした。

<u> 再現手順 </u>:

1. 以下のミューテーションを使用してユーザーを作成します。

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

<u> 期待される結果 </u>:

顧客は、アカウントのメールアドレスを更新すると、メール通知が届きます。

<u> 実際の結果 </u>:

新しいアドレスには購読メールのみが送信されます。メールアドレスの変更に関する確認メールは送信されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
