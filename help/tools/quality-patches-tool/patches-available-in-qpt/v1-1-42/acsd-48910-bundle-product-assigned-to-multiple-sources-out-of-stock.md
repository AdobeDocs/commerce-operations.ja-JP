---
title: ACSD-48910：複数のソースが割り当てられたバンドル商品が、請求書と発送後に在庫切れになる
description: ACSD-48910 パッチを適用して、複数のソースに割り当てられたバンドル商品が、注文の請求後に在庫切れになり、ゼロ以外の数量が残っている場合でも発送されるAdobe Commerceの問題を修正します。
feature: Products, Inventory
role: Admin, Developer
exl-id: c8d86531-2db5-4115-92d5-a8d391c4f75d
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# ACSD-48910：複数のソースが割り当てられたバンドル商品が、請求書と発送後に在庫切れになる

ACSD-48910 パッチは、注文が請求され、発送された後、ゼロ以外の数量がまだあっても、複数のソースに割り当てられたバンドル製品が在庫切れになる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.42がインストールされている場合に利用できます。 パッチ IDはACSD-48910です。 この問題は、Adobe Commerce 2.4.6で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

複数のソースに割り当てられたバンドル商品は、請求書や配送後、まだ入手可能であっても在庫切れとなります。

<u>複製する手順</u>:

1. 2つのweb サイトを作成する：
1. 2つのストア/ストアビューを作成します（web サイトごとに1つ）。
1. 2つのシンプルな商品（数量= 10）を作成し、在庫とweb サイトの両方に割り当てます。
1. バンドル商品を作成し、これらのシンプルな商品を追加します。 バンドルされた商品を両方のweb サイトに割り当てます。
1. ストアフロントに移動し、バンドルされた商品をカートに追加します。
1. チェックアウトして注文します。
1. 管理者から、請求書と注文の発送を行います。

<u>期待される結果</u>:

10個の商品のうち1個しか購入していないため、同梱商品は在庫を維持します。

<u>実際の結果</u>:

同梱商品は、在庫切れというステータスに変わります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
