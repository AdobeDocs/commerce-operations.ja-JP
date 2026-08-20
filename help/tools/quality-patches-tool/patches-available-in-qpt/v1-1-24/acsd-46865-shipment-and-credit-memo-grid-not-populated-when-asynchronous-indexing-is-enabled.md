---
title: '[!UICONTROL asynchronous indexing]が有効になっている場合、ACSD-46865: [!UICONTROL shipment]と[!UICONTROL credit memo]は入力されません'
description: ACSD-46865 パッチを適用して、[!UICONTROL asynchronous indexing]が有効になっているときに[!UICONTROL shipment]と[!UICONTROL credit memo] グリッドが入力されないAdobe Commerceの問題を修正します。
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 6f84f5b6-6c34-476c-aae5-9a8ba306f8e4
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# [!UICONTROL asynchronous indexing]が有効になっている場合、ACSD-46865: [!UICONTROL shipment]と[!UICONTROL credit memo]は入力されません

ACSD-46865 パッチは、[!UICONTROL asynchronous indexing]が有効になっている場合に[!UICONTROL shipment]と[!UICONTROL credit memo] グリッドが入力されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24がインストールされている場合に利用できます。 パッチ IDはACSD-46865です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!UICONTROL asynchronous indexing]が有効になっている場合、[!UICONTROL Shipment]と[!UICONTROL credit memo] グリッドは入力されません。

<u>複製する手順</u>:

1. [!DNL Commerce]管理者で、**[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *YES*&#x200B;に移動します。
2. もう一度&#x200B;**[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*&#x200B;に移動します。
3. 設定キャッシュをクリアします。
4. シンプルな商品のために新しいゲスト注文を行います。
5. cronを実行します。
6. **[!UICONTROL Sales]** > **[!UICONTROL Orders]**&#x200B;に移動して、[!UICONTROL Commerce]管理者で注文を開き、請求書とクレジットメモを生成します。
7. 注文を[!UICONTROL Archive]に移動します。
8. シンプルな商品のために別の注文を作成します。
9. cronを実行します。
10. 新しい注文に移動し、新しい配送、請求書、クレジットメモを生成します。
11. cronを実行します。
12. 管理画面で[!UICONTROL shipments]、[!UICONTROL invoices]、[!UICONTROL credit memo] グリッドを確認します。

<u>期待される結果</u>:

新しい[!UICONTROL shipment]、[!UICONTROL invoice]、[!UICONTROL credit memo]が表示されます。

<u>実際の結果</u>:

新しい[!UICONTROL shipment]、[!UICONTROL invoice]、[!UICONTROL credit memo]は表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
