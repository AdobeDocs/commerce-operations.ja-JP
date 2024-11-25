---
title: 「ACSD-62485:「async.operations.all」コンシューマーは、会社が作成されると動作を停止する」
description: B2B 会社が作成されると「async.operations.all」コンシューマーが機能しなくなるAdobe Commerceの問題を修正するために、ACSD-62485 パッチを適用します。
feature: B2B, Companies
role: Admin, Developer
source-git-commit: 8061f6df01c3c308b46e6164300192b01359ce94
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# ACSD-62485：会社が作成されると、`async.operations.all` の消費者は動作を停止します

ACSD-62485 パッチは、B2B 会社が作成されたときに `async.operations.all` コンシューマーが機能しなくなる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 がインストールされている場合に使用できます。 パッチ ID は ACSD-62485 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p7

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 ～ 2.4.6-p7、2.4.7 ～ 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

コンシューマーの実行中に B2B 会社が非同期で作成されると、`async.operations.all` コンシューマーはメッセージの処理を停止します。

<u> 前提条件 </u>:

B2B モジュールがインストールされ、有効になっています。

<u> 再現手順 </u>:

1. 2 つの顧客を作成します。
1. 2 つの会社を作成する REST 一括リクエストを送信し、作成した顧客を会社管理者として割り当てます。
1. 次のコマンドを使用してコンシューマーを起動します。

   ``` bin/magento queue:consumer:start async.operations.all --max-messages=20000 ```

<u> 期待される結果 </u>:

コンシューマーは 20,000 件のメッセージを処理し、正常に終了します。

<u> 実際の結果 </u>:

消費者は、実行時にすぐに作業を停止します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
