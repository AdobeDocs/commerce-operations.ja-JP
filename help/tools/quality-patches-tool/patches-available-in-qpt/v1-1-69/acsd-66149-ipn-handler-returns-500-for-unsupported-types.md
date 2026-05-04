---
title: 'ACSD-66149: IPN ハンドラーが、サポートされていないタイプの場合*500*を返す'
description: ACSD-66149 パッチを適用して、IPN ハンドラーがサポートされていないIPN タイプまたは不明なIPN タイプを無視せず、問題がログに記録されず、プロセスが中断され、500 エラーが返されるAdobe Commerceの問題を修正します。
feature: Payments
role: Admin, Developer
type: Troubleshooting
exl-id: d4794e24-1b6b-4bb5-b54c-9a248fa5f3bd
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-66149: IPN ハンドラーが、サポートされていないタイプの&#x200B;*500*&#x200B;を返します

ACSD-66149 パッチは、IPN （即時支払通知）ハンドラーが、サポートされていないIPN タイプまたは不明なIPN タイプに対して500 エラーを返す問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACSD-66149です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

問題は、サポートされていないIPN タイプまたは不明なIPN タイプに対して、*500* エラーを返すIPN ハンドラーです。 これは、Paypalが一部のフィールドが欠落した状態でIPNを送信する場合に発生します。

<u>複製する手順</u>:

1. PayPalからあらゆる種類の未知のIPN タイプをエミュレートするカスタムモジュールを作成します。
1. 少なくとも1つの商品を作成します。
1. 独自の資格情報でPayPal Expressを設定します。
1. Paypal Expressで注文します。
1. PayPal エミュレーターを実行します。

<u>期待される結果</u>:

アプリケーション IPN ハンドラーは誤ったIPN タイプを無視し、*500*&#x200B;個のエラーを生成しません。

`Order 000000001: Status processing — HTTP 500`

<u>実際の結果</u>:

アプリケーションは、誤ったIPNの処理中に多くの&#x200B;*500* エラーを生成し、想定されるフィールドが存在しない場合、一部の注文を散発的に処理しません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」ガイド

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール
