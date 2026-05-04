---
title: 'ACSD-63572: インデクサープロセスが終了すると、「catalogrule」インデクサーの一時テーブルがクリーニングされない'
description: ACSD-63572 パッチを適用して、[!UICONTROL CLI]でシステムのアップグレードまたは停止が原因でプロセスが終了したときにインデクサーテーブルがクリーンアップされないAdobe Commerceの問題を修正します。
feature: System
Role: Admin, Developers
exl-id: 1cab7058-ca20-4d43-bfca-9b0e3ad35f42
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-63572: `catalogrule` インデクサープロセスが終了すると、インデクサーの一時テーブルがクリーニングされない

ACSD-63572 パッチは、[!UICONTROL CLI]でシステム/アップグレードまたは停止が原因でプロセスが終了したときに、インデクサーの一時テーブルがクリーンアップされない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58がインストールされている場合に利用できます。 パッチ IDはACSD-63572です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

システムのアップグレードまたは[!UICONTROL CLI]の停止によりプロセスが終了した場合、インデクサーの一時テーブルはクリーンアップされません。

<u>複製する手順</u>:

1. [!UICONTROL CLI]を開きます。
1. コマンド `bin/magento indexer:reindex catalogrule_rule`を実行します。
1. 次を使用して処理を終了する前に、処理をキャンセルします：`^C`。
1. `bin/magento indexer:reset catalogrule_rule catalogrule_product`を使用してインデクサーをリセットします。
1. 前の手順を数回繰り返します。
1. データベースで作成された次の一時テーブルを確認します。

   ```text
   catalogrule_product__temp*
   catalogrule_product_price__temp*
   ```

<u>期待される結果</u>:

古い一時テーブルは、不要な場合に削除されます。

<u>実際の結果</u>:

古い一時テーブルは削除されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
