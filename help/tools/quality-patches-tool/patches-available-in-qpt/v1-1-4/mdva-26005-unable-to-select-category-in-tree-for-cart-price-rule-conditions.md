---
title: 'MDVA-26005: カート価格ルール条件のツリーでカテゴリを選択できません'
description: MDVA-26005 パッチは、ユーザーがカテゴリ ツリーで買い物かごの価格ルール条件のカテゴリを選択できない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.4がインストールされている場合に利用できます。 パッチ IDはMDVA-26005です。 この問題は、Adobe Commerce 2.3.6で修正されています。
feature: Categories, Orders, Price Rules, Shopping Cart
role: Admin
exl-id: 02d9eef4-89f0-48be-8bb9-c62bbdad76a5
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-26005: カート価格ルール条件のツリーでカテゴリを選択できません

MDVA-26005 パッチは、ユーザーがカテゴリ ツリーで買い物かごの価格ルール条件のカテゴリを選択できない問題を解決します。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.4がインストールされている場合に使用できます。 パッチ IDはMDVA-26005です。 この問題は、Adobe Commerce 2.3.6で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.3.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カート価格ルール条件のカテゴリ ツリーでカテゴリを選択できません。

<u>複製する手順</u>:

1. 新しいカート価格ルールを作成するか、既存のカート価格ルールを編集します。
1. 「アクション」セクションに移動し、「条件」で「カテゴリ」を選択します。
1. カテゴリツリーをレンダリングして、カテゴリを選択します。

<u>期待される結果</u>:

カテゴリを選択できます。

<u>実際の結果</u>:

JS エラーのため、カテゴリを選択できません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な[ パッチ」セクションを参照してください。
