---
title: 'ACSD-52736: [!UICONTROL Cart Price Rule]が期待どおりに動作しません'
description: 設定可能な製品数量の要件を含む[!UICONTROL Cart Price Rule]が期待どおりに動作しないAdobe Commerceの問題を修正するには、ACSD-52736 パッチを適用します。
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 80c3b14e-62ce-4cfc-b1ff-968e70e3a6f8
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-52736: [!UICONTROL Cart Price Rule]が期待どおりに動作しません

ACSD-52736 パッチは、設定可能な製品数量の要件を含む[!UICONTROL Cart Price Rule]が期待どおりに動作しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.36がインストールされている場合に利用できます。 パッチ IDはACSD-52736です。 この問題は、Adobe Commerce 2.4.6で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

設定可能な製品数量の要件を含む[!UICONTROL Cart Price Rule]が期待どおりに機能しません。

<u>複製する手順</u>:

1. 買い物かごルールの作成：
   * [!UICONTROL Apply] =製品価格割引の割合
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * 次の条件に一致するカート項目にのみルールを適用します。カート内の数量は1です
2. [!UICONTROL Qty] = 2の商品をカートに追加します。
3. カートの価格を確認する：

<u>期待される結果</u>:

買い物かごに入っている商品の数量が&#x200B;*2*&#x200B;であるため、このルールは適用されません。

<u>実際の結果</u>:

割引が適用されます。

<u> パッチのインストール後に必要な追加の手順</u>:

パッチを適用した後、*数量*&#x200B;属性を使用したカートルール条件を削除して、もう一度追加する必要があります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
