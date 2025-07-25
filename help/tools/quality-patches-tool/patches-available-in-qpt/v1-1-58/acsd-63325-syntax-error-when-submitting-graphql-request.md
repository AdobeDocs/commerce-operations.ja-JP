---
title: ACSD-63325：構文エラー：空のリクエストを送信中に&lt;EOF&gt; エラーが発生  [!DNL GraphQL]  る
description: ACSD-63325 パッチを適用すると、空のリクエストの送信時に構文エラーが発生するAdobe Commerceの問題を修正でき  [!DNL GraphQL]  す。
feature: GraphQL
Role: Admin, Developer
exl-id: a83a8c5f-a43a-4733-a601-7b92656e5325
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# ACSD-63325：空の [!DNL GraphQL] リクエストを送信中に「構文エラー：予期しない &lt; EOF >」エラーが発生する

ACSD-63325 パッチは、空の [!DNL GraphQL] リクエストを送信する際に「構文エラー：予期しない &lt; EOF >」エラーと 200 以外の応答コードが返される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 がインストールされている場合に使用できます。 パッチ ID は ACSD-63325 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

空の [!DNL GraphQL] リクエストを送信すると、200 応答コードではなく HTTP 内部サーバーエラーが発生します。

<u> 再現手順 </u>:

1. 空のGraphQL リクエストを送信

   ```graphql
   curl -i -X OPTIONS http://commerce.local/graphql
   ```

<u> 期待される結果 </u>:

リクエストの応答コードは 200 です。

```
curl -i -X OPTIONS http://commerce.local/graphql
```

<u> 実際の結果 </u>:

次に示すように、500 内部サーバーエラーが発生します。

```
HTTP/1.1 500 Internal Server Error
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)/パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
