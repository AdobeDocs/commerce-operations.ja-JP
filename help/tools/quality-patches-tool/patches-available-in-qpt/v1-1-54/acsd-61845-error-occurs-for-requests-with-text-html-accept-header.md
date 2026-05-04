---
title: 'ACSD-61845: text/html accept ヘッダーを持つリクエストでエラーが発生する'
description: ACSD-61845 パッチを適用して、*text/html* accept ヘッダーのみでHTTP リクエストを送信すると、B2B モジュールがインストールされた状態で500 エラーが発生するAdobe Commerceの問題を修正します。
feature: B2B
role: Admin, Developer
exl-id: 6fa6c3ff-bb45-4b9e-afd4-95692acb0a90
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-61845: *text/html*&#x200B;のaccept ヘッダーを持つリクエストでエラーが発生します

ACSD-61845 パッチでは、*text/html*&#x200B;のaccept ヘッダーのみを含むHTTP リクエストで、応答処理のメディアタイプの不一致が原因で500 エラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54がインストールされている場合に利用できます。 パッチ IDはACSD-61845です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

受け入れヘッダーに&#x200B;*text/html*&#x200B;のみを含むHTTP リクエストを送信すると、メディアタイプ設定の不一致により500 エラーが発生します。

<u>前提条件</u>:

B2B モジュールがインストールされ、有効になっている。

<u>複製する手順</u>:

1. 次のように、受け入れヘッダーに&#x200B;*text/html*&#x200B;のみを含むリクエストを送信します。

   ```shell
   curl -I --header "Accept: text/html, text/plain" http://<hostname>/pub/
   ```

<u>期待される結果</u>:

ページは&#x200B;*200 ステータスコード*&#x200B;で返されます。

<u>実際の結果</u>:

500 エラーが返され、`exception.log`に次のエラーメッセージが表示されます。

```text
Magento\Framework\Webapi\Exception: Server cannot match any of the given Accept HTTP header media type(s) from the request: "text/html" with media types from the config of response renderer. in vendor/magento/framework/Webapi/Rest/Response/RendererFactory.php:84
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

[[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
