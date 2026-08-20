---
title: ACSD-52606：ユーザーが「注文に通知する受け取り準備完了」をクリックするとエラーメッセージが表示される
description: ユーザーが**[!UICONTROL Notify Order is Ready for Pickup]**をクリックするとエラーメッセージが表示されるAdobe Commerceの問題を修正するには、ACSD-52606 パッチを適用します。
feature: Orders, User Account
role: Admin, Developer
exl-id: d0b5a7a6-0d32-4019-8f28-60722fce1a99
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# ACSD-52606：ユーザーが「注文に通知する受け取り準備完了」をクリックするとエラーメッセージが表示される

ACSD-52606 パッチでは、ユーザーが&#x200B;**[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;をクリックしたときに「*注文は受け取り準備ができていません*」というエラーメッセージが表示される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.37がインストールされている場合に利用できます。 パッチ IDはACSD-52606です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ユーザーが&#x200B;**[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;をクリックすると、「*注文は受け取り準備ができていません*」というエラーメッセージが画面に表示されます。

<u>前提条件</u>:

在庫モジュールが取り付けられています。

<u>複製する手順</u>:

1. 新しいインスタンスをインストールします。
1. 新しいソースと在庫を作成する。
1. 新しいソースをデフォルトのweb サイトに割り当てます。
1. 新しく作成したソースの受け取り場所を有効にします。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**&#x200B;に移動し、**[!UICONTROL In-Store Delivery]**&#x200B;を有効にします。
1. すべての在庫と&#x200B;*[!UICONTROL Manage Stock = No]*&#x200B;に対して&#x200B;*QTY=0*&#x200B;を持つ&#x200B;*In Stock*&#x200B;のシンプルな商品を作成し、両方のソースに割り当てます。
1. 前の手順で作成した製品でフロントエンドから注文を作成し、配信方法として&#x200B;*[!UICONTROL In-Store Pickup]*&#x200B;を選択します。
1. 管理画面で、**[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**&#x200B;に移動します。
1. **[!UICONTROL Notify order is ready for pickup]**&#x200B;をクリックします。

<u>期待される結果</u>:

エラーなく通知されます。

<u>実際の結果</u>:

次のエラーメッセージが表示されます。*注文は受け取り準備ができていません*。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
