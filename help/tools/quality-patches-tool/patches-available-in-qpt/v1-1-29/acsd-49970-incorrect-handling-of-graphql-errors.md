---
title: ACSD-49970:GraphQL エラーの誤った処理
description: '[!UICONTROL New Relic Reporting]がオンになっているときにGraphQL エラーの処理が正しくない場合にAdobe Commerceの問題を修正するには、ACSD-49970 パッチを適用します。'
feature: GraphQL, Observability
role: Admin
exl-id: f06f6cbf-ea85-406a-850d-f63e1001ff82
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-49970:GraphQL エラーの誤った処理

ACSD-49970 パッチは、*[!UICONTROL New Relic Reporting]*&#x200B;がオンになっているときにGraphQL エラーを正しく処理できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29がインストールされている場合に利用できます。 パッチ IDはACSD-49970です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`logDataHelper`にこのキーが含まれているかどうかに関係なく、`GraphQLOperationNames` キーは正しく処理されません。

<u>複製する手順</u>:

1. `bin/magento deploy:mode:set developer`を実行します。
1. Adminにログインします。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]**&#x200B;から&#x200B;**[!UICONTROL New Relic Integration]**&#x200B;を有効にする> **[!UICONTROL New Relic Reporting]**
（注：[!DNL New Relic]拡張機能が利用できないというエラーが表示された場合でも、設定は保存されます）。
1. この&#x200B;*GraphQL*&#x200B;のミューテーションを`http://yourMagentoDomain/graphql`に&#x200B;*[!DNL Altair]* クライアントまたは他のクライアントから、またはcURL経由で実行します。

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   （注：**[!UICONTROL Header]**&#x200B;を[!UICONTROL Content-Currency:CA]に設定してから実行してください）。

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>期待される結果</u>:

ログに&#x200B;*500例外*&#x200B;はなく、`GraphQLOperationNames` キーが正しく処理されています。

<u>実際の結果</u>:

ログに&#x200B;*500例外*&#x200B;があり、`GraphQLOperationNames` キーが正しく処理されていません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
