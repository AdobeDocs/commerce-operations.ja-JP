---
title: 'ACSD-66149: IPN ハンドラーは、サポートされていないタイプの*500*を返します'
description: IPN ハンドラーがサポートされていないタイプや不明なタイプの IPN を無視せず、問題がログに記録されず、プロセスが中断され、500 エラーが返されるAdobe Commerceの問題を、ACSD-66149 パッチを適用して修正してください。
feature: Payments
role: Admin, Developer
type: Troubleshooting
exl-id: d4794e24-1b6b-4bb5-b54c-9a248fa5f3bd
source-git-commit: cf0f5992c7b2a51b270a4a1a81fd50305a92759c
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-66149: IPN ハンドラーは、サポートされていない型に対して *500* を返します

ACSD-66149 パッチは、サポートされていない IPN タイプや不明な IPN タイプに対して IPN （Instant Payment Notification）ハンドラが 500 エラーを返す問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACSD-66149 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

問題は、IPN ハンドラが、サポートされていない IPN タイプまたは不明な IPN タイプに対して *500* エラーを返すことです。 この問題は、Paypal が一部のフィールドが欠落した状態で IPN を送信した場合に発生します。

<u> 再現手順 </u>:

1. PayPal からのあらゆる種類の不明な IPN タイプをエミュレートするカスタムモジュールを作成します。
1. 1 つ以上の製品を作成します。
1. 独自の認証情報で PayPal Express を設定します。
1. Paypal Express で注文します。
1. PayPal エミュレーターを実行します。

<u> 期待される結果 </u>:

アプリケーション IPN ハンドラは、間違った IPN タイプを無視し、*500* エラーを生成しません。

```Order 000000001: Status processing — HTTP 500```

<u> 実際の結果 </u>:

アプリケーションは、誤った IPN の処理中に多くの *500* エラーを生成し、期待されるフィールドがない場合、一部の注文を処理しないことがあります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドの
* クラウドインフラストラクチャー上のAdobe Commerce:[ アップグレードとパッチ適用 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) クラウドインフラストラクチャー上のCommerce ガイド

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]：品質向上パッチを適用するためのセルフサービス ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) ツール（『ツールガイド』）
