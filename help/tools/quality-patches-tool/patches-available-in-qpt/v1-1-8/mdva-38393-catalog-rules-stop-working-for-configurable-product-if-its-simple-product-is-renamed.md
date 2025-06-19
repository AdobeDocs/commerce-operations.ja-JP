---
title: MDVA-38393：設定可能な製品の単純な製品の名前が変更されると、その製品のカタログルールは機能しなくなります
description: MDVA-38393 パッチは、設定可能な製品の単純な製品の名前が変更されると、その製品のカタログルールが機能しなくなる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.8 がインストールされている場合に利用できます。 パッチ ID は MDVA-38393。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: Catalog Management, Categories, Configuration, Products
role: Admin
exl-id: 3d98671c-6ee7-4fe8-80d9-67fa697cae75
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-38393：設定可能な製品の単純な製品の名前が変更されると、その製品のカタログルールは機能しなくなります

MDVA-38393 パッチは、設定可能な製品の単純な製品の名前が変更されると、その製品のカタログルールが機能しなくなる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.8 がインストールされている場合に使用できます。 パッチ ID は MDVA-38393。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 ～ 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

設定可能な製品の単純な製品の名前が変更されると、カタログルールはその製品の機能を停止します。

<u> 再現手順 </u>:

1. 関連付けられたシンプルなプロダクトを使用して、設定可能なプロダクトを作成します。
1. カテゴリを作成します。
1. 設定可能な製品のみを新しいカテゴリに割り当てます。
1. 新しいカタログルールを作成します。
   * 条件= カテゴリに\&lt; 新しいカテゴリ ID> が含まれている
   * アクション = 50% 割引
   * アクティブ =はい
1. 再インデックスを実行します。
1. フロントエンドで設定可能な製品を確認します（割引を適用する必要があります）。
1. `catalogrule_product` の表を確認してください（シンプルな製品には割引が必要です）。
1. 管理者に移動して、シンプルな製品の名前を変更します。 これにより、`catalogrule_product_cl` テーブルにレコードが追加されます。
1. cron または `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1` コマンドを実行します。
1. `catalogrule_product` テーブルを確認します。

<u> 期待される結果 </u>:

設定可能な製品には割引があります。

<u> 実際の結果 </u>:

* 簡易商品に対して作成された割引レコードが `catalogrule_product` テーブルにありません。
* フロントエンドの設定可能な製品は、完全なオリジナルの価格を持っています。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
