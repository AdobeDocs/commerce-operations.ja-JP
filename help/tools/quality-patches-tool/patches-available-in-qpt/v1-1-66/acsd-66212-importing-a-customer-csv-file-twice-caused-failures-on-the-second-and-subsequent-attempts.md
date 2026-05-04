---
title: ACSD-66212：お客様のCSV ファイルを2回インポートすると、2回目以降の試行でエラーが発生しました
description: お客様のCSV ファイルを2回インポートすると、2回目以降の試行でエラーが発生するというAdobe Commerceの問題を修正するには、ACSD-66212 パッチを適用します。
feature: Data Import/Export, Customers
role: Admin, Developer
exl-id: ae41f341-6ca3-405e-877a-35bdc3bc5623
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-66212：お客様のCSV ファイルを2回インポートすると、2回目以降の試行でエラーが発生しました

ACSD-66212 パッチでは、2回目以降の試行で顧客CSV ファイルを読み込むとエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66がインストールされている場合に利用できます。 パッチ IDはACSD-66212です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

顧客CSV ファイルを2回インポートすると、2回目以降の試行でエラーが発生しました。

<u>複製する手順</u>:

顧客ステータスを含む顧客データを含むCSVをインポートします。

<u>期待される結果</u>:

ステータスが読み込まれ、正しく書き出されます。

<u>実際の結果</u>:

読み込み中にエラーが発生します。

```text
General system exception happened
Additional data: <div class="messages"><div class="message message-error error"><div data-ui-id="messages-message-error" >SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near " at line 1, query was: INSERT INTO company_advanced_customer_entity (customer_id*) VALUES </div></div></div>
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
