---
title: MDVA-38393：単純な製品の名前が変更された場合、カタログルールが設定可能な製品で機能しなくなる
description: MDVA-38393 パッチは、単純な製品の名前が変更された場合に、カタログ ルールが設定可能な製品で機能しなくなる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.8がインストールされている場合に利用できます。 パッチ IDはMDVA-38393です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Catalog Management, Categories, Configuration, Products
role: Admin
exl-id: 3d98671c-6ee7-4fe8-80d9-67fa697cae75
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-38393：単純な製品の名前が変更された場合、カタログルールが設定可能な製品で機能しなくなる

MDVA-38393 パッチは、単純な製品の名前が変更された場合に、カタログ ルールが設定可能な製品で機能しなくなる問題を修正します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.8がインストールされている場合に使用できます。 パッチ IDはMDVA-38393です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.3.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

単純な製品の名前が変更された場合、カタログルールは設定可能な製品で機能しなくなります。

<u>複製する手順</u>:

1. 関連付けられたシンプルな製品を使用して、設定可能な製品を作成します。
1. カテゴリを作成します。
1. 新しいカテゴリに設定可能な製品のみを割り当てます。
1. 新しいカタログルールの作成：
   * 条件= カテゴリに\&lt;新しいカテゴリ ID>が含まれています
   * アクション = 50%割引
   * アクティブ =はい
1. 再インデックスを実行します。
1. フロントエンドで設定可能な製品を確認してください（割引を適用する必要があります）。
1. `catalogrule_product` テーブルを確認してください（単純な製品には割引が必要です）。
1. 管理者に移動し、シンプルな製品の名前を変更します。 これにより、`catalogrule_product_cl` テーブルにレコードが追加されます。
1. cronまたは`bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1` コマンドを実行します。
1. `catalogrule_product` テーブルを確認します。

<u>期待される結果</u>:

設定可能な製品には割引があります。

<u>実際の結果</u>:

* シンプルな製品に対して作成された割引レコードが`catalogrule_product` テーブルにありません。
* フロントエンドの設定可能な製品には、完全なオリジナル価格があります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
