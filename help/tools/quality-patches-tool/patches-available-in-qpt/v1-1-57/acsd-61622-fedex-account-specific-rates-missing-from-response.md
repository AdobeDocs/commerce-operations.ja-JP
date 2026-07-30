---
title: 'ACSD-61622: [!DNL FedEx]  アカウント固有のレートがREST API応答にありません'
description: ACSD-61622 パッチを適用して、 [!DNL FedEx]  アカウント固有のレートがREST API レスポンスから欠落しているAdobe Commerceの問題を修正します。
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 59e33dc4-3f9b-4590-95b6-e98c77e750ee
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-61622: [!DNL FedEx] アカウント固有のレートがREST API応答にありません

ACSD-61622 パッチは、[!DNL FedEx's]個のアカウント固有のレートがREST API応答から欠落している問題を解決します。 Adobe Commerceから送信されたREST API リクエストに`ACCOUNT` レートリクエストタイプが[!DNL FedEx]に追加され、SOAP API レスポンスと同様のレスポンスが返されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-61622です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

REST API応答に[!DNL FedEx's]個のアカウント固有のレートがありません。

<u>複製する手順</u>:

1. クリーンなAdobe Commerce インスタンスをインストールします。
1. 重量5 ポンドのシンプルな製品を作成します。
1. REST API用に[!DNL FedEx]を設定します。
1. [!DNL FedEx]の配送方法を有効にして、キャッシュをクリアします。
1. ログ ファイルの監視を開始：`var/log/shipping.log`
1. カートにシンプルな商品を追加し、チェックアウト時に配送ページに移動します。 顧客データの例：

   * Postcode: 58601
   * 名前：John Doe
   * 住所：196 Eulalia Burg
   * 国：米国
   * 州：ノースダコタ州
   * 電話番号：187-563-3627

<u>期待される結果</u>:

`PAYOR_ACCOUNT_PACKAGE`のレートは、SOAP APIのレスポンスと同様に、REST APIのレスポンスで利用できます。

<u>実際の結果</u>:

応答で使用できるレートは`PAYOR_LIST_PACKAGE`のみです。つまり、[!DNL FedEx]から交渉済み（アカウント）レートはありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
