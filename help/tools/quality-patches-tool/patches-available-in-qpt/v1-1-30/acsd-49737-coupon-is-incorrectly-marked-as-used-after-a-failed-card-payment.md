---
title: ACSD-49737：カード支払いに失敗した後、クーポンが「使用されている」と誤ってマークされる
description: ACSD-49737 パッチを適用して、カード支払いに失敗した後にクーポンが「使用されました」と誤ってマークされるAdobe Commerceの問題を修正します。
feature: Orders, Payments
role: Admin
exl-id: 09060026-8d64-49f6-a85a-3230a52030fb
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-49737: カード決済が失敗した後、クーポンが&#x200B;*used*&#x200B;として誤ってマークされる

ACSD-49737 パッチでは、カード支払いに失敗した後にクーポンが&#x200B;*used*&#x200B;として誤ってマークされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.30がインストールされている場合に利用できます。 パッチ IDはACSD-49737です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カード決済に失敗した後、クーポンに&#x200B;*used*&#x200B;という誤ったマークが付けられます。

<u>前提条件</u>:

1. **[!UICONTROL Braintree sandbox payment]** メソッドを設定します。
1. [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=ja) コンシューマーがセットアップおよび実行されていることを確認します。

<u>複製する手順</u>:

1. 自動生成されたクーポンコードを使用して&#x200B;**[!UICONTROL Cart Price Rule]**&#x200B;を作成します。
1. 顧客としてログインします。
1. 商品をカートに追加します。
1. 自動生成されたクーポンコードを適用する。
1. 支払いが失敗した注文を試みます。
1. 「**[!UICONTROL Manage Coupon Codes]**」タブの「**[!UICONTROL Cart Price Rule]**」でクーポンの使用状況を確認します。

<u>期待される結果</u>:

支払いが失敗した場合、クーポンを&#x200B;*used*&#x200B;としてフラグ付けしないでください。

<u>実際の結果</u>:

* クーポンコードが表示されます – 使用済み：*はい*、使用回数：*1*
* クーポンコードは、1回限りの使用にのみ有効です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## パッチのインストール後に必要な追加手順

（このセクションはオプションです。問題を修正するためにパッチを適用した後に必要な手順がいくつかある場合があります）。 

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
