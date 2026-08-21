---
title: ACSD-49392：部分的な払い戻し後、注文ステータスが「クローズ」に変更される
description: ACSD-49392 パッチを適用して、同梱商品の一部払い戻し後に注文ステータスがクローズに変わるAdobe Commerceの問題を修正します。
feature: Orders
role: Admin
exl-id: e12cbf2d-219e-4cb5-a226-6c7ae4929549
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# ACSD-49392：部分的な払い戻し後、注文ステータスが「クローズ」に変更される

>[!NOTE]
>
>パッチ ACSD-49392は、バージョン 2.4.6-p7から2.4.6-p10のパッチ [ACSD-57003](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-57003-order-status-changed-to-complete-instead-of-processing.md)に置き換えられました。

ACSD-49392 パッチは、バンドルされた製品の一部払い戻し後に注文状況がクローズに変わる問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.31がインストールされている場合に利用できます。 パッチ IDはACSD-49392です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.3.7 - 2.3.7-p4および2.4.1 - 2.4.6-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

バンドルされた商品の部分的な払い戻し後、注文ステータスが「クローズ」に変更されます。

<u>複製する手順</u>:

1. Adobe Commerceにログインして、バンドル商品を作成するか、既存のバンドル商品を使用します。
1. この同梱商品の数量が1を超える商品を注文します。
1. 管理者に移動し、**[!UICONTROL Sales]** > **[!UICONTROL Order]**&#x200B;から手順2で作成した注文を開き、請求書を作成します。 注文ステータスの監視： 処理中です。
1. 部分的なクレジットメモを作成します（バンドル内のすべての製品の払い戻しはしないでください）。
1. 注文状況を確認します。

<u>期待される結果</u>

バンドルされた製品の部分的なクレジットメモを作成した後、注文ステータスは処理中です。

<u>実際の結果</u>

同梱商品の部分的なクレジットメモを作成すると、注文ステータスが完了します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
