---
title: ACSD-63090：管理者から製品を削除すると、ショッピングカートが空になります
description: ACSD-63090 パッチを適用して、ショッピングカートに追加された後に商品が削除された結果、顧客のショッピングカートの商品が消えたAdobe Commerceの問題を修正します。
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: c07778cb-390f-4202-9539-7bb159e4b714
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63090：管理者から製品を削除すると、ショッピングカートが空になります

ACSD-63090 パッチは、ショッピングカートに追加された後、製品が管理者から削除された結果、顧客のショッピングカート項目が消えた問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58がインストールされている場合に利用できます。 パッチ IDはACSD-63090です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

買い物かごに追加された後に製品が削除されると、買い物かごのアイテムが消えます。

<u>複製する手順</u>:

1. 2つの子商品を持つ設定可能な商品を作成します。
1. 登録済みの顧客としてログインします。
1. 両方の子商品をカートに追加します。
1. アカウントからログアウトします。
1. カタログから子商品の1つを削除します。
1. APIを使用して、他の子製品の価格を更新します。

<u>期待される結果</u>:

残りの製品がカートに表示され、既存の見積もりが`quote` データベース テーブルで更新されます。

<u>実際の結果</u>:

* ミニカートは空です。
* 新しい見積もりレコードが`quote` データベース テーブルに生成されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
