---
title: ACSD-47803：在庫切れ設定可能な商品スウォッチが使用可能として表示される
description: ACSD-47803 パッチを適用して、在庫切れの設定可能な商品スウォッチが使用可能として表示されるAdobe Commerceの問題を修正します。
feature: Configuration, Orders, Products
role: Admin
exl-id: c1b80949-65ed-4a44-8be4-25decda32142
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-47803：在庫切れ設定可能な商品スウォッチが使用可能として表示される

ACSD-47803 パッチは、在庫切れの設定可能な製品スウォッチが使用可能な状態で表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24がインストールされている場合に利用できます。 パッチ IDはACSD-47803です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

在庫切れの設定可能な商品スウォッチが利用可能として表示されます。

<u>複製する手順</u>:

>[!NOTE]
>
>以下の手順では、サンプルデータを例として示します。

1. [!UICONTROL Commerce]管理者で、**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]**&#x200B;に移動し、**[!UICONTROL Display Out of Stock Products]**&#x200B;を&#x200B;*はい*&#x200B;に設定します。
1. 繰り返しますが、管理者から&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動し、製品編集ページで設定可能な製品を編集します（サンプルデータを使用している場合は「WB04」 SKUなど）。
   * いずれかの設定バリアントの場合、数量を&#x200B;*0*&#x200B;に設定します（例：「WB04-M-Purple」）。
1. 次に、ストアフロントで設定可能な製品を開きます。
1. 在庫がゼロの設定可能なバリエーションの商品サイズ（M）を選択します。

<u>期待される結果</u>:

在庫切れオプションは無効になり、[!UICONTROL Out of Stock]としてマークされます。

<u>実際の結果</u>:

すべての色見本が有効になります（例えば[!UICONTROL Out of Stock]）。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
