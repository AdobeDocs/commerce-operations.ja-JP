---
title: 'MDVA-31763: カタログの価格ルールが手動でインデックスを再作成するまで元に戻される'
description: MDVA-31763 パッチは、カタログ価格ルールが手動でインデックス再作成されるまで元に戻される問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.5がインストールされている場合に利用できます。 パッチ IDはMDVA-31763です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Catalog Management, Orders, Price Rules
role: Admin
exl-id: 1d144bfc-c26b-43d0-a80c-26a9c2d8ef32
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# MDVA-31763: カタログの価格ルールが手動でインデックスを再作成するまで元に戻される

MDVA-31763 パッチは、カタログ価格ルールが手動でインデックス再作成されるまで元に戻される問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.5がインストールされている場合に使用できます。 パッチ IDはMDVA-31763です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.3.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

設定可能な製品で`catalogrule_product`部分インデクサーを実行すると、カタログルールが消えます。

<u>複製する手順</u>:

1. 管理者バックエンドにログインします。
1. **ストア** > **属性** > **製品**&#x200B;に移動し、「製造元」属性を検索します。
   * いくつかのオプションを追加し、「プロモーションルール条件に使用」を&#x200B;*Yes*&#x200B;に設定します。
1. **ストア** > **属性** > **属性セット**&#x200B;に移動します。
   * デフォルトの属性セットを選択し、「製造元」属性を追加します。
1. いくつかのバリエーションを使用して、設定可能な製品を作成します。
1. 以前に作成した設定可能な製品に「メーカー」属性値を設定します。
1. カタログルールの作成：
   * アクティブ =はい
   * Web サイト=メイン Web サイト
   * 顧客グループ = ログインしていません
   * 条件：メーカー= \&lt;設定可能な製品の選択値>
   * アクション：割引
1. 完全なインデックスを作成します。
1. PDPで商品価格を確認し、価格が正しいことを確認してください。
1. 作成した設定可能な製品の「重み」属性を更新します。
1. PDPで商品価格を確認する。

<u>期待される結果</u>:

設定可能な製品に設定されたカタログ価格ルールは、部分的なインデックス再作成時に削除されません。

<u>実際の結果</u>:

設定可能な製品に設定されたカタログ価格ルールは、部分的なインデックス再作成中に消えます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な パッチ」セクションを参照してください。
