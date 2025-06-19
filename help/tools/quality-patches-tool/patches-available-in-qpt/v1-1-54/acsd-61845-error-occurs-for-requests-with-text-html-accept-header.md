---
title: 'ACSD-61845: text/html accept ヘッダーを含むリクエストでエラーが発生する'
description: ACSD-61845 パッチを適用すると、*text/html* accept ヘッダーのみを含む HTTP リクエストを送信すると、B2B モジュールがインストールされた状態で 500 エラーが発生するAdobe Commerceの問題を修正できます。
feature: B2B
role: Admin, Developer
exl-id: 6fa6c3ff-bb45-4b9e-afd4-95692acb0a90
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-61845: *text/html* accept ヘッダーを含むリクエストでエラーが発生する

ACSD-61845 パッチでは、*text/html* accept ヘッダーのみを含む HTTP リクエストによって、応答処理のメディアタイプの不一致が原因で 500 エラーが発生する問題を修正しています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 がインストールされている場合に使用できます。 パッチ ID は ACSD-61845 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

Accept ヘッダーに *text/html* のみを含む HTTP リクエストを送信すると、メディアタイプの設定の不一致により 500 エラーが発生します。

<u> 前提条件 </u>:

B2B モジュールがインストールされ、有効になっています。

<u> 再現手順 </u>:

1. 次のように、accept ヘッダーに *text/html* のみを含むリクエストを送信します。

   ```
   curl -I --header "Accept: text/html, text/plain" http://<hostname>/pub/
   ```

<u> 期待される結果 </u>:

ページが *200 ステータスコード* と共に返されます。

<u> 実際の結果 </u>:

500 エラーが返され、次のエラーメッセージが `exception.log` に表示されます。

```
Magento\Framework\Webapi\Exception: Server cannot match any of the given Accept HTTP header media type(s) from the request: "text/html" with media types from the config of response renderer. in vendor/magento/framework/Webapi/Rest/Response/RendererFactory.php:84
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

[[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
