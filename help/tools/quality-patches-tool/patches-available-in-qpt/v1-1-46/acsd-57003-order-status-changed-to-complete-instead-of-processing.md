---
title: ACSD-57003：注文ステータスが*Processing*に変更されずに*Complete*に変更される
description: ACSD-57003 パッチを適用して、注文ステータスが*Processing*に変わるのではなく*Complete*に変わるAdobe Commerceの問題を修正します。
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: a28ecc35-5c9a-4bba-b0b9-67fbe37ed8c3
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-57003：注文ステータスが&#x200B;*処理中*&#x200B;ではなく&#x200B;*完了*&#x200B;に変更される

ACSD-57003 パッチは、注文状態が&#x200B;*Processing*&#x200B;に変更されるのではなく&#x200B;*Complete*&#x200B;に変更される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.46がインストールされている場合に利用できます。 パッチ IDはACSD-57003です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方式） 2.4.6-p3、2.4.6-p8、2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.6 - 2.4.6-p9、2.4.7-p2 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

注文が部分的に返金され、部分的に発送された場合、注文ステータスは&#x200B;*処理中*&#x200B;に変更されるのではなく、*完了*&#x200B;に変更されます。

<u>複製する手順</u>:

1. 2つの設定可能な製品を使用して注文を作成します。
1. すべての項目に請求書を発行します。
1. 最初の商品のみを発送します。
1. 発送済みの商品（*最初の商品*）に対してのみ、クレジットメモを返金/作成します。
1. 注文状況を確認します。

<u>期待される結果</u>:

注文ステータスは&#x200B;_処理中_&#x200B;状態である必要があります。

<u>実際の結果</u>:

一部発送された商品のクレジットメモを作成すると、注文状況が&#x200B;*完了*&#x200B;に変更されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
