---
title: ACSD-66965：ページ [!UICONTROL Print] オプション [!UICONTROL Requisition List] するとエラーが発生する
description: ACSD-66965 パッチを適用すると、[!UICONTROL Print] ページの [!UICONTROL Requisition List] オプションが原因でエラーが発生するAdobe Commerceの問題を修正できます。
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7682a326a6c703a08dd6d0fac5319ac38e1bc3c8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-66965：ページ **[!UICONTROL Print]** オプション **[!UICONTROL Requisition List]** するとエラーが発生する

ACSD-66965 パッチでは、**[!UICONTROL Print]** ページの **[!UICONTROL Requisition List]** オプションが原因でエラーが発生する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 がインストールされている場合に使用できます。 パッチ ID は ACSD-66965 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**[!UICONTROL Print]** ページの **[!UICONTROL Requisition List]** オプションを選択すると、`Grid.php` での null オブジェクト参照が原因でエラーが発生します。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/*[!UICONTROL Settings]*/**[!UICONTROL Configuration]**/**[!UICONTROL General]**/**[!UICONTROL B2B Features]** に移動します。
1. **[!UICONTROL Enable Company]**、**[!UICONTROL Enable Shared Catalog]** および **[!UICONTROL Enable Requisition List]** を `Yes` に設定します。
1. 2 つのシンプルな製品を作成します。
1. ストアフロントにログインし、**[!UICONTROL My Account]** のページを開きます。
1. 購買依頼リストの作成。
1. 両方の製品を購買依頼リストに割り当てます。
1. 購買依頼リストにアクセスし、製品をリストします。
1. 「**[!UICONTROL Print]**」をクリックします。

<u> 期待される結果 </u>:

**[!UICONTROL Print]** ページの「**[!UICONTROL Requisition List]**」オプションを選択すると、印刷プレビューがエラーなしで表示されます。

<u> 実際の結果 </u>:

次のエラーメッセージが表示されます。*アプリケーションの実行中にエラーが発生しました。 詳しくは、例外ログを参照してください。*

```
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
