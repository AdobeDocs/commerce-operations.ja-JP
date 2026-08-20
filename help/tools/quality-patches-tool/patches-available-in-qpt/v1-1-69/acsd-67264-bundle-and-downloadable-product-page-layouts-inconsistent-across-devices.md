---
title: ACSD-67264：デバイス間で一貫性のないバンドルおよびダウンロード可能な製品ページレイアウト
description: ACSD-67264 パッチを適用して、製品情報メディアブロックの並べ替えにより、Adobe Commerce バンドルとダウンロード可能ページでレイアウトの問題が発生した場合の修正を行います。
feature: Page Content, Products
role: Admin, Developer
type: Troubleshooting
exl-id: 783271ba-176c-4542-8dd8-82bc029ea453
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# ACSD-67264：デバイス間で一貫性のないバンドルおよびダウンロード可能な製品ページレイアウト

ACSD-67264 パッチは、バンドルとダウンロード可能な製品ページレイアウトがデバイス間で一貫性がない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACSD-67264です。 この問題は、Adobe Commerce 2.4.8で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

バンドルおよびダウンロード可能な製品ページは、製品情報メディアブロックの再配置により、レイアウトの問題が発生しました。

<u>複製する手順</u>:

1. サンプルデータをインストールします。
1. バンドル製品ページを開き、デスクトップのレイアウトを確認します。
1. バンドル製品ページをウィッシュリストに追加し、ウィッシュリストに移動して、編集アイコンをクリックし、レイアウトを確認します。
1. ダウンロード可能な製品について、手順2と3を繰り返します。

<u>期待される結果</u>:

バンドル製品のPDPは、問題なくレンダリングされます。

<u>実際の結果</u>:

バンドル製品のPDPは、ランダムなスペースでレンダリングされます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」ガイド

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール
