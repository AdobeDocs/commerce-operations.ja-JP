---
title: 'MDVA-31590: MySQL非同期キューを使用して属性を一括更新できない'
description: MDVA-31590 パッチは、ユーザーがMySQL非同期キューを使用して属性を一括で更新できない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.3がインストールされている場合に利用できます。 パッチ IDはMDVA-31590です。 この問題はAdobe Commerce 2.4.2で修正されています。
feature: Attributes, Services
role: Admin
exl-id: f8d1c3bd-e995-41ef-89e1-93eec6e8b1f1
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 0%

---

# MDVA-31590: MySQL非同期キューを使用して属性を一括更新できない

MDVA-31590 パッチは、ユーザーがMySQL非同期キューを使用して属性を一括で更新できない問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.3がインストールされている場合に使用できます。 パッチ IDはMDVA-31590です。 この問題はAdobe Commerce 2.4.2で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0-2.4.1-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ユーザーは、MySQL非同期を使用して属性を一括で更新することはできません。

<u>複製する手順</u>:

1. バックエンドのプロダクトグリッドで、複数の製品の属性値を更新するための一括操作を実行します。
   * 製品を確認し、「アクション」ドロップダウンから「**属性を更新**」を選択します。
1. 必要な属性の値を設定し、製品をweb サイトに割り当てて保存します。
1. ページがリロードされると、次のようなメッセージが表示されます。
   *タスク「選択されたN個の製品の属性を更新する」:1個のアイテムが更新のためにスケジュールされました。*
1. 数秒待って、バックエンドページをリロードします。

<u>期待される結果</u>:

1. ページには、「*1個の項目が正常に更新されました。*」のような更新が成功したメッセージが表示されます。
1. 関連製品の属性値が更新されます。
1. DBでは、`magento_bulk` テーブルと`magento_operation` テーブルの両方に新しいレコードが作成されます（一括処理に関連する操作）。
1. 新しいレコードが`queue_message` テーブルに作成されます（キュー`product_action_attribute.update`または`product_action_attribute.website.update`に関連）。
1. `queue_message_status` テーブルに、ステータスが「4」のレコードがあります。
1. `system.log`にエラーはありません。

<u>実際の結果</u>:

1. ページには、次のようなメッセージが表示されます。
   *タスク「選択されたN個の製品の属性を更新する」:1個のアイテムが更新のためにスケジュールされました。*
1. 製品の属性値が更新されます。
1. `message_bulk` テーブルに新しいレコードが作成されましたが、`magento_operation` テーブルに関連するレコードはありません。
1. 新しいレコードが`queue_message`および`queue_message_status`個のテーブルに作成されます。
1. `queue_message_status` テーブルに、エラー状態（ステータス値「6」）のレコードがあります。
1. `system.log`には、次のようなエラーが含まれています：

   ```sql
   *main.CRITICAL: Message has been rejected: SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'operation_key' cannot be null, query was: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?) [] []*
   ```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な パッチ」セクションを参照してください。
