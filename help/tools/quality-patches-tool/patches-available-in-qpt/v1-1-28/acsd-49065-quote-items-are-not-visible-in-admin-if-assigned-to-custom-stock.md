---
title: ACSD-49065：管理画面に見積もり項目が表示されない
description: 見積もり項目がカスタム在庫にのみ割り当てられている場合に、管理画面に見積もり項目が表示されないAdobe Commerceの問題を修正するには、ACSD-49065 パッチを適用します。
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
exl-id: fc3bea92-305b-4598-9915-3422d61c76ec
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# ACSD-49065：管理画面に見積もり項目が表示されない

ACSD-49065 パッチは、見積もり項目がカスタム在庫にのみ割り当てられている場合に、管理者に表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28がインストールされている場合に利用できます。 パッチ IDはACSD-49065です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

見積もり項目がカスタム在庫にのみ割り当てられている場合、見積もり項目は管理者に表示されません。

前提条件：

**[!UICONTROL B2B]**&#x200B;および&#x200B;**[!UICONTROL Inventory]** モジュールをインストールする必要があります。

<u>複製する手順</u>:

1. **[!UICONTROL Company]**&#x200B;と&#x200B;**[!UICONTROL B2B Quote]**&#x200B;を&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**&#x200B;で有効にします。
1. セカンダリ **[!UICONTROL Inventory Source]**&#x200B;を作成し、セカンダリ **[!UICONTROL Inventory Stock]**&#x200B;に割り当てます。
1. セカンダリ （デフォルト以外） **[!UICONTROL Inventory Source]**&#x200B;のみを割り当てて、新しい製品を作成します。
1. ストアフロントに移動し、新しい会社アカウントを作成します。 **[!UICONTROL Company Admin]**&#x200B;としてログインし、作成した商品をカートに追加します。
1. 買い物かごに移動して&#x200B;*[!UICONTROL Request a Quote]*。
1. 管理者に移動し、要求された見積もりを&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Quotes]**&#x200B;で表示します。

<u>期待される結果</u>:

新しい製品で作成された新しい見積もりには、製品を再保存することなくアイテムが表示されます。

<u>実際の結果</u>:

*[!UICONTROL Items Quoted]* セクションが空です。 新しく作成した商品を再保存すると、アイテムが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
