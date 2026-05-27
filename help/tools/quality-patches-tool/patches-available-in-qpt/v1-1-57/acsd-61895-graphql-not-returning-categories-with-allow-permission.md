---
title: 'ACSD-61895: [!DNL GraphQL]  カテゴリのクエリが、表示が制限されたプライベート共有カタログに対して失敗します'
description: ACSD-61895 パッチを適用して、同じカテゴリに対して制限を持つプライベート共有カタログが作成された場合、ゲストのお客様に対する [!DNL GraphQL] 応答が（許可されたすべてのカテゴリを含むパブリック共有カタログを使用して）カテゴリを返さないAdobe Commerceの問題を修正します。
feature: Categories, GraphQL, Roles/Permissions
role: Admin, Developer
exl-id: ef986fa6-e8bc-4322-80f2-fa0c5d5e8d40
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# ACSD-61895: [!DNL GraphQL] `categories` クエリが、ビューが制限されたプライベート共有カタログに対して失敗します

ACSD-61895 パッチでは、同じカテゴリに制限を持つプライベート共有カタログが作成されたときに、ゲスト顧客に対する[!DNL GraphQL]件の応答（許可されているすべてのカテゴリを含むパブリック共有カタログを使用）がカテゴリを返さない問題を修正します。

修正の後、ルートカテゴリがプライベート共有カタログの範囲で許可アクセス権を持っていない場合でも、ゲストユーザーに対する許可アクセス権（パブリック共有カタログ）を持つすべてのカテゴリが返されます。

このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-61895です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

同じカテゴリに対して制限を持つプライベート共有カタログを作成する場合、ゲスト顧客に対する[!DNL GraphQL]件の応答（許可されているすべてのカテゴリを含むパブリック共有カタログを使用）は、カテゴリを返しません。

<u>複製する手順</u>:

1. B2Bおよびサンプルデータを含むAdobe Commerceをインストールします。
1. B2B機能が有効になっていることを確認します。
1. 2つの共有カタログを作成します。1つはパブリックで、1つはプライベートです。

   * パブリック共有カタログ：

      * すべてのカテゴリをパブリックカタログに割り当てます。

   * プライベート共有カタログ：

      * `Gear` カテゴリとその子カテゴリのみをプライベートカタログに割り当てます。
      * テスト会社にプライベートカタログを割り当てます。

1. 会社ユーザーの作成：

   * プライベート共有カタログにリンクされたテスト会社に関連付けられたユーザーを作成します。
   * ユーザーがログイン時にフロントエンドで`Gear` カテゴリとその子カテゴリにのみアクセスできることを確認します。

1. API経由でカテゴリをクエリする：

   * API クライアントを使用して、顧客トークンなしで次の[!DNL GraphQL] クエリを実行します。

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
   * 同じ[!DNL GraphQL] カテゴリ クエリを実行しますが、ログイン ユーザーの顧客トークンを含めます。
   * 応答を監視し、`Gear` カテゴリとその子カテゴリのみが返されるかどうかを確認します。


<u>期待される結果</u>:

ゲスト企業ユーザーとしてクエリを実行する場合は、すべてのカテゴリを（想定どおりに）返す必要があります。

<u>実際の結果</u>:

`categories` クエリからの応答にカテゴリが表示されていません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
