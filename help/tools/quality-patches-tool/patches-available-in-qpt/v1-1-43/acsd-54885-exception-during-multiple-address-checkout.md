---
title: ACSD-54885：管理者が顧客としてログインした際に、複数のアドレスのチェックアウト中に例外が発生する
description: ACSD-54885 パッチを適用すると、管理者が*[!UICONTROL Login as Customer]*機能を使用している際に、複数のアドレスのチェックアウト中にエラーが発生するAdobe Commerceの問題を修正できます。
feature: Checkout
role: Admin, Developer
exl-id: c146bc2a-2df1-4825-9cfc-69e04095b3c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54885：管理者が顧客としてログインした際に、複数のアドレスのチェックアウト中に例外が発生する

ACSD-54885 パッチは、管理者が *[!UICONTROL Login as Customer]* 機能を使用している際に、複数のアドレスのチェックアウト中にエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 がインストールされている場合に使用できます。 パッチ ID は ACSD-54885 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

管理者が *[!UICONTROL Login as Customer]* 機能を使用している場合、複数のアドレスのチェックアウト中にエラーが発生します。

<u> 再現手順 </u>:

1. *[!UICONTROL Login as Customer]* が有効になっていることを確認します。 **[!UICONTROL Admin]**/**[!UICONTROL Stores]**/**[!UICONTROL Configurations]**/**[!UICONTROL Advanced]**/**[!UICONTROL Admin]**/**[!UICONTROL Admin Actions]**/**[!UICONTROL Logging]**/**[!UICONTROL Login as Customer]** に移動します。
1. シンプルな製品を作成します。
1. 住所を使用して新しい顧客アカウントを作成します。
1. バックエンドの顧客アカウントに移動します。

   * 「**[!UICONTROL Account Information]**」タブに移動し、*[!UICONTROL Allow remote shopping assistance]* = *はい* に設定します。
   * 「**[!UICONTROL Login as Customer]**」をクリックします。

1. 商品を買い物かごに追加し、*[!UICONTROL Checkout with multiple addresses]* に進みます。
1. 製品数量を更新します。
1. 買い物かごに戻ってみてください。

<u> 期待される結果 </u>:

買い物かごを更新し、複数の住所のチェックアウトを使用できます。

<u> 実際の結果 </u>:

買い物かごに戻ると、次のエラーが発生します。

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
