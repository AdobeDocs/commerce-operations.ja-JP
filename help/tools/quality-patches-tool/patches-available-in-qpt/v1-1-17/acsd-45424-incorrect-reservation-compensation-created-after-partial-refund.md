---
title: ACSD-45424：一部払い戻し後に誤った予約報酬が作成される
description: ACSD-45424 パッチは、一部払い戻し後に誤った予約報酬が作成される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.17がインストールされている場合に利用できます。 パッチ IDはACSD-45424です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。
feature: Orders
role: Admin
exl-id: 94435816-9f4a-40f9-be80-05836ed7781f
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---

# ACSD-45424：一部払い戻し後に誤った予約報酬が作成される

ACSD-45424 パッチは、一部払い戻し後に誤った予約報酬が作成される問題を修正します。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.17がインストールされている場合に使用できます。 パッチ IDはACSD-45424です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.4 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

一部払い戻し後、誤った予約報酬が作成される。

<u>複製する手順</u>:

1. 実店舗での配送方法を可能にする：
1. 3つの在庫ソースを作成し、各商品（source1、source2、source3）の受け取り場所がアクティブであることを確認します。
1. 新しい在庫を作成し、3つのソースを新しい在庫に割り当てます。
   * この在庫はメインのweb サイトに割り当てる必要があります。
1. シンプルな製品P3を作成し、すべてのソースをそれに割り当てます。
1. シンプルな製品のソースに対して次の数量を追加し、バックオーダーを有効にします。
   * デフォルトソース - 100
   * source1 - 0
   * source2 - 10
   * source3 - 0
1. フロントエンドからシンプルな商品をカートに追加し、配送フォームに進みます。
1. 配送場所として「source1」を選択します。
1. 注文を完了し、データベースで次のクエリを実行します。

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   `inventory_reservation` テーブルに配置された注文レコードを取得します。 数量は10です。正しいです。
1. この注文をバックエンドから請求書で送信します。
1. ここで、1つの商品だけのクレジットメモを作成します。 「*在庫に戻る*」チェックボックスを選択しないでください。
1. 手順8と同じクエリを実行します。

<u>期待される結果</u>:

クレジットメモの作成中に&#x200B;*Return to Stock*&#x200B;を選択しなかった場合、`inventory_reservation` テーブルには、クレジットメモに対応するレコードはありません。

<u>実際の結果</u>:

クレジットメモの作成中に&#x200B;*Return to Stock*&#x200B;を選択しませんでしたが、`creditmemo_created` イベントタイプを持つ`inventory_reservation` テーブルにレコードが追加されます。 また、`inventory_reservation` テーブルに追加されたクレジットメモのレコードは、1つの数量のクレジットメモを作成したにもかかわらず、10の数量を持ちます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
