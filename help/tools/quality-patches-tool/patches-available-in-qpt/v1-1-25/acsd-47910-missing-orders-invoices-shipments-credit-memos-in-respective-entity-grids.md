---
title: ACSD-47910：それぞれのエンティティグリッドの注文、請求書、出荷、クレジットメモが見つからない
description: ACSD-47910 パッチを適用して、それぞれのエンティティグリッドに注文、請求書、出荷、およびクレジットメモが見つからないAdobe Commerceの問題を修正します。
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 09115cf3-62c3-425e-bc99-e8971398dd20
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-47910：各エンティティグリッドの注文、請求書、出荷、クレジットメモが見つからない

ACSD-47910 パッチでは、それぞれのエンティティのグリッドに注文、請求書、出荷、およびクレジットメモが見つからない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.25がインストールされている場合に利用できます。 パッチ IDはACSD-47910です。 この問題が修正されるバージョンはまだ利用できません。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

それぞれのエンティティ・グリッドに注文、請求書、出荷およびクレジット・メモがありません。

<u>複製する手順</u>:

1. **[!UICONTROL Asynchronous indexing]**&#x200B;を&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**&#x200B;で有効にします。
1. 2つの注文を行います。
1. cronを実行して、注文をグリッドに同期します。
1. 注文の1つを開き、請求書を発行する準備をしてください。 請求書はまだ送信しないでください。
1. 新しい注文を作成し、フロントエンドに配置します。 まだ「注文を配置」ボタンをクリックしないでください。
1. `NotSyncedDataProvider::L43`の`foreach`に`sleep(30)`を追加します。
1. `bin/magento cron:run`を実行します。
1. 新しい順序を配置します。
1. 前回の注文を請求書に記入します。
1. 新しい注文が同期されることを期待して、cronを再度実行します。
1. 管理画面の注文グリッドに移動します。

<u>期待される結果</u>:

新しい注文が注文グリッドに表示されます。

<u>実際の結果</u>:

前回の注文更新がグリッド （**[!UICONTROL status: Processing]**）に同期されました。 新しい注文はグリッドに表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
