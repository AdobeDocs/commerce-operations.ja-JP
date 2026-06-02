---
title: 'ACSD-55566: [!UICONTROL mergeCart]の突然変異が [!DNL GraphQL] 応答の内部サーバーエラーで失敗します'
description: ACSD-55566 パッチを適用して、同じバンドルアイテムを持つソースと宛先のカートを結合する際に [!DNL GraphQL] 応答の内部サーバーエラーが発生し、「mergeCart」のミューテーションが失敗するAdobe Commerceの問題を修正します。
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84c6fbb9-73b3-4197-aff3-49743f0ebb2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# ACSD-55566: `mergeCart`の突然変異が[!DNL GraphQL]応答の内部サーバーエラーで失敗します

ACSD-55566 パッチは、[!DNL GraphQL]応答の内部サーバーエラーで`mergeCart`の突然変異が失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48がインストールされている場合に利用できます。 パッチ IDはACSD-55566です。 この問題は、Adobe Commerce 2.5.0で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`mergeCart`の変更が失敗し、同じバンドルアイテムを持つソースと宛先のカートを結合する際に[!DNL GraphQL]応答の内部サーバーエラーが発生します。

<u>複製する手順</u>:

1. カスタムソースとカスタム在庫の作成。
1. 作成した在庫をメイン web サイトに割り当てます。
1. 簡単な製品を作成し、作成したソースに割り当てます（qty=2）。
1. 1つのオプションと1つの子製品（手順3で作成した製品）を含むバンドル製品を作成します。
1. [!DNL GraphQL]経由でゲストカートを作成します。
1. 両方のオプションを選択したバンドル製品を追加します。
1. *cartID*&#x200B;を保存します。
1. 顧客を作成し、顧客トークンを生成します。
1. カートの作成。
1. 同じ設定の同じバンドル製品をカートに追加します。
1. ゲストカートと顧客カートを統合してみてください。

<u>期待される結果</u>:

顧客カートには、両方のカートの商品が含まれています。

<u>実際の結果</u>:

内部エラーが発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
