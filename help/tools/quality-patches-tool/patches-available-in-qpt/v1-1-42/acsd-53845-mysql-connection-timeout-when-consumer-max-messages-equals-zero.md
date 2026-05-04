---
title: ACSD-53845：消費者max_messages = 0の場合のMySQL接続タイムアウトの問題
description: コンシューマー「max_messages = 0」の場合にMySQL接続がタイムアウトするAdobe Commerceの問題を修正するには、ACSD-53845 パッチを適用します。
feature: REST, Configuration
role: Admin, Developer
exl-id: 437e29f4-b11a-466c-9928-3867821d2b8d
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-53845: コンシューマー`max_messages = 0`でのMySQL接続タイムアウトの問題

ACSD-53845 パッチは、コンシューマー`max_messages = 0`でMySQL接続がタイムアウトする問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.42がインストールされている場合に利用できます。 パッチ IDはACSD-53845です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

コンシューマー`max_messages = 0`の場合、MySQL接続がタイムアウトします。

ただし、トランザクションを開始すると、データベースへの接続は復元されます。

<u>複製する手順</u>:

1. `async/bulk/V1/products` REST API エンドポイントを使用して、製品を一括更新するリクエストを送信します。
1. `magento_operation` テーブルのステータスを確認します。

<u>期待される結果</u>:

製品が更新されます。

<u>実際の結果</u>:

1. エラーがログに記録されます。

   ```yaml
   report.CRITICAL: Message has been rejected: SQLSTATE[HY000]: General error: 2006 MySQL server has gone away [] []
   ```

1. この操作の&#x200B;*status*&#x200B;は、`magento_operation` テーブルの&#x200B;*4*&#x200B;のままです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」ガイド

## 関連トピックス

* [[!DNL Quality Patches Tool]  リリース：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します
* [Commerce実装プレイブックのデータベーステーブルを修正するためのベストプラクティス ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
