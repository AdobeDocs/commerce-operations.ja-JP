---
title: ACSD-53347：価格インデックスのパフォーマンスが時間の経過とともに低下する
description: 大規模な商品カタログの価格をインデックス再作成する際にパフォーマンスが徐々に低下するAdobe Commerceの問題を修正するには、ACSD-53347 パッチを適用します。
feature: Price Indexer
role: Admin
exl-id: 8986b685-55e4-47c7-852c-aca18e3b02e9
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-53347：価格インデックスのパフォーマンスが時間の経過とともに低下する

ACSD-53347 パッチは、大規模な製品カタログの価格をインデックス再作成する際にパフォーマンスが徐々に低下する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.38がインストールされている場合に利用できます。 パッチ IDはACSD-53347です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

大規模な製品カタログの価格をインデックス再作成する場合、インデックス作成処理中に実行されるクエリのパフォーマンスは徐々に低下します。

<u>複製する手順</u>:

1. 大規模なシンプルなカタログを作成し、これらの製品にカスタムオプションを割り当てます（カスタムオプションは、インデックス作成時に一時テーブルを使用します）。
1. 少なくとも200以上の顧客グループを作成して、問題の可視性を向上させます。
1. 10以上のweb サイトを作成し、それぞれに全製品を割り当てる：
1. 読み込まれた製品はほぼ同じで、SKUと名前だけが異なります。
1. **[!UICONTROL DB Logging]**&#x200B;を有効にします。
1. `bin/magento index:reindex catalog_product_price` コマンドを実行します。
1. `db.log`の&#x200B;`catalog_product_index_price_opt_agr_temp`*から* DELETEを確認します。

<u>期待される結果</u>:

*DB クエリ*&#x200B;の実行が効率的に実行されます。

<u>実際の結果</u>:

一時テーブル上の&#x200B;*DB クエリ*&#x200B;のパフォーマンスが時間の経過とともに遅くなるため、価格インデックス テーブルの完了には多くの時間がかかります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」ガイド

## 関連トピックス

* [[!DNL Quality Patches Tool]  リリース：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します
* [Commerce実装プレイブックのデータベーステーブルを修正するためのベストプラクティス ](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications)

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
