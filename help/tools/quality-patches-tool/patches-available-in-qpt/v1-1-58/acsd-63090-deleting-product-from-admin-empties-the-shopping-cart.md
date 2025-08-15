---
title: ACSD-63090：管理者から製品を削除すると、買い物かごが空になる
description: ACSD-63090 パッチを適用すると、商品が買い物かごに追加された後に削除された結果、顧客の買い物かごの商品が消えるというAdobe Commerceの問題が修正されます。
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: c07778cb-390f-4202-9539-7bb159e4b714
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63090：管理者から製品を削除すると、買い物かごが空になる

この ACSD-63090 パッチは、製品が買い物かごに追加された後、管理者から削除された結果、顧客の買い物かご項目が表示されなくなる問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 がインストールされている場合に使用できます。 パッチ ID は ACSD-63090 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

買い物かごに追加された商品が削除されると、買い物かごのアイテムが消える。

<u> 再現手順 </u>:

1. 2 つの子製品を持つ設定可能な製品を作成します。
1. 登録済みの顧客としてログインします。
1. 両方の子製品を買い物かごに追加します。
1. アカウントからログアウトします。
1. カタログから子製品の 1 つを削除します。
1. API を使用して、他の子製品の価格を更新します。

<u> 期待される結果 </u>:

残りの製品は買い物かごに表示され、既存の見積もりは `quote` のデータベーステーブルで更新されます。

<u> 実際の結果 </u>:

* ミニカートが空です。
* 新しい引用符レコードが `quote` データベース テーブルに生成されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
