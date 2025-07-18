---
title: ACSD-66212：顧客の CSV ファイルを 2 回インポートすると、2 回目以降の試行でエラーが発生しました
description: ACSD-66212 パッチを適用すると、お客様の CSV ファイルを 2 回読み込むと、2 回目以降の試行でエラーが発生するAdobe Commerceの問題を修正できます。
feature: Data Import/Export, Customers
role: Admin, Developer
source-git-commit: 97a5979a189e43b737c44cfe7a65025effae711c
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# ACSD-66212：顧客の CSV ファイルを 2 回インポートすると、2 回目以降の試行でエラーが発生しました

ACSD-66212 パッチでは、顧客の CSV ファイルを 2 回読み込むと、2 回目以降の試行でエラーが発生する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 がインストールされている場合に使用できます。 パッチ ID は ACSD-66212 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

顧客の CSV ファイルを 2 回読み込むと、2 回目以降の試行でエラーが発生しました。

<u> 再現手順 </u>:

顧客ステータスを含む顧客データを含む CSV を読み込みます。

<u> 期待される結果 </u>:

ステータスは正しくインポートおよびエクスポートされます。

<u> 実際の結果 </u>:

読み込み中にエラーが発生しました：

```
General system exception happened
Additional data: <div class="messages"><div class="message message-error error"><div data-ui-id="messages-message-error" >SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near " at line 1, query was: INSERT INTO company_advanced_customer_entity (customer_id*) VALUES </div></div></div>
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
