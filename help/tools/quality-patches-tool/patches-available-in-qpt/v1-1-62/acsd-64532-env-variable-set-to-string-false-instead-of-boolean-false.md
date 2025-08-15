---
title: ACSD-64532:*false*に設定された環境変数は、ブール値*FALSE*ではなく、文字列*false*として扱われます
description: ACSD-64532 パッチを適用すると、「ENV」変数が*false*に設定された場合、「BOOLEAN」*FALSE*ではなく文字列*false*として扱われるAdobe Commerceの問題が修正されます。
feature: Variables
role: Admin, Developer
exl-id: 7940df1f-d527-4b57-bde7-7a0216b12436
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-64532:「false」に設定された環境変数が、ブール値 FALSE ではなく、文字列「false」として扱われる

ACSD-64532 パッチでは、`ENV`false *に設定された* 変数が *数* FALSE`BOOLEAN` ではなく文字列 *false* として扱われる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 がインストールされている場合に使用できます。 パッチ ID は ACSD-64532 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**
Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p8

**Adobe Commerce バージョンとの互換性：**
Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`ENV`false *に設定* れた変数は、*数* FALSE`BOOLEAN` ではなく文字列 *false* として扱われます。

<u> 再現手順 </u>:
1. クラウドインフラストラクチャー上のAdobe Commerceの環境変数に、値 `env:MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK`false *の* を追加します。
1. 再デプロイを待ちます。
1. スクリプトを実行して、値を確認します。

   ```php
   <?php
   require '../app/bootstrap.php';
   $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
   $objectManager = $bootstrap->getObjectManager();
   $deploymentConfig = $objectManager->get('Magento\Framework\App\DeploymentConfig');
   $useAppLock = $deploymentConfig->get('indexer/use_application_lock');
   
   var_dump($useAppLock);
   
   $configParsedValue = $deploymentConfig->get('indexer/use_application_lock') ?: false;
   
   var_dump($configParsedValue); 
   ```

<u> 期待される結果 </u>:
メソッド `$configParsedValue` の結果である `isUseApplicationLock()` がメソッド `\Magento\Indexer\Model\Mview\View\State::getStatus()` 内で正しく解釈されるためには、負の値を返す必要があります。

<u> 実際の結果 </u>:
`$configParsedValue` の値は *`string(5) false`* です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。
* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
