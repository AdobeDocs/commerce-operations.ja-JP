---
title: MDVA-39153：管理画面での再発注中に割引額が正しく計算されない
description: MDVA-39153 パッチは、Adminでの再発注中に割引額が誤って計算される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.8がインストールされている場合に利用できます。 パッチ IDはMDVA-39153です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
exl-id: e8fe58ca-1218-4e76-b5fb-c7f935029cd2
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# MDVA-39153：管理画面での再発注中に割引額が正しく計算されない

MDVA-39153 パッチは、Adminでの再発注中に割引額が誤って計算される問題を修正します。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.8がインストールされている場合に使用できます。 パッチ IDはMDVA-39153です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理画面での再発注中に割引額が正しく計算されない。

<u>複製する手順</u>:

1. **管理者** > **店舗** > **設定** > **販売** > **税金**&#x200B;に移動します。
1. ショッピングカートに税金が表示されている送料の税金をオンにします。
1. 表レートの配送方法（$15）を有効にして設定します。
1. 組み込み税率（CA）の税ルールを作成します。
1. カート全体と配送金額に固定の5 ドルの割引を適用したカート価格ルールを作成します。
1. 価格が$12の商品をカートに追加し、ショッピングカートページに移動します。
1. カートに割引を適用します。
1. 「見積」セクションの配送方法を「定額料金」に設定します。
1. 手順を確認するまでチェックアウトを進めます（注文しないでください）。
1. ホームページに移動し、ショッピングカートに戻ります。
1. 「見積」セクションの出荷方法を「表レート」に変更します。

<u>期待される結果</u>:

割引は同じままです – 5 ドル。

<u>実際の結果</u>:

割引は6.31 ドルです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
