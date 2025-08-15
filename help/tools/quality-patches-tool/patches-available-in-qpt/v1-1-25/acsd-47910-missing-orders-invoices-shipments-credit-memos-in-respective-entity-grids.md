---
title: ACSD-47910：各エンティティ・グリッドに受注、請求書、出荷およびクレジット・メモが欠落している
description: ACSD-47910 パッチを適用すると、それぞれのエンティティグリッドに注文、請求書、出荷、およびクレジットメモがないAdobe Commerceの問題を修正できます。
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 09115cf3-62c3-425e-bc99-e8971398dd20
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47910：各エンティティ・グリッドに受注、請求書、出荷およびクレジット・メモが欠落しています

ACSD-47910 パッチは、各エンティティグリッドに注文、請求書、出荷、およびクレジットメモがない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 がインストールされている場合に使用できます。 パッチ ID は ACSD-47910 です。 この問題が修正されるバージョンは、まだ利用できません。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1

**Adobe Commerce バージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

各エンティティ・グリッドに受注、請求書、出荷およびクレジット・メモが欠落しています。

<u> 再現手順 </u>:

1. **[!UICONTROL Asynchronous indexing]**/**[!UICONTROL Stores]**/**[!UICONTROL Settings]**/**[!UICONTROL Configuration]**/**[!UICONTROL Advanced]**/**[!UICONTROL Developer]** で **[!UICONTROL Grid Settings]** を有効にします。
1. 注文を 2 回行います。
1. cron を実行して、これらの注文をグリッドに同期します。
1. 注文の 1 つを開き、請求する準備を整えます。 まだ請求書を送信しないでください。
1. フロントエンドに配置する準備ができている新しい注文を作成します。 [PLACE ORDER] ボタンはまだクリックしないでください。
1. `sleep(30)` の `foreach` に `NotSyncedDataProvider::L43` を追加します。
1. `bin/magento cron:run` を実行します。
1. 次に、新しい注文を行います。
1. 以前の注文を請求します。
1. 新しい注文が同期されることを期待して、cron を再度実行します。
1. 管理の注文グリッドに移動します。

<u> 期待される結果 </u>:

新しいオーダーがオーダーグリッドに表示されます。

<u> 実際の結果 </u>:

前回の注文の更新がグリッドに同期されました（**[!UICONTROL status: Processing]**）。 新しい注文はグリッドに表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
