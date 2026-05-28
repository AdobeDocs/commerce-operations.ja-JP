---
title: ACSD-54418：動的に価格が設定されたバンドルの子商品に誤って割引額が追加される問題を修正しました
description: ACSD-54418 パッチを適用して、動的に価格が設定されたバンドルの各子商品に固定割引額が誤って適用されるAdobe Commerceの問題を修正します。
feature: Shopping Cart
role: Admin, Developer
exl-id: f7b57361-9056-4eec-a393-dadb65aa595b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54418：動的に価格が設定されたバンドルの子商品に誤って割引額が追加される問題を修正しました。

ACSD-54418 パッチは、動的に価格が設定されたバンドルの各子製品に固定割引額が誤って適用される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.42がインストールされている場合に利用できます。 パッチ IDはACSD-54418です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

動的に価格が設定されたバンドルの各子商品に、固定割引額が誤って適用される。

<u>複製する手順</u>:

1. 動的な価格設定と&#x200B;*2*&#x200B;個のバンドルオプションを使用して&#x200B;**[!UICONTROL bundle product]**&#x200B;を作成します。
1. バンドルされた製品&#x200B;**[!UICONTROL SKU]**&#x200B;にのみ適用され、固定割引が適用される特定のクーポンコードを使用して&#x200B;**[!UICONTROL cart price rule]**&#x200B;を作成します。
1. 商品をカートに追加します。
1. **[!UICONTROL coupon code]**&#x200B;を適用します。
1. ショッピングカートに適用される割引を確認します。

<u>期待される結果</u>:

割引は、同梱商品全体に1回のみ適用されます。

<u>実際の結果</u>:

割引は各バンドル子商品に適用されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
