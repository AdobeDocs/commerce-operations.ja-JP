---
title: AC-14985:TLSを使用してSMTP メールを送信する際にエラーが発生する
description: Transport Layer Security （TLS）を使用してSimple Mail Transfer Protocol （SMTP）電子メールを送信する際にエラーが発生するAdobe Commerceの問題を修正するには、AC-14985 パッチを適用します。
feature: Configuration
role: Admin, Developer
type: Troubleshooting
exl-id: 98d91421-ebfd-4414-ade3-f25d29541874
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# AC-14985:TLSを使用してSMTP メールを送信する際にエラーが発生する

AC-14985 パッチは、Transport Layer Security （TLS）を使用してSimple Mail Transfer Protocol （SMTP）電子メールを送信する際にエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67がインストールされている場合に利用できます。 パッチ IDはAC-14985です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

TLSが有効になっているSMTP経由でメールを送信すると、エラーが発生します。

<u>複製する手順</u>:

1. SMTP設定を次のように設定します。
* トランスポート：SMTP
* ホスト：url.to.smtp.host
* ポート：587
* SSL: TLS

<u>期待される結果</u>:

電子メールはエラーなく正常に送信されました。

<u>実際の結果</u>:

次のエラーが表示されます。

```text
error:1408F10B:SSL routines:ssl3_get_record:wrong version number [] []
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
