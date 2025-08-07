---
title: AC-14985:TLS を使用して SMTP メールを送信する際にエラーが発生する
description: AC-14985 パッチを適用すると、Transport Layer Security （TLS）を使用して Simple Mail Transfer Protocol （SMTP）メールを送信する際にエラーが発生するAdobe Commerceの問題が修正されます。
feature: Configuration
role: Admin, Developer
type: Troubleshooting
source-git-commit: ed50e166c1fd34f5c19066297008cd74f36ccaaa
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# AC-14985:TLS を使用して SMTP メールを送信する際にエラーが発生する

AC-14985 パッチでは、Transport Layer Security （TLS）を使用して Simple Mail Transfer Protocol （SMTP）メールを送信するとエラーが発生する問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 がインストールされている場合に使用できます。 パッチ ID は AC-14985 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

TLS が有効になっている SMTP 経由でメールを送信すると、エラーが発生する。

<u> 再現手順 </u>:

1. 次のように SMTP 設定を行います。
* トランスポート：SMTP
* ホスト：url.to.smtp.host
* ポート：587
* SSL: TLS

<u> 期待される結果 </u>:

メールはエラーなしで正常に送信されました。

<u> 実際の結果 </u>:

次のエラーが表示されます。

```
error:1408F10B:SSL routines:ssl3_get_record:wrong version number [] []
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
