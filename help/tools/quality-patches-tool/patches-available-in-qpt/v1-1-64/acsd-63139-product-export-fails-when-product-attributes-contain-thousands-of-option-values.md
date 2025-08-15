---
title: ACSD-63139：製品属性に何千ものオプション値が含まれている場合、製品の書き出しが失敗する
description: ACSD-63139 パッチを適用すると、製品属性に何千ものオプション値が含まれている場合に製品の書き出しが失敗するAdobe Commerceの問題を修正できます。
feature: Data Import/Export
role: Admin, Developer
exl-id: 785907dc-aa3f-49e2-bd52-c3afe4393456
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63139：製品属性に何千ものオプション値が含まれている場合、製品の書き出しが失敗する

ACSD-63139 パッチは、製品属性に何千ものオプション値が含まれている場合に製品の書き出しが失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 がインストールされている場合に使用できます。 パッチ ID は ACSD-63139 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p10

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

製品属性に何千ものオプション値が含まれている場合、製品の書き出しが失敗します。

<u> 再現手順 </u>:

1. B2B モジュールと共にAdobe Commerceをインストールします。
1. 次のサイズの大きなデータベースダンプをインポートします。
   ～7,000 製品
   - 450 個までの製品属性
   - 100 個を超えるオプションを持つ属性もあります
1. 次のコマンドを実行して cron をインストールします（まだインストールしていない場合）。

   ```
   bin/magento cron:install
   ```

1. [!DNL RabbitMQ] 前提条件 [[!DNL RabbitMQ]  の手順に従って、](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/rabbitmq) を設定します。
1. `php.ini` ファイルを開き、メモリ制限を 4G に設定し、PHP サービスを再起動します。
1. 管理パネルで、**[!UICONTROL System]**/*[!UICONTROL Data Transfer]*/**[!UICONTROL Export]** に移動します。
1. 「*[!UICONTROL Export Settings]*」セクションで、「**[!UICONTROL Entity Type]**」を *製品* に設定し、下までスクロールして「**[!UICONTROL Continue]**」をクリックします。
1. 次のコマンドを実行して、エクスポートプロセッサーを起動します。

   ```
   bin/magento queue:consumers:start exportProcessor --max-messages=1
   ```

<u> 期待される結果 </u>:

製品の書き出しは正常に完了しました。

<u> 実際の結果 </u>:

製品の書き出しプロセスが失敗し、次の致命的なエラーが返されます。

```
Fatal error: Allowed memory size of 4294967296 bytes exhausted (tried to allocate 12288 bytes) in /var/www/html/app/code/Magento/Catalog/Model/ResourceModel/Product/Collection.php on line 597
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
