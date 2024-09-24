---
title: 「ACSD-50478：バックアップグリッドおよびデータベースロールバックコマンドでのロールバックアクションの JS の問題」
description: ACSD-50478 パッチを適用して、DB ダンプにトリガーと*delimiter* SQL コマンドが含まれている場合のバックアップ グリッドおよびデータベース ロールバック コマンドでのロールバック アクションの JS の問題を修正してください。
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-50478：バックアップグリッドおよびデータベースロールバックコマンドでのロールバックアクションの JS の問題

ACSD-50478 パッチは、DB ダンプにトリガーと *delimiter* SQL コマンドが含まれている場合のバックアップ グリッドおよびデータベース ロールバック コマンドでのロールバック アクションの JS の問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 がインストールされている場合に使用できます。 パッチ ID は ACSD-50478 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.4-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

DB ダンプにトリガーと *delimiter* SQL コマンドが含まれている場合のバックアップ グリッドおよびデータベース ロールバック コマンドのロールバック アクションに関する JS の問題。

<u> 再現手順 </u>:

1. インデクサーを [!UICONTROL Update on Schedule] モードに設定して、トリガーがデータベース内に作成されるようにします。
1. コマンドラインからバックアップ機能を有効にします。

   `bin/magento config:set system/backup/functionality_enabled 1`

1. **システム**/**ツール**/**バックアップ** に移動し、DB バックアップを生成します。
1. ブラウザーコンソールを開くと、次のエラーが表示されます。

   ```
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. コマンドラインから DB をインポートします。

   `bin/magento setup:rollback --db-file="<filename>"`

1. 次のエラーが表示されます。

   ```
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u> 期待される結果 </u>:

データベースの復元は、管理者とコマンドラインの両方から正常に行われます。

<u> 実際の結果 </u>:

手順 4 と手順 6 で示したエラーが表示されました。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
