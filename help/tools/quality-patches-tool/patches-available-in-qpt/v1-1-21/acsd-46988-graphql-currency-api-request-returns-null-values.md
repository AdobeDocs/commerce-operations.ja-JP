---
title: 'ACSD-46988: GraphQL currency API リクエストがnull値を返す'
description: ACSD-46988 パッチは、GraphQL currency API リクエストがカスタム通貨のnull値を返す問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.21がインストールされている場合に利用できます。 パッチ IDはACSD-46988です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。
feature: REST, GraphQL
role: Admin
exl-id: 276d2c75-6e7f-4888-b4d2-ac96bea93fc1
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-46988: GraphQL currency API リクエストがnull値を返す

ACSD-46988 パッチは、GraphQL currency API リクエストがカスタム通貨のnull値を返す問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.21がインストールされている場合に利用できます。 パッチ IDはACSD-46988です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

GraphQL currency API リクエストは、カスタム通貨のnull値を返します。

<u>複製する手順</u>:

1. 管理者でカスタム通貨を設定します。 **システム** > **設定** > **一般** > **通貨設定**&#x200B;に移動します。
1. 次のペイロードを含むGraphQL リクエストを送信します。

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

<u>期待される結果</u>:

リクエストは、null値ではなく通貨値を返します。

<u>実際の結果</u>:

リクエストは複数のnull値を返します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：品質パッチツールガイドの「[品質パッチツール/使用状況](/help/tools/quality-patches-tool/usage.md)」。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## パッチのインストール後に必要な追加手順

オンプレミスユーザーの場合：

* 実行：`composer require symfony/intl:"~5.4.11"`

クラウドユーザーの場合：

* 実行：`composer require symfony/intl:"~5.4.11"`
* `composer.json`および`composer.lock`個のファイルをパッチ ファイルと共にGit リポジトリにプッシュします。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、品質パッチツールガイドの「[[!DNL Quality Patches Tool]: パッチを検索](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
