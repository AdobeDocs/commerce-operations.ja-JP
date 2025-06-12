---
title: ACSD-49013：メールの確認が web サイトのロケールに翻訳されない
description: ACSD-49013 パッチを適用すると、一括 API を使用して顧客を作成する際に、メールの確認が web サイトのロケールに翻訳されないAdobe Commerceの問題を修正できます。
feature: Admin Workspace, Communications
role: Admin
exl-id: 1b0dc6aa-d5ee-4adf-882d-88f29a7eab34
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-49013：メールの確認が web サイトのロケールに翻訳されない

ACSD-49013 パッチは、一括 API を使用して顧客を作成する際に、メールの確認が web サイトのロケールに翻訳されない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 がインストールされている場合に使用できます。 パッチ ID は ACSD-49013 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

一括 API を使用して顧客を作成する場合、メールの確認は web サイトのロケールに翻訳されません。

<u> 再現手順 </u>:

1. `de_DE` のように別のロケールをインストールします。
1. *RabbitMQ* を設定します。
1. `bin/magento setup:upgrade` を実行して RabbitMQ にキューをインストールし、言語パックを設定します。
1. [!UICONTROL Admin]/**[!UICONTROL Stores]**/**[!UICONTROL All Stores]** で、追加の web サイトを作成します。
1. [!UICONTROL Admin]/**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL General]**/**[!UICONTROL Locale Options]** で、この新しい Web サイトのロケールを `de_DE` に設定します。
1. API 呼び出しを実行して、一括 API を使用してカスタマーアカウントを作成します。 対応する `website_id` を使用します。

   `Endpoint: /rest/async/bulk/V1/customers`

   ```
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

1. `bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10` を実行します。
1. 指定した Web サイトで顧客アカウントが正しく作成されていることがわかります。
1. 受信した電子メールで顧客登録を確認します。

<u> 期待される結果 </u>:

顧客は指定した web サイトで作成されるので、登録メールは、その web サイトのロケールを使用して送信されます。

<u> 実際の結果 </u>:

顧客は指定した web サイトで正しく作成されますが、登録メールは、一括 API が使用される場合、デフォルトのロケールを使用して送信されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
