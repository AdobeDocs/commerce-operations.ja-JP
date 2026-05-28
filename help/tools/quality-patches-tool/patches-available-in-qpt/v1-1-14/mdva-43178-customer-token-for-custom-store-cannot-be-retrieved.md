---
title: 'MDVA-43178: カスタムストアの顧客トークンをGraphQLで取得できない'
description: MDVA-43178 パッチは、カスタムストアの顧客トークンをGraphQLで取得できない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.14がインストールされている場合に利用できます。 パッチ IDはMDVA-43178です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: GraphQL
role: Admin
exl-id: 8dd9c9e7-573c-4c7a-8fd0-3b3886649af3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# MDVA-43178: カスタムストアの顧客トークンをGraphQLで取得できない

MDVA-43178 パッチは、カスタムストアの顧客トークンをGraphQLで取得できない問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14がインストールされている場合に使用できます。 パッチ IDはMDVA-43178です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カスタムストアの顧客トークンは、GraphQLで取得できません。

<u>複製する手順</u>:

1. デフォルトストア用に2つのストアビューを作成します。
1. 新しいWeb サイト、1つのストア、1つのストアビューを作成します。 このストアビューに「test3」という名前を付けます。
1. 新しいweb サイトの顧客を作成する。
1. API管理トークンを生成：

   `http://domain/rest/all/V1/integration/admin/token`

   <pre>
    <code class="language-graphql">
    &lbrace;
      "username": "login",
      "password": "password"
    &rbrace;
    </code>
    </pre>

1. GraphQLを送信して、管理者として顧客トークンを取得します。管理者トークンを認証に使用し、ヘッダーに「store」 = 「test3」を付けます。

   <pre>
    <customer_email>
      </pre>

<u>期待される結果</u>:

顧客トークンが生成されます。

<u>実際の結果</u>:

顧客トークンが生成されない。 加盟店には、応答として&#x200B;*お客様の電子メールが存在しません*&#x200B;が表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
