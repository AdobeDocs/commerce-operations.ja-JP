---
title: 'ACSD-47937: アプリケーションレベルのキャッシュが原因で値下げ通知が送信されない'
description: アプリケーションレベルのキャッシュにより、値下げ通知が必ずしも送信されないAdobe Commerceの問題を修正するには、ACSD-47937 パッチを適用します。
feature: Admin Workspace, Cache, Orders
role: Admin
exl-id: 91d8e677-c2bb-4230-bbe3-a2c5f9b82e16
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# ACSD-47937: アプリケーションレベルのキャッシュが原因で値下げ通知が送信されない

ACSD-47937 パッチは、アプリケーションレベルのキャッシュにより、値下げ通知が常に送信されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26がインストールされている場合に利用できます。 パッチ IDはACSD-47937です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4および2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4、2.4.5、および2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

顧客には、その後の製品価格変更に関する製品価格低下メールは配信されていません。

<u>複製する手順</u>:

1. **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**&#x200B;の&#x200B;*[!UICONTROL Price Changes]*&#x200B;と&#x200B;*[!UICONTROL Back in Stock]*&#x200B;の両方で&#x200B;**[!UICONTROL Product Alert]**&#x200B;を有効にします。
1. **[!UICONTROL Display Out of Stock Products]**&#x200B;を有効にします。
1. 数量= 0の簡易製品（ABC）を作成します。
1. ストアフロントで顧客を作成し、上記の商品に登録すると、値下げ時に商品アラートが届きます。
1. 顧客に対する製品アラートを開始します。

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. ABC製品の価格を下げます。
1. 商品アラートのcronをトリガーします。

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. ABC商品の価格を再度下げます。
1. 商品アラートのcronをトリガーします。

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>[!DNL n98] ツールに慣れていない場合は、通常どおり`bin/magento cron:run command`を実行し、`cron_schedule` テーブルを監視して、`catalog_product_alert` ジョブが成功ステータスを取得することを確認できます。

<u>期待される結果</u>:

2回目の値下げメールを送信します。

<u>実際の結果</u>:

2回目の値下げメールは送信されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」ガイド

## 関連トピックス

* [[!DNL Quality Patches Tool]  リリース：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します
* [Commerce実装プレイブックのデータベーステーブルを修正するためのベストプラクティス ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
