---
title: 'ACSD-62671: [!DNL GraphQL]  は、最初の試行時に更新されたアドレスを返しません'
description: ACSD-62671 パッチを適用すると、Adobe Commerceの問題を修正できます。この問題では、ア  [!DNL GraphQL]  リクエストが最初の試行で最新のアドレス情報を返しません。
feature: GraphQL
role: Admin, Developer
exl-id: afd75ad2-e801-4f8a-b68f-526ca5168413
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-62671: [!DNL GraphQL] は、最初の試行時に更新されたアドレスを返しません

ACSD-62671 パッチは、[!DNL GraphQL] リクエストが最初の試行で最新のアドレス情報を返さない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-62671 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL GraphQL Application Server] を使用する場合、顧客アドレスのリクエストで最新のデータが返されない。

<u> 再現手順 </u>:

1. [!DNL GraphQL Application Server] をインストールして起動します。
1. キャッシュタイプ `graphQL_query_resolver_result` 有効になっていることを確認します。
1. [!DNL GraphQL] を使用すると、次のことができます。

   * 顧客を作成します。
   * トークンを生成します。
   * トークンを使用して、上記の顧客用に複数のアドレスを作成します。

1. 顧客 [!DNL GraphQL] アドレスを取得するリクエストを送信します。
1. 新しい住所を顧客に追加します。
1. 応答で返されるアドレス数を監視しながら、ステップ #4 からのリクエストを複数回繰り返します。

<u> 期待される結果 </u>:

応答 [!DNL GraphQL] 正しい数の顧客アドレスが含まれています。

<u> 実際の結果 </u>:

場合によっては、[!DNL GraphQL] 応答で誤ったアドレス数が返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
