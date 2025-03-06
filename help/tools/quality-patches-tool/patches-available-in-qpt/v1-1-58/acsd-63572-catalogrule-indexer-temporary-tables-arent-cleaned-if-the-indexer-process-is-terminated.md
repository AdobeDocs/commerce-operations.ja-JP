---
title: 'ACSD-63572: インデクサープロセスが終了した場合、「catalogrule」インデクサーの一時テーブルが消去されない'
description: ACSD-63572 パッチを適用すると、システムアップグレードが原因でプロセスが終了したとき、または [!UICONTROL CLI] で停止したときにインデクサーテーブルがクリーンアップされないAdobe Commerceの問題を修正できます。
feature: System
Role: Admin, Developers
source-git-commit: 588a543a8c0bfb8067f81e7131d0a53e5cdc340a
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# ACSD-63572：インデクサー `catalogrule` ロセスが終了しても、インデクサーの一時テーブルが消去されない

ACSD-63572 パッチは、システムまたはアップグレードが原因でプロセスが終了した場合、または [!UICONTROL CLI] で停止した場合に、インデクサーの一時テーブルがクリーンアップされない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 がインストールされている場合に使用できます。 パッチ ID は ACSD-63572 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

インデクサーの一時テーブルは、システムのアップグレードまたは [!UICONTROL CLI] の停止が原因でプロセスが終了しても、クリーンアップされません。

<u> 再現手順 </u>:

1. [!UICONTROL CLI] を開きます。
1. コマンド `bin/magento indexer:reindex catalogrule_rule` を実行します。
1. `^C` を使用して処理を終了する前に、処理をキャンセルしてください。
1. 次を使用してインデクサーをリセット：`bin/magento indexer:reset catalogrule_rule catalogrule_product`。
1. 上記の手順を数回繰り返します。
1. データベースに作成された次の一時テーブルを確認します。

   ```
   catalogrule_product__temp*
   catalogrule_product_price__temp*
   ```

<u> 期待される結果 </u>:

古い一時テーブルは、不要になると削除されます。

<u> 実際の結果 </u>:

古い一時テーブルは削除されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
