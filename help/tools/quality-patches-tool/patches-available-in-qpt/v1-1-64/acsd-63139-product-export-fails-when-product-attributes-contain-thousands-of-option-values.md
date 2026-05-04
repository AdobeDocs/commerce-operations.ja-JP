---
title: ACSD-63139：製品属性に数千のオプション値が含まれている場合、製品の書き出しが失敗する
description: 製品属性に数千のオプション値が含まれている場合に製品の書き出しが失敗するAdobe Commerceの問題を修正するには、ACSD-63139 パッチを適用します。
feature: Data Import/Export
role: Admin, Developer
exl-id: 785907dc-aa3f-49e2-bd52-c3afe4393456
type: Troubleshooting
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-63139：製品属性に数千のオプション値が含まれている場合、製品の書き出しが失敗する

ACSD-63139 パッチでは、製品属性に数千ものオプション値が含まれている場合に製品の書き出しが失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64がインストールされている場合に利用できます。 パッチ IDはACSD-63139です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p10

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品属性に数千のオプション値が含まれている場合、製品の書き出しは失敗します。

<u>複製する手順</u>:

1. B2B モジュールを使用してAdobe Commerceをインストールします。
1. 以下を使用して大規模なデータベースダンプを読み込みます。
   &#x200B;- ～7,000製品
   &#x200B;- ～450個の製品属性
   &#x200B;- 100を超えるオプションを持つ一部の属性
1. 次のコマンドを実行して、cronをインストールします（まだインストールされていない場合）。

   ```shell
   bin/magento cron:install
   ```

1. [[!DNL RabbitMQ] 前提条件](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/message-brokers/rabbitmq)の指示に従って[!DNL RabbitMQ]を設定します。
1. `php.ini` ファイルを開き、メモリ制限を4Gに設定し、PHP サービスを再起動します。
1. 管理パネルで、**[!UICONTROL System]** > *[!UICONTROL Data Transfer]* > **[!UICONTROL Export]**&#x200B;に移動します。
1. *[!UICONTROL Export Settings]* セクションで、**[!UICONTROL Entity Type]**&#x200B;を&#x200B;*製品*&#x200B;に設定し、一番下までスクロールして&#x200B;**[!UICONTROL Continue]**&#x200B;をクリックします。
1. 次のコマンドを実行して、エクスポートプロセッサを起動します。

   ```shell
   bin/magento queue:consumers:start exportProcessor --max-messages=1
   ```

<u>期待される結果</u>:

製品の書き出しは正常に終了する必要があります。

<u>実際の結果</u>:

製品の書き出しプロセスが失敗し、次の致命的なエラーが返されます。

```text
Fatal error: Allowed memory size of 4294967296 bytes exhausted (tried to allocate 12288 bytes) in /var/www/html/app/code/Magento/Catalog/Model/ResourceModel/Product/Collection.php on line 597
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
