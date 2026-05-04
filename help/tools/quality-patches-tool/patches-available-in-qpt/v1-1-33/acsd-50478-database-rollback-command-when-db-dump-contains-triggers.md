---
title: 'ACSD-50478: backups gridおよびdatabase rollback コマンドでのロールバックアクションのJSの問題'
description: ACSD-50478 パッチを適用して、DB ダンプにトリガーと*delimiter* SQL コマンドが含まれている場合のバックアップグリッドでのロールバックアクションのJS問題とデータベースのロールバックコマンドを修正します。
exl-id: 2f47fbf6-44fc-487c-91fe-6e2e52fcdb2b
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# ACSD-50478: backups gridおよびdatabase rollback コマンドでのロールバックアクションのJSの問題

ACSD-50478 パッチは、DB ダンプにトリガーと&#x200B;*区切り* SQL コマンドが含まれている場合の、バックアップグリッドのロールバックアクションとデータベースのロールバックコマンドのJS問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-50478です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.4-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

DB ダンプにトリガーと&#x200B;*区切り* SQL コマンドが含まれている場合のBackups グリッドおよびdatabase rollback コマンドでのロールバックアクションのJSの問題。

<u>複製する手順</u>:

1. トリガーがデータベースに作成されるように、インデクサーを[!UICONTROL Update on Schedule] モードに設定します。
1. コマンドラインからバックアップ機能を有効にします。

   `bin/magento config:set system/backup/functionality_enabled 1`

1. **システム** > **ツール** > **バックアップ**&#x200B;に移動し、DB バックアップを生成します。
1. ブラウザーコンソールを開くと、次のエラーが表示されます。

   ```text
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. コマンドラインからDBをインポートしてみてください。

   `bin/magento setup:rollback --db-file="<filename>"`

1. 次のエラーが表示されます。

   ```graphql
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u>期待される結果</u>:

データベースの復元は、管理者とコマンドラインの両方から成功します。

<u>実際の結果</u>:

手順4と手順6で説明したエラーを確認しました。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
