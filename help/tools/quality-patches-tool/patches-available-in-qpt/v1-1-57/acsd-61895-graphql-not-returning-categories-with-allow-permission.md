---
title: '表示が制限されたプライベート共有カタログの ACSD-61895: [!DNL GraphQL] categories クエリが失敗する'
description: '同じカテゴリに対して制限付きのプライベート共有カタログが作成された場合、（許可されたすべてのカテゴリを含むパブリック共有カタログを使用して）ゲスト顧客の応答がカテゴリを返さないAdobe Commerceの問題を修正するために ACSD-61895 パッチを適用します  [!DNL GraphQL] '
feature: Categories, GraphQL, Roles/Permissions
role: Admin, Developer
exl-id: ef986fa6-e8bc-4322-80f2-fa0c5d5e8d40
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# ACSD-61895：表示が制限されたプライベート共有カタログの [!DNL GraphQL] `categories` クエリが失敗する

ACSD-61895 パッチは、同じカテゴリに対して制限を持つプライベート共有カタログが作成された場合に、ゲスト顧客の [!DNL GraphQL] 応答（許可されたすべてのカテゴリを含むパブリック共有カタログを使用）がカテゴリを返さなかった問題を修正します。

修正後、ルートカテゴリがプライベート共有カタログのスコープ内で許可する権限を持っていない場合でも、ゲストユーザーのすべてのカテゴリと許可する権限（パブリック共有カタログ）が返されます。

このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-61895 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

同じカテゴリに対して制限を持つプライベート共有カタログを作成する場合、ゲスト顧客の [!DNL GraphQL] 応答（許可されたすべてのカテゴリを含むパブリック共有カタログを使用）では、カテゴリは返されません。

<u> 再現手順 </u>:

1. B2B とサンプルデータを使用してAdobe Commerceをインストールする
1. B2B 機能が有効になっていることを確認します。
1. 2 つの共有カタログ（1 つのパブリックと 1 つのプライベート）を作成します。

   * 公開共有カタログ :

      * すべてのカテゴリを公開カタログに割り当てます。

   * プライベート共有カタログ：

      * `Gear` カテゴリとその子カテゴリのみをプライベート カタログに割り当てます。
      * プライベートカタログをテスト会社に割り当てます。

1. 会社ユーザーを作成します。

   * プライベート共有カタログにリンクされたテスト会社に関連付けられたユーザーを作成します。
   * ユーザーが、ログインしたときに、フロントエンドの `Gear` カテゴリとその子カテゴリにのみアクセスできることを確認します。

1. API を使用してカテゴリをクエリします。

   * API クライアントを使用して、顧客トークンなしで次の [!DNL GraphQL] クエリを実行します。

   ```graphql
   query Categories { 
       categories { 
           items { 
               children_count 
               children { 
                   uid 
                   name 
                   children_count 
                   children { 
                   uid 
                   name 
                   } 
               } 
           } 
       } 
   }
   ```

1. 応答を監視し、`Gear` カテゴリと他のカテゴリが返されるかどうかを確認します。
1. 次に、顧客トークンを使用してカテゴリをクエリします。

   * テスト会社ユーザーとしてログインします。
   * 同じ [!DNL GraphQL] カテゴリクエリを実行し、ログインユーザーの顧客トークンを含めます。
   * 応答を監視し、`Gear` カテゴリとその子カテゴリのみが返されるかどうかを確認します。


<u> 期待される結果 </u>:

ゲストの会社ユーザーとしてクエリを実行する場合は、すべてのカテゴリが（期待どおりに）返されます。

<u> 実際の結果 </u>:

`categories` クエリからの応答にカテゴリが表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
