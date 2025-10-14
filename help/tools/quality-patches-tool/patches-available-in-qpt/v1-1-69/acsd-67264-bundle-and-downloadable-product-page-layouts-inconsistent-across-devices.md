---
title: ACSD-67264：バンドルおよびダウンロード可能な製品ページレイアウトがデバイス間で一貫していない
description: ACSD-67264 パッチを適用して、Adobe Commerce バンドルおよび Downloadable pages experience layout issues due to rearrangement of the product info media block を修正してください。
feature: Page Content, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9b6794366ba552d86cdfc6a3d6f699c307fcd8f6
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# ACSD-67264：バンドルおよびダウンロード可能な製品ページレイアウトがデバイス間で一貫していない

ACSD-67264 パッチは、バンドルとダウンロード可能な製品ページのレイアウトがデバイス間で一貫していない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACSD-67264 です。 この問題はAdobe Commerce 2.4.8 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

バンドルおよびダウンロード可能な製品ページで、製品情報メディアブロックの再配置に起因するレイアウトの問題が発生しました。

<u> 再現手順 </u>:

1. サンプルデータをインストールします。
1. バンドル製品ページを開き、デスクトップでレイアウトを確認します。
1. バンドル製品ページをウィッシュリストに追加し、ウィッシュリストに移動して、編集アイコンをクリックし、レイアウトを確認します。
1. ダウンロード可能な製品に対して、手順 2 と 3 を繰り返します。

<u> 期待される結果 </u>:

バンドル製品の PDP は問題なくレンダリングされます。

<u> 実際の結果 </u>:

バンドル製品 PDP は、ランダムなスペースでレンダリングされます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドの
* クラウドインフラストラクチャー上のAdobe Commerce:[&#x200B; アップグレードとパッチ適用 &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja) クラウドインフラストラクチャー上のCommerce ガイド

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]：品質向上パッチを適用するためのセルフサービス &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) ツール（『ツールガイド』）
