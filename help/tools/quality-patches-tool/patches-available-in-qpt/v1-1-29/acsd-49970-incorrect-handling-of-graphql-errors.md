---
title: ACSD-49970:GraphQL エラーの誤った処理
description: ACSD-49970 パッチを適用して、[!UICONTROL New Relic Reporting] がオンになっているときにAdobe Commerce エラーの誤った処理があるGraphQLの問題を修正してください。
feature: GraphQL, Observability
role: Admin
exl-id: f06f6cbf-ea85-406a-850d-f63e1001ff82
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-49970:GraphQL エラーの誤った処理

ACSD-49970 パッチでは、*[!UICONTROL New Relic Reporting]* がオンになっている場合にGraphQL エラーが誤って処理される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 がインストールされている場合に使用できます。 パッチ ID は ACSD-49970 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`GraphQLOperationNames` `logDataHelper` このキーが含まれているかどうかに関わらず、キーは正しく処理されません。

<u> 再現手順 </u>:

1. `bin/magento deploy:mode:set developer` を実行します。
1. 管理者にログインします。
1. **[!UICONTROL New Relic Integration]**/**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL General]** から **[!UICONTROL New Relic Reporting]** を有効にします
（メモ：[!DNL New Relic] 拡張機能が使用できないというエラーが表示された場合でも、設定は保存されます）。
1. *クライアントまたはその他のクライアントから、または cURL 経由で、* に対してこの `http://yourMagentoDomain/graphql`GraphQL *[!DNL Altair]* ミューテーションを実行します。

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   （メモ：実行する前に、**[!UICONTROL Header]** を [!UICONTROL Content-Currency:CA] に設定します）。

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u> 期待される結果 </u>:

ログに *500 例外がありません* キー `GraphQLOperationNames` 正しく処理されています。

<u> 実際の結果 </u>:

ログに *500 例外* があります。キー `GraphQLOperationNames` 正しく処理されていません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
