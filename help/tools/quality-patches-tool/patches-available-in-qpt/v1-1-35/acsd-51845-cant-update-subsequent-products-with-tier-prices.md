---
title: ACSD-51845：非同期バルク  [!DNL API]を使用して、階層価格と異なる属性セットを含む後続の製品を更新できない
description: ACSD-51845 パッチを適用して、非同期バルク  [!DNL REST API]を介して、価格帯や属性セットが異なる後続の製品を更新できないAdobe Commerceの問題を修正します。
feature: REST, Products
role: Admin
exl-id: 83d97946-83da-4c1b-8f2a-21a64ee84e93
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-51845：非同期バルク [!DNL API]を使用して、階層価格と異なる属性セットを含む後続の製品を更新できない

ACSD-51845 パッチは、非同期バルク [!DNL REST API]を介して、階層価格と異なる属性セットを含む後続の製品を更新できない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35がインストールされている場合に利用できます。 パッチ IDはACSD-51845です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

非同期バルク [!DNL REST API]を介して、階層価格と異なる属性セットを持つ後続の製品の更新が失敗します。

<u>複製する手順</u>:

1. [!DNL RabbitMQ]を設定します。
1. 2つの属性セットを作成します。
1. 2つの&#x200B;**シンプル製品**&#x200B;を作成し、各製品を異なる属性セットに割り当てます。
1. 各製品に&#x200B;**顧客グループ価格**&#x200B;を追加します。
1. 同じ一括[!DNL API]更新で両方の製品を更新します。
1. `bin/magento queue:consumers:start async.operations.all` コマンドが実行されていることを確認します。
1. 一括[!DNL API] ステータスを確認します。

<u>期待される結果</u>:

サービスの実行が成功しました。

<u>実際の結果</u>:

システムがエラーメッセージを返します：*製品を保存できませんでした。 もう一度やり直してください。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
