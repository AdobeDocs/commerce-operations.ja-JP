---
title: 「ACSD-44851：サブカテゴリを含むカテゴリが開けない、または展開できない」
description: この記事では、ユーザーがサブカテゴリを持つカテゴリを開いたり展開したりできない問題の解決策について説明します。
feature: Categories
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-44851：サブカテゴリが開けない、または展開できないカテゴリ

ACSD-44851 パッチは、サブカテゴリを持つカテゴリをユーザーが開いたり展開したりできない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)1.1.20 がインストールされている場合に使用できます。 パッチ ID は ACSD-44851 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

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

* Adobe CommerceまたはMagento Open Sourceオンプレミス：品質パッチツールガイドの [ 品質パッチツール/使用状況 ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。

* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかをサポートナレッジベースで確認します ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html)。

QPT で使用可能なその他のパッチの詳細は、『品質向上パッチ ツール ガイド』の「[[!DNL Quality Patches Tool]：パッチの検索 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
