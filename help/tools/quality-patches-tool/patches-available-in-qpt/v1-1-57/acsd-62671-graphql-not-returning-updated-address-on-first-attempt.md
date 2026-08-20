---
title: 'ACSD-62671: [!DNL GraphQL] は、最初の試行で更新されたアドレスを返しません'
description: ACSD-62671 パッチを適用して、 [!DNL GraphQL]  リクエストが最初の試行で最新のアドレス情報を返さないAdobe Commerceの問題を修正します。
feature: GraphQL
role: Admin, Developer
exl-id: afd75ad2-e801-4f8a-b68f-526ca5168413
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-62671: [!DNL GraphQL]が最初の試行で更新されたアドレスを返さない

ACSD-62671 パッチは、[!DNL GraphQL] リクエストが最初の試行で最新のアドレス情報を返さない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-62671です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL GraphQL Application Server]を使用する場合、お客様のアドレス要求は最新のデータを返しません。

<u>複製する手順</u>:

1. [!DNL GraphQL Application Server]をインストールして開始します。
1. `graphQL_query_resolver_result` キャッシュの種類が有効になっていることを確認します。
1. [!DNL GraphQL]を使用して以下を行います：

   * 顧客の構築：
   * トークンを生成します。
   * トークンを使用して、上記のお客様の複数のアドレスを作成します。

1. [!DNL GraphQL] リクエストを送信して、顧客のアドレスを取得します。
1. 顧客に新しい住所を追加します。
1. 応答で返されるアドレス数を監視しながら、Step #4からのリクエストを複数回繰り返します。

<u>期待される結果</u>:

[!DNL GraphQL]件の応答に正しい数の顧客アドレスが含まれています。

<u>実際の結果</u>:

場合によっては、[!DNL GraphQL]応答で誤った数のアドレスが返されることがあります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
