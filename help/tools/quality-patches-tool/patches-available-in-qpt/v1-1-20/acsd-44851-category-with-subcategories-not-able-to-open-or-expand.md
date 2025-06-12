---
title: ACSD-44851：サブカテゴリが開けない、または展開できないカテゴリ
description: この記事では、ユーザーがサブカテゴリを持つカテゴリを開いたり展開したりできない問題の解決策について説明します。
feature: Categories
role: Admin
exl-id: c1ad13d8-94e1-47cf-ad65-9bc5ce1c26ad
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-44851：サブカテゴリが開けない、または展開できないカテゴリ

ACSD-44851 パッチは、サブカテゴリを持つカテゴリをユーザーが開いたり展開したりできない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.20 がインストールされている場合に使用できます。 パッチ ID は ACSD-44851 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.5

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

サブカテゴリを含むカテゴリを開いたり展開したりできない。

<u> 再現手順 </u>:

1. Adobe Commerce Admin で、2 つのルートカテゴリとそれぞれのサブカテゴリを持つカテゴリツリーを作成します。
1. モバイルビュー/エミュレーターを開くか、レイアウトがモバイルになるまでウィンドウの幅を狭めます。
1. カタログのメインメニューを開きます。
1. ルートカテゴリを展開してみてください。
1. カテゴリを開いてみます。

<u> 期待される結果 </u>:

メニューにアクセスできます。

<u> 実際の結果 </u>:

モバイルメニューの 2 番目のレベルが開きません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：品質パッチツールガイドの [ 品質パッチ ツール/使用方法 ](/help/tools/quality-patches-tool/usage.md)。

* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
