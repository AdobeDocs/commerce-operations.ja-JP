---
title: ACSD-54264：お客様が交渉可能な見積もりでチェックアウトしようとするとエラーが発生する
description: 「リクエストされた属性を更新できません」というエラーメッセージが表示されるAdobe Commerceの問題を修正するには、ACSD-54264 パッチを適用します。 お客様が別のストアビューから交渉可能な見積もりを使用してチェックアウトしようとすると、行ID:store_id」が表示されます。
feature: B2B, Checkout
role: Admin, Developer
exl-id: b1696228-b2ed-44eb-9e75-bf25ccf2f1cd
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# ACSD-54264：お客様が交渉可能な見積もりでチェックアウトしようとすると、エラーが表示される

ACSD-54264 パッチは、エラーメッセージ *要求された属性を更新できない問題を修正します。 お客様が別のストアビューから交渉可能な見積もりを使用してチェックアウトしようとすると、行ID : store_id*&#x200B;が表示されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.42がインストールされている場合に利用できます。 パッチ IDはACSD-54264です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

エラーメッセージ *要求された属性を更新できません。 お客様が別のストアビューから交渉可能な見積もりを使用してチェックアウトしようとすると、行ID : store_id*&#x200B;が表示されます。

<u>前提条件</u>:

Adobe Commerce B2B モジュールがインストールされ、有効になっている。

<u>複製する手順</u>:

1. デフォルトのweb サイトの追加ストアビューを作成します。
1. 設定で&#x200B;*[!UICONTROL B2B Quote]*&#x200B;を有効にします。
1. いずれかのストアビューで会社のお客様としてログインします。
1. 商品を&#x200B;*[!UICONTROL Shopping Cart]*&#x200B;に追加します。
1. 見積もりをレビュー用に送信します。
1. 管理者ユーザーとして、**[!UICONTROL Sales]** > **[!UICONTROL Quotes]**&#x200B;に移動し、承認済みの見積もりを送信します。
1. 会社のお客様として、ストアビューを別のストアビューに変更します。
1. チェックアウトしてみてください。

<u>期待される結果</u>:

お客様がこの見積もりで注文します。

<u>実際の結果</u>:

* 出荷情報の保存中にエラーが発生します。

  `You cannot update the request attribute. Row ID: store_id =#`

* 次のエラーが記録されます。

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
