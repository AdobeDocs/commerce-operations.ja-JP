---
title: ACP2E-3689：カテゴリツリーに関する複数の問題が、より深いレベルで表示され、アンカー/アンカー以外の関係が反映されます
description: ACP2E-3689 パッチを適用して、深さ 4 以上のネストおよびアンカー/アンカー以外の関係の反映にカテゴリツリーが表示されるAdobe Commerceの問題を修正してください。
feature: Categories, Page Content
role: Admin, Developer
source-git-commit: af8b7b44274b828b3f60f92fd78f9f3d3983abb8
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---


# ACP2E-3689：カテゴリツリーに関する複数の問題が、より深いレベルで表示され、アンカー/アンカー以外の関係が反映されます

>[!NOTE]
>
>このパッチは、バージョン 2.4.7 以降の [ACSD-62689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-62689-customer-add-categories-issue-related-product-rules-and-widgets.md) に代わるものです。

ACP2E-3689 パッチは、深さ 4 以上のネストおよびアンカー/アンカー以外の関係を反映したカテゴリツリー表示に関する複数の問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 がインストールされている場合に使用できます。 パッチ ID は ACP2E-3689 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

深いレベル（4+）のカテゴリツリーが正しく表示されず、アンカー/アンカー以外の関係が反映されています。

<u> 再現手順 </u>:

1. 4 レベルを超えるネストされたカテゴリを含むカテゴリツリーを設定します。
1. 様々な場所に表示される管理者のカテゴリツリーを展開します。
   1. [!UICONTROL Related Products Rule] を設定し、カテゴリに基づいて条件を設定します。
   1. ウィジェットを作成し、[!UICONTROL Layout Updates] で [!UICONTROL Anchor categories] を選択します。

<u> 期待される結果 </u>:

カテゴリツリーのすべてのレベルが正しく表示されます。

<u> 実際の結果 </u>:

カテゴリ ツリーの最初の数レベル （&lt;4）のみ使用できます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
