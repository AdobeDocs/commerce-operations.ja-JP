---
title: 「MDVA-31763：カタログ価格ルールは、手動で再インデックスするまで元に戻されます」
description: MDVA-31763 パッチは、カタログ価格ルールが手動で再インデックスされるまで元に戻される問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches） 1.1.5 がインストールされている場合に利用できます。 パッチ ID は MDVA-31763。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-31763: カタログ価格ルールは、手動で再インデックスするまで元に戻されます

MDVA-31763 パッチは、カタログ価格ルールが手動で再インデックスされるまで元に戻される問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)1.1.5 がインストールされている場合に使用できます。 パッチ ID は MDVA-31763。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 ～ 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

設定可能な製品 `catalogrule_product` 対して部分インデクサーを実行すると、カタログルールが表示されなくなります。

<u> 再現手順 </u>:

1. 管理バックエンドにログインします。
1. **ストア**/**属性**/**製品** に移動し、「manufacturer」属性を検索します。
   * いくつかのオプションを追加し、「プロモルール条件に使用」を *はい* に設定します。
1. **ストア**/**属性**/**属性セット** に移動します。
   * デフォルトの属性セットを選択し、そのセットに「manufacturer」属性を追加します。
1. いくつかのバリエーションを持つ設定可能な製品を作成します。
1. 以前に作成した設定可能な製品の「製造元」属性値を設定します。
1. カタログルールを作成：
   * アクティブ =はい
   * Web サイト = メイン Web サイト
   * 顧客グループ =未ログイン
   * 条件：製造元= \&lt; 設定可能な製品に対して選択された値 >
   * アクション：任意の割引
1. 完全なインデックスを作成します。
1. PDP の製品価格を確認し、価格が正しいことを確認してください。
1. 作成した設定可能な商品の「重み」属性を更新します。
1. PDP の製品価格を確認します。

<u> 期待される結果 </u>:

設定可能な製品に設定されたカタログ価格ルールは、部分再インデックス中に削除されません。

<u> 実際の結果 </u>:

設定可能な製品に設定されたカタログ価格ルールは、部分再インデックス中に表示されなくなります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチについては、[QPT で使用可能なパッチ ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) の節を参照してください。
