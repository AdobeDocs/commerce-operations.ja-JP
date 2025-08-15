---
title: ACSD-52606：ユーザーが「注文の受け取りの準備が整ったことを通知」をクリックすると表示されるエラーメッセージ
description: ACSD-52606 パッチを適用して、**[!UICONTROL Notify Order is Ready for Pickup]**をクリックするとエラーメッセージが表示されるAdobe Commerceの問題を修正してください。
feature: Orders, User Account
role: Admin, Developer
exl-id: d0b5a7a6-0d32-4019-8f28-60722fce1a99
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-52606：ユーザーが「注文の受け取りの準備が整ったことを通知」をクリックすると表示されるエラーメッセージ

ACSD-52606 パッチは、ユーザーが *をクリックしたときにエラーメッセージ* 注文は受け取りの準備ができていません **[!UICONTROL Notify Order is Ready for Pickup]** が表示される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.37 がインストールされている場合に使用できます。 パッチ ID は ACSD-52606 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ユーザーが *をクリックすると、エラーメッセージ* 注文を受け取る準備ができていません **[!UICONTROL Notify Order is Ready for Pickup]** が画面に表示されます。

<u> 前提条件 </u>:

インベントリモジュールがインストールされます。

<u> 再現手順 </u>:

1. 新しいインスタンスをインストールします。
1. 新しいソースと在庫を作成します。
1. 新しいソースをデフォルトの web サイトに割り当てます。
1. 新しく作成されたソースの取得場所を有効にします。
1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Delivery Methods]**/**[!UICONTROL In-Store Delivery]** に移動し、**[!UICONTROL In-Store Delivery]** を有効にします。
1. すべての在庫と在庫に対して *QTY=0* の *在庫中* シンプル製品を作成し、両方の *[!UICONTROL Manage Stock = No]* ースに割り当てます。
1. 前の手順で作成した製品を使用して、フロントエンドから注文を作成し、配信方法として *[!UICONTROL In-Store Pickup]* を選択します。
1. 管理者で、**[!UICONTROL Sales]**/**[!UICONTROL Orders]**/**[!UICONTROL Invoice that order]** に移動します。
1. 「**[!UICONTROL Notify order is ready for pickup]**」をクリックします。

<u> 期待される結果 </u>:

エラーなしで通知されます。

<u> 実際の結果 </u>:

次のエラーメッセージが表示されます。*注文を受け取る準備ができていません*。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
