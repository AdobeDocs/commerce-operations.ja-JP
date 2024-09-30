---
title: 「ACSD-46988:GraphQL通貨 API リクエストで null 値が返される」
description: ACSD-46988 パッチは、GraphQL通貨 API リクエストがカスタム通貨に対して null 値を返す問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches） 1.1.21 がインストールされている場合に利用できます。 パッチ ID は ACSD-46988 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。
feature: REST, GraphQL
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-46988:GraphQL通貨 API リクエストで null 値が返される

ACSD-46988 パッチは、GraphQL通貨 API リクエストがカスタム通貨に対して null 値を返す問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.21 がインストールされている場合に使用できます。 パッチ ID は ACSD-46988 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

GraphQL通貨 API リクエストが、カスタム通貨に対して null 値を返します。

<u> 再現手順 </u>:

1. 管理者でカスタム通貨を設定します。 **システム**/**設定**/**一般**/**通貨設定** に移動します。
1. 次のペイロードを持つGraphQL リクエストを送信します。

<pre>
<code class="language-graphql">
{
    currency {
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates {
            currency_to
            rate
        }
    }
}
</code>
</pre>

<u> 期待される結果 </u>:

このリクエストは、null 値ではなく通貨の値を返します。

<u> 実際の結果 </u>:

このリクエストは複数の null 値を返します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：品質パッチツールガイドの [ 品質パッチツール/使用状況 ](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## パッチのインストール後に必要な追加手順

オンプレミス ユーザーの場合：

* 実行：`composer require symfony/intl:"~5.4.11"`

クラウドユーザーの場合：

* 実行：`composer require symfony/intl:"~5.4.11"`
* `composer.json` ファイルと `composer.lock` ファイルをパッチファイルと共に Git リポジトリにプッシュします。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細は、『品質向上パッチ ツール ガイド』の「[[!DNL Quality Patches Tool]：パッチの検索 ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。