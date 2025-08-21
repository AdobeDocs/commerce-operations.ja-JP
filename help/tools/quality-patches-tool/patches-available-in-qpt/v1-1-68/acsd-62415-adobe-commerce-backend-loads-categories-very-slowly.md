---
title: ACSD-62415:Adobe Commerce バックエンドの読み込み [!UICONTROL Categories] 非常に遅い
description: 多数のアンカカテゴリが存在する場合に、[!UICONTROL Categories] ントロールパネルの [!UICONTROL Admin] ページのパフォーマンスの読み込みに非常に時間がかかるAdobe Commerceの問題を修正するために、ACSD-62415 パッチを適用してください。
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8040414630cf3c992e0d68d5693990f8f50fdbcb
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# ACSD-62415：アンカーカテゴリが存在する場合、Adobe Commerce バックエンドの読み込みに非常に時間が **[!UICONTROL Categories]** かる

ACSD-62415 パッチは、多数のアンカーカテゴリが存在する場合に、**[!UICONTROL Categories]** パネルの **[!UICONTROL Admin]** ページのパフォーマンスの読み込みに非常に時間がかかる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 がインストールされている場合に使用できます。 パッチ ID は ACSD-62415 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

多数のアンカーカテゴリが存在する場合、**[!UICONTROL Categories]** パネルの **[!UICONTROL Admin]** ページの読み込みに時間がかかります。

<u> 再現手順 </u>:

1. 3K アンカーカテゴリを生成します。
1. **[!UICONTROL Catalog]** パネルで **[!UICONTROL Categories]** / **[!UICONTROL Admin]** ページを開きます。

<u> 期待される結果 </u>:

**[!UICONTROL Categories]** ページはすぐに読み込まれ、クエリを 1,000 回繰り返さないようにします。

<u> 実際の結果 </u>:

読み込みには 7～20 秒かかり、クエリは 1,000 回以上実行されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
