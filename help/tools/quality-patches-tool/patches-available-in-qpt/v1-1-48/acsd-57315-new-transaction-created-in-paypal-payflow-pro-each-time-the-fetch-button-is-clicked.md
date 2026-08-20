---
title: 'ACSD-57315: フェッチ ボタンをクリックするたびに [!DNL PayPal Payflow Pro] に新しいトランザクションが作成される'
description: 「[!UICONTROL Admin]」の「トランザクションを表示」画面で「フェッチ」ボタンをクリックするたびに、新しいトランザクションが [!DNL PayPal Payflow Pro] に作成されるAdobe Commerceの問題を修正するには、ACSD-57315 パッチを適用します。
feature: Payments
role: Admin, Developer
exl-id: 1fb8a5af-fda1-4c24-859d-d45424bde12f
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-57315：取得ボタンをクリックするたびに[!DNL PayPal Payflow Pro]に新しいトランザクションが作成される

ACSD-57315 パッチは、[!UICONTROL Admin]のトランザクションの表示画面でフェッチ ボタンをクリックするたびに[!DNL PayPal Payflow Pro]に新しいトランザクションが作成される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.48がインストールされている場合に利用できます。 パッチ IDはACSD-57315です。 この問題は、Adobe Commerce 2.5.0で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!UICONTROL Admin]の「トランザクションを表示」画面でフェッチ ボタンをクリックするたびに、[!DNL PayPal Payflow Pro]に新しいトランザクションが作成されます。

<u>複製する手順</u>:

1. [!DNL PayPal Payflow Pro]を設定します。
1. トランザクション方法を&#x200B;*[!UICONTROL Sale]*&#x200B;に設定します。
1. *クレジットカード*&#x200B;で注文します。
1. [!UICONTROL Admin]からのトランザクションを開きます。
1. 「**[!UICONTROL Fetch]**」ボタンをクリックします。
1. 配置された注文に関連するトランザクションについて、[!DNL PayPal] アカウントを確認してください。

<u>期待される結果</u>:

新しい支払いトランザクションは作成されません。

<u>実際の結果</u>:

既に支払われた注文に対して、新しい支払いトランザクションが作成されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
