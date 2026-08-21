---
title: 'ACSD-64532: ENV変数を*false*に設定すると、BOOLEAN *FALSE*ではなく、文字列*false*として扱われます'
description: ACSD-64532 パッチを適用して、「ENV」変数が*false*に設定されているAdobe Commerceの問題を、「BOOLEAN」*FALSE*ではなく文字列*false*として扱う問題を修正します。
feature: Variables
role: Admin, Developer
exl-id: 7940df1f-d527-4b57-bde7-7a0216b12436
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-64532: ENV変数が「false」に設定されている場合、BOOLEAN FALSEではなく文字列「false」として扱われます

ACSD-64532 パッチでは、`ENV`変数が&#x200B;*false*&#x200B;に設定されていても、`BOOLEAN` *FALSE*&#x200B;ではなく&#x200B;*false*&#x200B;文字列として扱われる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62がインストールされている場合に利用できます。 パッチ IDはACSD-64532です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチは次のAdobe Commerce バージョン用に作成されます。**
Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p8

**Adobe Commerce版との互換性：**
Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

*false*&#x200B;に設定された`ENV`変数は、`BOOLEAN` *FALSE*&#x200B;ではなく、*false*&#x200B;文字列として扱われます。

<u>複製する手順</u>:
1. クラウドインフラストラクチャ上のAdobe Commerceの環境変数に、値&#x200B;*false*&#x200B;の`env:MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK`を追加します。
1. 再展開を待ちます。
1. 値を確認するスクリプトを実行します。

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

<u>期待される結果</u>:
メソッド `isUseApplicationLock()`の結果である`$configParsedValue`は、メソッド `\Magento\Indexer\Model\Mview\View\State::getStatus()`内で正しく解釈するために負の値を返す必要があります。

<u>実際の結果</u>:
`$configParsedValue`の値は&#x200B;*`string(5) false`*&#x200B;です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。
* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
