---
title: 'ACSD-61622: [!DNL FedEx] account 固有のレートが REST API 応答にありません'
description: ACSD-61622 パッチを適用して、REST API の応答でアカウント固有のレートが欠落しているAdobe Commerceの問題を修正してくださ  [!DNL FedEx] 。
feature: Shipping/Delivery
role: Admin, Developer
source-git-commit: 24acc5f369e0001c8aeab3f81a2e1b51bc523333
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-61622:[!DNL FedEx] アカウント固有のレートが REST API 応答にありません

ACSD-61622 パッチを使用すると、REST API 応答 [!DNL FedEx's] アカウント固有のレートが欠落している問題が解決されます。 Adobe Commerceから [!DNL FedEx] に送信される REST API リクエストに `ACCOUNT` 速のリクエストタイプを追加して、SOAP API レスポンスと同様のレスポンスを返します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-61622 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

アカウン [!DNL FedEx's] 固有のレートが REST API 応答にありません。

<u> 再現手順 </u>:

1. クリーンなAdobe Commerce インスタンスをインストールします。
1. 重量 5 ポンドのシンプルな製品を作成します。
1. REST API 用に [!DNL FedEx] を設定します。
1. 発送方法 [!DNL FedEx] 有効にし、キャッシュをクリアします。
1. ログファイルの監視を開始：`var/log/shipping.log`
1. 簡単な商品をカートに追加し、チェックアウト時に配送ページに移動します。 顧客データの例：

   * 郵便番号：58601
   * 名前：John Doe
   * 住所：196 Eulalia Burg
   * 国：米国
   * 州：ノースダコタ
   * 電話番号：187-563-3627

<u> 期待される結果 </u>:

REST API 応答では、SOAP API 応答と同様に、`PAYOR_ACCOUNT_PACKAGE` のレートを使用できます。

<u> 実際の結果 </u>:

応答では `PAYOR_LIST_PACKAGE` 件のレートのみが使用可能です。つまり、[!DNL FedEx] からの交渉された（アカウント）レートはありません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
