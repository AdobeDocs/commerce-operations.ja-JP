---
title: 'MDVA-43178: GraphQLでカスタム ストアの顧客トークンを取得できません'
description: MDVA-43178 パッチでは、カスタムストアのカスタムトークンをGraphQLで取得できない問題を修正しています。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.14 がインストールされている場合に利用できます。 パッチ ID は MDVA-43178。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: GraphQL
role: Admin
exl-id: 8dd9c9e7-573c-4c7a-8fd0-3b3886649af3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-43178: GraphQLでカスタム ストアの顧客トークンを取得できません

MDVA-43178 パッチでは、カスタムストアのカスタムトークンをGraphQLで取得できない問題を修正しています。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.14 がインストールされている場合に使用できます。 パッチ ID は MDVA-43178。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1 - 2.4.4

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

カスタムストアのカスタムトークンは、GraphQLで取得できません。

<u> 再現手順 </u>:

1. デフォルトストアに対して 2 つのストア表示を作成します。
1. 新しい Web サイト、1 つのストア、1 つのストアビューを作成します。 このストア表示に「test3」という名前を付けます。
1. 新しい web サイトの顧客を作成します。
1. API 管理トークンを生成：

   `http://domain/rest/all/V1/integration/admin/token`

   <pre>
    <code class="language-graphql">
    {
      "username": "login",
      "password": "password"
    }
    </code>
    </pre>

1. GraphQLを送信して、管理者としてカスタマートークンを取得します。認証には管理者トークンを使用します。ヘッダーには「store」 = 「test3」と記載されています。

   <pre>
    <customer_email>
      </pre>

<u> 期待される結果 </u>:

顧客トークンが生成されます。

<u> 実際の結果 </u>:

顧客トークンが生成されていません。 マーチャントは、応答して *提供された顧客のメールは存在しません* を取得します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
