---
title: 「ACSD-55238：空の製品メタ説明の保存」
description: ACSD-55238 パッチを適用すると、や別のHTMLエディターで生成されたHTMLコードを含む製品説明が常にメタ説明に表示され  [!DNL Page Builder]  空に設定できないAdobe Commerceの問題が修正されます。
feature: Products, Page Builder, Page Content
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-55238：空の製品メタ説明の保存

ACSD-55238 パッチは、HTMLエディタによって生成されたHTMLコードを含む製品説明が常にメタ説明に表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 がインストールされている場合に使用できます。 パッチ ID は ACSD-55238 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL Page Builder] または他のHTMLエディターで生成されたHTMLコードを含む商品説明は、常にメタ説明に表示され、空に設定することはできません。

<u> 再現手順 </u>:

1. **[!UICONTROL Admin]**/**[!UICONTROL Content]**/**[!UICONTROL Block]** に移動し、任意のコンテンツを含む新しいブロックを作成します。
1. **[!UICONTROL Admin]**/**[!UICONTROL Catalog]**/**[!UICONTROL Product]** に移動して、新しい製品を作成します。 メタの説明を空に設定します。
1. 「*[!UICONTROL Content]*」タブの「*[!DNL Page Builder]*」を使用して、上記で作成したブロックを追加し、製品を保存します。
1. ストアフロントで製品を開き、そのドキュメント要素の `meta name = "description"` を確認します。

<u> 期待される結果 </u>:

メタ説明が空です。

<u> 実際の結果 </u>:

製品の説明にブロックが含まれている場合、製品のメタ説明に使用されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
