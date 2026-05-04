---
title: ACSD-57086：条件が有効になっているデフォルト以外のweb サイトからの注文が正しく処理されない
description: 条件が有効になっているデフォルト以外のweb サイトからの注文が正しく処理されないAdobe Commerceの問題を修正するには、ACSD-57086 パッチを適用します。
feature: Orders
role: Admin, Developer
exl-id: d9f2ef50-12c4-4a2d-b140-dfd0e8948fd3
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# ACSD-57086：条件が有効になっているデフォルト以外のweb サイトからの注文が正しく処理されない

ACSD-57086 パッチでは、条件が有効になっているデフォルト以外のweb サイトからの注文が正しく処理されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49がインストールされている場合に利用できます。 パッチ IDはACSD-57086です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

AsyncOrder処理でマルチストア設定を使用する場合、キューコンシューマーコードでのスコープ処理に関する問題により、メインサイト以外のweb サイトまたはストアで行われた注文は拒否されます。

<u>複製する手順</u>:

1. [!DNL RabbitMQ]をインストールして`bin/magento setup:upgrade`を実行し、[!DNL RabbitMQ]のキューを作成します。
1. AsyncOrder処理を次で設定します。

   ```shell
   bin/magento setup:config:set --checkout-async 1
   ```

1. セカンダリ web サイト、ストア、ストアビューを作成する。
1. 両方のweb サイト間で共有される製品を作成します。
1. 利用条件を有効にする：
   1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**&#x200B;に移動します。
   1. *[!UICONTROL Enable Terms And Conditions]*&#x200B;を&#x200B;*はい*&#x200B;に設定します。
1. 両方のweb サイトの利用条件を設定します。
   1. **[!UICONTROL Stores]** > **[!UICONTROL Terms And Conditions]** > **[!UICONTROL Add New Condition]**&#x200B;に移動します。
   1. 次の設定を使用します。
      * *[!UICONTROL Condition Name]*: *何でも*
      * *[!UICONTROL Status]*: *[!UICONTROL Enabled]*
      * *[!UICONTROL Applied]*: *[!UICONTROL Manually]*
      * *[!UICONTROL Store View]*: *[!UICONTROL Default Store View]*
   1. 2番目のweb サイト/ストアビュー用に別の条件を作成します。
1. **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**&#x200B;に移動して、既定のWeb サイトを変更します。 2番目のWeb サイトをクリックし、*[!UICONTROL Set as Default]*&#x200B;を確認して保存します。
1. 次のコマンドでキャッシュをクリアします。

   ```shell
   bin/magento cache:clear
   ```

1. ストアフロントに移動し、商品をカートに追加します。 チェックアウトに進み、注文します（利用条件に同意するには、支払い方法の手順にチェックボックスが表示されます）。
1. 注文後に「管理者」に戻り、デフォルトのweb サイトを元のメイン web サイトに戻して保存します。
1. キャッシュをクリアします。

   ```shell
   bin/magento cache:clear
   ```

1. 次のコマンドを実行して、キューコンシューマーを起動します。

   ```shell
   bin/magento queue:cons:start placeOrderProcessor
   ```

<u>期待される結果</u>:

注文は処理され、自動的に拒否されることはありません。

<u>実際の結果</u>:

次のコメントが付いた注文ステータスは&#x200B;*拒否*&#x200B;です：

*注文が行われませんでした。 最初に利用条件に同意してから、もう一度ご注文ください。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
