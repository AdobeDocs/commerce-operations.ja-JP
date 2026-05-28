---
title: ACSD-49013：メール確認がweb サイトのロケールに翻訳されない
description: 一括APIを使用して顧客を作成する際に、メール確認がweb サイトのロケールに変換されないAdobe Commerceの問題を修正するには、ACSD-49013 パッチを適用します。
feature: Admin Workspace, Communications
role: Admin
exl-id: 1b0dc6aa-d5ee-4adf-882d-88f29a7eab34
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# ACSD-49013：メール確認がweb サイトのロケールに翻訳されない

ACSD-49013 パッチは、一括APIを使用して顧客を作成する際に、メール確認がweb サイトのロケールに変換されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27がインストールされている場合に利用できます。 パッチ IDはACSD-49013です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

一括APIを使用して顧客を作成する場合、メール確認はweb サイトのロケールに翻訳されません。

<u>複製する手順</u>:

1. `de_DE`のような別のロケールをインストールしてください。
1. *RabbitMQ*&#x200B;を設定します。
1. `bin/magento setup:upgrade`を実行してRabbitMQにキューをインストールし、言語パックを設定します。
1. [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**&#x200B;に追加のweb サイトを作成します。
1. この新しいWeb サイトのロケールを`de_DE`に設定します（[!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale Options]**）。
1. API呼び出しを実行して、一括APIを使用して顧客アカウントを作成します。 対応する`website_id`を使用します。

   `Endpoint: /rest/async/bulk/V1/customers`

   ```text
   [{
       "customer": {
       "email": "test@example.com",
       "firstname": "test",
       "lastname": "test",
       "website_id": 2
       },
       "password": "Passw0rd!"
   }]
   ```

1. `bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10`を実行します。
1. 指定したweb サイトで顧客アカウントが正しく作成されていることがわかります。
1. お客様登録用に受信したメールを確認します。

<u>期待される結果</u>:

お客様は指定のweb サイトで作成されるので、そのweb サイトのロケールを使用して登録メールが送信されます。

<u>実際の結果</u>:

指定したweb サイトで顧客が正しく作成されますが、bulk APIを使用すると、登録メールはデフォルトのロケールを使用して送信されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
