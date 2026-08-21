---
title: MDVA-40401：注文が失敗するとクーポン使用率が変更される
description: MDVA-40401 パッチは、注文が失敗した後でもクーポン使用価値が変更される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.4がインストールされている場合に利用できます。 パッチ IDはMDVA-40401です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Orders
role: Admin
exl-id: bc8eedd6-977f-4f21-bcd1-b5f6c4a6704f
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# MDVA-40401：注文が失敗するとクーポン使用率が変更される

MDVA-40401 パッチは、注文が失敗した後でもクーポン使用価値が変更される問題を修正します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.4がインストールされている場合に使用できます。 パッチ IDはMDVA-40401です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方式） 2.3.6 - 2.3.7-p2、2.4.1 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ユーザーは、失敗した順序で使用したクーポンを再適用することはできません。

<u>複製する手順</u>:

1. 自動生成されたクーポンを使用してショッピングカートのルールを作成します。
1. 商品をカートに追加し、クーポンを適用します。
1. **チェックアウト**&#x200B;に移動します。
1. 注文する前に、追加した商品を「在庫切れ」にしておきます。
1. *在庫切れ* エラーが発生する必要があります。
1. cronを実行します。
1. カートに移動し、その商品を削除します。
1. 別の商品を追加し、クーポンを適用します。

<u>期待される結果</u>:

前の注文が行われなかったため、クーポンコードは正常に適用されます。

<u>実際の結果</u>:

*クーポンコードが無効です* エラーが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメントタイプに応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で使用可能な パッチ」セクションを参照してください。
