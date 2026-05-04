---
title: ACSD-58739：部分的なインデックス再作成でエラーがスローされる
description: ACSD-55241 パッチを適用して、部分的なインデックス再作成によってエラーがスローされるAdobe Commerceの問題を修正します。
feature: Inventory, Products
role: Admin, Developer
exl-id: b4e6b8b4-43de-4434-94fb-6269a75e1c28
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-58739：部分的なインデックス再作成でエラーがスローされる

>[!NOTE]
>
>このパッチは[ACP2E-3705](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3705-fixes-an-issue-where-the-indexer.md)に置き換えられます。

ACSD-58739 パッチは、部分的なインデックス再作成によってエラーがスローされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49がインストールされている場合に利用できます。 パッチ IDはACSD-58739です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

部分インデックス再作成でエラーが発生する。

<u>複製する手順</u>:

1. `app/etc/env.php`にスレーブ接続設定を追加します。
1. 最大10000製品を生成し、次のコマンドを実行します。

   ```shell
   bin/magento index:reindex
   ```

1. 生成された製品IDを`catalogsearch_fulltext_cl` DB テーブルに追加します。

   ```sql
   insert into catalogsearch_fulltext_cl (entity_id) select entity_id from catalog_product_entity;
   ```

1. 次のコマンドを実行して、部分的なインデックスをトリガーします。

   ```shell
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1 
   ```

1. `var/log/support_report.log` ファイルを確認してください。

<u>期待される結果</u>

エラーなし。

<u>実際の結果</u>:

部分的なインデックス再作成が実行されると、*ベーステーブルまたはビューが見つかりません* エラーが発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」ガイド

## 関連トピックス

* [[!DNL Quality Patches Tool]  リリース：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します
* [Commerce実装プレイブックのデータベーステーブルを修正するためのベストプラクティス ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
