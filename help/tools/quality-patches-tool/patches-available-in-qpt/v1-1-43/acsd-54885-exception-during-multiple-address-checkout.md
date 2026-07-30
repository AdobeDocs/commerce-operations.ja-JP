---
title: ACSD-54885：管理者が顧客としてログインする際の複数のアドレスチェックアウト中に例外が発生する
description: 管理者が*[!UICONTROL Login as Customer]*機能を使用しているときに複数のアドレスのチェックアウト中にエラーが発生するAdobe Commerceの問題を修正するには、ACSD-54885 パッチを適用します。
feature: Checkout
role: Admin, Developer
exl-id: c146bc2a-2df1-4825-9cfc-69e04095b3c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# ACSD-54885：管理者が顧客としてログインする際の複数のアドレスチェックアウト中に例外が発生する

ACSD-54885 パッチは、管理者が&#x200B;*[!UICONTROL Login as Customer]*&#x200B;機能を使用しているときに複数のアドレス チェックアウト中にエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43がインストールされている場合に利用できます。 パッチ IDはACSD-54885です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者が&#x200B;*[!UICONTROL Login as Customer]*&#x200B;機能を使用している場合、複数アドレスのチェックアウト中にエラーが発生します。

<u>複製する手順</u>:

1. *[!UICONTROL Login as Customer]*&#x200B;が有効になっていることを確認します。 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**&#x200B;に移動します。
1. シンプルな商品の作成。
1. アドレスを持つ新しい顧客アカウントを作成します。
1. バックエンドの顧客アカウントに移動します。

   * **[!UICONTROL Account Information]** タブに移動し、*[!UICONTROL Allow remote shopping assistance]* = *はい*&#x200B;と設定します。
   * **[!UICONTROL Login as Customer]**&#x200B;をクリックします。

1. 商品をカートに追加し、*[!UICONTROL Checkout with multiple addresses]*&#x200B;に進みます。
1. 製品数量を更新します。
1. ショッピングカートに戻ってみましょう。

<u>期待される結果</u>:

買い物かごを更新し、複数の住所のチェックアウトを使用できます。

<u>実際の結果</u>:

ショッピングカートに戻ると、次のエラーが表示されます。

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
